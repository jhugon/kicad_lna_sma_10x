# Low Noise Amplifier SMA 10x Board in KiCAD

This KiCad board is a low noise amplifier with SMA input and output.

- 100 kHz to 20 MHz
- 10 times amplitude amplification
- ≤ 100 µV RMS noise
- AC coupled input

## Notes on Performance as-built

I've been setting +/- 5 V supplies, 20 mA current limit, with +/- 6V OVP and 25 mA OCP.

- Idle current: 9 mA with +/- 5 V supplies
- Current draw rises above 20 mA for large signals
- Noise 1478 µV RMS at output (without subtracting noise floor), with a broad bump around 8-10 MHz in the FFT
- In trying to analyze with a square wave, the AC-coupling low-pass filter frequency seems
  quite high compared to the bandwidth. Maybe it should be at 10 kHz instead of
  100 kHz?
- Sin response:
    - Gain peaks ~ 9 MHz at 17 dB
    - Gain -3 dB from peak a little above 10 MHz
- Step response:
    - 10-90% rise time: 22 ns
    - 0-99% rise time: 32 ns
    - Overshoot: 28%
    - 1 pct settling time: ~200 ns
- Hooked up to SiPM and LED pulser:
    - Detect pulses with 10s of mV peak heights
    - Ringing is evident, lasts ~ 250 ns
    - Pulse width 50-100 ns
    - Can't see pulse height quantization, it's just one big smeared gaussian

With 10 pF (leaded) decoupling cap soldered between U1 output and inverting input:

- Noise a bit lower than before; FFT is flat compared to a broad, low peak around 20 MHz before
- Sin response:
    - Gain max ~flat between 400 kHz and 100 MHz
    - Gain -3 dB from peak at 100 kHz and 3 MHz
- Step response:
    - Minimal overshoot/settling, probably overdamped now
    - 10-90% rise time: 112 ns
    - 0-99% rise time: 293 ns
    - Overshoot: <1%
    - 1 pct settling time: ~250 ns
- Hooked up to SiPM and LED pulser:
    - Pulse height seems lower than before
    - No ringing, maybe baseline is a bit lower on tail
    - Pulse width 100-150 ns
    - Can't see pulse height quantization, it's just one big smeared gaussian

## To-Do

- Decoupling cap(s) from V+ to V-?
- Compensation cap between gain-amp out and in-?
- Lower input blocking filter freq?
- Forgot about factor of 1/2 from 50 Ohm termination voltage divider--need extra factor of 2 gain
- Add input/output labels on SMAs
- Add +/- signs on DC in
- SMA terminator for noise measurements
