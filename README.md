# High-Voltage Power Supplies for DBD Plasma

Design, construction, and development of custom high-voltage power supplies for dielectric barrier discharge (DBD) plasma systems used in analytical chemistry research.

<br>

<img width="7474" height="1499" alt="Evolution of high-voltage power supplies" src="https://github.com/user-attachments/assets/64fdb9b7-e652-4876-96dd-c089151b8b42" />

<br>

These systems were developed and built in-house over several years as part of the development of plasma-based analytical instrumentation.

The project evolved from high-voltage DC supplies based on commercial CRT flyback transformers to high-frequency AC supplies using custom-designed and hand-wound high-voltage transformers.

Multiple units based on both architectures were built and used in laboratory DBD systems, including systems reported in peer-reviewed scientific publications.

<br>

## Project Overview

Two main high-voltage architectures were developed.

### 1. Flyback-Based High-Voltage DC Supply

The first architecture used a commercial CRT flyback transformer driven by a PWM-controlled switching stage.

The low-voltage stage consisted of a 230 V AC step-down transformer followed by a bridge rectifier and capacitor filtering. The resulting DC voltage was switched using a PWM-controlled MOSFET and applied to a primary winding assembled directly on the ferrite core of a commercial CRT flyback transformer.

Since the flyback transformer incorporated internal high-voltage rectification, the resulting output was unidirectional high voltage.

```text
230 V AC
    ↓
Step-down transformer
    ↓
Bridge rectifier + filtering
    ↓
Low-voltage DC
    ↓
PWM-controlled MOSFET switching stage
    ↓
CRT flyback transformer
    ↓
High-voltage DC
    ↓
DBD plasma
```

Several versions based on this architecture were constructed. The first system operated at approximately 15 kHz, while a later version was extensively characterized at approximately 40 kHz and produced high-voltage outputs of several tens of kilovolts.

<br>

**Electronic schematic of the flyback-based high-voltage power supply:**

<img width="613" height="431" alt="image" src="https://github.com/user-attachments/assets/0bfe6b55-0060-413f-b8da-392681e04972" />

<br>
<br>

### 2. Custom-Transformer High-Voltage AC Supply

The second architecture was developed to obtain a high-frequency alternating high-voltage output without the internal high-voltage rectification present in commercial CRT flyback transformers.

A laboratory-built ferrite-core transformer with custom primary and secondary windings provided high-frequency AC output. Its construction, insulation, and winding specifications are detailed below.

<br>

**Electronic schematic of the AC transformer high-voltage power supply:**

<img width="602" height="440" alt="image" src="https://github.com/user-attachments/assets/d59ac55f-7bc8-4de4-a5f5-b2b3a4ab5d59" />

<br>

In the laboratory DBD reactors, this AC architecture improved plasma ignition and discharge stability compared with the earlier internally rectified flyback systems, as discussed below.

Later versions also replaced the large AC/DC rectifier stage, consisting of a line-frequency step-down transformer, bridge rectifier, and capacitor filtering, with a compact switched-mode AC/DC power supply. An adjustable DC regulator was incorporated to independently control the voltage supplied to the switching stage.

```text
230 V AC
    ↓
Switched-mode AC/DC power supply
    ↓
Adjustable DC stage
    ↓
PWM-controlled switching stage
    ↓
Custom high-voltage transformer
    ↓
High-frequency AC output
    ↓
DBD plasma
```

<br>

## Custom High-Voltage Transformer

One of the main developments of this project was the design and construction of a high-voltage transformer specifically for the DBD systems.

The transformer uses a ferrite core with an AWG 14 primary winding and a secondary winding consisting of approximately **1500 turns of AWG 32 insulated copper wire**. The secondary winding is distributed across **eight sections of a custom PTFE holder**, which I machined using a lathe, to improve electrical insulation between winding sections.

Depending on the power supply version, 6 or 8 primary turns were used.

The complete transformer is immersed in mineral oil for additional high-voltage insulation and suppression of unwanted external discharges.

### Transformer Construction

The PTFE winding holder was fabricated in-house using a lathe. I also wound the transformer coils and assembled and insulated the complete transformer in the laboratory.

<br>

**Secondary winding in the PTFE holder, and AC transformers immersed in mineral oil in a 3D printed box:**

<img width="1920" height="719" alt="pfte holder and coil-horz" src="https://github.com/user-attachments/assets/517b2f47-e64c-4ab3-9521-97bbf83f7422" />

<br>
<br>

A video showing the winding and assembly process of the custom high-voltage transformer is available below.

<br>

https://github.com/user-attachments/assets/6445c7bf-8871-4f6d-a35a-a43146dfecba

<br>
<br>

## Electronic Design

The high-voltage transformers are driven by PWM-controlled power switching stages. The PWM generator provides independent adjustment of switching frequency and duty cycle, while the adjustable DC stage controls the voltage supplied to the transformer primary.

Different versions of the system used either MOSFET or IGBT switching devices. The earlier flyback-based systems primarily used an **IRFZ44N MOSFET**, while one of the custom-transformer AC versions used an **IRG4PH50UD IGBT**.

For this high-voltage transformer application, the IGBT provided better practical performance than the IRFZ44N used in the earlier designs and was therefore adopted during the development of the higher-power custom-transformer system.

<br>

### Operating Frequency

The switching frequency was not selected as a fixed value applicable to all power supply versions. Instead, it was experimentally adjusted according to the electrical characteristics of each transformer and power supply configuration.

The most suitable operating frequency depends on several characteristics of the transformer, including the ferrite core, primary and secondary windings, inductance, winding geometry, and parasitic capacitances. Consequently, transformers with different constructions can exhibit significantly different electrical behavior at the same switching frequency.

For each power supply, the operating frequency was therefore experimentally selected to obtain a favorable compromise between **high-voltage output, stable operation, and low power consumption**.

For example, the first flyback-based system was operated at approximately **15 kHz**, while a later flyback configuration was optimized around **40 kHz**. For the custom-transformer AC supplies, the experimentally selected operating frequency was **50 or 70 kHz**, depending on the high-voltage transformer configuration.

This optimization is important because operating a transformer outside a favorable frequency range can reduce the obtainable high-voltage output while increasing current consumption and energy losses.

<br>

## AC vs. DC Operation for DBD Plasma

One of the most important practical observations during the development of these power supplies was the substantial improvement obtained when the DBD reactors were operated with **AC rather than the unidirectional high-voltage output of the CRT flyback systems**.

The flyback-based supplies were capable of generating the required high voltage and successfully producing DBD plasma. However, after the development of the custom-transformer AC supply, a clear improvement in plasma behavior was observed.

In the DBD configurations investigated in the laboratory, the alternating high-voltage output was considerably more effective for both **plasma ignition and, especially, maintaining a stable discharge**.

This practical improvement led to the adoption of the custom-transformer AC architecture for subsequent DBD systems developed in the laboratory.

<br>

## High-Voltage Characterization

The high-voltage power supplies were characterized using an oscilloscope and a high-voltage probe rated up to 40 kV. The reported measurements describe the power-supply output under the stated measurement conditions, not necessarily the voltage across an operating plasma discharge.

For voltages exceeding the probe limit, a spark-gap method was investigated as an approximate estimate based on the electrode separation at air breakdown. The probe and spark-gap estimates showed good agreement over their common measurement range, although breakdown voltage also depends on electrode geometry and environmental conditions.

The influence of operating parameters such as switching frequency, duty cycle, and primary-side power on the high-voltage output was also experimentally investigated.

<br>

<img width="1286" height="838" alt="image" src="https://github.com/user-attachments/assets/0c8c0b66-f1b9-46b2-a635-aed2957a7b9a" />

<br>
<br>

Oscilloscope measurements were also used to investigate the switching stage and high-voltage output waveform.

For the flyback-based architecture, measurements confirmed the unidirectional nature of the high-voltage output resulting from the internal rectification of the CRT flyback transformer.

<br>

<img width="1215" height="695" alt="image" src="https://github.com/user-attachments/assets/6f1f410b-a704-401f-bcc3-51720da79a43" />

<br>
<br>

For the **custom-transformer AC supplies**, oscilloscope measurements were also used to examine the alternating high-voltage waveform and operating frequency. Depending on the transformer configuration, the selected operating frequency was **50 or 70 kHz**. Measurements made without an operating plasma load should not be interpreted as the voltage directly across the discharge.

**AC high-voltage output waveform (oscilloscope):**

<img width="1733" height="965" alt="image" src="https://github.com/user-attachments/assets/498f7e7f-ef6e-4f38-b58c-08b44a3eeee3" />

<br>
<br>

## Development

The project started in **2020** and evolved through several hardware generations as experience with high-voltage electronics and the requirements of the DBD systems increased.

```text
2020
First flyback-based HV DC supply
        ↓
Improved flyback architecture
        ↓
HV and waveform characterization
        ↓
Custom HV transformer development
        ↓
High-voltage AC operation
        ↓
IGBT-based switching
        ↓
Switched-mode low-voltage supply
        ↓
Current compact HV AC architecture
```

### 2020 — First Flyback-Based HV Supply

The first system combined a mains step-down transformer, rectification and filtering, PWM-controlled IRFZ44N MOSFET switching, and a commercial CRT flyback transformer.

The primary winding consisted of copper wire wound directly on the flyback ferrite core. A selectable primary winding configuration allowed the number of turns to be changed to adjust the high-voltage output.

The system also incorporated practical laboratory controls:
- **External trigger input:** Allowed laboratory instruments to activate the plasma remotely.
- **Selectable primary winding turns:** Allowed the flyback primary configuration to be changed.
- **Programmable timer:** Automatically switched off the plasma after a user-defined operating time.

Operating at **15 kHz** with a **50% duty cycle**, this relatively inexpensive laboratory-built supply generated several tens of kilovolts and sustained the DBD plasma used in analytical experiments.

<br>

<img width="5046" height="2138" alt="20201104_080946-horz" src="https://github.com/user-attachments/assets/53aa1805-9be1-4430-984f-4e258032d4b1" />

<br>

### Improved Flyback-Based System

The flyback architecture was subsequently improved and characterized in greater detail.

The effects of switching frequency, duty cycle, input power, and operating voltage were investigated together with the high-voltage and switching waveforms.

One optimized operating condition used **40 kHz and a 60% duty cycle**.

This version was used in a plasma-mediated mercury vapor generation system.

<br>

**Flyback-based high-voltage power supply:**

<img width="2571" height="1096" alt="IMG_0396-horz" src="https://github.com/user-attachments/assets/ec0583c6-50d3-4a73-95cd-3d6c1998ee46" />

<br>
<br>

### Transition to Custom-Transformer AC

The transition to a custom high-frequency AC transformer provided greater control over winding geometry, insulation, and electrical characteristics, enabling the high-voltage stage to be adapted to the DBD reactors.

Later versions incorporated a compact switched-mode AC/DC supply, adjustable primary-side voltage, improved power switching, and the laboratory-built high-voltage transformer.

This architecture resulted in a more compact and practical system and was subsequently reproduced for multiple DBD plasma setups.

<br>

**AC transformer high-voltage power supply:**

<img width="2331" height="1000" alt="49-horz" src="https://github.com/user-attachments/assets/3e679948-8d89-432b-8024-dbb5a36bab1c" />

<br>
<br>

## DBD Plasma Applications

The high-voltage power supplies were developed specifically for dielectric barrier discharge systems used in analytical chemistry research.

The systems have been applied to several plasma-based analytical approaches, including:

- Plasma-mediated atomization of methylmercury
- Plasma-mediated vapor generation of mercury species
- Mercury vapor generation after microwave-induced combustion
- Integrated arsenic vapor generation and atomization

<br>

<img width="2338" height="553" alt="IMG_1541-horz" src="https://github.com/user-attachments/assets/a1e04512-70c6-49a1-ad44-07842a49418c" />

<br>

<img width="1880" height="1330" alt="IMG_9451" src="https://github.com/user-attachments/assets/c3e6f364-bd96-4508-b4d8-c802843c476c" />

<br>

https://github.com/user-attachments/assets/291c9979-036a-42b4-9958-6b1318a3132e

<br>
<br>

The power supplies were therefore not developed solely as electronic prototypes. Multiple units were integrated into functional analytical instrumentation and used in scientific experiments.

<br>

## Scientific Publications

The development and application of these high-voltage power supplies have been reported in peer-reviewed scientific publications, all authored and written by me. 

The supplementary materials of these articles provide extensive technical information on the power supplies, including their electronic designs, construction details, operating parameters, and experimental characterization.

### Flyback-Based HV Power Supply

**Dielectric barrier discharge-assisted determination of methylmercury in particulate matter by atomic absorption spectrometry**

**Link:** https://doi.org/10.1039/d1ay02048j 

<br>

**Plasma-mediated vapor generation of mercury species in a dielectric barrier discharge: Direct analysis in a single drop by atomic absorption spectrometry**

**Link:** https://doi.org/10.1016/j.sab.2022.106596

<br>

### Custom-Transformer AC Power Supply

**Plasma-mediated mercury vapor generation after microwave-induced combustion of fish tissue with detection by atomic absorption spectrometry**

**Link:** https://doi.org/10.1016/j.sab.2024.107055

<br>

**Vapor generation and analyte atomization integrated into a single dielectric barrier discharge reactor: Reagent-free arsenic determination by AAS**

**Link:** https://doi.org/10.1016/j.aca.2025.344444

<br>

## Skills Demonstrated

- Power electronics and high-voltage power supply design
- Custom transformer design, winding, and insulation
- MOSFET/IGBT switching and PWM control
- Circuit prototyping, assembly, and troubleshooting
- Oscilloscope measurements and electrical characterization
- Switching-frequency optimization
- Lathe machining and fabrication of custom PTFE components
- Laboratory instrumentation and DBD plasma integration

<br>

## Safety

> **Warning**
>
> These systems operate at potentially lethal voltages. The information provided in this repository documents laboratory research equipment and is not intended as a construction guide for inexperienced users. High-voltage systems should only be operated by appropriately trained personnel using appropriate insulation, grounding, enclosures, and safety procedures.

<br>

## Author

**Gilberto Coelho**

Design, machining, assembly, electronic integration, testing, and documentation of the high-voltage systems presented in this repository.

This project was developed as part of plasma-based analytical instrumentation research.
