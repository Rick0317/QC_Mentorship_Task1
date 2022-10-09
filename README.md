# QC_Mentorship_Task1
Creating Quantum Circuit for Integer Multiplication 

## Background
### Quantum Computing
Quantum Computing is an emerging field of study into which many researchers and companies put resources.  
Quantum Computing is a different way of calculation compared to classical computing which is used by this Mac book I'm using to type these words.  In quantum computing, the information is represented by Qubits instead of bits.  
These qubits represent some discrete phenomenon of the nature such as excited states of atoms. The discreteness also applies to classical bits, which use the measurement of voltage as whether the result is higher than a certain value or not.  
The difference is that the information represented by qubits are continuous, and this is realized by the superposition of two quantum states.  The visualization of this is achieved by Bloch Sphere which you can search up online or take a look at my repository (Quantum 3D Game)[https://github.com/Rick0317/Humans-vs-Quantum-Computers---IBM] 
Due to these special properties of quantum computing, we can calculate certain problems way faster than classical computers, which we call Quantum Supremacy.  Algorithm such as Deutsch Algorithm and Deutasch-Jozsa algorithm are proved to be calculated faster by quantum computing than by classical computing.  

### Integer Multiplication

## Algorithm

1, Shift-and-Add algorithm  
This is basically the algorithm we use to do multiplication of two integers in elementary school.  
We have Multiplicand, Multiplier, and Register. We multiply each digit of Multiplier to Multiplicand and store the result in Register.  
![Shift and Add](https://github.com/Rick0317/QC_Mentorship_Task1/blob/master/images/shift_add_algo.jpg)  


## Implementation
When I was implementing the integer multiplication quantum circuit, I did not refer to any past research. I later looked at the past papers and works and knew there exist better solutions. I will present my implementation and the implementation based on the past work  

### My implementation
1, Encoding  
The given integers will be encoded into quantum states using numpy and X_gate. 

2, qubit registers

3, Quantum Circuit

4, 

### Based on the past implementations


## Discussion


## References
[1] Addition on a Quantum Computer, Thomas G. Draper, 1998  
[2] T-count Optimized Design of Quantum Integer Multiplication, Edgard Mu ˜noz-Coreas, Himanshu Thapliyal, 2017  
[3] Quantum arithmetic with the Quantum Fourier Transform, Lidia Ruiz-Perez ∗1 and Juan Carlos Garcia-Escartin1, 2017  