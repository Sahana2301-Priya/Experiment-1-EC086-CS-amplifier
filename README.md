# Experiment-1-EC086-CS-amplifier
# DC analysis,AC analysis and Transient Analysis of Common Source Amplifier
A common-source amplifier is a type of FET amplifier where the input signal is applied to the gate, and the output is taken from the drain. The source is typically grounded. It provides high voltage gain and **180-degree phase shift** (inversion) between the input and output. It’s widely used for amplifying weak signals in analog circuits, with the voltage gain determined by the load resistor and the transconductance of the FET.

### <u>Key Components and their roles</u>:
1. **Rd (Drain Resistor):** Provides the required voltage drop to amplify the signal.
2. **W (Transistor Width):** Affects the transconductance (gm), influencing gain and bandwidth.
3. **Vdd (Drain Supply Voltage):** Provides DC biasing for the NMOS transistor.
4. **AC Input (SINE source):** The test signal used to analyze circuit response.

**Circuit diagram:**
![circuit](https://github.com/user-attachments/assets/e77c51d3-075d-4a7b-b173-9035c590d979)

This report presents the DC analysis, AC analysis, Transient analysis of a common-source NMOS amplifier. The objective of this analysis is to determine the DC biasing conditions, gain and output impedence using Transient analysis, and to find frequency response using AC analysis.

## **Component Details:**
The circuit consists of a TSMC 500nm NMOS transistor (CMOSN), a drain resistor and two voltage sources. The drain resistor limits the current through the transistor and affects the small-signal gain. The NMOS transistor operates in saturation region, making it suitable for amplification.
**Model:** **CMOSN**

**Channel Length:** 500nm

**Channel Width:** 450nm

**Threshold Voltage:** 0.366V

**Resistor:** 1000 ohm

**Supply Voltage:** 1.8V

**DC Voltage:** 0.9V

**Amplitude:** 50mV

**Frequency:** 1kHz

# DC analysis:
![Screenshot (4)](https://github.com/user-attachments/assets/ace138bb-4999-45ce-af52-ea14d6f1847b)


If the Power dissipation is 50µW across the resistor, then the current through the resistor is given by:
**Id** = Power/Voltage = 50µ / 1.8 = **27.778 µA**

**Vov = Vgs - Vth = 0.9 - 0.36 = 0.534 V**.
As 'L' is 500nm and 'W' is 450nm the Id value will be 25.9112 µA. Keeping the L constant and start varying the width to get the required current Id value from the simulation.
| Width     | Current(Id) |
|:---------|:---:|
| 400nm   | 23.4594 µA|
| 450nm     | 25.9112  µA |
| 480nm | 27.384 µA|
|485nm  | 27.6295  µA |
|487nm | 27.7277 µA|


![current dc analysis](https://github.com/user-attachments/assets/ff164e37-7b1d-4ecc-b6e7-9eec18d31a55)

From the simulation result we got the approximate current value of **27.7277 µA ≈ Id** and **Vout = 1.77227 V**

The output load line equation is given by


**Vout = Vdd - (Id * Rd)**


   Rd = (Vdd - Vout) / Id

   
    = (1.8 - 1.77227)/27.7277 µA

    
   = 1000.082 Ω

Therefore **Rd = 1000.082 Ω**

The DC operating point analysis confirms that the NMOS transistor operates in the saturation region with Id ≈ 27.7277μA.


**Vds = Vout =  1.77227 V**


Vov = Vgs - Vth = 0.9 - 0.366 = 0.534V


i.e **Vds > ( Vgs - Vth)**


# AC analysis:

In this experiment, we will conduct an AC analysis to evaluate the frequency response of the circuit, including parameters such as gain, output impedance, and phase shift. By applying a small-signal AC input, we can assess how the circuit amplifies signals and how it behaves under varying frequencies.

For the same circuit, in the configure analysis select decade as type of sweep, with starting frequenciy o.1Hz and stop frequency as 1THz.

**Circuit diagram:**
![ac analysis](https://github.com/user-attachments/assets/eccc5409-b35b-41c4-ba8e-0fda4dfa59f1)

**Voltage gain = Vout / Vin**

= 1.77227/ 0.9 = 1.969 V

 **in dB = 20log10(Vout / Vin)**


     = 20log10(1.969)

     
     = 5.884dB - 3dB

**in dB = 2.884 dB**


# Transient Analysis:

Transient analysis in a common-source amplifier examines how the amplifier reacts to time-varying inputs, such as step or sinusoidal signals. It helps assess the time-domain response, including key parameters like rise time, settling time, and distortion from capacitive effects. The analysis shows how quickly the output responds and whether there are any delays, overshoot, or instability.

For this experiment, we will find the gain and output impedence of the circuit.
For the same circuit, we will perform the transient analysis keeping the sinusoidal voltage signal  **DC offset as 0.9V**, and **amplitude 50mV**, and **frequency = 1kHz**
And the **AC amplitude as 1V**.
In the configure analysis select  **stop time as 5ms**.

**Circuit Diagram:**

![transient time varying signal](https://github.com/user-attachments/assets/c7181ce3-7e6b-44eb-8e96-dc7db4fbb09a)

Overall gain (Av) = Vout / Vin
      = 1.969

From calculations:

**gm = 2(Id)/(Vov)**

i.e Vov = Vgs - Vth


   = 2(27.7277.5μ) / ( 0.534)

   
**gm = 103.84 μA/V**

Rout = Rd = 1000 Ω


Overall gain :

**Av = gm * Rout**
             
    =  103.84 μ * 1000
    
   **Av = 0.1038**


   # Results:
   
Id = 27.7277.5μA

Vov = 0.534 V

Vout = 1.77227 V

Voltage gain = 1.969 V (in dB = 2.884 dB)

gm = 103.84 μA/V

Overall gain =  0.1038

# Inference:

 **DC Analysis:**
  The transistor is working correctly in the saturation region, which is needed for amplification. The current flowing through the circuit is 27.7277.5 µA, and the resistor value 1kΩ is verified. The output voltage is around 1.77227V, and the input voltage is 0.9V. The transistor is properly biased for amplification.


**AC Analysis:**
The circuit maintains a stable gain over different frequencies, proving it works well for amplification. The voltage gain is 1.969 (or 2.884 dB), and the -3 dB point (where gain drops) confirms its frequency limits. Simulation and theoretical results are in close agreement, with minor variations due to parasitic effects.


**Transient Analysis:**
The output signal is amplified and flipped by 180° (inverted), which is expected in a Common Source amplifier. The gain of the circuit is around 1.969. The circuit has an output resistance of 1kΩ, affecting how it drives the next stage in a system.



   









  










