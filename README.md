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
