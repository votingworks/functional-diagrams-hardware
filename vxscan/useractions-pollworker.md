# Diagram of User Actions (activity diagram): Poll Worker

This diagram models expected user action sequences with the system.  Actions that can be done in any order are grouped together without links.

This user is:
*Poll Worker*

For each user action, ask:  
1. How will the user do this?  
2. How could this go really well, and how likely is this?  
3. How could this go wrong, and how likely is this?  
4. Are there requirements or constraints related to this action, and should there be?
5. What happens if the order of actions changes?
6. Are any actions missing?  Extra?


```mermaid

---
title: VxScan User Actions Diagram - Poll Worker
---

flowchart TD

    subgraph a[" "]
        a1["Receive scanner"]
        a2["Receive ballot receptacle"]
        a3["Receive UPS"]
        a4["Receive VxAdmin"]
        a5["Get smartcards"]
        a6["Get peripherals, cords, etc."]
        a7["Get USBs"]
    end

    subgraph b[" "]
        b1["Identify systems"]
        b2["Organize placement of all things"]
        b3["Move, lift, distribute parts"]
        b4["Take from storage, packaging"]
    end

    subgraph c[" "]
        c1["Inspect, test parts"]
        c2["Clean parts"]
        c3["Explain how to use system"]
        c4["Monitor system status"]
        c5["Move system"]
    end

    a --> b & c
    b <--> c

    subgraph d[" "]
        d1["Set up ballot box"]
        d2["Position ballot box "]
        d3["Place scanner on ballot box"]
        d4["Reposition ballot box"]
        d5["Lock/ unlock ballot box"]
        d6["Open/close ballot box"]
    end

    b --> d
    d <--> c

    subgraph e[" "]
        e1["Place scanner on ballot box"]
        e2["Secure system, apply seals"]
        e3["Plug in power, UPS"]
        e4["Open scanner case"]
    end

    d --> e
    e <--> c

    subgraph f[" "]
        f1["Look at screen"]
        f2["Press on screen"]
        f3["Listen to alerts"]
        f4["Handoff system to voter"]
        f5["Insert ballot"]
        f6["Remove ballot from infeed"]
    end

    subgraph g[" "]
        g1["Open access door"]
        g2["Insert, remove USBs"]
        g3["Insert, remove smartcards"]
        g4["Open/close scanner"]
        g5["Insert, remove thermal paper"]
        g6["Clean exposed parts"]
        g7["Remove jammed ballots"]
        g8["Close access door"]
    end

    e --> f & g
    f <--> g
    f & g <--> c

    subgraph h[" "]
        h1["Unplug scanner, store plug"]
        h2["Close scanner case"]
        f3["Detach scanner from box"]
        f4["Empty, collapse ballot box"]
        f5["Clear jams in ballot box"]
        f6["Break security seals"]
    end

    f & g --> h
    h <--> c

    subgraph i[" "]
        i1["Identify systems"]
        i2["Pack parts"]
        i3["Store, stack parts"]
        i4["Move, lift, distribute parts"]
    end

    h --> i

    j["Handoff to election administrator"]
    k["Handoff to transporters"]

    i --> a
    i --> j & k


    %% style key actions
    classDef highlight color:red;
    class a1,a2,a3,a4,a5,a6,a7,j,k highlight;
    style test fill:none,stroke-width:0;

```