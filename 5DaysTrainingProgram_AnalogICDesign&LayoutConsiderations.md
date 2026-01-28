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
+ 

**Saturation Region**

+ VGS ≥ VTH and large VDS
+ Channel pinches off near drain
+ ID becomes almost constant
+ Used in amplifiers
