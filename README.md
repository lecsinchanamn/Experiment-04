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
- Takes two inputs: V1 and V2
- If V1 = V2 → Output = 0 (ideal case)
- If V1 ≠ V2 → Output = Amplified difference
- Rejects common noise present in both inputs
1. Current Flow:
- Current splits between M1 and M2
- Vin1 > Vin2 → M1 gets more current
- Vin2 > Vin1 → M2 gets more current
2. Small Input:
- Both transistors ON
- Works in linear region (good amplification)
3. Gain:
Av = gm × Rout
4. Transconductance:
gm = (2 × ID) / Vov
5. Large Input:
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
