# Functional Diagrams: Hardware

## About

These diagrams represent how different VotingWorks systems function.  They are meant to document systems in a variety of contexts, including:

* The abstract functions or behaviors of systems, ignoring specific parts
* User actions (or activities or behaviors), when they are using a system
* Ideas for design and redesign
* Final designs
* Helping identify failure modes

## Diagrams

### VxScan 4.0 

*Functional models*
* [Black box diagram (scanner hardware only): inputs and outputs](./vxscan/black-box-scanner.md)
* [Functional Diagram of Scanner and Ballot Receptacle System](./vxscan/system-diagram-hardware.md)
* [Functional Diagram of Scanner and Ballot Receptacle System, Focusing on Inputs and Outputs](./vxscan/system-diagram-hardware-io.md)
* Functional model: System-level (physical hardware only)

*User Actions*
* Assembler
* Transporter
* Purchaser
* Election Administrator
* Poll Worker
* Voter (general)


## Making, Using, and Sharing Diagrams

These are coded with [Mermaid.js](https://mermaid.js.org/).  Some notes on using this to make/edit/share diagrams:
* GitHub may not support the latest Mermaid.js syntax.  TO be safe, use quotes-notation for labeling nodes and connections, e.g. `A["my label"]-->|"connector label"|["another one"]` 
* You can use [Mermaid Live Editor](https://mermaid.live/) to view and export the charts if they don't show on GitHub.


## License

GPLv3