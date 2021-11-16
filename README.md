# Dominance Fault Collapsing and Parallel Fault Simulation and Deductive Fault Simulation
This project is based on Digital VLSI Testing and Testability. The netlist and input_vector is given as input, the code performs Dominance fault collapsing, Parallel fault simulation, Deductive fault simulation.


# Prerequisite for this project
1) Create a netlist by naming all wires with numbers (increasing order 1,2,3,.....), starting from input to output. example is shown below
2) Save the netlist in .txt format and edit netlist file name in code. (Don't give extra spacing at end of netlist).
3) install plotly Python library. This Python library is used to tabulate simulation result.     ```pip install plotly``` 
4) Change input vectors as needed, numbering of input vector is from increasing order of inputs of the circuit. This input vector is used for both Parallel fault simulation and Dominace fault simulation.

# Example (4:1 MUX netlist is used for simulation)
```
NAND 5 3 4
AND 14 6 7
AND 15 8 9
AND 16 10 11
AND 17 12 13
OR 21 14 15
OR 23 16 17
NAND 24 19 20
AND 25 21 24
AND 26 22 23
OR 27 25 26
INPUT 1 7 9 11 13 18
OUTPUT 27
FANOUT 1 2 8 12
FANOUT 2 3 4
FANOUT 5 6 10
FANOUT 18 19 20 22
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

The code takes input_vector as input and perform parallel fault simulation and tabulate the simulated output and calculate fault coverage for corresponding input vector.

![pf2](https://user-images.githubusercontent.com/63975346/141890694-709cc906-b26e-4c53-99a7-d1864a58f6b1.png)

![pfsr](https://user-images.githubusercontent.com/63975346/141890717-ec6a1146-62aa-4962-af8f-23d74d54fcd2.png)


# Deductive Fault Simulation
Use gate level model with zero or unit delay and two level signal.
This is One-pass simulation, where each line k contains a list Lk of faults detectable on it. Considering true-value simulation of each vector, fault lists of all gate output lines are updated using set-theoretic rules, signal values, and gate. 

![drf](https://user-images.githubusercontent.com/63975346/141422620-380c164a-6cbf-4613-8a6d-d461e03114b1.png)

![df](https://user-images.githubusercontent.com/63975346/141422010-d60948d9-755b-49d2-ae14-d02ae49c4f0f.PNG)



The code takes input_vector as input and perform deductive fault simulation and tabulate the propagated faults at output node and calculate fault coverage for corresponding input vector.


# Limitations of Code
1) Netlist need to be numbered in ascending order from input to output.
2) The circuit will may/may not work if feedback is given.
3) Works only for AND,OR,NAND,NOR gates. The not gate should be modeled as NAND inverter / NOR inverter.
4) Can't run netlist with more than 2 input gates.

# Acknowledgement
Dr. Rathnamala Rao, Assistant Professor, NITK Surathkal

# THANK YOU
