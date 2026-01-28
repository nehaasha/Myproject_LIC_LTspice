# DAY 1
## Introduction to MOSFET and Mixes- Signal IC Architecture

### Purpose of the session:
Day 1 of the workshop focused on building a strong foundation in core VLSI concepts. The session covered the fundamental concepts of MOSFETs, with emphasis on device equations and operating regions. In addition, an introduction to mixer signal ICs was provided, including a detailed explanation of the BGR circuit. The session also included an overview of the Cadence design environment, where the instructor explained the uses and importance of various toolkits in Cadence for circuit design and analysis.
### Introduction to Mixed Signal ICs
Mixed Signal Integrated Circuits (ICs) are circuits that contain both analog and digital components on the same chip. These ICs are designed to process real-world analog signals (such as voltage, current, temperature, sound, and light) and also perform digital processing (such as logic operations, control, and data storage).

In modern electronic systems, most signals from sensors and the environment are analog in nature, while processing and control are done digitally. Mixed signal ICs provide an efficient way to interface between the analog and digital domains.

+ Common examples of mixed signal ICs include:
+ Analog-to-Digital Converters (ADC)
+ Digital-to-Analog Converters (DAC)
+ Phase Locked Loops (PLL)
+ Power Management ICs (PMIC)
+ RF transceivers
+ Sensor interface ICs
+ Microcontrollers with built-in ADCs and DACs

Mixed signal ICs are widely used in applications such as mobile phones, IoT devices, automotive electronics, medical instruments, and communication systems.

### Why MOSFETs Are Preferred Over BJTs in Mixed Signal ICs
MOSFETs (Metal-Oxide-Semiconductor Field-Effect Transistors) are preferred over BJTs (Bipolar Junction Transistors) in mixed signal ICs for several important reasons:

+ Low Power Consumption
+ High Input Impedance
+  Ease of Integration (CMOS Technology)
+ High Packing Density
+ Lower Noise Coupling in Digital Circuits
+ Scalability with Technology Shrinking
+ Better Compatibility with Digital Blocks

### MOSFET structure and regions of operation

**1. MOSFET Structure (n-channel MOSFET)**

A MOSFET mainly consists of four terminals:

+ Gate (G)
+ Source (S)
+ Drain (D)
+ Substrate / Body (B)

Construction:
+ The substrate is made of p-type semiconductor (for n-channel MOSFET).
+ Two heavily doped n⁺ regions are formed in the substrate:
      1.One is the Source
      2.The other is the Drain
+ A thin layer of silicon dioxide (SiO₂) is grown on the substrate between source and drain.
+ A metal or polysilicon gate is placed on top of the SiO₂ layer.
+ The SiO₂ layer acts as an insulator, so no direct current flows into the gate.

**2. Physical Operation of MOSFET (n-channel)**

The operation depends on the gate-to-source voltage (VGS).

Case 1: VGS = 0 (MOSFET OFF)

+ No voltage is applied to the gate.
+ There is no conducting channel between source and drain.
+ The p-type substrate blocks electron flow.
+ Drain current (ID = 0)
+ Therefore,  MOSFET is in cut-off region.

Case 2: 0 < VGS < VTH (Depletion region)

+ A small positive voltage is applied to the gate.
+ Positive charges on the gate repel holes in the substrate.
+ A depletion region is formed near the oxide layer.
+ Still, no continuous channel is formed.
+ ID ≈ 0
+ Therefore, MOSFET remains OFF.

Case 3: VGS ≥ VTH (Inversion & Conduction)

+ When gate voltage reaches the threshold voltage (VTH):
+ Electrons are attracted to the surface under the oxide.
+ A thin n-type inversion layer (channel) is formed.
+ This channel connects source and drain.
+ If VDS is applied, electrons flow from source to drain.
+ Drain current (ID) flows
+ Therfore, MOSFET turns ON.

**3. Regions of Operation**

**Cut-off Region**

+ VGS < VTH
+ No channel
+ ID = 0
+ ID​=0

**Triode (Linear) Region**

+ VGS ≥ VTH and small VDS
+ Channel is formed
+ MOSFET behaves like a variable resistor
+ I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L [(V<sub>GS</sub>-V<sub>TH</sub>)(V<sub>DS</sub>)-(V<sub>DS</sub>)<sup>2</sup>/2)]

**Saturation Region**

+ VGS ≥ VTH and large VDS
+ Channel pinches off near drain
+ ID becomes almost constant
+ Used in amplifiers
+ I<sub>D</sub> = 1/2U<sub>n</sub>C<sub>ox</sub>W/L (V<sub>GS</sub>-V<sub>TH</sub>)<sup>2</sup>

### Challenges Faced in Mixed Signal Generation
+ Noise and Interference
+ Clock Jitter and Timing Errors
+ Analog–Digital Isolation
+ Power Supply Noise
+ Signal Integrity Issues
+ Limited Resolution and Accuracy
+ Process Variations
+ Thermal Effects

### Role of BJT in Mixed-Signal IC
BJTs play an important role in mixed-signal ICs by providing high gain, low noise, and good linearity for analog signal processing. They are widely used in amplifiers, current mirrors, and biasing circuits to ensure stable and accurate operation. Due to their predictable temperature characteristics, BJTs are essential in bandgap reference circuits. They also offer better matching and high-speed performance, making them suitable for interfacing and buffering between sensitive analog blocks and noisy digital sections.

### Major Analog Blocks in Chip Design :
**1. Phase Locked Loop (PLL):**
PLL is used to generate a stable and accurate clock signal by locking the output frequency and phase to a reference clock, and it is widely used in communication systems and processors.

**2. Bandgap Reference (BGR):**
BGR provides a stable reference voltage that is independent of temperature, supply voltage, and process variations, making it essential for reliable operation of analog and mixed-signal circuits.

**3. Low Dropout Regulator (LDO):**
LDO is used to supply a constant and noise-free regulated voltage to sensitive analog and digital blocks even when the input voltage is close to the output voltage.

### Mixed Signal IC Design FLow

Domain-specific design

1. Analog/RF
+ Schematic capture
+ Analog simulation\
2. Digital
+ Design entry
+ Behavioral simulation\
3. Mixed-signal analysis\
4. Physical design\
5. Analog/RF
+ Physical layout
+ Physical verification
+ Post layout simulation\
6. Digital
+ Synthesis
+ Place and route
+ Functional verification\
7. Full chip assembly & physical verification\
8. Mixed-signal functional verification\/
9. Tape-out

### Bandgap Reference Circuit
<img width="411" height="371" alt="Image" src="https://github.com/user-attachments/assets/85221bae-7ac1-4fda-b50b-dc4a56145184" /> <img width="259" height="229" alt="Image" src="https://github.com/user-attachments/assets/b846f6a1-e52d-42b8-9c72-d5446b17e256" />

**Temperature Independent Reference**
+ It provides reference voltages and/or currents with little dependence to temperature which are useful in many analog circuits. 
+ Key idea: add two quantities with opposite temperature coefficient with proper weighting -  the resultant quantity exhibits zero temperature
coefficient.
+ base-emitter voltage of bipolar transistors or, more generally, the forward voltage of a pn-junction diode exhibits a **negative TC**.∂VBE/∂T ≈ -1.5 mV/K.
+ if two bipolar transistors operate at unequal current densities, then the difference between their base-emitter voltages is directly proportional to the absolute
temperature
+ VBE difference exhibits a positive temperature coefficient i.e **Positive TC**, this TC is independent of the temperature or behavior of the collector currents
+ With the negative- and positive-TC voltages obtained, we can now develop areference (VREF ) that has a nominally zero temperature coefficient.,\
**VREF = α1VBE + α2(VTln(n))**,\
where VTln(n) is the difference between the base-emitter voltages of the two bipolar transistors operating at different current densities.
+ the reference voltage exhibiting a nominally-zero TC is given by a few fundamental numbers: bandgap voltage of silicon, Eg/q, the temperature exponent of mobility, m, and thethermal voltage, VT.\
  V<sub>ref</sub> ~ V<sub>BE</sub>+17.2V<sub>T</sub>\
  V<sub>ref</sub> ~ (E<sub>g</sub>/q)+(4+m)V<sub>T</sub>\
  The term “bandgap” is used here because as T=0, V<sub>ref</sub> ~ (E<sub>g</sub>/q)
+ Hence the PTAT (proportional to absolute temperature) voltage is added to the CTAT (complementary to absolute temperature) voltage (like VBE of a BJT), the resulting voltage converges to a value near Eg/q (Eg divided by electronic charge) at 0 K. Therefore they are called as BGR circuits.

### Introduction to Cadense Tool
Cadence Virtuoso is a specialized tool within the Cadence EDA suite used for analog, digital, and mixed-signal IC design. It provides an integrated environment for schematic capture, circuit simulation, layout design, and verification. Virtuoso allows designers to create complex circuits, perform transistor-level simulations, and generate layouts that can be fabricated as integrated circuits. Its tight integration of design and verification tools ensures accurate, high-performance designs with reduced development time.\
**Steps to Create a Library and Cell in Cadence Virtuoso:**
+ Open Cadence Virtuoso, create a folder, and open a terminal. Type csh, then source /home/install/cshrc, and finally virtuoso to launch the tool.
+ In Virtuoso, go to Tools → Library Manager, then File → New → Library. Name it BGR_test and attach it to the existing library GPDK045.
+ To create a cell, select BGR_test, then File → New → Cell View. Name the cell test, set View and Type as schematic, and click OK.\
**Steps to Add Instances in Cadence Virtuoso:**
+ Press I on the keyboard to add an instance.
+ To add a resistor, select analogLib as the library and RES as the cell.
+ To add an NMOS transistor, select GPDK045 as the library and NMOS_1V as the cell.
+ To add power and ground:
VDC: library = analogLib, cell = Vdc\
GND: library = analogLib, cell = gnd\
VDD: library = analogLib, cell = Vsin\
**Basic Operations in Cadence Virtuoso:**
+ To add a component, press I.
+ To change the value of a component, select it and press Q.
+ To connect wires, press W.
+ To assign a wire name, press L.\
**DC analysis:**
+ Launch ADE L and select Analysis → Choose, then set DC Analysis. Save the DC operating point.
+ Go to Output, select the signals to be plotted, choose Select on Device, and run the simulation to get the output.
+ To view all DC operating points, go to Results → Annotate → DC Operating Point.
+ To check parameters of each component, go to Results → Print → DC Operating Point.
+ To simulate for different component values, select the component, open Edit Properties, replace the value with a variable name, and click OK.
+ In ADE L, go to Variables → Copy from Cell View, set the new values, and run the simulation to get updated outputs. \
**Parameter Sweep (DC Range Analysis):**
+ In ADE L, select Edit → Sweep Variable.
+ Choose the design variable (e.g., Vbias), set Start and Stop values, sweep type as Linear, and number of steps (e.g., 5).
+ Click OK and run the simulation.
+ For multiple parameters, use EDL → Parameter Analysis, select variable names, define ranges, and run.\
**Transient Analysis:**
+ Go to Simulation → Choose → Transient.
+ Set the Stop Time and select Conservative option, then run the simulation.\
**AC Analysis:**
+ Go to Simulation → Choose → AC Analysis.
+ Set Start and Stop frequencies, sweep type as Logarithmic, and points per decade.
+ Select the input voltage, open Edit Properties, and set AC Magnitude = 1 V, then run the simulation.\
**Saving the Schematic:**
+ In ADE, press Fission, choose Save State, select the cell view, and click OK.

### Example Circuit
![Image](https://github.com/user-attachments/assets/1714bbce-dd02-4494-9203-d82ad65b5462)
