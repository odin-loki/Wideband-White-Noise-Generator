# 100W Wideband Noise Generator

A complete Verilog implementation of a high-power RF noise generation system based on the Chua circuit topology, featuring comprehensive control and protection systems for safe operation.

## Features

### Core Noise Generation
- Chua circuit-based chaotic oscillator for true random noise generation
- Dynamically tunable frequency range via variable components
- Configurable nonlinearity characteristics for optimized noise distribution
- High-precision op-amp control with programmable bias and gain settings

### RF Power Chain
- Complete driver and power amplifier stages
- 100W maximum output capability
- Configurable impedance matching network
- Selectable filter banks for spectral shaping
- Variable output attenuation control

### Protection Systems
- Comprehensive thermal management with multi-point sensing
- VSWR protection with automatic impedance matching
- Arc detection and fast shutdown capability
- Over-current and power supply fault protection
- Safety interlocks and emergency shutdown systems
- Automatic cooling control with variable fan speed

### Power Management
- Sequenced startup and shutdown procedures
- Multiple regulated power supplies for various stages
- Crowbar protection for catastrophic fault conditions
- Current and voltage monitoring on critical rails

### User Interface
- Real-time frequency and power adjustment
- LCD display for parameter visualization
- Status LED indicators for system monitoring
- Standby mode for rapid power cycling

## System States

The noise generator implements a robust state machine with the following operational modes:

1. OFF - System powered down
2. INIT - Initial power-up and self-test
3. STANDBY - Ready state with minimal power consumption
4. STARTUP - Sequenced power-up of all subsystems
5. RUN - Normal operation with full monitoring
6. FAULT - Protected shutdown on error condition
7. SHUTDOWN - Sequenced power-down procedure

## Safety Features

The system incorporates multiple layers of protection:

- Temperature monitoring across 8 critical points
- VSWR monitoring and automatic shutdown
- Arc detection with microsecond response
- Door interlock for operator safety
- Airflow monitoring for cooling verification
- Overcurrent protection on all power rails
- Automatic impedance matching to prevent reflected power

## Technical Specifications

- Maximum Output Power: 100W
- VSWR Protection Threshold: 3:1
- Maximum Operating Temperature: 85°C
- Comprehensive current limiting
- Multiple regulated power supplies
- Variable frequency control
- Digital bias and gain control
- Real-time power monitoring
- LCD frequency display

## Implementation

The system is implemented in Verilog and designed for synthesis on FPGA platforms. Key components include:

- Main state machine controller
- Protection system monitor
- Power sequencing logic
- LCD interface controller
- Temperature management system
- Real-time parameter adjustment
- Status monitoring and display

## Usage Notes

1. The system requires proper cooling installation before operation
2. All interlocks must be satisfied for system enablement
3. Allow proper warm-up time in standby mode
4. Monitor VSWR during initial power-up
5. Observe maximum temperature and power ratings

## Getting Started

1. Ensure all power and control connections are properly made
2. Verify cooling system operation
3. Close all safety interlocks
4. Enable main power switch
5. Wait for initialization completion
6. Exit standby mode when ready
7. Adjust frequency and power as needed

## Contributing

When contributing to this project, please:

1. Fork the repository
2. Create a feature branch
3. Follow the existing code style
4. Add comprehensive test coverage
5. Submit a pull request

# Research

## Considerations
- Analogue
- High Power
- Simplicity
- Wide band generation

## Theory

- Volatge Controlled Oscillators (Variable Resistance (Potentiometer)
- Capacitance Controlled Oscillators (Voltage Controlled Components (Varactor) / Mechanical Components (Butterfly or Differential))
- Inductance Controlled Oscillators (Mechanical (Moveable Ferrite Core))
- Avalanche Breakdown (Source of White Noise (Avalanche Diode))
- Avalanche Transistor

## Components
- Considering High Voltage Zener Diode (Avalanche) (White Noise)
- Considering IMPAT Diode (White Noise)

### Power Transistors (Will Give a Sweep Sinusoidal Wave)
- Best (100w, DC to 14 Ghz): https://www.qorvo.com/products/p/TGF2023-2-20#overview
- Second (250w, DC to 4 Ghz): https://www.qorvo.com/products/p/TGF2819-FL#overview
- Other: https://store.qorvo.com/products/detail/qpd0020-qorvo/637038/
- Other: https://www.ampleon.com/products/general-purpose-wideband/50-v/CLF1G0060S-30.html

### Normal Resistors and Capacitors:

- https://www.ohmite.com/high-power/
- http://www.vishay.com/resistors-fixed/power-100-to-500/
- http://www.avx.com/products/supercapacitors/scc-series/

### Broadband Inductor:

- https://www.coilcraft.com/bcr.cfm
- https://www.coilcraft.com/bcl.cfm
- https://www.gowanda.com/military/
- https://www.gowanda.com/conical-inductors/

### Varactor Diodes (varicap):

- https://www.macom.com/products/diodes/varactor-tuning-diodes
- https://www.microsemi.com/product-directory/rf-microwave-a-millimeter-wave/1591-diodes-varactor
- https://www.rfmw.com/userewavepreview.aspx?pid=565
- https://www.skyworksinc.com/en/Products/Diodes?gclid=EAIaIQobChMIrPPq3bn25wIV2RwrCh3NRABqEAAYASAAEgK6CPD_BwE

### Varistor:

- http://www.vishay.com/varistors/list/product-29081/

## General
Project most probably made using a IMPAT diode and decent oscillator circuits. White Noise may be generated using a Single Feedback Zener Diode. I still need to do some research on White Noise Generation. I cannot be bothered modulating anything. All design should be simple, cheap and making use of High Power Components that do simply what they are mathematically intended to do.

## Notes 12/08/2024
I implemented a Wideband Noise Generator with Chuas Circuit and primarily analogue controls using Claude AI. Looking at my past notes, theres a lot that can be done.

## Notes 29/02/2020
Since I found a High Power Transistor/Amplifier. Pretty sure I just need to find some High Power RLC components and build an Oscillator and give it power. What I really need to do, is figure out how to make the Oscillator tunable, so I get the full 100 watts across the DC to 14 Ghz Spectrum. That is with a Varactor or Potentiometer. I want a feedback circuit, so when the frequency is high enough (14 Ghz) it will cutoff and rebegin at DC. Maybe off the Reactance of the LC components. I will research if frequency Based Multiplexing to RLC circuits is a thing. At any rate I found the Components I need to build such a circuit. I am not considering Wideband Resistors or Capacitors, I feel at a Larger level they are simple enough in design to handle Broadband whilst 0402 SMT sizes needs specialised design considerations and testing. (Make it High Power, Make it Chunky.)

## Notes 01/03/2020
Just noticed it is a leap year. Incidently while I slept I asked myself if I could drive the amplifier transistor in Avalanche Breakdown mode at about 10 volts or something above the Recomended Voltage. The point is it is above the Breakdown Voltage. The current has to drop accordingly to keep the 100 watt power rating. So I am emailing the Manufacturer to ask them about the characteristics of this transistor. Will update later, it would be nice if it just generated white noise constantly distributed across the response spectrum. I also thought of a basic number for the Resistor of 100 Kilo Ohms, 400 Henries for a Inductor and 60 Farads for a Capacitor. Have no idea why but I will profile with these numbers.

## Notes 06/03/2020

##### More Advanced Circuit Design:
Considering using the Oscillator Loop as an amplifier for a Phase Synced PLL Signal Generator. The PLL Generator will generate desired frequencys up to 14 GHz and feed it to the Oscillator Loop. The Loop will generate the Frquencys sent via adjusting capacitance / inductance or something?
The question remains how to use the circuit like an amplifier to acheieve Frquency Selection or to avoid frequencys across a desired spectrum.

##### Simple Circuit:
Found suitable Voltage Supply circuits for a Simple Circuit. Will connect to power point, via adaptor. Should be universally powered.
https://tracopower.com, TPP 100A-J Series.
https://rdtech.en.alibaba.com/ 100 Watt, AC-DC Selectable Power Supply.

