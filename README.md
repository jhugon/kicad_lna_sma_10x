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
- Noise 290 µV RMS at output (without subtracting noise floor), when the input is hooked
  up to 1 ft RG-174 terminated in a BNC T-adapter with only a 50 Ohm terminator
  attached. But get 1478 µV another time?
- In trying to analyze with a square wave, the AC-coupling low-pass filter frequency seems
  quite high compared to the bandwidth. Maybe it should be at 10 kHz instead of
  100 kHz?
- Step response:
    - 10-90% rise time: 22 ns
    - 0-99% rise time: 32 ns
    - Overshoot: 28%
    - 1 pct settling time: ~200 ns

## To-Do

- Decoupling cap(s) from V+ to V-?
- Compensation cap between gain-amp out and in-?
- Lower input blocking filter freq?
- Forgot about factor of 1/2 from 50 Ohm termination voltage divider--need extra factor of 2 gain
- Add input/output labels on SMAs
- Add +/- signs on DC in
- SMA terminator for noise measurements
