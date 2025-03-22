# Experiment 6
### Aim: Design and Analyze current mirror circuit as load active in amplifier circuit
### Theory:
+ A current mirror is an analog circuit designed to copy a reference current from one branch to another while maintaining a constant and predictable output current. It is a fundamental building block in integrated circuits (ICs) and is widely used for biasing, voltage references, and current amplification in analog circuits. The key advantage of a current mirror is its ability to provide a stable current that is largely independent of voltage variations in the circuit.
+ The basic current mirror consists of two or more transistors with matched electrical characteristics. One transistor, called the reference transistor, is configured to establish a set current, while the other transistor, the output transistor, is designed to copy or "mirror" that current. If the transistors are identical and operate in the same conditions, their drain (or collector) currents will be equal, ensuring accurate current replication.
+ In BJT (Bipolar Junction Transistor) current mirrors, the base-emitter voltage (V_BE) of both transistors is made equal by connecting their bases together. Since the transistors are matched, they will conduct the same collector current. However, BJTs suffer from base current mismatch, which slightly affects the accuracy of the mirrored current. This can be improved using Wilson or cascode configurations.
+ For MOSFET current mirrors, the circuit operates based on the MOSFET's gate-source voltage (V_GS) and saturation current equation. The simplest MOSFET current mirror consists of two matched MOSFETs where one transistor is diode-connected (gate and drain shorted). The second transistor, which receives the same gate voltage as the first, operates in saturation and mirrors the reference current accurately. MOSFET current mirrors are widely used in CMOS ICs due to their high input impedance and excellent current replication properties.
+ To improve performance, advanced current mirrors such as Wilson and cascode designs are used. A Wilson current mirror improves output resistance, reducing variations in the output current. A cascode current mirror, which adds an additional transistor for voltage shielding, significantly enhances output impedance and accuracy by minimizing channel-length modulation effects in MOSFETs. These modifications are essential in high-precision analog designs, such as operational amplifiers and differential amplifier biasing.
+ Current mirrors find widespread applications in analog circuit design. They are commonly used as biasing circuits in amplifiers, constant current sources in voltage regulators, and active loads in differential amplifiers. Their ability to maintain a stable current independent of supply voltage variations makes them an essential component in modern electronic circuits, especially in integrated circuits (ICs) where precision and stability are crucial.
+ These type of circuits makes Precise Current Replication, Load Independence, High Output Resistance, Compact and IC-Friendly, Better Temperature Stability, Multiple Outputs from One Reference, Lower Power Consumption, Improved Performance in Analog Circuits, More Control Over Current Scaling, Easier to Integrate in ICs compared to other traditional passive current source.

<br>

### Analysing the Circuit:

1. **DC analysis** : DC analysis determines the biasing conditions of the transistors, ensuring that they operate in the saturation region for proper amplification.\
The total bias current is split equally between the two transistors:  <br>           I<sub>D1</sub> = I<sub>D2</sub>  \
For a MOSFET operating in the saturation region, the drain current is given by:<br>  I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L (V<sub>GS</sub>-V<sub>TH</sub>)<sup>2</sup>\
width is directly proportional to current I<sub>D</sub>\
I<sub>total</sub> = I<sub>ref</sub> + I<sub>x</sub>\
I<sub>total</sub> = power/Vdd

<br>

2. **Transient analysis** : Transient analysis examines the time-domain response of the amplifier when subjected to a time-varying input.The transient response is largely influenced by the parasitic capacitances and the load connected to the amplifier.It provides the V<sub>out</sub> peak to peak value so that by using inout peak to peak value we get the gain of the circuit.

<br>

3. **Ac analysis** : AC analysis evaluates the small-signal gain, frequency response, and bandwidth of the differential amplifier.
<br> 
### Circuit 1:



