# Diagram of User Actions (activity diagram): Transporter

This diagram models expected user action sequences with the system.  Actions that can be done in any order are grouped together without links.

This user is:
*Transporter*

For each user action, ask:  
1. How will the user do this?  
2. How could this go really well, and how likely is this?  
3. How could this go wrong, and how likely is this?  
4. Are there requirements or constraints related to this action, and should there be?
5. What happens if the order of actions changes?
6. Are any actions missing?  Extra?


```mermaid

---
title: VxScan User Actions Diagram - Transporter
---

flowchart TB

    subgraph a[" "]
        a1["Communicate with assemblers"]
        a2["Receive payment"]
        a3["Receive shipment"]
        a4["Measure, weigh shipment"]
        a5["Pack, box shipment"]
        a6["Label shipment"]
    end

    subgraph b[" "]
        b1["Lift shipment"]
        b2["Stack shipment"]
        b3["Store shipment"]
        b4["Push, pull, slide, rotate shipment"]
        b5["Track, scan shipment"]
        b6["Drive shipment"]
        b6["Fly shipment"]
        b7["Sort, organize shipment"]
        b8["Secure shipment"]
    end

    a --> b

    subgraph c[" "]
        c1["Deliver shipment"]
        c2["Communicate with recipient"]
        c3["Place shipment in container"]
    end
    
    b --> c

    subgraph d["Undesired actions"]
        d1["Drop, throw shipment"]
        d2["Expose shipment to elements"]
        d3["Open shipment"]
        d4["Repackage shipment"]
        d5["Find lost shipment"]
        d6["Flip, shake shipment"]
    end

    a & b & c <-.-> d

    e["Handoff to Purchaser"]

    d -.-> e
    c --> e


    %% style key actions
    classDef highlight color:red;
    class a3,e highlight;

```