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


### Theory

- Volatge Controlled Oscillators (Variable Resistance (Potentiometer)
- Capacitance Controlled Oscillators (Voltage Controlled Components (Varactor) / Mechanical Components (Butterfly or Differential))
- Inductance Controlled Oscillators (Mechanical (Moveable Ferrite Core))
- Avalanche Breakdown (Source of White Noise (Avalanche Diode))
- Avalanche Transistor

### Components
- High Voltage Zener Diode (Avalanche)
- IMPAT Diode

Project most probably made using a IMPAT diode and decent oscillator circuits. White Noise may be generated using a Single Feedback Zener Diode. I still need to do some research on White Noise Generation. I cannot be bothered modulating anything. All design should be simple, cheap and making use of High Power Components that do simply what they are mathematically intended to do.
