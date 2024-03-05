# Diagram of User Actions (activity diagram): Voter

This diagram models expected user action sequences with the system.  Actions that can be done in any order are grouped together without links.

This user is:
*Voter*

For each user action, ask:  
1. How will the user do this?  
2. How could this go really well, and how likely is this?  
3. How could this go wrong, and how likely is this?  
4. Are there requirements or constraints related to this action, and should there be?
5. What happens if the order of actions changes?
6. Are any actions missing?  Extra?


```mermaid

---
title: VxScan User Actions Diagram - Voter
---

flowchart LR


    subgraph main[" "]
        direction BT
        subgraph test[" "]
            a["Go near scanner"]
            b["Recognize ballot infeed"]
            a --> b
            c["Place ballot in infeed"]
            b --> c
            d["Wait for result"]
            c --> d

            subgraph e[" "]
                e1["Hear alert"]
                e2["See screen information"]
            end
            d --> e

            f["Recognize ballot acceptance"]
            g["Recognize ballot rejection"]
            h["Recognize ballot jam"]
            e --> f & g & h

            i["Go away from scanner"]
            f --> i

            j["Remove ballot from infeed"]
            k["Prepare ballot for acceptance"]
            g --> j --> k

            l["Ask for help"]
            m["Wait for jam to clear"]
            n["Give ballot to worker for emergency ballot storage"]
            h --> l --> m --> k --> n
            n --> i
        end

        k --> c
    end

    o["Get help"]
    style o stroke-dasharray: 5 5;
    main <-.-> o

    %% style key actions
    classDef highlight color:red;
    class a,c,i highlight;
    style test fill:none,stroke-width:0;
    style main fill:none,stroke-width:2;

```