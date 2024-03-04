# Diagram of User Actions (activity diagram): Purchaser

This diagram models expected user action sequences with the system.  Actions that can be done in any order are grouped together without links.

This user is:
*Purchaser*

For each user action, ask:  
1. How will the user do this?  
2. How could this go really well, and how likely is this?  
3. How could this go wrong, and how likely is this?  
4. Are there requirements or constraints related to this action, and should there be?
5. What happens if the order of actions changes?
6. Are any actions missing?  Extra?


```mermaid

---
title: VxScan User Actions Diagram - Purchaser
---

flowchart TB

    subgraph a[" "]
        a1["Order, pay for system"]
        a2["Get peripherals"]
        a3["Learn about system"]
        a4["Communicate with seller"]
    end

    subgraph b[" "]
        b1["Wait for system"]
        b2["Plan receipt of shipment"]
    end

    a --> b

    subgraph c[" "]
        c1["Identify package"]
        c2["Store package"]
        c3["Move package"]
        c4["Receive package"]
    end

    b --> c

    subgraph d[" "]
        d1["Unpack system"]
        d2["Dispose of packaging"]
        d1 --> d2
    end

    c --> d

    subgraph e[" "]
        e1["Store, stack system"]
        e2["Move system"]
        e3["Learn how to use system"]
        e4["Train on system with one"]
        e5["Test system"]
        e6["Demo system"]
    end

    d --> e

    subgraph f[" "]
        f1["Organize space for systems"]
        f2["Train on system without one"]
        f3["Communicate to community"]
        f4["Plan for end-of-life"]
    end

    g["Handoff to election workers"]
    h["Take from election workers"]
    i["Dispose of system"]

    h --> e
    e --> g --> h 
    h --> i
    f --> i

    a & b & c & d & e --> f

    %% style key actions
    classDef highlight color:red;
    class a3,a4,g highlight;

```