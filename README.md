# Low Noise Amplifier SMA 10x Board in KiCAD

This KiCad board is a low noise amplifier with SMA input and output.

- 100 kHz to 20 MHz
- 10 times amplitude amplification
- ≤ 100 µV RMS noise
- AC coupled input

## Notes on Performance as-built

- Idle current: 9 mA with +/- 5 V supplies
- Current draw rises above 20 mA for large signals
- Noise 290 µV RMS (without subtracting noise floor), when the input is hooked
  up to 1 ft RG-174 terminated in a BNC T-adapter with only a 50 Ohm terminator
  attached
- In trying to analyze with a square wave, the AC-coupling low-pass filter frequency seems
  quite high compared to the bandwidth. Maybe it should be at 10 kHz instead of
  100 kHz?
- There is a fair amount of overshoot ~30%
  - It seems to damp out in < 200 ns
