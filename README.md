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

# Procedure:

1.Create a new folder and name it as project file.Save the LT spice file in this folder.

2.Name the mosfet as CMOSN and the length as 500nm and width as 450um initially.

3.**DC Analysis**: Set up the circuit as per the circuit diagram with proper connections ensuring valid circuit for further analysis. Apply the DC voltage of Vdd=1.8V and Vgs = 0.9 V . Go to simulate option in the tab and edit simulation command, click on DC analysis and press ok.(.op) Click on Run in the tab menu to get the DC operating point ,Vout and Id.

4.**Transient Analysis:** Apply a sine wave input of Vgs=0.9V with an amplitude of 50mV and frequency of 1kHz by going to advanced menu in the voltage setting option.go to simulate option in tab ,edit simulation command , click on transient analysis and give the stop time as 5m and click ok. Now Run to visualise the response of the circuit to a time varying signal.

5.**AC Analysis:** Go to spice directive and give the library file path for the simulator to access the data through the path . Go to simulate option in the tab , edit simulation command , click on AC analysis and mention the time of sweep as decade , no of points as 20 and frequency as 1kHz to 1THz and click on ok. Now Run to analyze the gain and frequency response of the circuit


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
In the configure analysis select  **stop time as 5ms**. There is **180 degree phase shift** between input and output and a DC level phase shift observed.

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












## Circuit-2:

A **Diode connected mosfet** transistor always is in saturation and acts as a constant current source and acts as a amplifier. The different type of analysis are done here also DC Analysis, AC Analysis and Transient analysis. The drain current obtained is given by the formula:

**Id = 1/2 kn Vov2** ; 

**Vov=Vgs-Vth** and 

**kn=un Cox W/L**



**Circuit Diagram:**
![cir](https://github.com/user-attachments/assets/675b9a86-65e0-481b-9489-54944bcecc6b)

The procedure is same as above;.for the pmos name it as CMOSP and set the **length as 500nm** and **width as 487nm** respectively.

# DC analysis:

![Screenshot (14)](https://github.com/user-attachments/assets/85fcd20a-d081-4a72-aaf1-3e79ac8d499e)


the **Q point** is (**1.45223 V , 27.394 μA**)


# AC analysis:

![ac](https://github.com/user-attachments/assets/f9f4bac8-0717-45e1-9775-b49c78ae5f78)

**Voltage gain = 0.806**


# Transient analysis:

![trans](https://github.com/user-attachments/assets/acafd7c3-aec1-4cbc-a22b-3a807b2b26ab)

There is **180 degree phase shift** between input and output and a DC level phase shift observed.


# Results:

Id = 27.394 μA

Vov = 0.534 V

Vout = 1.4522 V

Voltage gain =  0.806

# Inference:

1.The Current Id is dependent on width and hence it changes when the width changes whereas the remaining parameters remain constant.

2.DC Analysis ensures proper biasing and hence the mosfet operates in saturation and Q point stability is attained.

3.The Transient analysis gives the response of the circuit to time domain ssignal and determines how quickly the circuit responds to variation.
This is essential in high speed applications.

4.AC Analysis helps in designing circuits with desired gain and helps in impedance matching. Also helps in understanding the frequency response and small signal behaviour of the circuit.

5.Together all the analysis helps in designing and opyimising an amplifier.




   









  










