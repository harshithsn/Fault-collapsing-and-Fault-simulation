# Dominance Fault Collapsing and Parallel Fault Simulation and Deductive Fault Simulation
This project is based on Digital VLSI Testing and Testability. The netlist and input_vector is given as input, the code performs Dominance fault collapsing, Parallel fault simulation, Deductive fault simulation.


# Prerequisite for this project
1) Create a netlist by naming all wires with numbers (increasing order 1,2,3,.....), starting from input to output. example is shown below
2) Save the netlist in .txt format and edit netlist file name in code. (Don't give extra spacing at end of netlist).
3) install plotly Python library. This Python library is used to tabulate simulation result.     ```pip install plotly``` 
4) Change input vectors as needed, numbering of input vector is from increasing order of inputs of the circuit. This input vector is used for both Parallel fault simulation and Dominace fault simulation.

# Example (4:1 MUX netlist is used for simulation)
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

![mux-01](https://user-images.githubusercontent.com/63975346/140762141-6ed6b118-ce2d-4609-ae6a-2e8b598c3c0f.png)



The code contain many variable and functions which are used in fault collapsing and fault simulation. Each cell in code contain description of variabels and function. 



# Dominance Fault Collapsing
Fault F2 is said to dominate the fault F1 if all tests of fault F1 detect another fault F2. If fault F2 dominates F1, then F2 is removed from the fault list.
To collapse faults of a gate, all faults from the output can be eliminated retaining one type of fault on each input and the other type on any one of the inputs. The collapsing rules are different for different gates (AND,OR,NAND,NOR).
Collapse ratio is better.

The code first initializes fault at each node. 
```sa0_5``` this implies that ```stuck at 0 at node 5```.

Consider fault is present at each node. Then traverse throuth output of circuit to input of circuit and Collapse fault considering rules for dominance fault collapsing.


![DominanceFault-01](https://user-images.githubusercontent.com/63975346/140766293-fb370220-e5e5-49a5-9b39-3263b9ac1809.png)


# Parallel Fault Simulation
Parallel fault simulation most effective, Circuit consists of only logic gates where all gates are assumed to have the same delay. Simulate stuck-at fault using bit-parallelism of logical operations in a digital computer.

The code takes input_vector as input and perform parallel fault simulation and tabulate the simulated output.


# Deductive Fault Simulation
Use gate level model with zero or unit delay and two level signal.
This is One-pass simulation, where each line k contains a list Lk of faults detectable on it. Considering true-value simulation of each vector, fault lists of all gate output lines are updated using set-theoretic rules, signal values, and gate.


# Limitations of Code
1) Netlist need to be numbered in ascending order from input to output.
2) The circuit will may/may not work if feedback is given.
3) Works only for AND,OR,NAND,NOR gates. The not gate should be modeled as NAND inverter / NOR inverter



# THANK YOU
