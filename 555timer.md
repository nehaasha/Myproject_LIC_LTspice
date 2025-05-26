# Monostable multivibrator using 555 timer IC .
## Aim
### Generate pulse of width 0.5 ms using input triggers.
A monostable multivibrator is an electronic circuit that has one stable state and one temporary (quasi-stable) state. It remains in its stable state until an external trigger pulse is applied, upon which it switches to the quasi-stable state for a fixed period of time and then automatically returns to its stable state. This circuit is commonly used for generating precise time delays, single pulses, and debouncing mechanical switches. The duration of the output pulse is determined by external components, typically a resistor and a capacitor. One of the most common implementations is using the 555 timer IC in monostable mode, where the output pulse width is given by the formula T = 1.1 × R × C. Monostable multivibrators are widely used in digital electronics for timing applications, signal conditioning, and pulse generation.

## Working
In a monostable multivibrator built with a 555 timer, the output remains in its stable state until a trigger is received. This stable state occurs when both the internal transistor and capacitor are essentially "shorted."

When the voltage at pin 2 of the 555 IC drops below a certain threshold, the output switches to a high state. This high state is referred to as the quasi-stable state. The circuit then transitions from its stable state to this quasi-stable state. At this point, the internal discharge transistor turns off, allowing the capacitor to begin charging towards the Vcc (supply voltage) through resistor R1. The charging time is governed by the time constant R1C1.   

As the capacitor charges, its voltage steadily increases. Once the capacitor's voltage exceeds 2/3 of Vcc, it triggers the internal control flip-flop, which in turn switches off the 555 timer IC. This action causes the output to return to its original stable (low) state from the quasi-stable state.   

The duration of this output pulse, often denoted as T, is calculated by the formula:
T=1.1×R×C

where R is in Ohms (Ω) and C is in Farads.   

Ultimately, in a 555 timer monostable multivibrator, the output typically stays low until a trigger input is applied. Upon triggering, the output goes high for a specific duration determined by the RC components, and then returns to its low state. This behavior is commonly used in "push-to-operate" systems where a single input press generates a controlled output pulse.   


Sources and related content
## Circuit Diagram:
![image](https://github.com/user-attachments/assets/bb37f20b-66b4-4744-901d-e0262de2926d)

## Calculation:
Given that T=0.5ms and assume c=.1uF.

T=1.1RC



R =  0.5mS/(1.1×1uF) = 4.5454 KΩ.
 
## Output Waveform
![image](https://github.com/user-attachments/assets/4ff3113f-d845-4684-b053-e50b7d29faac)

In the above circuit when the trigger pulse is lesser then 1/3 Vcc, We get output as high.
## Inference:
1.When a negative trigger pulse is applied to pin 2 of the 555 timer IC, the circuit switches from its stable state to the quasi-stable state.

2.As a result, the output (pin 3) goes HIGH and remains in this state for a duration of 0.5 milliseconds.
3.This pulse duration is determined by the values of the external resistor (R) and capacitor (C) connected to the circuit, based on the formula T = 1.1 × R × C.

4.After 0.5 ms, the capacitor charges to 2/3 of the supply voltage, causing the timer to automatically reset and bring the output back to LOW.

5.The circuit then waits in its stable (LOW) state for the next trigger pulse.

6.This confirms that the 555 timer IC accurately generates short, timed output pulses in monostable mode.
# Astable multivibrator and monostable multivibrator using 555 timer IC
## Aim
## Generate pulse of width 0.5ms using 555 timer IC.
## Theory
An astable multivibrator, often called a "free-running" multivibrator, is a circuit that generates a continuous rectangular waveform. Unlike its monostable counterpart, it doesn't need an external trigger to switch its output state. Instead, the duration of its high and low output states is determined by two resistors and a capacitor connected externally to the 555 timer chip.   


In a differentiator amplifier circuit, the positions of the capacitor and resistor are swapped compared to an integrator. Here, the capacitor 
 is connected to the input of the inverting amplifier, while the feedback element across the operational amplifier remains a resistor 
 This circuit performs the mathematical operation of differentiation. Essentially, the faster or larger the change in the input voltage signal, the greater the input current, and consequently, the more pronounced the output voltage change will be, often appearing as a "spike." Similar to the integrator, the RC network formed by the resistor and capacitor plays a crucial role, with the capacitor's reactance 
 being particularly significant in the differentiator's performance.   

A clipper circuit is used to remove or "clip" specific portions of a waveform, such as negative voltage spikes. The output of this clipper circuit then serves as the trigger signal for a monostable multivibrator.   

A monostable multivibrator, also known as a one-shot, has only one stable state. Its purpose is to generate a single output pulse of a specific width (either high or low) when an external trigger pulse is applied. This trigger pulse initiates a timing cycle, causing the output to change its state. The output then remains in this second, unstable state for a duration determined by the RC time constant of its capacitor (C) and resistor (R), after which it automatically reverts to its original stable state. It will stay in this stable state until another input signal is received. Monostable multivibrators are capable of producing much longer rectangular waveforms. The rising edge of the output waveform coincides with the external trigger pulse, while the falling (trailing) edge is governed by the RC time constant of the feedback components. This RC time constant can be adjusted over time to produce a series of pulses, each with a fixed time delay relative to the original triggered pulse.
## Procedure
