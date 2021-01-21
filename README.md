# Digital Combinational Lock #
 ## Objective: ##
A Digital Combinational Lock is to be designed using MAGIC layout tool. The key would be a 3 digit number. The key will be preset. We will have to give 3 values in sequence. If the values match the key, the lock will be opened. If there is any error, the clock must be reset. The system has these inputs: the values, new, start. The output is whether the lock is closed or open.The NEW must be made high when we enter a new value. The output becomes high when the lock is opened.
## Block Diagram: ##
![Block Diagram](https://github.com/SameerSDurgoji/VLSIdesign/blob/main/Block%20diagram.jpg)
## Description: ##
The designed system has a controller block, a multiplexer and a comparator. In the design, the decimal to binary converter is not included, hence the input values must be given in binary system. The key will be in the format P0 P1 P2. The controller consists of a finite state machine. The inputs to this block are new, start, and the equal signal from the comparator. The clock is fed to this block. The designed FSM is a Moore machine. The FSM starts when the start signal goes high. If the entered new value and the key match, the state of the FSM will be updated. If they are not equal, the FSM will be reset. The output of the controller block is the mux control and the status of the lock. The mux control consists 3 bits. Each bit represents the digit of the key which is to be compared. 

They are as follows: 
* 001: The entered digit is the first digit and is to be compared with the first digit of the key P0. 
* 010: The entered digit is the second digit and will be compared with the second digit of the key P1. 
* 100: The entered digit is the third digit and is to be compared with the third digit of the key P2.

A fourth bit (MSB) is added to these three bits fed to the multiplexer to represent the status of the lock. The overall states of the FSM are as follows: 
* 0000: Closed, FSM not started. 
* 0001 (S0): Closed, first digit being compared. 
* 0010 (S1): Closed, second digit being compared. 
* 0100 (S2): Closed, third digit being compared. 
* 1000 (S3): Lock Open! 

The FSM is designed with 5 states. The states of FSM represent the digit of the key that is to be compared and whether the lock is open or closed. The state diagram of the FSM is as shown below:
