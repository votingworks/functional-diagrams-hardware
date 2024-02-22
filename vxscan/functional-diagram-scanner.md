# Functional diagram: System-level (physical hardware only)

The functions in this diagram correspond roughly with a separate list of functions (and failure modes) that we should prepare for in our designs. Finally, these functions correspond to our Engineering Design Requirements, which in turn correspond with 
the Voluntary Voting System Guidelines (VVSG 2.0).

<!-- Nodes in this Mermaid.js diagram are named according to important functions, inputs, and outputs in this system.
f = function
i = input
o = output 
s = another system outside the scanner
The numbers in the node name correspond with the VotingWorks dFMEA document as of February 2024.
Each block of nodes and connections represent roughly a functional chain for one type of major input and output.
-->

```mermaid

---
title: Functional Diagram of VxScan Precinct Scanner Hardware
---

flowchart TB

    i1.00("ballot 
        (all types)")
    f1.00["Accept ballot"]
    f1.01["Align and direct ballot"]
    f3.00["Scan ballot"]
    f2.01["Redirect accepted ballot"]
    f2.02["Release accepted ballot"]
    o2.02("accepted ballot")
    s1["Receive accepted ballot 
        into ballot receptacle"]
    i1.00 ==> f1.00 ==> f1.01 ==> f3.00 ==> f2.01 ==> f2.02 ==> o2.02 ==> s1
    o1.00("indicator of where
        to insert ballot")
    f1.00 -.-> o1.00
    i1.01("gravity")
    i1.01 --> f1.01
    i2.02("gravity")
    i2.02 --> f2.02

    f2.03["Redirect rejected ballot"]
    f2.04["Hold rejected ballot"]
    f2.05["Release rejected ballot 
        back to user"]
    o2.05("rejected ballot")
    f3.00 ==> f2.03 ==> f2.04 ==> f2.05 ==> o2.05
    i2.04("gravity")
    i2.04 --> f2.04
    o2.04("indicator of where
        to get rejected ballot")
    f2.04 -.-> o2.04

    %% styling
    classDef ioMaterials font-size:10pt,stroke-width:0px,fill-opacity:0,color:blue;
    classDef ioEnergy font-size:10pt,stroke-width:0px,fill-opacity:0,color:red;
    classDef ioInformation font-size:10pt,stroke-width:0px,fill-opacity:0,color:green;    
    classDef system font-size:14pt,stroke-width:2px;
    class i1.00,o2.02,o2.05 ioMaterials;
    class i1.01,i2.02,i2.04 ioEnergy;
    class o1.00,o2.04 ioInformation;
    class s1 system;

```