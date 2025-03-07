# Experiment 2
# Differential Amplifiers- DC,Transient and AC analysis using LTspice
## Aim:
Design differential amplifier for the following specifications. V<sub>DD</sub>=2V,  P<=1mW,   V<sub>icm</sub> =1V,  v<sub>ocm</sub> =1.1V,  V<sub>P</sub> =0.4V. Perform DC analysis, Transient analysis and frequency response and extract the required parameters for all types of circuits.

### Theory:
A differential amplifier is a fundamental building block in analog circuits, used for amplifying the difference between two input signals while rejecting common-mode signals. When implemented using NMOS transistors, it forms the input stage of operational amplifiers, sensor interfaces, and communication circuits.

<br>
The NMOS differential amplifier offers high gain, excellent noise rejection, and linearity. It is widely used in analog and mixed-signal applications such as instrumentation amplifiers and high-speed data converters.
<br>

The NMOS differential amplifier consists of two identical NMOS transistors (M1 and M2) connected in a symmetrical configuration using a resistor (R<sub>SS</sub>) as the tail bias making the circuit more dependent on input common-mode voltage variations. This results in a lower Common-Mode Rejection Ratio (CMRR) compared to the ideal current-source configuration.To maintain the better stability, higher gain  we would use current source or a mosfet instead of resistor.All these maintains the constant cuurents throughout the circuits. It operates by modulating the drain currents of the transistors based on the difference in their gate voltages. The circuit can be analyzed using DC analysis, transient analysis, and AC analysis to determine its performance. To work in the active region, the transistor must satisfy the condition V<sub>DS</sub> > (V<sub>GS</sub>-V<sub>TH</sub>).

<br>

1. **DC analysis** : DC analysis determines the biasing conditions of the transistors, ensuring that they operate in the saturation region for proper amplification.\
The total bias current is split equally between the two transistors:  <br>           I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2 \
For a MOSFET operating in the saturation region, the drain current is given by:<br>  I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L (V<sub>GS</sub>-V<sub>TH</sub>)<sup>2</sup>\
width is directly proportional to current I<sub>D</sub> and output depends on the value of R<sub>D</sub> value that is if R<sub>D</sub> increases output decreases inversely.
Since V<sub>GS1</sub> = V<sub>GS2</sub> for a perfectly matched pair, both transistors will have equal drain currents when no differential input is applied and will have V<sub>D1</sub> = V<sub>D2</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub>  which defines the operating point of the circuit. 
<br>

2. **Transient analysis** : Transient analysis examines the time-domain response of the amplifier when subjected to a time-varying input.The transient response is largely influenced by the parasitic capacitances and the load connected to the amplifier.It provides the V<sub>out</sub> peak to peak value so that by using inout peak to peak value we get the gain of the circuit.

<br>

3. **Ac analysis** : AC analysis evaluates the small-signal gain, frequency response, and bandwidth of the differential amplifier.
<br> 

**Formulas to be used** : 
1. I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2 
2. I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L (V<sub>GS</sub>-V<sub>TH</sub>)<sup>2</sup>
3. V<sub>incm</sub> = V<sub>GS</sub> + V<sub>P</sub>
4. V<sub>outcm</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub>
5. g<sub>m</sub> = 2I<sub>D</sub>/V<subOV</sub>
6. A<sub>V</sub> = -g<sub>m</sub>R<sub>D</sub>
7. A<sub>V</sub>dB = 20log(A<sub>V</sub>)
8. V<sub>incm(min)</sub> = V<sub>TH</sub> + V<sub>P</sub>
9. V<sub>incm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> + V<sub>TH</sub>
10. imput max swing = V<sub>incm(min)</sub> - V<sub>incm(max)</sub>
11. V<sub>outcm(min)</sub> = V<sub>OV</sub> + V<sub>p</sub>
12. V<sub>outcm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub>
13. output max swing = V<sub>outcm(min)</sub> - V<sub>outcm(max)</sub>

### circuit 1:
![Image](https://github.com/user-attachments/assets/34ddbb5e-9243-4838-b228-da4f71b0baa5)

## components -
Resistors (3.600050k and 0.8k ohm) - 2, NMOSFET - 2, supply volatges(2V and 1V) - 3, ac ground, wires.

### Procedure:
1. Build the common source amplifier circuit as the circuit diagram using LTspice.
2. Set the Resistor R<sub>D(1,2)</sub> value as 3.600050Kohm and R<sub>SS</sub> value as 0.8Kohm, DC voltage as 2V, input common mode volatge as 1V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN as given in the library file, length as 180nm and vary the width till you get the exact Q point.
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. To get the V<sub>out</sub> as per the given value, vary the R<sub>D</sub> value.
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 1V, Amplitude 50mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Take the difference of V<sub>out1</sub> and V<sub>out2</sub> waveforms,and calculate the diffrential gain.Also note down for what valur of input amplitude the distortion starts.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

### Calculation:
P=1mW\
I<sub>SS</sub> = P/V = 1mW/2V = 0.5mA.\
I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2 = 0.25mA.\
V<sub>GS</sub> = V<sub>incm</sub> - V<sub>P</sub> = 1-0.4 = 0.6V.\
R<sub>D</sub> = V<sub>outcm</sub>-V<sub>DD</sub>/ I<sub>D</sub> = 1.1-2/0.25m = 3.6Kohm.\
R<sub>SS</sub> = V<sub>p</sub>/ I<sub>SS</sub> = 0.4/0.5m = 0.8Kohm.\
g<sub>m</sub> = 2I<sub>D</sub>/V<subOV</sub> = 2(0.25m)/0.6-0.36 = 2.08m.\
A<sub>V</sub> = -g<sub>m</sub>R<sub>D</sub> = -2.08m(3.6K) = 7.488V/V.\
A<sub>V</sub>dB = 20log(A<sub>V</sub>) = 20log(7.488) = 17.48.\
V<sub>incm(min)</sub> = V<sub>TH</sub> + V<sub>P</sub> = 0.36 + 0.4 = 0.76V.\
V<sub>incm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> + V<sub>TH</sub> = 2-(0.25m)(3.6K)+0.36 = 1.46V.\
imput max swing = V<sub>incm(min)</sub> - V<sub>incm(max)</sub> = 0.7V.\
V<sub>outcm(min)</sub> = V<sub>OV</sub> + V<sub>p</sub> = 0.64V.\
V<sub>outcm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> = 1.1V.\
output max swing = V<sub>outcm(min)</sub> - V<sub>outcm(max)</sub> = 0.46V.\

### Tabular Column:
|   Width  | CurrentI<sub>D</sub> | V<sub>out</sub>  |
|----------|----------------------|------------------|
|    16um  |       0.243uA        |      1.12382V    |
|    17um  |       0.245uA        |      1.11613V    |
|    18um  |       0.245uA        |      1.10898V    |
|    19um  |        0.249uA       |      1.1023V     |
|   19.1um |        0.249uA       |      1.10166V    |
|  19.33um |        0.249uA       |      1.10019V    |
|  19.36um |        0.249mA       |      1.1V        |

### Simulation Result :
1. DC analysis:
   ![Image](https://github.com/user-attachments/assets/ac6894cb-b152-45b3-9136-272200414433)
V<sub>out1</sub> = V<sub><out2</sub> = 1.1V.\
I<sub>D</sub> = 0.249mA which satisfy the condition P<=1mW.\
sub>P</sub> = 0.399992V.\
I<sub>SS</sub> = 0.499991mA.\
Q point = (V<sub>DS</sub>, I<sub>D</sub>) = (0.7V,0.249mA)

<br>

2. Transient Analysis:
   ![Image](https://github.com/user-attachments/assets/39327a19-6ad4-40b5-a40f-0db8f9bb3aa3)

   Distortion starts for 250mV input amplitude.\
   input peak to peak voltage = 100mV.\
   output peak to peak voltage = 1.766V.\
   A<sub>V</sub> = 1.766V/100mV = 0.01766m = 17.66V/V.

<br>

3. AC analysis :
   ![Image](https://github.com/user-attachments/assets/917cf5b9-a1d3-4060-9f55-7f5e3b9ba969)
   3dB gain = 0 to 9.03GHz.\
   CMRR = Differential gain (g<sub>m</sub>R<sub>D</sub>) / Common mode gain (V<sub>out</sub>/V<sub>incm</sub>) = 12.54.

<br>

### Inference:
1. current varies with respect to width.
2. To get the expected output vary R<sub>D</sub> value inversly.
3. Mosfet should be in the saturation region.
4. Both the transistors and resistors should be identical.
5. By connecting both the transistors to a single R<sub>SS<sub> , current is kept constant. ultimately this type of connection helps to maintain the constant current throughout the circuit by acting as a feedback network even if there are any small changes in the current flowing through the transistors.
6. Noise cancelation which is CMRR that is it will cancel the noise by taking the difference of input signals by cancelling the common mode signals.
7. from dc analysis we get operating point,dirfferential gain, maximum input and output swing.
8. form transient analysis we get input and output peak to peak values so that we can calculate the gain of the circuit.
9. from ac analysis we get 3dB gain and CMRR of the circuit.

### comparision table:

|        Parameters      |     theoritical      |      simulation    |
|------------------------|----------------------|--------------------|
|     I<sub>SS</sub>     |       0.5mA          |      0.499991mA    |
|     R<sub>D</sub>      |       3.6Kohm        |      3.600050Kohm  |
|     R<sub>SS</sub>     |       0.8Kohm        |      0.8Kohm       |
|      V<sub>GS</sub>    |        0.6V          |      0.6V          |
|      g<sub>m</sub>     |        2.08m         |      2.12m         |
|      A<sub>V</sub>     |        7.488         |      7.63V         |

   
   
