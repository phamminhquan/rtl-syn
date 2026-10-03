# About
This repository is a RTL logic synthesis tool written in Golang that translate
Verilog (or SystemVerilog) into a gate-level netlist. The scope for this is to
build a Minimum Viable Produc (MVP) that can do the following:
* Parse a Verilog file (or multiple files) and turn it into a structure that
can be processed effectively in Golang.
* Elaborate the design structure into a data structure that can be optimized.
* Optimize the design.
* Map optimized design into a few custom primitive gates (AND and XOR).
* Generate the final netlist from the optimized and mapped design.
