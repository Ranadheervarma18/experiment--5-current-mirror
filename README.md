# experiment--5
# **Design and Analysis of Current Mirror Circuit**

## **1. Introduction**
A current mirror is an essential circuit used to replicate a reference current across another branch while maintaining a constant current regardless of variations in the load. It is widely implemented in biasing circuits and as active loads in amplifiers.

### **Objective**
The goal of this project is to design and analyze a current mirror circuit that meets the following specifications:
- **Voltage Gain (Av) > -10 V/V**
- **Power Supply (VDD) = 1.8 V**
- **Power Consumption (P) ≤ 1 mW**
- Perform **DC Analysis, Transient Analysis, and AC Analysis** while maintaining the same **W/L ratio** for different values of transistor length (L).
- Calculate the **maximum output swing** and **bandwidth** of the circuit.

---

## **2. Circuit Design**
### **2.1 Current Mirror Design**

#### **Step 1: Total Current Calculation**
\[ I_{TOTAL} = \frac{P}{VDD} = \frac{1 mW}{1.8 V} = 0.555 mA \]

#### **Step 2: Reference Current Calculation**
- **For a 1:1 ratio**
  \[ I_{REF} = \frac{I_{TOTAL}}{2} = \frac{0.555 mA}{2} = 0.2775 mA \]
- **For a 1:2 ratio**
  \[ I_{REF} = \frac{I_{TOTAL}}{3} = \frac{0.555 mA}{3} = 0.185 mA \]
  \[ I_{D} = 2 \times I_{REF} = 0.37 mA \]
![image](https://github.com/user-attachments/assets/bc843d37-619f-4f36-af01-0a8a7b4fd2c2) ![image](https://github.com/user-attachments/assets/641af6d0-d6b7-4f8e-a9ca-903b5940cb1c)

#### **Circuit Parameters**
| Parameter | PMOS (M1) | PMOS (M2) | NMOS (M3) |
|-----------|----------|----------|----------|
| Length (L) | 180 nm | 180 nm | 180 nm |
| Width (W) | 2.35 µm | 2.35 µm | 2.9 µm |

---

## **3. Analysis & Results**

### **3.1 DC Analysis**
Observing variations in **Vout** and **ID** with different transistor lengths:

#### **1:1 Ratio Current Mirror**
| Length (L) | Width (W1) | Width (W2) | Width (W3) | IREF (mA) | ID (mA) | Vout (V) |
|-----------|-----------|-----------|-----------|------------|----------|-----------|
| 180 nm | 2.35 µm | 2.35 µm | 2.9 µm | 0.277 | 0.27711 | 0.552 |
| 500 nm | 2.35 µm | 2.35 µm | 8.37 µm | 0.277 | 0.284 | 0.289 |
| 1 µm | 2.35 µm | 2.35 µm | 19.11 µm | 0.277 | 0.285 | 0.213 |

#### **1:2 Ratio Current Mirror**
| Length (L) | Width (W1) | Width (W2) | Width (W3) | IREF (mA) | ID (mA) | Vout (V) |
|-----------|-----------|-----------|-----------|------------|----------|-----------|
| 180 nm | 2.5 µm | 5 µm | 3.897 µm | 0.185 | 0.370 | 0.682 |
| 500 nm | 2.5 µm | 5 µm | 10.825 µm | 0.185 | 0.380 | 0.288 |
| 1 µm | 2.5 µm | 5 µm | 21.65 µm | 0.185 | 0.382 | 0.212 |
![image](https://github.com/user-attachments/assets/f9ff3fdc-2e2e-49cb-ac97-7e7328955b95)
![image](https://github.com/user-attachments/assets/cfbc1d06-1197-470f-b321-8300a9b55363)

---

### **3.2 Transient Analysis**
- **1:1 Ratio**: Gain (Av) = \(-12 V/V\)
- **1:2 Ratio**: Gain (Av) = \(-11.2 V/V\)
![image](https://github.com/user-attachments/assets/c5133b4e-fc0f-4a2e-946f-9719ba165aab)
![image](https://github.com/user-attachments/assets/cbb72799-b72a-4768-9ac8-2ebbca9bfae2)

### **3.3 AC Analysis**
- **1:1 Ratio**: Gain = 21.6 dB, Bandwidth = 770.570 MHz
- **1:2 Ratio**: Gain = 20.984 dB, Bandwidth = 815.968 MHz
![image](https://github.com/user-attachments/assets/be0ecf8f-dba9-4d95-9396-6dc369812988)
![image](https://github.com/user-attachments/assets/bd49cd1b-6e46-4b7a-8cf2-ac59969166f4)

---

## **4. Design B: Differential Amplifier**
A differential amplifier is designed using the current mirror circuit instead of a resistor load. This enhances gain, stability, and reduces offset variations.

### **Specifications**
- **Power Supply (VDD) = 3.3 V**
- **Power Consumption (P) ≤ 3 mW**
- **Common-Mode Input Voltage (VICM) = 1.65 V**
- **Output Common-Mode Voltage (Vocm) = 1.7 V**
- **Bias Voltage (VP) = 0.5 V**

### **Circuit Parameters**
| Parameter | PMOS (M3) | PMOS (M4) | NMOS (M1) | NMOS (M2) | NMOS (M5) | NMOS (M6) |
|-----------|----------|----------|----------|----------|----------|----------|
| Length | 180 nm | 180 nm | 180 nm | 180 nm | 1 µm | 1 µm |
| Width | 2.214 µm | 2.214 µm | 1.82 µm | 1.82 µm | 200 µm | 100 µm |

### **Analysis & Results**
- **Transient Analysis**: Gain (Av) = \(-65 mV / 2 mV\)
- **AC Analysis**: Gain = 8.299 dB

![image](https://github.com/user-attachments/assets/c1f333ad-f61f-4aca-8960-57af785d374e)
![image](https://github.com/user-attachments/assets/db124154-793b-4f8e-b5c8-d597d813dc08)
![image](https://github.com/user-attachments/assets/bc581199-2e7b-492e-954f-db78f5c32503)

---

## **5. Inference & Observations**
- **Impact of Length Increase on NMOSFET**:
  - **Vout decreases**
  - **Drain current (ID) slightly increases**
  - **Output resistance increases**, improving current matching and stability

- **Comparison of 1:1 vs 1:2 Ratio Current Mirror**

| Feature | 1:1 Ratio | 1:2 Ratio | Observation |
|---------|----------|----------|-------------|
| Current Accuracy | Higher accuracy | Slight mismatch | 1:1 provides better current matching |
| Transistor Sizing | Smaller | Larger | 1:1 is more area-efficient |
| Power Consumption | Lower | Higher | 1:2 consumes more power |

- **Differential Amplifier Performance**
  - The use of a **current mirror instead of a resistor load** enhances amplifier **gain and stability**.
  - Reduces **offset variations**, leading to a more robust design.

---

## **6. Conclusion**
This project successfully analyzed and designed a current mirror circuit while maintaining the required specifications. The impact of transistor length variation was observed, and a comparison between different current mirror ratios was provided. Additionally, the effectiveness of a current mirror in a differential amplifier was evaluated, demonstrating improvements in performance compared to a resistor load. The results indicate that using a current mirror enhances current stability and amplifier efficiency.

---

### **Repository Contents**
- **Circuit Schematics**
- **Simulation Results**
- **MATLAB/Python Scripts for Analysis**
- **LTSpice/NgSpice Simulation Files**

---

## **References**
1. Sedra, A. S., & Smith, K. C., *Microelectronic Circuits*.
2. Razavi, B., *Design of Analog CMOS Integrated Circuits*.
3. Gray, P. R., Hurst, P. J., Lewis, S. H., & Meyer, R. G., *Analysis and Design of Analog Integrated Circuits*.
