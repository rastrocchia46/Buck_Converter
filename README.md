# 🔋 Synchronous Buck Converter – 60V to 3.3V @ 8A

Design and simulation of a **high-frequency, microcontroller-monitored synchronous buck converter** for wide input voltage applications.
The project focuses on **power stage dimensioning, efficiency optimization, thermal behavior, power supply management, user interfaces, PCB layout and 3D integration**, and **ADC signal conditioning** for embedded monitoring.

<img width="1141" height="701" alt="immagine" src="https://github.com/user-attachments/assets/643a8cc9-9d21-49be-a600-432712502013" />

---

## 📌 Project Overview

* **Topology:** Synchronous Buck Converter
* **Input Voltage:** 30 V – 60 V
* **Output Voltage:** 3.3 V
* **Output Current:** up to 8 A
* **Switching Frequency:** 400 kHz
* **Control & Monitoring:** External microcontroller with ADC (**[LPC1313FHN33 (NXP)]**)
* **Simulation Tool:** Simetrix
* **PCB & Mechanical Design:** Fusion 360

This project was developed as part of the course **Design of Electronic Circuits and Systems**, with emphasis on **practical power electronics design choices** and **engineering trade-offs**.

---

## 🎯 Design Objectives

* Achieve **high efficiency** over a wide input voltage range
* Maintain **low output voltage ripple** suitable for digital loads (< 50 mV)
* Ensure **continuous conduction mode (CCM)** over full operating range
* Implement a structured **power supply management architecture**
* Provide basic **user interfaces for system status control**
* Design an **EMI-aware PCB layout** suitable for high-frequency switching
* Integrate electrical and mechanical aspects through **3D PCB modeling**
* Verify **thermal behavior** of power components

---

## ⚙️ Power Stage Design

**Main components:**

* **High-side and Low-side MOSFETs:** **[IAUCN10S7L040]**
* **Gate driver:** **[UCC27282DRCR]**
* **Inductor:** **[SRP1038WA-4R7M]**
* **Input capacitors:** 2xMLCCs **[GRM55ER72A475KA01]** + 1xElectrolytic **[MAL213639479E3]**
* **Output capacitors:** 2xMLCCs **[GRM21BR61C226ME44]**

The power stage was fully dimensioned considering:

* Inductor value selection based on ripple current and saturation limits
* MLCC output capacitor sizing including **DC bias derating**
* MOSFET selection based on:

  * Conduction losses
  * Switching losses
  * RDS(on) and gate charge
* Gate driver compatibility with 400 kHz operation

<img width="595" height="448" alt="Power stage schematic" src="https://github.com/user-attachments/assets/3115dc0f-134d-43d1-8b63-80713bbf4529" />

---

## 🔌 Power Supply Management

A dedicated **power supply management architecture** was implemented to ensure stable and safe system operation.

**Main elements:**

* **Primary DC-DC converters:** 60 V → 12 V **[R-78HB12-0.5]** + 12 V → 5 V **[LT8610AB]**
* **Auxiliary regulators:** 12 V → 10 V **[LM2940]** + 5 V → 3.3 V **[AP7387Q]**

The design ensures:

* Correct power-up sequencing
* Stable supply rails for analog and digital sections
* Reduced noise coupling between power and signal domains

<img width="650" height="524" alt="immagine" src="https://github.com/user-attachments/assets/37770ed9-3ec4-4b6c-92a8-43ffae5c01dd" />

---

## 📐 ADC Front-End & Signal Conditioning

* **Operational amplifier:** **[TLV2781]**

To enable accurate voltage monitoring via a microcontroller ADC, a dedicated analog front-end was designed, including:

* Precision **voltage divider** for 3.3 V ADC compatibility
* **RC anti-aliasing filter** for noise reduction
* **Rail-to-rail operational amplifier buffer** to ensure ADC driving capability

The design balances bandwidth, noise attenuation, and ADC sampling constraints.

<img width="474" height="721" alt="ADC front-end schematic" src="https://github.com/user-attachments/assets/b2ec2919-5314-472d-b500-41e068400ef9" />

---

## 🧩 User Interfaces

Basic **user interfaces** were implemented to support system monitoring and debugging.

**Interfaces include:**

* **Buttons:** **Reset** and **Wakeup** operations
* **Display:** **[NHD-C0216CiZ-FSW-FBW-3V3]**

<img width="408" height="594" alt="immagine" src="https://github.com/user-attachments/assets/9f0c1a13-ec10-42c6-adb5-3fd2d5144c4b" />

---

## 🌡️ Thermal Analysis

Thermal behavior of the circuit was analyzed considering:

* Power dissipation on MOSFETs
* Inductor copper and core losses
* Impact of switching frequency on thermal stress

The analysis confirms safe operation within component thermal limits under nominal load conditions.

<img width="737" height="332" alt="Thermal analysis" src="https://github.com/user-attachments/assets/bee32b67-97b0-4a4e-90eb-4ba028c347cd" />

---

## 📊 Simulation & Validation

All simulations were performed using **Simetrix**, validating both steady-state and dynamic behavior.

### Key Results

* **Efficiency:**

  * Up to **91.5%** at 30 V input
  * Above **85%** at 60 V input

* **Output Voltage Ripple:**

  * Less than **15 mV** peak-to-peak

* **Operating Mode:**

  * Continuous Conduction Mode (CCM) across full Vin range

<img width="1480" height="717" alt="Efficiency results" src="https://github.com/user-attachments/assets/862043a1-038b-4c17-b6a4-57ea4460d30b" />
<img width="1482" height="688" alt="Waveforms" src="https://github.com/user-attachments/assets/429128d6-dd1e-42a7-84ce-f5d6f030dad7" />

---

## 🖥 PCB Layout & 3D Integration (Fusion 360)

The complete PCB was designed in **Fusion 360**, focusing on both **electrical performance and mechanical integration**.

Key aspects of the PCB design include:

* Optimized **high-current power paths**
* Minimized **switching loops** for EMI reduction
* Proper **component placement** for thermal dissipation
* Ground plane strategy for signal integrity
* 3D PCB visualization to verify:

  * Component clearances
  * Mechanical constraints
  * Overall form factor

<img width="1563" height="774" alt="PCB layout" src="https://github.com/user-attachments/assets/9b35599f-e570-432d-aaa5-ae16790859a7" />
<img width="1635" height="634" alt="3D PCB" src="https://github.com/user-attachments/assets/53cc6f00-e100-49f7-ba4e-96c4ec664413" />

---

## 🛠 Tools & Technologies

* **Simulation:** Simetrix
* **PCB & Mechanical Design:** Fusion 360
* **Power Electronics:** DC-DC converters, MOSFETs, gate drivers
* **Analog Design:** Op-amps, filters, signal conditioning
* **Embedded Context:** MCU ADC interfacing

---

## 👤 Authors

* [**Raffaele Strocchia**](https://www.linkedin.com/in/raffaele-strocchia/)
* [**Salvatore Turboli**](https://www.linkedin.com/in/salvatore-turboli-a51188396/)
* [**Andrea Trimarchi**](https://www.linkedin.com/in/andrea-trimarchi-a36a75361/)

MSc Students in Electronic Engineering – Double Degree
University of Naples Federico II & Lodz University of Technology

---
