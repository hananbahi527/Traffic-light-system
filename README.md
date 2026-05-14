# LED Traffic Light System Project

## Table of Contents
1. [Project Overview](#project-overview)
2. [Working Principle](#working-principle)
3. [Technical Notes](#technical-notes)
4. [Components Used](#components-used)

## Project Overview

This repository contains the design and implementation of a sequential LED Traffic Light System using a 555 Timer IC and a CD4017 Decade Counter.

![Traffic Light System](Traffic%20light%20system.jpeg)

## Working Principle

The circuit operates through a two-stage process involving a pulse generator and a sequential counter:

* **Pulse Generation:** The **555 Timer IC** operates as an **astable multivibrator**. In this mode, it generates a continuous stream of square-wave clock pulses.
* **Sequential Logic:** These pulses are fed directly into the **CD4017 Decade Counter** at its clock input pin.
* **LED Sequencing:** The CD4017 activates its output pins one by one in response to each clock pulse. This causes the Red, Yellow, and Green LEDs to turn ON in a sequential order.
* **Speed Control:** A **variable resistor (RV1)** is used to adjust the time constant of the 555 Timer, allowing the user to change the speed at which the lights transition.
* **Continuous Loop:** Once the sequence reaches the end, it resets and repeats continuously, mimicking a real-world traffic light.

![Traffic Light Output](traffic%20lights.jpeg)

## Technical Notes

> [!IMPORTANT]
> When assembling the circuit, please keep the following technical considerations in mind:

1.  **Pin Configuration:** In integrated circuits like the 555 Timer and CD4017, the pin names (e.g., CLOCK, RESET) do not always correspond to sequential pin numbers. Always refer to the datasheet for the exact pin mapping.
2.  **Simulation Software (Proteus):** If you are using Proteus for simulation, note that power pins like **VCC** and **GND** might be hidden by default. Ensure they are manually connected to ensure the circuit functions correctly.
3.  **Power Supply:** The circuit supports a VCC voltage of **5V or 9V**. However, **9V is preferred** for better performance and brighter LED output.

## Components Used

* 555 Timer IC
* CD4017 Decade Counter IC
* LEDs (Red, Yellow, Green)
* Variable Resistor (Potentiometer)
* Resistors and Capacitors
* Breadboard or PCB
* 9V Power Source
