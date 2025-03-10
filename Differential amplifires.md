# Experiment 3
# Differential Amplifiers- DC,Transient and AC analysis using LTspice
## Aim:
Design differential amplifier for the following specifications. V<sub>DD</sub>=2V,  P<=1mW,   V<sub>icm</sub> =1V,  v<sub>ocm</sub> =1.1V,  V<sub>P</sub> =0.4V. Perform DC analysis, Transient analysis and frequency response and extract the required parameters for all types of circuits.

### Theory:
A differential amplifier is a fundamental building block in analog circuits, that uses two identical MOSFETs for amplifying the difference between two input signals while rejecting common-mode signals. When implemented using NMOS transistors, it forms the input stage of operational amplifiers, sensor interfaces, and communication circuits.

<br>
The NMOS differential amplifier offers high gain, excellent noise rejection, and linearity. It is widely used in analog and mixed-signal applications such as instrumentation amplifiers and high-speed data converters.
<br>

The NMOS differential amplifier consists of two identical NMOS transistors (M1 and M2) connected in a symmetrical configuration. To work in the saturation region, the transistor must satisfy the condition V<sub>DS</sub> > (V<sub>GS</sub>-V<sub>TH</sub>).
<br>
### Working principle of Differential amplifiers:
* The circuit typically consists of two identical MOSFETs with a common-source connection.
* The two input signals are applied to the gate terminals of the MOSFETs, while the source terminals are connected to a common current source.
* When a differential voltage (i.e., difference in input voltages) is applied, the MOSFETs conduct different currents, causing a voltage difference at the drain terminals. This difference is then amplified and available as the output.
* If the two input signals are identical (common-mode voltage), both MOSFETs will conduct equally, and the output voltage will be zero, canceling out any noise or interference.
* The output voltage is directly proportional to the difference in input voltages, making it highly effective for noise rejection and differential signal amplification.
  <br>
  
Basically, A differential amplifier in common mode operation is designed to reject any common signal or noise present at both input terminals and provide minimal output. In common mode input, the same voltage is applied to both input terminals, i.e., V<sub>in1</sub> = V<sub>in2</sub> = V<sub>cm</sub>. Ideally, the differential amplifier should produce zero output because the difference between the inputs is zero  V<sub>in1</sub> - V<sub>in2</sub> = 0. V<sub>out1</sub> = V<sub>out2</sub> = V<sub>DD</sub>-I<sub>D</sub>R<sub>D</sub> = V<sub>D1</sub> = V<sub>D2</sub>. When V<sub>D1</sub> - V<sub>D2</sub> = 0, V<sub>in1</sub> = V<sub>in2</sub>. For saturation region Drain current will be I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L (V<sub>GS</sub>-V<sub>TH</sub>)<sup>2</sup>.A higher CMRR indicates better noise rejection capability. For the amplifier to effectively reject common mode signals, it must have matched transistors, identical load resistors, and a constant tail current. In an ideal case, the common mode gain should be zero, ensuring complete noise rejection. However, practically, there will be a small common mode output due to mismatched components or thermal variations.\
* Vincm(min) = VTH + VP ,to find minimum input common mode voltage
* Vincm(max) = VDD - IDRD + VTH ,to find maximum input common mode voltage
* imput max swing = Vincm(min) - Vincm(max)
* Voutcm(min) = VOV + Vp ,to find minimum output common mode voltage
* Voutcm(max) = VDD - IDRD ,,to find maximum input common mode voltage
* output max swing = Voutcm(min) - Voutcm(max)
<br>

### Types of Diffrential Amplifier:
1. Differential Amplifier with Resistor Load :
 * Provides a stable voltage drop and acts as a load.
 * Simple design, low cost.
 * Stabilizes biasing.
 * Low voltage gain.
 * Poor Common Mode Rejection Ratio (CMRR).
 * High power dissipation in the load resistor.
    <br>

2. Differential Amplifier with Current Source Load (Tail Current Source):
 * Higher voltage gain compared to resistor load.
 * Improved CMRR.
 * Provides stable and balanced output.
 * Requires a stable current source.
 * Design complexity increases.
 * Temperature drift may affect the current source.
<br>

3. Differential Amplifier with MOSFET:
 * Provides extremely high voltage gain.
 * High CMRR and linearity.
 * Very low power consumption.
 * Complex circuit design.
 * Requires perfect current matching between MOSFETs.
    
<br>

### Analysing the Circuit:

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

## circuit 1:(with R<sub>SS</sub>)
![Image](https://github.com/user-attachments/assets/008010cf-91f4-4acb-8ef9-00a71464b45a)

## components -
Resistors (3.600010kohm -2 and 0.8k ohm- 1, NMOSFET - 2, supply volatges(2V and 1V) - 3, ac ground, wires.

### Procedure:
1. Build the circuit as per the circuit diagram using LTspice.
2. Set the Resistor R<sub>D(1,2)</sub> value as 3.600010Kohm and R<sub>SS</sub> value as 0.8Kohm, DC voltage as 2V, input common mode volatge as 1V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN as given in the library file, length as 180nm and vary the width till you get the exact Q point.
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. To get the V<sub>out</sub> as per the given value, vary the R<sub>D</sub> value.
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 1V, Amplitude 50mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Take the difference of V<sub>out1</sub> and V<sub>out2</sub> waveforms,and calculate the diffrential gain.Also note down for what valur of input amplitude the distortion starts.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

### Calculation:
* P=1mW
* I<sub>SS</sub> = P/V = 1mW/2V  <table><td>=0.5mA</td><table>
* I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2  <table><td>=0.25mA</td><table> 
* V<sub>GS</sub> = V<sub>incm</sub> - V<sub>P</sub> = 1-0.4  <table><td>=0.6V</td><table>
* R<sub>D</sub> = V<sub>outcm</sub>-V<sub>DD</sub>/ I<sub>D</sub> = 1.1-2/0.25m <table><td>=3.6Kohm</td><table> 
* R<sub>SS</sub> = V<sub>p</sub>/ I<sub>SS</sub> = 0.4/0.5m <table><td>=0.8Kohm</td><table> 
* g<sub>m</sub> = 2I<sub>D</sub>/V<subOV</sub> = 2(0.25m)/0.6-0.36 <table><td>=2.08m</td><table>
* A<sub>V</sub> = -g<sub>m</sub>R<sub>D</sub> = -2.08m(3.6K) <table><td>=7.488V/V</td><table> 
* A<sub>V</sub>dB = 20log(A<sub>V</sub>) = 20log(7.488) <table><td>=17.48</td><table>
* V<sub>incm(min)</sub> = V<sub>TH</sub> + V<sub>P</sub> = 0.36 + 0.4  <table><td>=0.76</td><table> 
* V<sub>incm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> + V<sub>TH</sub> = 2-(0.25m)(3.6K)+0.36 <table><td>=1.46V</td><table> 
* imput max swing = V<sub>incm(min)</sub> - V<sub>incm(max)</sub> <table><td>=0.7V</td><table> 
* V<sub>outcm(min)</sub> = V<sub>OV</sub> + V<sub>p</sub> <table><td>=0.64V</td><table>
* V<sub>outcm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> <table><td>=1.1V</td><table> 
* output max swing = V<sub>outcm(min)</sub> - V<sub>outcm(max)</sub> <table><td>=0.46V</td><table>
  <br>

### Tabular Column:
|   Width  | CurrentI<sub>D</sub> | V<sub>out</sub>  | V<sub>P</sub>|
|----------|----------------------|------------------|--------------|
|    16um  |       0.243379mA     |      1.12382V    |    0.38906   |  
|    18um  |       0.247503mA     |      1.10899V    |   0.396004V  |
|    19um  |       0.249357mA     |      1.10231V    |   0.398971V  |
|  19.1um  |        0.249536mA    |      1.10167V    |   0.399257V  |
|   19.3um |        0.24989mA     |      1.10039V    |  0.399824V   |
|  19.36um |        0.249996mA    |      1.10001V    |   0.399993V  |
|19.3625um |        0.25mA        |      1.1V        |      0.4V    |

<br>

### Simulation Result :

1.DC analysis:\
![Image](https://github.com/user-attachments/assets/c7feb8d3-8a85-40c0-8d7e-d33e7593b04f)
![Image](https://github.com/user-attachments/assets/626b570b-4369-4982-82cf-cca7081c483b)

+ V<sub>out1</sub> = V<sub><out2</sub> = 1.1V.
* I<sub>D</sub> = 0.25mA which satisfy the condition P<=1mW.
* V<sub>P</sub> = 0.4V.
* I<sub>SS</sub> = 0.5mA.
* Q point = (V<sub>DS</sub>, I<sub>D</sub>) = (0.7V,0.25mA)
<br>

2.Transient Analysis: for Vin= 1V and varying input amplitude
   ![Image](https://github.com/user-attachments/assets/e9078a2e-ed84-45d6-b0ee-c4747ab0f6e5)
* input peak to peak volatge 200mV.
* Distortion occurs
    
   <br>
  
   ![Image](https://github.com/user-attachments/assets/39327a19-6ad4-40b5-a40f-0db8f9bb3aa3)

  
* input peak to peak voltage = 100mV (linear amplifier range).
* output peak to peak voltage = 1.766V.
* A<sub>V</sub> = 1.766V/100mV = 0.01766m = 17.66V/V.
Hence if the Amplitude increases distortion ocuurs. To maintain the circuit as linear amplifier set the input amplitude volatge and between minimum to maximum input common mode volatge properly otherwise circuit enters to cut off region and distortion occurs therefore it no longer will be the linear amplifier.

<br>

***To Calculate Output maximum swing***
![Image](https://github.com/user-attachments/assets/c77ccf10-fecb-4d6a-8b14-d78866e5b8bc)
Here the Output is started from 1.0991V to 1.5358V. Therefore the maximum output swing is 1.5358-1.0991=0.4367 which matches the theoritical value 0.46V.
<br>

![Image](https://github.com/user-attachments/assets/88e5a865-a6ff-472a-8f4d-5e5b01dbd6f3)
Here the input is started from 1V to 1.0494V. Therefore The maximum input swing is 0.0494V.
<br>
- The Differential Gain is given by maximum output swing/maximum input swing = 18.92dB.


<br>

3.AC analysis :
   ![Image](https://github.com/user-attachments/assets/35511c29-551f-4d5a-98a5-3e63091e768c)
  * 3dB Gain= 16.5dB
  * 3dB gain bandwidth = 0 to 3.839GHz.
  * CMRR = Differential gain (g<sub>m</sub>R<sub>D</sub>) / Common mode gain (V<sub>out</sub>/V<sub>incm</sub>) = 12.5.

<br>

### Inference:
1.current varies with respect to width.\
2.To get the expected output vary R<sub>D</sub> value inversly.\
3.Mosfet should be in the saturation region.\
4.Both the transistors and resistors should be identical.\
5.By connecting both the transistors to a single R<sub>SS</sub>, current is kept constant. ultimately this type of connection helps to maintain the constant current throughout the circuit by acting as a feedback network even if there are any small changes in the current flowing through the transistors.\
6.Noise cancelation which is CMRR that is it will cancel the noise by taking the difference of input signals by cancelling the common mode signals.\
7.from dc analysis we get operating point,dirfferential gain, maximum input and output swing.\
8.form transient analysis we get input and output peak to peak values so that we can calculate the gain of the circuit.\
9.from ac analysis we get 3dB gain and CMRR of the circuit.\

### comparision table:

|        Parameters      |     theoritical      |      simulation    |
|------------------------|----------------------|--------------------|
|     I<sub>SS</sub>     |       0.5mA          |      0.5mA         |
|     I<sub>D</sub>      |       0.25mA         |      0.25mA        |
|     R<sub>D</sub>      |       3.6Kohm        |      3.600010Kohm  |
|     R<sub>SS</sub>     |       0.8Kohm        |      0.8Kohm       |
|      V<sub>GS</sub>    |        0.6V          |      0.6V          |
|      V<sub>Th</sub>    |        0.3662V       |     0.497V         |
|      g<sub>m</sub>     |        2.08m         |      4.5m          |
|        gain(V/V)       |        7.488         |      17.66         |

   
<br>

## Circuit 2 (Current source) :
![Image](https://github.com/user-attachments/assets/abc1b776-2e14-4103-aa85-efa53d071bd9)

## components -
Resistors (3.600010kohm) - 2, NMOSFET - 2, supply volatges(2V and 1V) - 3, ac ground, wires, Current source - 0.5mA.

### Procedure : 

1.Build the circuit as per the circuit diagram using LTspice.\
2. Set the Resistor R<sub>D(1,2)</sub> value as 3.600010Kohm, DC voltage as 2V, input common mode volatge as 1V,and replace Rss by current source with 0.5mA value.\
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)\
4. Create a folder. Save the library file and LTspice file to the folder.\
5. Import the library file to LTspice using spice directive(.op).\
6. Find the current value for the given power rating.\
7.  Set the mosfet model name CMOSN as given in the library file, length as 180nm and vary the width till you get the exact Q point.\
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. To get the V<sub>out</sub> as per the given value, vary the R<sub>D</sub> value.\
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 1V, Amplitude 50mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Take the difference of V<sub>out1</sub> and V<sub>out2</sub> waveforms,and calculate the diffrential gain.Also note down for what valur of input amplitude the distortion starts.\
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.\
    
### Calculation:
* P=1mW
* I<sub>SS</sub> = P/V = 1mW/2V  <table><td>=0.5mA</td><table>
  
* I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2  <table><td>=0.25mA</td><table> 
* V<sub>GS</sub> = V<sub>incm</sub> - V<sub>P</sub> = 1-0.4  <table><td>=0.6V</td><table>
* R<sub>D</sub> = V<sub>outcm</sub>-V<sub>DD</sub>/ I<sub>D</sub> = 1.1-2/0.25m <table><td>=3.6Kohm</td><table> 
* R<sub>SS</sub> = V<sub>p</sub>/ I<sub>SS</sub> = 0.4/0.5m <table><td>=0.8Kohm</td><table> 
* g<sub>m</sub> = 2I<sub>D</sub>/V<subOV</sub> = 2(0.25m)/0.6-0.36 <table><td>=2.08m</td><table>
* A<sub>V</sub> = -g<sub>m</sub>R<sub>D</sub> = -2.08m(3.6K) <table><td>=7.488V/V</td><table> 
* A<sub>V</sub>dB = 20log(A<sub>V</sub>) = 20log(7.488) <table><td>=17.48</td><table>
* V<sub>incm(min)</sub> = V<sub>TH</sub> + V<sub>P</sub> = 0.36 + 0.4  <table><td>=0.76</td><table> 
* V<sub>incm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> + V<sub>TH</sub> = 2-(0.25m)(3.6K)+0.36 <table><td>=1.46V</td><table> 
* imput max swing = V<sub>incm(min)</sub> - V<sub>incm(max)</sub> <table><td>=0.7V</td><table> 
* V<sub>outcm(min)</sub> = V<sub>OV</sub> + V<sub>p</sub> <table><td>=0.64V</td><table>
* V<sub>outcm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> <table><td>=1.1V</td><table> 
* output max swing = V<sub>outcm(min)</sub> - V<sub>outcm(max)</sub> <table><td>=0.46V</td><table> 

### Tabular Column:
|   Width  | CurrentI<sub>D</sub> | V<sub>out</sub>  | V<sub>P</sub>|
|----------|----------------------|------------------|--------------|
|    16um  |       0.243379mA     |      1.12382V    |    0.38906   |  
|    18um  |       0.247503mA     |      1.10899V    |   0.396004V  |
|    19um  |       0.249357mA     |      1.10231V    |   0.398971V  |
|  19.1um  |        0.249536mA    |      1.10167V    |   0.399257V  |
|   19.3um |        0.24989mA     |      1.10039V    |  0.399824V   |
|  19.36um |        0.249996mA    |      1.10001V    |   0.399993V  |
|19.3625um |        0.25mA        |      1.1V        |      0.4V    |

### Simulation Result :
1.DC analysis:\
 ![Image](https://github.com/user-attachments/assets/c7feb8d3-8a85-40c0-8d7e-d33e7593b04f)
 ![Image](https://github.com/user-attachments/assets/626b570b-4369-4982-82cf-cca7081c483b)
  
* V<sub>out1</sub> = V<sub><out2</sub> = 1.1V.
* I<sub>D</sub> = 0.25mA which satisfy the condition P<=1mW.
* V<sub>P</sub> = 0.4V.
* I<sub>SS</sub> = 0.5mA.
* Q point = (V<sub>DS</sub>, I<sub>D</sub>) = (0.7V,0.25mA)

  <br>

2.Transient Analysis: for Vin= 1V and varying input amplitude.
   ![Image](https://github.com/user-attachments/assets/e9078a2e-ed84-45d6-b0ee-c4747ab0f6e5)
* input peak to peak volatge 200mV.
* Distortion occurs

  <br>

    ![Image](https://github.com/user-attachments/assets/39327a19-6ad4-40b5-a40f-0db8f9bb3aa3)

* input peak to peak voltage = 100mV (linear amplifier range).
* output peak to peak voltage = 1.766V.
* A<sub>V</sub> = 1.766V/100mV = 0.01766m = 17.66V/V.
Hence if the Amplitude increases distortion ocuurs. To maintain the circuit as linear amplifier set the input amplitude volatge and between minimum to maximum input common mode volatge properly otherwise circuit enters to cut off region and distortion occurs therefore it no longer will be the linear amplifier.

<br>

***To Calculate Output maximum swing***
![Image](https://github.com/user-attachments/assets/c77ccf10-fecb-4d6a-8b14-d78866e5b8bc)
Here the Output is started from 1.0991V to 1.5358. Therefore the maximum output swing is 1.5358-1.0991=0.4367 which matches the theoritical value 0.46V.
<br>

![Image](https://github.com/user-attachments/assets/88e5a865-a6ff-472a-8f4d-5e5b01dbd6f3)
Here the input is started from 1V to 1.0494V. Therefore The maximum input swing is 0.0494V.
<br>
- The Differential Gain is given by maximum output swing/maximum input swing = 18.92dB.

<br>

3.AC analysis:\
 ![Image](https://github.com/user-attachments/assets/c4981b32-a038-4c58-bfd8-53ccbdce238b)
  * 3dB Gain= 16.5dB
  * 3dB gain bandwidth = 0 to 3.90GHz.
  * CMRR = Differential gain (g<sub>m</sub>R<sub>D</sub>) / Common mode gain (V<sub>out</sub>/V<sub>incm</sub>) = 12.54.

### Inference:
1.current varies with respect to width.\
2.To get the expected output vary R<sub>D</sub> value inversly.\
3.Mosfet should be in the saturation region.\
4.Both the transistors and resistors should be identical.\
5.By connecting both the transistors to a single current source, current is kept constant. ultimately this type of connection helps to maintain the constant current throughout the circuit by acting as a feedback network even if there are any small changes in the current flowing through the transistors.\
6.Noise cancelation which is CMRR ,that is it will cancel the noise by taking the difference of input signals by cancelling the common mode signals is increases in this type of circuit\
7.from dc analysis we get operating point,dirfferential gain, maximum input and output swing.\
8.form transient analysis we get input and output peak to peak values so that we can calculate the gain of the circuit.\
9.from ac analysis we get 3dB gain and CMRR of the circuit.\
10.The gain will be nearly same as in the circuit with Rss but stability is increased in this circuit.


### Circuit 3 :
![Image](https://github.com/user-attachments/assets/01fb5d56-0bd2-4dbd-aa3e-00f26d4da2cc)
<br>

## components -
Resistors (3.6kohm) - 2, NMOSFET - 3, supply volatges(2V and 1V) - 3, ac ground, wires.

### Procedure : 

1.Build the circuit as per the circuit diagram using LTspice.\
2. Set the Resistor R<sub>D(1,2)</sub> value as 3.6Kohm , DC voltage as 2V, input common mode volatge as 1V,and replace  current source with NMOSFET.\
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)\
4. Create a folder. Save the library file and LTspice file to the folder.\
5. Import the library file to LTspice using spice directive(.op).\
6. Find the current value for the given power rating.\
7. Fix the Vb value of the mosfet such that all the three mosfet should be in the saturation region and get the expected calculated results while simulation (Vb<= Vp + Vth).\
8.  Set the mosfet model name CMOSN as given in the library file, length as 180nm and vary the width till you get the exact Q point.Keep the width and length of differential amplifier mosfets and vary the aspect ratio of third mosfet to fix the designed values.\
9. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. To get the V<sub>out</sub> as per the given value, vary the R<sub>D</sub> value.\
10. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 1V, Amplitude 50mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Take the difference of V<sub>out1</sub> and V<sub>out2</sub> waveforms,and calculate the diffrential gain.Also note down for what value of input amplitude the distortion starts.\
11. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.\

### Calculation:
* P=1mW
* I<sub>SS</sub> = P/V = 1mW/2V  <table><td>=0.5mA</td><table>
  
* I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub>/2  <table><td>=0.25mA</td><table> 
* V<sub>GS</sub> = V<sub>incm</sub> - V<sub>P</sub> = 1-0.4  <table><td>=0.6V</td><table>
* V<sub>b</sub> <= V<sub>P</sub> + V<sub>TH</sub> = 0.4+0.366 <table><td>=0.76V</td><table>
* R<sub>D</sub> = V<sub>outcm</sub>-V<sub>DD</sub>/ I<sub>D</sub> = 1.1-2/0.25m <table><td>=3.6Kohm</td><table> 
* R<sub>SS</sub> = V<sub>p</sub>/ I<sub>SS</sub> = 0.4/0.5m <table><td>=0.8Kohm</td><table> 
* g<sub>m</sub> = 2I<sub>D</sub>/V<subOV</sub> = 2(0.25m)/0.6-0.36 <table><td>=2.08m</td><table>
* A<sub>V</sub> = -g<sub>m</sub>R<sub>D</sub> = -2.08m(3.6K) <table><td>=7.488V/V</td><table> 
* A<sub>V</sub>dB = 20log(A<sub>V</sub>) = 20log(7.488) <table><td>=17.48</td><table>
* V<sub>incm(min)</sub> = V<sub>TH</sub> + V<sub>P</sub> = 0.36 + 0.4  <table><td>=0.76</td><table> 
* V<sub>incm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> + V<sub>TH</sub> = 2-(0.25m)(3.6K)+0.36 <table><td>=1.46V</td><table> 
* imput max swing = V<sub>incm(min)</sub> - V<sub>incm(max)</sub> <table><td>=0.7V</td><table> 
* V<sub>outcm(min)</sub> = V<sub>OV</sub> + V<sub>p</sub> <table><td>=0.64V</td><table>
* V<sub>outcm(max)</sub> = V<sub>DD</sub> - I<sub>D</sub>R<sub>D</sub> <table><td>=1.1V</td><table> 
* output max swing = V<sub>outcm(min)</sub> - V<sub>outcm(max)</sub> <table><td>=0.46V</td><table>


### Tabular Column:
|   Width  | CurrentI<sub>SS</sub> | V<sub>out</sub> |
|----------|----------------------|------------------|
|    6um   |       0.338232mA     |      1.39118V    |      
|    8um   |       0.443078mA     |      1.20246V    |   
|    9um   |       0.49495mA      |      1.10909V    |   
|  9.01um  |        0.495467mA    |      1.10816V    |   
|   9.05um |        0.497533mA    |      1.10444V    |  
|  9.09um  |        0.4996mA      |      1.10072V    |   
|9.09776um |        0.5mA         |      1.1V        |   


### Simulation Result :
1.DC analysis:\
![Image](https://github.com/user-attachments/assets/9d6da6ae-5adb-4ae8-8c41-7ecd546bfd4b)
![Image](https://github.com/user-attachments/assets/847d8ae1-9183-4816-b2f4-aedf1f4f79f7)

* V<sub>out1</sub> = V<sub><out2</sub> = 1.1V.
* I<sub>D</sub> = 0.25mA which satisfy the condition P<=1mW.
* V<sub>P</sub> = 0.4V.
* I<sub>SS</sub> = 0.5mA.
* Q point of M1 and M2 = (V<sub>DS</sub>, I<sub>D</sub>) = (0.7V,0.25mA)
* Q point of M3 = (V<sub>DS</sub>, I<sub>SS</sub>) = (0.4V,0.5mA)

2.Transient Analysis: for Vin= 1V and varying input amplitude.
   ![Image](https://github.com/user-attachments/assets/e9078a2e-ed84-45d6-b0ee-c4747ab0f6e5)
* input peak to peak volatge 0.2mV.
* Transistor is in cut off region.

  <br>

    ![Image](https://github.com/user-attachments/assets/14602887-93ec-4258-adc6-59b2074e65a6)

* input peak to peak voltage = 100mV (linear amplifier range).
* output peak to peak voltage = 1.7692V.
* A<sub>V</sub> = 1.792V/100mV = 0.01792m = 17.62V/V.
 To maintain the circuit as linear amplifier set the input amplitude volatge and between minimum to maximum input common mode volatge properly otherwise circuit enters to cut off region and distortion occurs therefore it no longer will be the linear amplifier.

<br>

***To Calculate Input and Output maximum swing***

Here the Output is started from 1.0991V to 1.5358. Therefore the maximum output swing is 1.5358-1.0991=0.4367 which matches the theoritical value 0.46V.
<br>

![Image](https://github.com/user-attachments/assets/b7201076-a409-474a-8349-0be26a449310)
Here the input is started from 1V to 1.0494V. Therefore The maximum input swing is 0.0494V.
<br>
- The Differential Gain is given by maximum output swing/maximum input swing = 18.92dB.
3.AC analysis:\
 ![Image](https://github.com/user-attachments/assets/c4981b32-a038-4c58-bfd8-53ccbdce238b)
  * 3dB Gain= 16.5dB
  * 3dB gain bandwidth = 0 to 3.90GHz.
  * CMRR = Differential gain (g<sub>m</sub>R<sub>D</sub>) / Common mode gain (V<sub>out</sub>/V<sub>incm</sub>) = 12.54.
