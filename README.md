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
Ckt 01 ckt diogram.png
