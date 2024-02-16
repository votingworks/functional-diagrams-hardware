# VxScan 4.0 Functional Diagram of Scanner and Ballot Receptacle System, Focusing on Inputs and Outputs, Functional I/O Only

```mermaid

---
title: VxScan Functional Diagram of Scanner and Ballot Receptacle System
---

flowchart LR

    scanner["VxScan: 
        Ballot Scanner"]
    ballotReceptacle["Ballot 
        receptacle"]
    ups["UPS"]

    inputsMaterialScanner["ballots, thermal paper, 
        USBs, smart cards, 
        security seals, power plug, 
        power cable, tools"]
    inputsMaterialScanner ==> scanner

    outputsMaterialScanner["invalid ballots, 
        thermal paper, 
        USBs, smart cards, 
        security seals, 
        power cable"]
    scanner ==> outputsMaterialScanner

    outputsInformationScanner["digital visual feedback,
        digital audio feedback,
        security statuses, machine IDs"]
    scanner -.-> outputsInformationScanner

    scanner ===> |"valid scanned ballots"|ballotReceptacle

    inputsMaterialsBallotReceptacle["security seals, keys"]
    inputsMaterialsBallotReceptacle ==> ballotReceptacle

    outputsMaterialsBallotReceptacle["scanned ballots, 
        security seals, keys"]
    ballotReceptacle ==> outputsMaterialsBallotReceptacle

    outputsInformationBallotReceptacle["system information, 
        security statuses"]
    ballotReceptacle -.-> outputsInformationBallotReceptacle

    ups --> |"electrical power, plug"|scanner

    outputsInformationUps["UPS statuses"]
    ups -.-> outputsInformationUps

    inputsEnergyUps["electrical power,
        plug from mains"]
    inputsEnergyUps --> ups

    classDef io font-size:10pt,stroke-width:0px,fill-opacity:0;
    class inputsEnergyCommon,inputsMaterialScanner,inputsEnergyCommon,outputsMaterialScanner,outputsMaterialsCommon,outputsEnergyCommon,inputsMaterialsBallotReceptacle,outputsInformationScanner,outputsMaterialsBallotReceptacle,outputsInformationBallotReceptacle,inputsEnergyBallotReceptacle,inputsMaterialsCommon,outputsInformationUps,inputsEnergyUps,inputsMaterialsUps io;

```
