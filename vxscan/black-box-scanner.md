# VxScan 4.0 Black box diagram 
*Hardware only*

```mermaid

---
title: VxScan Black Box Diagram Hardware Inputs and Outputs
---

graph LR

    system["VxScan 
        precinct scanner"]

    input-material[Material Inputs]

    input-energy[Energy Inputs]

    input-information[Information Inputs]

    input-material-->system
    input-energy-->system
    input-information-->system

    output-material[Material Outputs]

    output-energy[Energy Outputs]

    output-information[Information Outputs]

    system-->output-material
    system-->output-energy
    system-->output-information

```