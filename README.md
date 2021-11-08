# Fault-collapsing-and-Fault-simulation
This project is based on Digital VLSI Testing and Testability. The netlist is given as input, the code performs Dominance fault collapsing, Parallel fault simulation, Deductive fault simulation.


# Prerequisite for this project
1) Create a netlist by naming all wires with numbers (increasing order 1,2,3,.....), starting from input to output.
2) Save the netlist in .txt format and edit netlist file name in code. (Don't give extra spacing at end of netlist).
3) install plotly Python library. This Python library is used to tabulate simulation result.     ```pip install plotly``` 
4) Change input vectors as needed, numbering of input vector is from increasing order of inputs of the circuit. This input vector is used for both Parallel fault simulation and Dominace fault simulation.

# Example (netlist used by me for simulation)
```
NAND 5 2 3
AND 13 6 7
AND 14 8 9
AND 15 10 11
AND 16 4 12
OR 20 13 14
OR 22 15 16
NAND 23 18 19
AND 24 20 23
AND 25 21 22
OR 26 24 25
INPUT 1 7 9 11 12 17
OUTPUT 26
FANOUT 17 18 19 21
FANOUT 5 6 10
FANOUT 1 2 3 8 4 
```

