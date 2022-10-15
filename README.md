# QC_Mentorship_Task1
Creating Quantum Circuit for Integer Multiplication 
The work also can be seen from here (GoogleDocs)[https://docs.google.com/document/d/1AGYOtXuWy6AGSZnMSDDcjJylRU1vtpDijRHKxpIY6mk/edit?usp=sharing]

## Background
### Quantum Computing
Quantum Computing is an emerging field of study into which many researchers and companies put resources.  
Quantum Computing is a different way of calculation compared to classical computing which is used by this Mac book I'm using to type these words.  In quantum computing, the information is represented by Qubits instead of bits.  
These qubits represent some discrete phenomenon of the nature such as excited states of atoms. The discreteness also applies to classical bits, which use the measurement of voltage as whether the result is higher than a certain value or not.  
The difference is that the information represented by qubits are continuous, and this is realized by the superposition of two quantum states.  The visualization of this is achieved by Bloch Sphere which you can search up online or take a look at my repository (Quantum 3D Game)[https://github.com/Rick0317/Humans-vs-Quantum-Computers---IBM] 
Due to these special properties of quantum computing, we can calculate certain problems way faster than classical computers, which we call Quantum Supremacy.  Algorithm such as Deutsch Algorithm and Deutasch-Jozsa algorithm are proved to be calculated faster by quantum computing than by classical computing.  

### Integer Multiplication
Integer Multiplication can be decomposed into some Integer Additions.

## Algorithm

1, Shift-and-Add algorithm  
This is basically the algorithm we use to do multiplication of two integers in elementary school.  
We have Multiplicand, Multiplier, and Register. We multiply each digit of Multiplier to Multiplicand and store the result in Register.  


## Implementation
When I was implementing the integer multiplication quantum circuit, I did not refer to any past research. I later looked at the past papers and works and knew there exist better solutions. I will present my implementation and the implementation based on the past work  

### My implementation

1, Encoding  
The given integers will be encoded into quantum states using numpy and X_gate.  
Let a, b be the two integers. I encoded a-1 to the first set of registers and encoded b twice in the second and third set of registers.  

2, Quantum Circuit
Now, the quantum states of the registers are prepared with the binary representations of a-1 and b.  
QFT will be applied to the third set of registers (2nd b).  
Next, b will be added to itself based on the binary representation of a-1 using our control gate.  
The control gate adds phase based on b.  
The formula is simple: b + (a-1) * b  
After the addition part ends, inverse QFT will be added to the third set of registers (2nd b).  
This enables us to measure the result.  

3, Disadvantage of this implementation
At this point (10/9), the implementation does not take care of the phase properly, which basically means you do not get the result of multiplication directly. For example, if you do 4 times 5, you will get 4 which is 20 - 8*2 (8 represents one cycle of the phase)  
However, we can estimate the result with certain possibility.  
Let the output of the circuit be p.  
In our case, if b is odd, we claim the result is likely to be (a-1) * 2^{ceil(log2(n))} + p
if b is even, we claim if a < b/2, the result is likely to be (a-1) * 2^{ceil(log2(n))} + p
if z > b/2, the result is likely to be (a-2) * 2^{ceil(log2(n))} + p

### Based on the past implementations
Based on the past paper, I implemented the circuit with QFT, controlled rotation gates, and inverse QFT.  
The circuit has 2*(n_1 + n_2) number of qubits.

Problems I faced:
(1)How do we prepare the states |a> and |0> (How many registers I need, Should I implement in the superposition states)  
(2)How do we prepare the controlled rotation gate  

Solution to (1):  
For |a>, I prepared the state with binary representation of a. 
For |0>, I prepared the state with qubits1 + qubits2 number of registers

Solution to (2):  
The difficulty is how to add a to the superposition state which has different number of registers.
My solution: rot_gate.cp(2・np.pi/2・・(qubits1 + qubits2-control -i-qubit), qubits2-1-control, qubits1+2*qubits2-1-qubit-i)
did not work. 
I tried many ways to implement the rotation gates but none of them works

### Implementation that works
the function multiply utilizes the implementation from [4].  

It basically adds multiplicand to itself until multiplier becomes 0.  
The registers were prepared as above implementations except for this implementation has one register used for subtracting 1 from the multiplier  


## Discussion
One of the difficulty I found during creating the multiplication function is understanding what happens to the superposition states when we apply controlled rotation gates. To how many gates should I apply rotational gates or not was the problem I spent much time on.


## References
[1] Addition on a Quantum Computer, Thomas G. Draper, 1998  
[2] T-count Optimized Design of Quantum Integer Multiplication, Edgard Mu ˜noz-Coreas, Himanshu Thapliyal, 2017  
[3] Quantum arithmetic with the Quantum Fourier Transform, Lidia Ruiz-Perez ∗1 and Juan Carlos Garcia-Escartin1, 2017   
[4] Arithmetic on Quantum Computers: Multiplication, Sashwat Anagolum, 2018 
