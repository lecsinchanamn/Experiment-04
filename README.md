# Experiment-04
# Design analysis the the MOS differential amplifer circuit for the following specifications for the all three circuits.
- VDD =O.9V
- VinCM =0v
- VSS = -0.9V
- VoCM =0v
- P< 2mW
- VP =-0.7V
# What is differential amplifer?
A differential amplifier is an electronic circuit that amplifies the difference between two input signals while rejecting any signals that are common to both inputs (called common-mode signals).
A basic MOS differential amplifier consists of two matched MOSFETs (M1 and M2) whose sources are connected together and biased using a constant current source. The drains are connected to load elements such as resistors or active loads.
- Formula:
Output ∝ (V1 - V2)
 # Working:
1. Takes two inputs: V1 and V2
- If V1 = V2 → Output = 0 (ideal case)
- If V1 ≠ V2 → Output = Amplified difference
- Rejects common noise present in both inputs
2. Current Flow:
- Current splits between M1 and M2
- Vin1 > Vin2 → M1 gets more current
- Vin2 > Vin1 → M2 gets more current
3. Small Input:
- Both transistors ON
- Works in linear region (good amplification)
4. Gain:
Av = gm × Rout
5. Transconductance:
gm = (2 × ID) / Vov
6. Large Input:
- If input difference is large (vid > 2Vov):
  → One transistor OFF
  → Other carries all current
  → Output becomes non-linear
# Key Features:
- High Common Mode Rejection (CMRR)
- Accurate signal amplification
- Noise reduction
# Applications:
- Operational Amplifiers (Op-Amps)
- Audio systems
- Sensor circuits
- Communication systems
# CIRCUIT 01
#  Design ans analysis the differential amplifer with the resistive load
# Definition:
A differential amplifier with resistive load is a circuit that amplifies the difference between two input voltages using two transistors and resistors (RD) as loads.
1. Circuit:
- Two matched transistors (M1, M2)
- One constant current source (ISS)
- Two resistors (RD) at the drains
2. Input:
- vid = Vin1 − Vin2
3. Working:
- Total current (ISS) is divided between M1 and M2
- Vin1 > Vin2 → M1 current increases, M2 decreases
- Vin2 > Vin1 → M2 current increases, M1 decreases
4. Output:
- Current through RD creates voltage drop
- Output is taken at drains
- Produces differential output voltage

5. Small Input:
- Both transistors ON (saturation)
- Linear operation
- Output proportional to input
6. Large Input:
- One transistor OFF
- Other carries full current
- Non-linear behavior
7. Gain:
Av = gm × RD
8. Transconductance:
gm = (2 × ID) / Vov
DIFFERENTIAL AMPLIFIER DESIGN PARAMETERS (Simple Table)
# Circuit parameter given:

| Parameter                     | Value / Details                     |
|--------------------------------|-----------------------------------|
| **Power Limit (P)**            | ≤ 1.8 mW                           |
| **Load Capacitance (CL)**      | 10 pF                              |
| **MOSFET Channel Length (Ln)** | 480 nm                             |
| **Threshold Voltage (VT)**     | ≈ 0.36 V                           |
| **Supply Voltage (VDD)**       | +0.9 V                             |
| **Negative Supply (VSS)**      | −0.9 V                             |
| **Tail Node Voltage (Vp)**     | −0.7 V                             |
| **Input Common-Mode Voltage**  | Vin,CM = 0 V                        |
| **Output Common-Mode Voltage** | Vo,CM = 0 V                         |
| **Technology**                 | TSMC 180 nm                        |

# Circuit diogram
https://github.com/lecsinchanamn/Experiment-04/blob/46c4f172a8a7dadc5ce9e2321c71c1a5fb978056/Ckt%2001%20ckt%20diogram.png

# Calcultion table with justification

| Parameter / Calculation        | Value / Formula / Notes                                      | Justification / Explanation                                                |
|--------------------------------|-------------------------------------------------------------|----------------------------------------------------------------------------|
| **Total Power (P)**            | P = (VDD − VSS) × ISS = 1.8 × 1 mA = 1.8 mW               | Ensures power constraint is satisfied; fully utilizes available budget.   |
| **Tail Current (ISS)**         | ISS ≤ 1 mA → chosen ISS = 1 mA                             | Maximum current that meets power constraint and ensures proper bias.      |
| **Drain Currents (ID1, ID2)**  | ID1 = ID2 = ISS / 2 = 0.5 mA                                | Balanced differential amplifier splits tail current equally.              |
| **Output Voltage (Vout)**      | Vout = VDD − ID × RD = 0 V                                  | Common-mode output centered at 0 V for linear operation.                  |
| **Load Resistance (RD)**       | RD = (VDD − Vout) / ID = 0.9 / 0.5 mA = 1.8 kΩ             | Converts drain current into voltage; ensures proper output swing.         |
| **Input Common-Mode Voltage**  | Vin,CM = 0 V                                               | Ensures gates are at the same reference for differential operation.       |
| **Gate Voltages (VG1, VG2)**  | VG1 = VG2 = 0 V                                            | Matches input common-mode to maintain symmetry.                            |
| **Source Voltage (VS)**        | VS = Vp = −0.7 V                                           | Sets tail node voltage to bias both transistors correctly.                |
| **Gate-Source Voltage (VGS)**  | VGS = VG − VS = 0 − (−0.7) = 0.7 V                         | Ensures MOSFET is properly turned on.                                      |
| **Overdrive Voltage (VOV)**    | VOV = VGS − VT = 0.7 − 0.36 = 0.34 V                        | Determines level above threshold; ensures saturation operation.           |
| **Drain Voltage (VD)**         | VD = Vout = 0 V                                            | Keeps drain voltage centered for proper differential output.              |
| **Drain-Source Voltage (VDS)** | VDS = VD − VS = 0 − (−0.7) = 0.7 V                          | VDS > VOV → confirms both transistors operate in saturation.             |
| **Saturation Check**           | VDS > VOV → 0.7 > 0.34                                     | Confirms linear region of operation.                                      |
| **Bias Point Summary**         | VG = 0 V, VS = −0.7 V, VD = 0 V, VGS = 0.7 V, VDS = 0.7 V  | Provides operating point for linear amplification.                        |
| **Width Calculation (Theoretical)** | W = 2 × ID × L / (μnCox × VOV²) ≈ 17.57 μm               | First-order calculation using ideal MOSFET equations.                     |
| **Width Calculation (Simulation)**  | W ≈ 28.475 μm                                             | Fine-tuned in simulation to account for non-ideal effects and exact bias. |
| **Notes**                      | —                                                           | Width deviation due to channel modulation, mobility degradation, and other non-idealities. |

# DC Analysis
https://github.com/lecsinchanamn/Experiment-04/blob/7262382e6cf850db5b6f745db8b03de8090f55aa/Ckt%2001%20DC%20analysis.png

# Input Common-Mode Range (ICMR)  
Input Common-Mode Range (ICMR)  for which all MOSFETs in a differential amplifier remain in saturation, 
ensuring linear operation.
# Points:
- Ensures linear behavior of the amplifier.
- If input goes outside this range, transistors may enter triode or turn OFF.
- Depends on supply voltages, threshold voltage (VT), overdrive voltage (VOV), and transistor configuration.
# Typical NMOS Differential Pair:
ICMR_min ≈ VS + VOV
ICMR_max ≈ VDD − VOV − VDSsat_load
Where:
VS = Source voltage of the differential pair
VOV = Overdrive voltage (VGS − VT)
VDSsat_load = Minimum VDS for load transistor to stay in saturation

# DIFFERENTIAL INPUT VOLTAGE RANGE

| Parameter                     | Value / Formula                  | Explanation / Justification                                      |
|--------------------------------|---------------------------------|------------------------------------------------------------------|
| Condition for Linear Operation | |Vid| ≤ 2 × VOV                  | Linear behavior when both transistors stay in saturation         |
| Overdrive Voltage (VOV)        | 0.34 V                           | From bias and transistor calculation                              |
| Maximum Differential Input (Vid max) | 2 × 0.34 = 0.68 V             | Upper limit for linear operation                                   |
| Minimum Differential Input (Vid min) | −0.68 V                        | Lower limit for linear operation                                   |
| Final Linear Input Range       | −0.68 V ≤ Vid ≤ 0.68 V          | Safe differential input range for linear amplification           |

# Input Common-Mode Range (ICMR)  

# Maximum Input Common Mode Voltage

| Parameter                        | Value / Formula                       | Justification / Explanation                                        |
|----------------------------------|--------------------------------------|--------------------------------------------------------------------|
| **Drain-Source Condition**        | VDS ≥ VOV                             | Ensures NMOS transistors remain in saturation.                     |
| **Drain Voltage (VD)**            | VD = 0 V                              | From previous bias calculation.                                     |
| **Source Voltage (VS)**           | VS = −0.7 V                           | Tail node voltage sets source reference.                            |
| **Drain-Source Voltage (VDS)**    | VDS = VD − VS = 0 − (−0.7) = 0.7 V   | Confirms transistor is in saturation (VDS > VOV).                  |
| **Maximum Input Common-Mode (VICM max)** | VICM(max) = VD + VT = 0 + 0.36 = 0.36 V | Maximum input voltage while keeping NMOS in saturation.            |
| **Minimum Input Common-Mode (VICM min)** | VICM(min) ≈ −VOV = −0.34 V           | Minimum voltage to keep differential pair in saturation.           |
| **Final Input Common-Mode Range** | −0.34 V ≤ VICM ≤ 0.36 V               | Safe input voltage range for linear differential amplification.    |

# Minimum Input Common Mode Voltage

| Parameter                  | Value / Formula         | Explanation /justification                                 |
|-----------------------------|-----------------------|---------------------------------------------|
| Drain-Source Condition      | VDS ≥ VOV             | Keeps NMOS in saturation                     |
| Drain Voltage (VD)          | 0 V                   | From bias calculation                        |
| Source Voltage (VS)         | −0.7 V                | Tail node voltage                             |
| Drain-Source Voltage (VDS)  | 0 − (−0.7) = 0.7 V    | Confirms saturation (VDS > VOV)             |
| Maximum Input (VICM max)   | VD + VT = 0 + 0.36 = 0.36 V | Max input keeping NMOS in saturation         |
| Minimum Input (VICM min)   | ≈ −VOV = −0.34 V      | Min input keeping differential pair on      |
| Input Common-Mode Range     | −0.34 V ≤ VICM ≤ 0.36 V | Safe input range for linear operation       |

# Final input and output common mode range
| Parameter                     | Value / Formula                | Explanation / Justification                               |
|-------------------------------|--------------------------------|-----------------------------------------------------------|
| Input Common-Mode Range (ICMR) | −0.34 V ≤ VICM ≤ 0.36 V       | Safe range for input to keep NMOS transistors in saturation |
| Output Common-Mode Range (Vout,CM) | Determined by NMOS saturation and proper operation | Ensures output voltage stays within limits for linear amplification |

# Maximum and Minimum output voltage with the final output common mode range

| Parameter                       | Value / Formula                     | Explanation / Justification                                   |
|---------------------------------|-------------------------------------|---------------------------------------------------------------|
| Maximum Output Voltage (VOCM max) | VOCM(max) = VDD = 0.9 V            | Limited by supply voltage and ensures current flows through load |
| Minimum Output Voltage (VOCM min) | VOCM(min) = VS + VOV = −0.7 + 0.34 = −0.36 V | Keeps NMOS transistors in saturation for proper operation      |
| Final Output Common-Mode Range   | −0.36 V ≤ VOCM ≤ 0.9 V             | Safe output voltage range for linear differential amplification |

#  Transient Analysis and Linearity cheaking
# Linear region
https://github.com/lecsinchanamn/Experiment-04/blob/8981e3f660f29664d967ed91ad2d0fec3420cf93/ckt%2001%20TA%20liner.png

LINEARITY VERIFICATION OF DIFFERENTIAL AMPLIFIER
| Parameter / Case          | Value / Observation                           | Explanation / Justification                       |
|---------------------------|-----------------------------------------------|---------------------------------------------------|
| Condition for Linearity   | |Vid| < 2 × VOV                                | Ensures both transistors stay in saturation      |
| Calculated Linear Limit   | 2 × 0.34 = 0.68 V                              | Maximum differential input for linear operation  |
| Test Input (Case 1)       | Vid = 0.1 V < 0.68 V                           | Input is within linear range                     |
| Output Observation        | Sinusoidal waveform, no distortion            | Confirms linear operation of amplifier           |
| Transistor Operation      | Both NMOS transistors in saturation           | Required for linear behavior                      |
| Amplifier Behavior        | Linear amplification                           | Output proportional to input difference          |

# Non Linear region

https://github.com/lecsinchanamn/Experiment-04/blob/3e6659a57346894be7a314dd1cffdb37c726e0bc/ckt%2001%20TA%20non-liner.png

NON-LINEAR REGION OF DIFFERENTIAL AMPLIFIER

| Parameter / Case          | Value / Observation                        | Explanation / Justification                          |
|---------------------------|--------------------------------------------|------------------------------------------------------|
| Condition for Non-Linearity | |Vid| > 2 × VOV                             | Differential input exceeds linear range             |
| Calculated Linear Limit    | 2 × 0.34 = 0.68 V                           | Maximum input for linear operation                  |
| Test Input (Case 2)       | Vid = 0.6 V > 0.68 V                         | Input exceeds linear range                           |
| Output Observation        | Distorted waveform, clipping observed       | Amplifier no longer behaves linearly               |
| Transistor Operation      | One transistor enters cutoff                 | Only one transistor carries the current             |
| Amplifier Behavior        | Non-linear amplification                     | Output not proportional to input difference         |

#  SIMULATION VS THEORETICAL values of the  DIFFERENTIAL AMPLIFIER GAIN:

https://github.com/lecsinchanamn/Experiment-04/blob/579019e810619c3748a6b5e3a4e98d2b25fa91a4/ckt%2001%20SandT.png

| Practical / Simulation                  | Theoretical                                               |
|---------------------------------------|------------------------------------------------------------------|
| **Input Signal**                        | **Channel Length Modulation**                                     |
| Type: Sine, f = 1 kHz,                  | λ = 0.1 V⁻¹                                                      |
| Amplitude: 50 mV differential, DC 0 V |                                                                  |
| **Input (p-p)**                          | **Output Resistance (ro)**                                        |
| Vin(p-p) = 100 mV                       | ro = 1 / (λ × ID) = 1 / (0.1 × 0.5 mA) = 20 kΩ                   |
| **Output (p-p)**                         | **Effective Output Resistance**                                    |
| Vout(p-p) = 604 mV                       | ro,eff = ro1 ∥ ro2 = 20 kΩ ∥ 20 kΩ = 10 kΩ                        |
| **Voltage Gain (Av)**                     | **Transconductance (gm)**                                         |
| Av = Vout / Vin = 604 mV / 100 mV ≈ 6.04| gm = 2 × ID / VOV = 2 × 0.5 mA / 0.34 V ≈ 2.94 mS                |
| **Gain in dB**                            | **Load Resistance (Rout)**                                        |
| Av(dB) = 20 log10(6.04) ≈ 15.62 dB      | Rout = RD ∥ ro,eff = 1.8 kΩ ∥ 10 kΩ ≈ 1.53 kΩ                     |
|                                       | **Differential Gain (Ad)**                                        |
|                                       | Ad = gm × Rout = 2.94 mS × 1.53 kΩ ≈ 4.5                          |
|                                       | **Gain in dB**                                                    |
|                                       | Ad(dB) = 20 log10(4.5) ≈ 13.06 dB                                 |
| **Observation**                         | **Observation**                                                   |
| Output shows practical effects,          | Theoretical gain lower due to ideal assumptions (no parasitics,  |
| parasitic capacitance, etc.             | perfect current matching).                                        |

# Reason why there is diffrence between  Simulation and Theoretical      

1. Channel Length Effect: Real MOSFETs’ channel length changes slightly reduce gain.
2. Output Resistance: Limited transistor resistance lowers the effective load and gain.
3. Mobility Drop: Electron movement slows at high fields, reducing amplifier gain.
4. Overdrive Shift: Small changes in V_OV change currents and affect gain.
5. Parasitics & Measurement: Internal capacitances and measurement errors slightly alter gain.

# DC Analysis

AC analysis is used to study how the differential amplifier responds to small alternating signals (like sine waves) at different frequencies. It helps us find:
- Gain (Av): How much the amplifier increases the input signal.
- Bandwidth (BW): The range of frequencies over which the amplifier works effectively.
- Cutoff Frequencies (fL and fH): The frequencies where the gain drops by 3 dB from its maximum value.
- Frequency Response: Shows how the amplifier amplifies signals at low, mid, and high frequencies.
- 
https://github.com/lecsinchanamn/Experiment-04/blob/378f5600733350dafb8527d1769f2941a2587dbc/README.md

| Parameter                    | Value / Notes                          |
|-------------------------------|---------------------------------------|
| **Midband Gain (Av)**         | 9.871 dB                               |
| **−3 dB Gain**                | 6.871 dB                               |
| **Lower Cutoff Frequency (fL)** | 0 Hz                                   |
| **Upper Cutoff Frequency (fH)** | 4.819 MHz                             |
| **Bandwidth (BW)**            | fH − fL = 4.819 − 0 = 4.819 MHz       |
| **Unity Gain Bandwidth (UGB)** | Av × BW = 6.04 × 4.819 MHz ≈ 29.106 MHz |

# Result

| Parameter              | Theoretical Value     | Simulated Value      |
|------------------------|---------------------|--------------------|
| Voltage Gain (Av)      | 4.5 V/V             | 6.04 V/V           |
| Gain in dB             | 14.46 dB            | 15.62 dB           |

# Conclusion:
The differential amplifier with resistive load was successfully designed and works as expected.  
- Power ≤ 1.8 mW, VDD = 0.9 V, VSS = -0.9 V, Vocm = 0 V.  
- Tail current ISS = 1 mA, split equally: ID1 = ID2 = 0.5 mA.  
- Both NMOS transistors stay in saturation with VS ≈ -0.7 V.  
- Gain: Theoretical ≈ 4.5–5.3 V/V, Simulated ≈ 6.04 V/V.  
- Bandwidth ≈ 4.819 MHz, Unity Gain Bandwidth ≈ 15 MHz.  
- Differences between theory and simulation are due to real MOSFET effects.  
- Amplifier is linear for small input voltages; distortion occurs for larger inputs.  
The design meets specifications and provides proper amplification and frequency response.

# CIRCUIT 02
# Design and analysis the differential amplifer with PMOS active load and an NMOS current source
# what is the  differential amplifer with PMOS active load and an NMOS current source
- The circuit has two matched NMOS transistors (M1, M2) as a differential pair, with their sources connected to a current source NMOS (M5) and drains connected to a PMOS current mirror load (M3, M4).  
- A differential input, vid = vin1 − vin2, steers the tail current ISS between M1 and M2:  
  - If vin1 > vin2 → M1 conducts more, M2 less.  
  - If vin2 > vin1 → M2 conducts more, M1 less.  
- M3 is diode-connected and sets the reference current; M4 mirrors it to the other branch, providing a high-resistance active load.  
- Changes in M1/M2 currents create voltage differences at OUT1 and OUT2 → differential output.  
- M5 provides a nearly constant tail current, but its finite resistance slightly reduces gain.  
- Small inputs → all transistors in saturation → linear amplification.  
- Large inputs → one transistor may turn OFF → non-linear behavior.  
- Using a PMOS active load increases gain compared to a resistive-load amplifier.

# Parameter given.
 | Parameter                     | Value                |
|--------------------------------|--------------------|
| Technology                     | TSMC 180 nm        |
| Supply Voltage (VDD)           | +0.9 V             |
| Negative Supply (VSS)          | −0.9 V             |
| Power Constraint (P)           | ≤ 1.8 mW           |
| Channel Length (Ln)            | 480 nm             |
| Input Common-Mode Voltage      | 0 V                |
| Output Common-Mode Voltage     | 0 V                |
| Tail Node Voltage (Vp)         | −0.7 V             |
| Load Capacitance (CL)          | 10 pF              |
| Threshold Voltage (VT)         | ≈ 0.36 V           |

# circuit diogram
https://github.com/lecsinchanamn/Experiment-04/blob/367df556852a9f3583d20d1573f739e4d5d294bd/ckt%2002%20ckt%20diogram.png

# Differential Amplifier Transistor Bias and Width Summary

| Transistor | Type | Key Voltages / Conditions                         | Saturation Check                | Initial Width (μm) | Tuned Width (μm) |
|------------|------|--------------------------------------------------|--------------------------------|------------------|----------------|
| M1, M2     | NMOS | VS = −0.7 V, VD = 0 V, VOV = 0.34 V            | VDS ≥ VOV → 0.7 ≥ 0.34 V       | 17.56            | 29.852         |
| M5         | NMOS | VS = −0.9 V, VD = −0.7 V, VOV = 0.2 V          | VDS ≥ VOV → 0.2 ≥ 0.2 V        | 101.5            | 195.85         |
| M3, M4     | PMOS | VS = 0.9 V, VD = 0 V, VOV sufficient           | VSD > VOV → 0.9 > VOV          | —                | —              |

# Differential Amplifier Explanation (Simple)

1 **M1 & M2 (NMOS Pair)**
  - Source: Tail node VS ≈ −0.7 V
  - Drain: Connected to PMOS load
  - VOV = 0.34 V → Saturation OK (VDS ≥ VOV)
  - Width tuned: 17.56 μm → 29.85 μm for correct current

2 **M5 (NMOS Current Source)**
  - Source: VSS = −0.9 V
  - Drain: Tail node VD = −0.7 V
  - VOV ≈ 0.2 V → Saturation OK
  - Width tuned: 101.5 μm → 195.85 μm to provide 1 mA current

3 **M3 & M4 (PMOS Load / Current Mirror)**
  - Source: VDD = 0.9 V
  - Drain: Output VD = 0 V
  - VSD > VOV → Saturation OK
  - Mirrors current and gives high output resistance

# DC Analysis 
https://github.com/lecsinchanamn/Experiment-04/blob/42d2b3b9042f5b7d74661072340a34210ec45856/ckt%2002%20ckt%20diogram.png

# Input Common-Mode Range (ICMR)
| Parameter                        | Value          | Notes / Condition                                      |
|----------------------------------|----------------|--------------------------------------------------------|
| Minimum Input Common-Mode Voltage | -0.34 V        | NMOS transistors M1, M2 ON; tail current source M5 in saturation |
| Maximum Input Common-Mode Voltage | 0.39 V         | PMOS load transistors M3, M4 remain in saturation     |
| Input Common-Mode Range (ICMR)    | -0.34 V to 0.39 V | Range where all transistors operate in saturation    |

# Output Common-Mode Range (OCMR)
| Parameter                         | Value       | Notes / Condition                                      |
|----------------------------------|------------|--------------------------------------------------------|
| Minimum Output Common-Mode Voltage | -0.36 V    | NMOS transistors M1, M2 remain in saturation         |
| Maximum Output Common-Mode Voltage | 0.65 V     | PMOS load transistors M3, M4 remain in saturation    |
| Output Common-Mode Range (OCMR)    | -0.36 V to 0.65 V | Range where all transistors operate in saturation |

# Differential Input Voltage Range 

| Parameter                        | Value        | Notes / Condition                                  |
|---------------------------------|-------------|---------------------------------------------------|
| Maximum Differential Input Voltage | 0.5 V       | At the boundary where one transistor starts to turn OFF |
| Minimum Differential Input Voltage | -0.5 V      | Symmetrical for linear operation                  |
| Linear Differential Input Range    | -0.5 V to 0.5 V | Both NMOS transistors (M1, M2) remain in saturation |

# Transient Analysis and cheaking linear or non-linear

1. Linearity
When the differential input voltage is small, both NMOS transistors (M1 and M2) remain in saturation, and the PMOS active load (M3 and M4) also stays in saturation. The tail current from the NMOS current source (M5) splits evenly between the NMOS transistors. The amplifier produces a clean, amplified output that is proportional to the input, with no distortion. Transient analysis in this region shows a sinusoidal output waveform that faithfully follows the input signal.

https://github.com/lecsinchanamn/Experiment-04/blob/bbe78cd60794b10f250b3ea2a2509593b252c096/ckt%2002%20TA%20linear.png

| Parameter                  | Value / Condition          | Observation / Notes                                         |
|-----------------------------|---------------------------|-------------------------------------------------------------|
| Differential Input (Vid)    | 100 mV < 0.34 V           | Within linear range                                        |
| Output Waveform             | Sinusoidal                | No distortion                                              |
| NMOS Transistors (M1, M2)   | Saturation                | Operating normally                                         |
| PMOS Load (M3, M4)          | Saturation                | Ensures proper load                                        |
| Amplifier Behavior           | Linear                    | Output proportional to input difference                   |

2. Non-Linearity
 If the differential input voltage becomes large, one NMOS transistor may enter cutoff while the other carries most of the current. The PMOS load continues to operate, but the output waveform becomes distorted and clipped. The gain decreases, and the amplifier no longer behaves linearly. Transient analysis in this region reveals the limits of the amplifier’s linear operation and highlights the onset of non-linear behavior.
  
https://github.com/lecsinchanamn/Experiment-04/blob/8c968d8143ae255ddad0c57165b87911c4ecdcb7/Ckt%2002%20TA%20non-linear.png

| Condition                  | Differential Input (Vid) | Circuit Behavior                         |
|-----------------------------|-------------------------|-----------------------------------------|
| Within Linear Range         | 100 mV < 0.34 V         | Output sinusoidal, M1 & M2 in saturation, linear amplification |
| Beyond Linear Range         | 600 mV > 0.34 V         | Output distorted/clipped, one NMOS off, current steered, non-linear amplification |

# Justification

- Differential pair becomes unbalanced as one transistor turns off.
- Overall voltage gain drops due to loss of current in one branch.
- Output waveform gets clipped at high input differences.
- Tail current flows mostly through a single NMOS transistor.
- Distortion appears in the output signal, changing its shape.
- PMOS load still works but cannot maintain linear amplification.
- Harmonics are introduced because the amplifier is no longer linear.

 # Differnce btween theory and simulation Gain (Av)
 
| Parameter                  | Simulation                     | Theory                        |
|----------------------------|--------------------------------|-------------------------------|
| Input Signal               | 50 mVpp Sine, 1 kHz, 0 V DC   | —                             |
| Output Signal              | 181 mVpp                       | —                             |
| Voltage Gain (Av)          | 1.81 V/V                       | 41.7 V/V                      |
| Gain in dB (Av_dB)         | 5.15 dB                        | 32.4 dB                       |
| Transconductance (gm)      | —                              | 4.17 mS                        |
| Output Resistance (Rout)   | —                              | 10 kΩ                          |
| Amplifier Behavior         | Amplified & Inverted           | Linear (ideal, saturation)     |

# Factors Affecting Theoretical vs Simulated Gain

1. Temperature Effects:
   - Simulation includes temperature variations.
   - MOSFET parameters like VT and mobility slightly change, affecting gain.

2. Supply Voltage Fluctuations:
   - VDD and VSS are not perfectly constant in simulation.
   - Small voltage drops reduce effective output swing and gain.

3. Mismatch Between Transistors:
   - Device mismatches in width, threshold, or current.
   - Leads to unequal current splitting, affecting differential gain.

4. Nonlinearities in MOSFETs:
   - For larger input signals, transistors enter non-linear regions.
   - Causes gain compression compared to ideal theoretical gain.

5. Load Capacitance Effects:
   - The external CL affects frequency response.
   - Reduces gain at higher frequencies due to RC roll-off.

# AC Analysis 
AC analysis of a differential amplifier studies its response to small, time-varying input signals.
The NMOS current source provides a stable tail current, steering it between the differential pair.
The PMOS active load converts the differential currents into output voltage with high gain.
Midband gain is flat and linear, while high frequencies roll off due to parasitic capacitances.
AC analysis helps predict gain, bandwidth, and frequency response without full transient simulation.

https://github.com/lecsinchanamn/Experiment-04/blob/40eaaa172de73b30c5c506e3bd0d3f3c473f3132/Ckt%2002%20AC%20analysis.png

# calucalion of Midband gain/Cutoff Frequencies/Bandwidth/Bandwidth

| Parameter                   | Value                  |
|-----------------------------|-----------------------|
| Midband Gain (Av)           | 5.2 dB                |
| -3 dB Gain                  | 2.2 dB                |
| Lower Cutoff Frequency (fL) | 0 Hz                  |
| Upper Cutoff Frequency (fH) | 2.2 GHz               |
| Bandwidth (BW)              | 2.2 GHz               |
| Unity Gain Frequency (f0dB) | 4.8 GHz               |
| Unity Gain Bandwidth (UGB)  | 8.688 GHz             |

# conclusion
1. The differential amplifier operates within power and voltage limits, with balanced current splitting between the NMOS pair.  
2. Practical factors like non-ideal current source, finite output resistance, and device imperfections lower the gain compared to theoretical predictions.  
3. Frequency response shows a stable midband region with a high-frequency roll-off due to parasitic and load capacitances.  
4. Small differential inputs produce clean, linear output without distortion, ensuring proper signal amplification.  
5. Large differential inputs push the amplifier into non-linear operation, causing one branch to dominate and resulting in waveform distortion.  

# CIRCUIT 03
# Design and analysis CMOS Differential Amplifier (DC Analysis & verify the Saturation Conditions for all MOSFETs)
# Circuit diogram 

https://github.com/lecsinchanamn/Experiment-04/blob/37b09390f01edf2c37d182f82b4983893630e7af/ckt%2003%20ckt%20diogram.PNG

The CMOS differential amplifier is designed using a pair f NMOS transistors (M1 and M2) forming the differential input stage, a PMOS active load (M3 and M4) for high output resistance, and an NMOS current source (M5) providing the tail current. The key design objective is to ensure all transistors operate in the saturation region while satisfying the given supply and power constraints.
1. DC Operating Point:
   - The tail current (ISS) is set to a value that satisfies the power budget (e.g., 1 mA for a 1.8 mW limit).
   - Under balanced input conditions, this current splits equally between M1 and M2.
   - The gate-source voltages of the NMOS input transistors are chosen to keep them ON and in saturation.
2. Saturation Verification:
   - NMOS Input Transistors (M1, M2):
     Condition: VDS ≥ VOV
     - Ensures proper linear amplification.
   - NMOS Current Source (M5):
     Condition: VDS ≥ VOV
     - Maintains constant tail current, avoiding gain variation.
3. DC Bias Adjustment:
   - Tail node voltage is tuned via transistor width adjustment to ensure M5 operates at the edge of saturation.
   - Gate voltages of PMOS transistors are set to establish the desired output common-mode voltage.
4. Impact of Non-Idealities:
   - Finite output resistance of M5 and PMOS load slightly reduces the gain.
   - Channel length modulation and mobility degradation introduce deviations from theoretical values.
   - Matching of device sizes ensures balanced current splitting and minimizes offset.
5. Verification Procedure:
   - Calculate drain, gate, and source voltages for all transistors.
   - Check the VDS (NMOS) and VSD (PMOS) against VOV to confirm saturation.
  #  Given parameter
  
  | Transistor | Type |  Vg   |  Vs   |  Vd   | Vgs / Vsg | Vds / Vsd | Saturation Condition | Status             |
|------------|------|-------|-------|-------|-----------|-----------|--------------------|------------------|
| M1         | NMOS | 0     | -0.7  | 0.3   | 0.7       | 1.0       | VDS ≥ VGS − Vt     | Saturation        |
| M2         | NMOS | 0     | -0.7  | 0.3   | 0.7       | 1.0       | VDS ≥ VGS − Vt     | Saturation        |
| M3         | PMOS | 0.3   | 0.9   | 0.3   | 0.6       | 0.6       | VSD ≥ VSG − |Vt|  | Saturation        |
| M4         | PMOS | 0.3   | 0.9   | 0.3   | 0.6       | 0.6       | VSD ≥ VSG − |Vt|  | Saturation        |
| M5         | NMOS | 0.366 | -0.35 | -0.7  | 0.716     | 0.35      | |VDS| ≥ VGS − Vt   | Edge of Saturation|

# DC Analysis 
DC analysis refers to studying the steady-state behavior of a circuit when no AC input signal is applied. It focuses on voltages and currents at all nodes to ensure proper biasing of transistors. For a CMOS differential amplifier with NMOS input pair, PMOS active load, and NMOS current source,

https://github.com/lecsinchanamn/Experiment-04/blob/b1df0baffe213c9c818677890352e68fc19abcde/ckt%2003%20DC%20analysis.PNG

| Parameter / Node            | Transistor / Node | Value (V / mA)         | Notes / Observations                              |
|-----------------------------|-----------------|-----------------------|--------------------------------------------------|
| Supply Voltage              | VDD             | 0.9 V                 | Positive rail                                    |
| Negative Supply             | VSS             | -0.9 V                | Negative rail                                    |
| Ground Reference            | GND             | 0 V                   | Reference node                                   |
| Tail Node Voltage           | Vp              | -0.7218 V             | NMOS tail node                                   |
| Bias Node Voltage           | Vg5             | -0.37 V               | Gate voltage of NMOS current source M5          |
| Tail Current                | M5              | 1.0487 mA             | Total tail current                               |
| Differential Pair Current   | M1              | 0.5243 mA             | Half of tail current                              |
| Differential Pair Current   | M2              | 0.5243 mA             | Half of tail current                              |
| PMOS Load Current           | M3              | -0.5243 mA            | Opposite to NMOS current                          |
| PMOS Load Current           | M4              | -0.5243 mA            | Opposite to NMOS current                          |
| Output Voltage              | Vout1           | 0.8876 V              | Equal outputs indicate zero differential input   |
| Output Voltage              | Vout2           | 0.8876 V              | Same as Vout1                                    |
| VGS / VSG (M1, M2)         | -               | 0.7218 V              | Gate-source voltage for NMOS transistors         |
| VDS / VSD (M1, M2)         | -               | 1.6094 V              | Drain-source voltage for NMOS transistors        |
| VGS (M5)                    | -               | 0.53 V                | Gate-source voltage of NMOS current source       |
| VDS (M5)                    | -               | 0.1782 V              | Drain-source voltage of NMOS current source      |
| Current Consistency Check   | -               | 1.0487 ≈ 0.5243+0.5243 mA | Tail current equals sum of differential pair currents |

# Transient Analysis
Transient analysis is used to study how the amplifier responds to time-varying signals (AC inputs) as opposed to just DC conditions. While DC analysis ensures all MOSFETs are biased correctly and in saturation, transient analysis shows the dynamic response of the amplifier when actual input signals are applied.
# Neds of Transient Analysis
- To verify the linear amplification range of the differential amplifier.
- To observe output waveforms and detect any distortion or clipping.
- To confirm that all transistors remain in saturation during signal swings.
- To check the tail current sharing between the NMOS input pair (M1 & M2).
- To evaluate timing-related behavior like rise time, fall time, and delay in the output.

  1. Linear region

  | Parameter        | Value      |
|------------------|------------|
| Technology       | 180 nm     |
| VDD              | +0.9 V     |
| VSS              | -0.9 V     |
| Power            | ≤ 1.8 mW   |
| Channel Length   | 480 nm     |
| Vin,CM           | 0 V        |
| Vo,CM            | 0 V        |
| Vp               | -0.7 V     |
| CL               | 10 pF      |
| VT               | 0.36 V     |

2. NON linear region
| Parameter          | Value / Observation                                      |
|-------------------|----------------------------------------------------------|
| Differential Input | Vid = 600 mV > 0.48 V                                    |
| Circuit            | Circuit 3                                                |
| Output Waveform    | Distorted with clipping                                   |
| NMOS Behavior      | One transistor (M1 or M2) enters cutoff                  |
| Current Flow       | Steered completely to one branch                          |
| PMOS Load          | Operates normally                                        |
| Amplifier Behavior | Non-linear amplification                                 |

https://github.com/lecsinchanamn/Experiment-04/blob/dc04c95ee7d1f9cbcd6e4d376b2428bb9c07190d/ckt%2003%20TA.PNG

# Conclusion
| Condition                | Behavior                                               |
|--------------------------|--------------------------------------------------------|
| |Vid| < 2VOV              | Linear operation; output waveform is undistorted      |
| |Vid| > 2VOV              | Non-linear behavior; current steering and transistor cutoff occur |

# Theoretical Gain and simulation gain calucation

| Parameter                  | Value / Observation                           |
|----------------------------|-----------------------------------------------|
| Input Signal               | Sine wave, 1 kHz, 10 mV peak-to-peak         |
| Output Signal (Simulated)  | 385 mV peak-to-peak, inverted                 |
| Simulated Gain (Av)        | 38.5 V/V                                      |
| Simulated Gain (dB)        | 31.7 dB                                       |
| Theoretical Gain (Av)      | 29.4 V/V                                      |
| Theoretical Gain (dB)      | 29.36 dB                                      |
| Reasons for Deviation      | Channel length modulation, PMOS load, non-ideal tail current, mobility loss, parasitics, DC offset |
| Conclusion                 | Simulation gain differs from theory due to real MOSFET effects and non-idealities |
# AC Analysis

https://github.com/lecsinchanamn/Experiment-04/blob/464ff2620e1dc8a02c20465a4ce2f4e9a410a8ec/ckt%2003%20AC%20analysis.PNG

# ransconductance (gm)/ Overdrive Voltage/ Output Resistance/ Gain Calculations/ Theoretical and Practical Results

| Step                     | Final Correct Value        | Formula / Note                          |
|--------------------------|----------------------------|-----------------------------------------|
| Overdrive Voltage (Vov)  | 0.354 V                    | Vov = VGS − Vt = 0.72 − 0.366           |
| Drain Current (Id)       | 0.524 mA                   | From DC analysis                        |
| Transconductance (gm)    | 2.96 mS                    | gm = 2Id / Vov                          |
| Output Resistance (ro)   | 19.08 kΩ                   | ro = 1 / (λId), λ = 0.1 V⁻¹             |
| Effective Rout           | 9.5 kΩ                     | Rout = ro || ro ≈ ro/2                  |
| Theoretical Gain (Ad)    | 28.1 V/V                   | Ad = gm × Rout                          |
| Gain in dB (Theory)      | 28.97 dB                   | 20 log(28.1)                            |
| Expected Practical Gain  | ≈ 20–30 dB                 | Considering non-ideal effects           |
| Expected Linear Gain     | ≈ 10–30 V/V                | Should be > 1                           |
| Final Conclusion         | Amplifier gain is positive | Circuit should amplify, not attenuate   |

