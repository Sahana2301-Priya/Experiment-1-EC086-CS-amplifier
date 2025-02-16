# Experiment-1-EC086-CS-amplifier
# DC analysis,AC analysis and Transient Analysis of Common Source Amplifier
A common-source amplifier is a type of FET amplifier where the input signal is applied to the gate, and the output is taken from the drain. The source is typically grounded. It provides high voltage gain and **180-degree phase shift** (inversion) between the input and output. It’s widely used for amplifying weak signals in analog circuits, with the voltage gain determined by the load resistor and the transconductance of the FET.

### <u>Key Components and their roles</u>:
1. **Rd (Drain Resistor):** Provides the required voltage drop to amplify the signal.
2. **W (Transistor Width):** Affects the transconductance (gm), influencing gain and bandwidth.
3. **Vdd (Drain Supply Voltage):** Provides DC biasing for the NMOS transistor.
4. **AC Input (SINE source):** The test signal used to analyze circuit response.

**Circuit diagram:**
![Circuit Diagram](https://github.com/Sahana2301-Priya/Experiment-1-EC086-CS-amplifier/main/circuit.png
)











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









