# Experiment 6
### Aim: Design and Analyze current mirror circuit as load active in amplifier circuit with Av>-10v/v, P<=1mW, Vdd=1.8V.
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

### Circuit 1: for 1:1 ratio
![Image](https://github.com/user-attachments/assets/ff0d4688-0a59-45a7-9b92-b7737bb2e189)

### Components :
PMOSFET-2, NMOSFET- 1, supply volatage-2, current source-1.

### Procedure:

1. Build the circuit as per the circuit diagram using LTspice.
2. Set the Vdd as 1.8V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN for NMOSFET and CMOSP for PMOSFET as given in the library file, length as 180nm and vary the width  of NMOSFET till you get the exact Q point. Set the gate volatge of NMOSFET as 0.5V. 
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. Since we are doing current mirroring the current of both mosfets should be same as the reference current even the output also should match too. 
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.5V, Amplitude 1mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.find the maximum output swing.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

<br>

### Calculations:
* Power <= 1mW
* Vdd = 1.8V
* I<sub>total</sub> = power/Vdd = 1mW/1.8 = 55.5mA
* I<sub>D</sub>= I<sub>total</sub>/2 = 0.2775mA.

<br>

### Simulation Results:
### DC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/fef1b93f-5e4e-410a-877a-4675bce7aa96)

PMOSFET = length is 180nm, width is 10um\
NMOSFET = length is 180nm, width is 114.025um\
V<sub>out</sub>= 0.967276V\
V<sub>x</sub>= 0.967276V\
I<sub>ref</sub> = 0.277mA\

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/54d86e54-5ccb-4043-9d74-c6aaf0379e79)

PMOSFET = length is 500nm, width is 10um\
NMOSFET = length is 500nm, width is 207.617um\
V<sub>out</sub>= 0.644713V\
V<sub>x</sub>= 0.644703V\
I<sub>ref</sub> = 0.277mA\

3.Case 3: 1umm
![Image](https://github.com/user-attachments/assets/301f9c59-7da5-4b5e-b553-28679c231c6b)

PMOSFET = length is 1um, width is 10um\
NMOSFET = length is 1um, width is 251.54um\
V<sub>out</sub>= 0.293193V\
V<sub>x</sub>=  0.293177V\
I<sub>ref</sub> = 0.277mA

### Tabular column:
|  Length  |            Width           |   V<sub>x</sub>  | V<sub>out</sub>  |   I<sub>ref</sub>|
|----------|----------------------------|------------------|------------------|------------------|
|   180nm  | pmos= 10u; nmos=114.025u   |    0.967276V     |     0.967276V    |    0.277mA       |
|   500nm  | pmos= 10u; nmos=207.617u   |    0.644703V     |     0.644713V    |    0.277mA       |
|    1um   | pmos= 10u; nmos=251.54u    |    0.293177V     |     0.293193V    |    0.277mA       |

### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/893a38ab-0455-4193-8bb9-052746ef2e42)
* Peak to Peak volatge = 1.934V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00847-0.36)+(0.5-0.36)= 2.29V

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/8786450e-c70e-4efd-8edf-bf6ba5d635ee)
* Peak to Peak volatge = 1.28V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00000907-0.36)+(0.5-0.36)= 2.29V

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/e58a1237-fc27-4672-a463-ea0b2869f16f)
* Peak to Peak volatge = 0.607V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(0.0000165-0.36)+(0.5-0.36)= 2.29V

<br>

### AC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/930f7ecd-c47f-4642-a996-0b1da4b510a2)
* 3dB gain = 27dB
* 3dB bandwidth= 265.18509MHz

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/e2fd23ef-52a1-4385-a9bc-30a4c2a5e1f2)
* 3dB gain = 36dB
* 3dB bandwidth= 52.464564MHz

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/3678ebb6-9c12-4d7b-8492-cb5e70852461)
* 3dB gain = 35.75dB
* 3dB bandwidth= 39.494824MHz

### Inference:
* Reference current is copied or mirrored for other two mosfets.The output currentis exactly equal to the reference current.
* The output current remains the same regardless of the connected load, as long as the transistor stays in the saturation region
* V<sub>x</sub> and V<sub>out</sub> will be same when current gets mirrored.
* As length increases V<sub>x</sub> and V<sub>out</sub> decreases.
* As gain increases bandwidth decreases.
* As the refence current is 0.277mA and doing 1:1 ratio of current mirroring the Current must be copied of the same that is 0.277mA.
* In transient analysis we see the maximum output swing caused.
  
<br>

### Circuit 1: for 1:2 ratio
![Image](https://github.com/user-attachments/assets/ff0d4688-0a59-45a7-9b92-b7737bb2e189)

### Components :
PMOSFET-2, NMOSFET- 1, supply volatage-2, current source-1.

### Procedure:

1. Build the circuit as per the circuit diagram using LTspice.
2. Set the Vdd as 1.8V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN for NMOSFET and CMOSP for PMOSFET as given in the library file, length as 180nm and vary the width  of NMOSFET till you get the exact Q point. Set the gate volatge of NMOSFET as 0.5V. 
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. Since we are doing current mirroring the current of both mosfets should be same as the reference current even the output also should match too. 
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.5V, Amplitude 5mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.Find the maximum output swing.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

<br>

### Calculations:
* Power <= 1mW
* Vdd = 1.8V
* I<sub>total</sub> = power/Vdd = 1mW/1.8 = 55.5mA
* I<sub>D</sub>= I<sub>total</sub>/3 = 0.185mA.
* 1:2 ratio = 0.185mA : 0.37mA.

<br>

### Simulation Results:
### DC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/035b9dd2-ffb3-46f0-bd5d-2d969f255fd4)

PMOSFET 1 = length is 180nm, width is 70um : PMOSFET 2 = width is 140nm\
NMOSFET = length is 180nm, width is 135.867um\
V<sub>out</sub>=  1.20094V\
V<sub>x</sub>=  1.20934V\
I<sub>ref</sub> = 0.185mA\

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/8335044c-f581-451c-a812-1930b087f9fc)

PMOSFET 1 = length is 180nm, width is 70um : PMOSFET 2 = width is 140nm
NMOSFET = length is 500nm, width is 256.773um\
V<sub>out</sub>=  1.15935V\
V<sub>x</sub>=  1.16085V\
I<sub>ref</sub> = 0.185mA\

3.Case 3: 1umm
![Image](https://github.com/user-attachments/assets/c8c33457-63b5-4718-9d2c-7c7fa2790d4f)

PMOSFET 1 = length is 180nm, width is 70um : PMOSFET 2 = width is 140nm
NMOSFET = length is 1um, width is 307.294uum\
V<sub>out</sub>=  1.08026V\
V<sub>x</sub>=  1.07969V\
I<sub>ref</sub> = 0.277mA

### Tabular column:
|  Length  |                Width            |   V<sub>x</sub>  | V<sub>out</sub> | I<sub>ref</sub>  |
|----------|---------------------------------|------------------|-----------------|------------------|
|   180nm  | pmos= 70u,140u; nmos=135.867um  |     1.20934V     |     1.20094V    | 0.185mA : 0.37mA |
|   500nm  | pmos= 70u,140u; nmos=256.773um  |     1.16085V     |     1.15935V    | 0.185mA : 0.37mA |
|    1um   | pmos= 70u,140u;nmos=307.294um   |    1.07969V      |     1.08026V    | 0.185mA : 0.37mA |

### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/8c284faf-3cc2-4d40-9825-6c3828aaa47a)
* Peak to Peak volatge = 2.39V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.00847-0.36)+(0.5-0.36)= 2.30V

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/cc6165a4-5622-4568-9bfb-d315660a3fa5)
* Peak to Peak volatge = 2.25V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.0015-0.36)+(0.5-0.36)= 2.3015V

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/a12f8b4f-703c-4cd3-b717-5f2250123bd7)
* Peak to Peak volatge = 2.048V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(0.000575-0.36)+(0.5-0.36)= 2.2V

### AC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/b8b8ad2b-0b46-4004-a28f-6868b577305f)
* 3dB gain = 26.212dB
* 3dB bandwidth= 105.81654MHz

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/7858a8fe-0311-4dd4-8c97-74cea3ade55d)
* 3dB gain = 34.71dB
* 3dB bandwidth= 29.731326MHz

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/2c44f1ca-d88d-4a11-ae5b-f0aff5c9ea2b)
* 3dB gain = 37dB
* 3dB bandwidth= 18.6247MHz

### Inference:
* Reference current is copied or mirrored for other two mosfets.The output currentis exactly equal to the reference current.
* The output current remains the same regardless of the connected load, as long as the transistor stays in the saturation region
* V<sub>x</sub> and V<sub>out</sub> will be same when current gets mirrored.
* As length increases V<sub>x</sub> and V<sub>out</sub> decreases.
* As gain increases bandwidth decreases.
* As the refence current is 0.277mA and doing 1:2 ratio of current mirroring the Current must be copied of the same that is in the form of 0.185mA : 0.37mA..
* In transient analysis we see the maximum output swing caused.

### Comparison Table:
|  Length  |                Width            |   V<sub>x</sub>  | V<sub>out</sub> | I<sub>total</sub>|
|----------|---------------------------------|------------------|-----------------|------------------|
|   180nm  | pmos= 70u,140u; nmos=135.867um  |     1.20934V     |     1.20094V    | 0.185mA : 0.37mA |
|   500nm  | pmos= 70u,140u; nmos=256.773um  |     1.16085V     |     1.15935V    | 0.185mA : 0.37mA |
|    1um   | pmos= 70u,140u;nmos=307.294um   |    1.07969V      |     1.08026V    | 0.185mA : 0.37mA |

<br>

### Circuit 3: 
### Aim : Design the diffrential amplifier having VDD=2V, P<=1mW, Vicm =1V as per the 3rd experiment and perform DC, Transient , AC analysis
### Circuit Diagram:
![Image](https://github.com/user-attachments/assets/7de06806-b2d7-444e-bb9c-d1d51266a55b)

### Components:
PMOSFET-2, NMOSFET- 4, supply volatage-4, current source-1, ground, wires.

### Circuit overview:
1.Differential Pair (M3, M4):
* M3 and M4 form a differential pair using NMOS transistors.
* They receive differential input signals and control the output voltage.

<br>

2.Active Load (M1, M2):
* M1 and M2 are PMOS transistors serving as a current mirror load.
* This helps in converting the differential input signal into a single-ended output.

<br>

3.Current Source (M5, M6, I1):
* M6 is an NMOS transistor acting as a current source to bias the differential pair.
* I1 (0.25 mA) sets the tail current, ensuring proper operation.

<br>

4.Biasing Voltages (V1, V2, V3, V5):
* V1 and V2 (1V) provide gate biasing for M3 and M4.
* V3 and V5 (2V) power the PMOS transistors and ensure proper operation.

<br>
  
5.Output (Vout):
* The output is taken from the common node of M2 and M4.
* It provides an amplified voltage signal.

<br>

Working Principle:
* The circuit functions as an operational amplifier, amplifying the difference between two input signals.
* The current mirror load (M1, M2) ensures proper differential-to-single-ended conversion.
* The biasing network (M5, M6, I1) stabilizes the operating point.

<br>

### Procedure:

1. Build the circuit as per the circuit diagram using LTspice.
2. Set the Vdd as 2V, input common mode voltage as 1V.
3. Download the library file [tsmc018 (1).txt](https://github.com/user-attachments/files/18785407/tsmc018.1.txt)
4. Create a folder. Save the library file and LTspice file to the folder.
5. Import the library file to LTspice using spice directive(.op).
6. Find the current value for the given power rating.
7.  Set the mosfet model name CMOSN for NMOSFET and CMOSP for PMOSFET as given in the library file, length as 180nm and vary the width  of NMOSFET i.e M3 and M4 till you get the exact Q point. Keep Current ratio of M1, M2 as 1:1, M5,M6 as 1:2, M3, M4 as 1:1.
8. DC analysis: In edit simulation option, change to dc offset to get list of values obtained from the circuit. We should get the calculated current value in the simulation result.So that we need to vary the value of width since width is directly proportional to Drain current(Id) keeping other parameters constant. Since we are doing current mirroring the current of both mosfets should be same as the reference current.Keep the reference current as per the calculated design specifications.
9. Transient analysis: In edit simulation option, change from dc offset to transient. Set the dc offset as 0.5V, Amplitude 1mV, frequency 1KHz. Keep stop time for 3ms and run to get the expected waveform.find the maximum output swing.
10. AC analysis : In edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of points per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected ac waveform. Note down the 3dB gain of the circuit and its bandwidth.

<br>

### Calculation:
* P=1mW
* I<sub>total</sub> = P/V = 1mW/2V  <table><td>=0.5mA</td><table>
* I<sub>D1</sub> = I<sub>D2</sub> = I<sub>total</sub>/2 = I<sub>ref</sub> <table><td>=0.25mA</td><table> 
* V<sub>DD</sub>= 2V
* V<sub>inCM</sub>=1V

<br>

### Simulation Results:
### DC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/6472d2c3-037f-4b65-ba03-1e6e13b0f21c)

PMOSFET 1,2 = width is 70um \
M3, M4  = width is 238.7um\
M5 = width is 70um\
M6 = width is 140um\
V<sub>out</sub>=  1.39017V\
I<sub>ref</sub> = 0.277mA\

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/8335044c-f581-451c-a812-1930b087f9fc)

PMOSFET 1,2 = width is 70um \
M3, M4  = width is 238.7um\
M5 = width is 70um\
M6 = width is 140um\
V<sub>out</sub>=  1.39017V\
I<sub>ref</sub> = 0.277mA\


3.Case 3: 1umm
![Image](https://github.com/user-attachments/assets/c8c33457-63b5-4718-9d2c-7c7fa2790d4f)

PMOSFET 1,2 = width is 70um \
M3, M4  = width is 238.7um\
M5 = width is 70um\
M6 = width is 140um\
V<sub>out</sub>=  1.39017V\
I<sub>ref</sub> = 0.277mA\

<br>

### Tabular column:  
|  Length  |                       Width                   |  V<sub>out</sub> | I<sub>ref</sub>  |
|----------|-----------------------------------------------|------------------|------------------|
|   180nm  | M1,M2=70um,M3, M4 =238.7um,M5 =70um, M6=140um |      1.39017V    |  0.277mA         |
|   500nm  | pmos= 70u,140u; nmos=256.773um                |      1.15935V    |  0.277mA         |
|    1um   | pmos= 70u,140u;nmos=307.294um                 |      1.08026V    |  0.277mA         |

<br>

### Transient analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/d1f8f534-fc52-464d-ab68-8d3d93f859bc)
* Peak to Peak volatge = 2.7794V

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/cc6165a4-5622-4568-9bfb-d315660a3fa5)
* Peak to Peak volatge = 2.25V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(-0.0015-0.36)+(0.5-0.36)= 2.3015V

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/a12f8b4f-703c-4cd3-b717-5f2250123bd7)
* Peak to Peak volatge = 2.048V
* Maximum output swing = Vdd-Vov2+Vov3 = 1.8-(0.000575-0.36)+(0.5-0.36)= 2.2V

<br>

### AC analysis:
1.Case 1: 180nm
![Image](https://github.com/user-attachments/assets/d090373d-b863-4904-a226-598fdcc27d55)
* 3dB gain = 32dB
* 3dB bandwidth= 107.9033MHz

<br>

2.Case 2: 500nm
![Image](https://github.com/user-attachments/assets/7858a8fe-0311-4dd4-8c97-74cea3ade55d)
* 3dB gain = 41.131
* 3dB bandwidth= 17.075083MHz

<br>

3.Case 3: 1um
![Image](https://github.com/user-attachments/assets/2c44f1ca-d88d-4a11-ae5b-f0aff5c9ea2b)
* 3dB gain = 37dB
* 3dB bandwidth= 18.6247MHz
