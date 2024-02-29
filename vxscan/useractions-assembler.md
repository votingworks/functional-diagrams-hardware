# Diagram of User Actions (activity diagram): Assembler

This diagram models expected user action sequences with the system.  Actions that can be done in any order are grouped together without links.

This user is:
*Assembler*

For each user action, ask:  
1. How will the user do this?  
2. How could this go really well, and how likely is this?  
3. How could this go wrong, and how likely is this?  
4. Are there requirements or constraints related to this action, and should there be?
5. What happens if the order of actions changes?
6. Are any actions missing?  Extra?


```mermaid

---
title: VxScan User Actions Diagram - Assemblers
---

flowchart TB

    subgraph a[" "]
        a1["Read assembly instructions"]
        a2["Gather parts"]
        a3["Count parts"]
        a4["Organize parts"]
    end

    subgraph b[" "]
        b1["Gather tools"]
        b2["Organize tools"]
    end

    a <--> b

    subgraph c[" "]
        c1["Inspect, test parts"]
        c2["Measure, cut parts"]
        c3["Clean, desticker parts"]
    end

    a & b --> c

    subgraph d[" "]
        d1["Lift parts"]
        d2["Align, rotate parts"]
        d3["Place parts"]
        d4["Secure parts"]
    end

    c --> d

    subgraph e[" "]
        e1["Inspect assemblies"]
        e2["Clean assemblies"]
    end

    d --> e

    subgraph f[" "]
        f1["Lift assemblies"]
        f2["Align assemblies"]
        f3["Place assemblies"]
        f4["Secure assemblies"]
    end

    d & e --> f

    subgraph g[" "]
        g1["Inspect system"]
        g2["Clean system"]
    end

    f --> g

    subgraph h[" "]
        h1["Move, lift system"]
        h2["QA system"]
        h3["Document, photograph system"]
        h4["Apply labels"]
        h5["Apply security seals"]
    end

    f & g --> h

    subgraph i[" "]
        i1["Package system"]
        i2["Move, lift system"]
        i3["Store, stack system"]
        i4["Transport system"]
        i5["Label package"]
        i6["Communicate with shippers"]
        i7["Pay for shipping"]
    end

    h --> i

    j["Handoff to Transporter"]

    i --> j

    %% style key actions
    classDef highlight color:red;
    class a2,j highlight;

```