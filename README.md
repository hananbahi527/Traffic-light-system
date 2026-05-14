# Traffic Light Control System (555 + 4017)

> Ever wondered how those massive metal towers at every intersection "think"? It turns out you don't need a high-powered computer to manage a busy junction—just a handful of clever components and a steady pulse.

This project features a **Sequential Traffic Light Controller** built using two legendary ICs: the **NE555 Timer** and the **CD4017 Decade Counter**. It serves as a perfect demonstration of hardware-based state machines and diode logic.

##  Table of Contents
1. [Pulse Generator (The Heart)](#-pulse-generator-the-heart)
2. [Sequence Controller (The Brain)](#-sequence-controller-the-brain)
3. [Diode Logic Gate (The Director)](#-diode-logic-gate-the-director)
4. [Output Protection](#-output-protection)
5. [⚠️ Hardware Safety & Cautions](#-hardware-safety--cautions)
6. [Summary of Operation](#-summary-of-operation)

---

##  Pulse Generator (The Heart)
The circuit starts with **U1 (NE555 Timer)** configured in **Astable Mode**. 
* **Function:** Generates a continuous square wave (clock pulse) at Pin 3.
* **Control:** By adjusting the potentiometer **RV1 (1k)**, the RC constant changes, allowing you to speed up or slow down the traffic cycle.

##  Sequence Controller (The Brain)
The clock signal feeds into Pin 14 (CLK) of **U2 (CD4017)**. 
* **Decade Counter:** For every pulse received, it shifts its HIGH output one pin at a time (Q0 → Q1 → ... → Q9).
* **Reset:** After the 10th pulse, it automatically resets to the beginning, creating a permanent loop.

##  Diode Logic Gate (The Director)
To simulate realistic timing where Red and Green stay on longer than Yellow, **1N4148 Diodes** act as "OR Gates" to group outputs.

| Light | Sequence Steps (U2 Outputs) | Duration |
| :--- | :--- | :--- |
| **🔴 RED** | Q0, Q1, Q2, Q3 | 4 Clock Cycles |
| **🟡 YELLOW** | Q4, Q9 | 2 Clock Cycles |
| **🟢 GREEN** | Q5, Q6, Q7, Q8 | 4 Clock Cycles |

![Traffic Light Output](traffic%20lights.jpeg)

---

## ⚠️ Hardware Safety & Cautions

Before moving from the simulator to the breadboard, please review these safety notes to avoid damaging components:

### 1. Capacitor Polarity (The "Pop" Factor)
The **C1 (100uF)** electrolytic capacitor is polarized.
* **Danger:** Connecting it backward or exceeding its voltage rating can cause the electrolyte to boil and burst the casing. 
* **Prevention:** Always align the negative stripe on the capacitor with the circuit ground.



### 2. Electrostatic Discharge (ESD)
The **CD4017** is a CMOS chip and is highly sensitive to static electricity.
* **Danger:** A tiny static shock from your finger can fry the internal logic gates.
* **Prevention:** Touch a grounded metal object before handling ICs.

### 3. Current Overload
The CD4017 has a limited output current (approx. 10-15mA).
* **Danger:** Removing the **100Ω resistors** to make LEDs brighter will overheat the IC and likely burn it out.
* **Prevention:** Always use current-limiting resistors as shown in the schematic.

### 4. Component Clearance
* **Caution:** When building on a breadboard, the long metal leads of the **1N4148 diodes** can easily touch, causing a short circuit. Trim your leads or ensure they are properly spaced.

![Traffic Light System](Traffic%20light%20system.jpeg)

---

## ⚙️ Summary of Operation
1. The **555 Timer** pulses.
2. The **4017 Counter** increments.
3. The **Diode Matrix** directs power to the correct LED based on the current step.
4. The system loops indefinitely, orchestrating a perfect flow of simulated traffic.

---
*Developed as a hardware logic simulation project.*
