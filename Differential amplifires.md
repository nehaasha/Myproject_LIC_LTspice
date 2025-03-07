# Experiment 2
# Differential Amplifiers- DC,Transient and AC analysis using LTspice
## Aim:
Design differential amplifier for the following specifications. V<sub>DD</sub>=2V,  P<=1mW,   V<sub>icm</sub> =1V,  v<sub>ocm</sub> =1.1V,  V<sub>P</sub> =0.4V. Perform DC analysis, Transient analysis and frequency response and extract the required parameters for all types of circuits.
## components -
Resistors (3.600050k and 0.8k ohm) - 2, NMOSFET - 2, supply volatges(2V and 1V) - 3, ac ground, wires.
### Theory:
A differential amplifier is a fundamental building block in analog circuits, used for amplifying the difference between two input signals while rejecting common-mode signals. When implemented using NMOS transistors, it forms the input stage of operational amplifiers, sensor interfaces, and communication circuits.<br>
The NMOS differential amplifier offers high gain, excellent noise rejection, and linearity. It is widely used in analog and mixed-signal applications such as instrumentation amplifiers and high-speed data converters.<br>
The NMOS differential amplifier consists of two identical NMOS transistors (M1 and M2) connected in a symmetrical configuration with a current source (I<sub>SS</sub>) at the tail. It operates by modulating the drain currents of the transistors based on the difference in their gate voltages. The circuit can be analyzed using DC analysis, transient analysis, and AC analysis to determine its performance.<br>
**DC analysis** : DC analysis determines the biasing conditions of the transistors, ensuring that they operate in the saturation region for proper amplification.

### circuit 1:
![Image](https://github.com/user-attachments/assets/34ddbb5e-9243-4838-b228-da4f71b0baa5)

