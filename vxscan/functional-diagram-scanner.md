# Functional diagram: System-level (physical hardware only, all details)

The functions in this diagram correspond roughly with a separate list of functions (and failure modes) that we should prepare for in our designs. Finally, these functions correspond to our Engineering Design Requirements, which in turn correspond with 
the Voluntary Voting System Guidelines (VVSG 2.0).

<!-- Nodes in this Mermaid.js diagram are named according to important functions, inputs, and outputs in this system.
f = function
i = input
o = output 
s = function from another system outside the scanner
The numbers in the node name correspond with the VotingWorks dFMEA document as of February 2024.
Each block of nodes and connections represent roughly a functional chain for one type of major input and output.
-->

```mermaid

---
title: Functional Diagram of VxScan Precinct Scanner Hardware
---

flowchart TB

    %% function chain: accepted ballots 
    i1.00("ballot 
        (all types)")
    f1.00["Accept ballot"]
    f1.01["Align and direct ballot"]
    f1.02["Detect ballot presence
        before scanning"]
    f3.00["Scan ballot"]
    f2.01["Redirect accepted ballot"]
    f2.02["Release accepted ballot"]
    o2.02("accepted ballot")
    s1{{"Receive accepted ballot 
        into Ballot Receptacle"}}
    i1.00 ==> f1.00 ===> f1.01 ===> f1.02 ==> f3.00 ==> f2.01 ==> f2.02 ==> o2.02 ==> s1
    f1.00 -.-> o1.00("indicator of where
        to insert ballot")
    i1.01("gravity") --> f1.01
    i2.02("gravity") --> f2.02
    f3.00 --> o3.00a("noise, vibration, heat,
        ESD, RF, EMI")
    f3.00 ==> o3.00b("paper dust")

    %% function chain: rejected ballots
    f2.03["Redirect rejected ballot"]
    f2.04["Hold rejected ballot"]
    f2.05["Release rejected ballot 
        back to user"]
    o2.05("rejected ballot")
    f3.00 ===> f2.03 ==> f2.04 ==> f2.05 ==> o2.05
    i2.04("gravity") --> f2.04
    f2.04 -.-> o2.04("indicator of where
        to get rejected ballot")

    %% function chain: jammed ballots
    f2.06["Detect jammed ballot"]
    f2.07["Hold jammed ballot"]
    f2.08["Expose jammed ballot 
        for removal"]
    f2.09["Release jammed ballot"]
    o2.09("jammed ballot")
    f3.00 ==> f2.06 ==> f2.07 ===> f2.08 ==> f2.09 ==> o2.09
    i2.07("gravity") --> f2.07
    f2.07 -.-> o2.07("indicator of where
        to get jammed ballot")
    i2.08b("hand") <==> f2.08
    i2.08a("human forces") --> f2.08
    i2.09b("hand") <==> f2.09
    i2.09a("human forces") --> f2.09

    %% function chain: electrical power
    s2{{"Transmit stable
        electrical power from
        Universal Power Supply 
        (UPS)"}}
    i22.01("electrical power")
    f22.01["Accept electrical 
        power"]
    s2 --> i22.01 --> f22.01

    i22.02("power cable plug")
    f22.02["Accept power 
        cable plug"]
    s2 <==> i22.02 ===> f22.02 ==> f22.01
    f22.05["Release power 
        cable plug"]
    f22.02 ==> f22.05 ==> i22.02
    i22.02b("hand") <==> f22.02
    i22.02a("human pushing 
        force") --> f22.02
    i22.05b("hand") <==> f22.05
    i22.05a("human pulling 
        force") --> f22.05

    f22.03["Transmit and protect
        electrical power"]
    f22.03 --> o22.03("RF, EMI")
    f22.04["Control electrical 
        system (CPU)"]
    f22.04 --> o22.04("heat, RF, EMI")
    f22.01 --> f22.03 --> f22.04 & f1.02 & f3.00 
    f6.01["Display and direct 
        visual information"]
    f6.02["Synchronize visual 
        and audio information"]
    f6.03["Play and direct
        audio information"]
    f6.02 -.-> f6.01 & f6.03
    f22.04 --> f6.01 & f6.02 & f6.03
    f6.01 -.-> o6.01("screen output")
    f6.03 -.-> o6.03("audio output")


    %% selected key information flows to/from CPU (not all of them)
    f22.04 <-.-> f3.00

    %% styling
    classDef ioMaterials font-size:10pt,stroke-width:0px,fill-opacity:0,text-align:center,color:blue;
    classDef ioEnergy font-size:10pt,stroke-width:0px,fill-opacity:0,text-align:center,color:red;
    classDef ioInformation font-size:10pt,stroke-width:0px,fill-opacity:0,text-align:center,color:green;    
    classDef system font-size:14pt,stroke-width:3px,text-align:center;
    class i1.00,o2.02,o2.05,o2.09,i2.08b,i2.09b,i22.02,o3.00b,i22.02a,i22.05a ioMaterials;
    class i1.01,i2.02,i2.04,i2.07,i2.08a,i2.09a,i22.01,o3.00a,o22.03,o22.04,i22.02b,i22.05b ioEnergy;
    class o1.00,o2.04,o2.07,o6.01,o6.03 ioInformation;
    class s1,s2 system;

```