# Wideband White Noise Generator
~100 Watt, Wideband (1 Hz to 6 Ghz), White Noise RF Signal Generator, with Sweep function.

## Use Case
- Jamming
- Testing

## Considerations
- Analogue
- High Power
- Simplicity
- Wide band generation
- Minimal elimination of SNR.
- Initial Hand Calculations
- Use of this free tool to verify, http://www.spectrum-soft.com/index.shtm


## Theory

- Volatge Controlled Oscillators (Variable Resistance (Potentiometer)
- Capacitance Controlled Oscillators (Voltage Controlled Components (Varactor) / Mechanical Components (Butterfly or Differential))
- Inductance Controlled Oscillators (Mechanical (Moveable Ferrite Core))
- Avalanche Breakdown (Source of White Noise (Avalanche Diode))
- Avalanche Transistor

## Components
- High Voltage Zener Diode (Avalanche)
- IMPAT Diode

### Power Transistors
- Best (100w, DC to 14 Ghz): https://www.qorvo.com/products/p/TGF2023-2-20#overview
- Second (250w, DC to 4 Ghz): https://www.qorvo.com/products/p/TGF2819-FL#overview
- Other: https://store.qorvo.com/products/detail/qpd0020-qorvo/637038/
- Other: https://www.ampleon.com/products/general-purpose-wideband/50-v/CLF1G0060S-30.html

## General
Project most probably made using a IMPAT diode and decent oscillator circuits. White Noise may be generated using a Single Feedback Zener Diode. I still need to do some research on White Noise Generation. I cannot be bothered modulating anything. All design should be simple, cheap and making use of High Power Components that do simply what they are mathematically intended to do.

## Notes 29/02/2020
Since I found a High Power Transistor/Amplifier. Pretty sure I just need to find some High Power RLC components and build an Oscillator and give it power. What I really need to do, is figure out how to make the Oscillator tunable, so I get the full 100 watts across the DC to 14 Ghz Spectrum. That is with a Varactor or Potentiometer. I want a feedback circuit, so when the frequency is high enough (12 Ghz) it will cutoff and rebegin at DC. Maybe off the Reactance of the LC components.
