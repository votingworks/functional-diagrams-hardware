# VxScan 4.0 Black box diagram 
*Hardware only*

```mermaid

---
title: VxScan Black Box Diagram Hardware Inputs and Outputs
---
%%{init: {"flowchart": {"htmlLabels": false}} }%%

flowchart LR

    system["VxScan 
        precinct 
        scanner"]
    classDef box font-size:32pt,stroke-width:5px,text-align:center;
    class system box;

    subgraph inputMaterial["Material Inputs"]
        inputMaterialsList["ballots
            thermal paper
            USBs
            smart cards
            security seals 
            (ties & labels)
            human hands, 
            fingers, clothes
            cleaning materials
            atmosphere
            transport materials
            power plug (from wall or UPS)
            power cable (for internal storage)
            dirt/dust
            ballot receptacle interfaces
            tools"]
    end

    subgraph inputEnergy["Energy Inputs"]
        inputEnergyList["gravity and weight
            human forces
            impact forces
            electrical power
            electrostatic discharge (ESD)
            electromagnetic (EM) fields
            radiofrequency (RF) signals
            heat
            light
            vibrations"]
    end

    subgraph inputInformation["Information Inputs"]
        inputInformationList["election definitions
            election manager inputs
            maintenance worker and SysAdmin inputs
            pollworker inputs
            voter inputs"]
    end

    inputMaterial ==> system
    inputEnergy --> system
    inputInformation -.-> system

    subgraph outputMaterial["Material Outputs"]
        outputMaterialList["ballots
        thermal paper
        USBs
        smart cards
        security seals (ties & labels)
        human hands, fingers, clothes
        cleaning materials
        atmosphere
        transport materials
        power plug (from wall or UPS)
        power cable (for internal storage)
        dirt/dust
        ballot receptacle interfaces
        tools"]
    end

    subgraph outputEnergy["Energy Outputs"]
        outputEnergyList["physical reaction forces
            vibrations
            electrostatic discharge (ESD)
            electromagnetic (EM) fields
            radiofrequency (RF) signals
            noise, sound
            heat
            light"]
    end

    subgraph outputInformation["Information Outputs"]
        outputInformationList["voting data
            visual feedback
            audio feedback
            security statuses
            machine IDs
            indicators of how to use system features"]
    end

    system==>outputMaterial
    system-->outputEnergy
    system-.->outputInformation


    style inputMaterial stroke-width:0px,fill:#;
    classDef longList text-align:left;
    class inputMaterialsList,inputEnergyList,inputInformationList longList;

```
