# Craftbeerpi4 Kettle Logic Plugin

## PID Logic with boil threshold.

If the target Temperature is above a configurable threshold the PID will be ignored and heater is switched on to the max output value. This is helpful if you use the same kettle for mashing and boiling.

Once the boil threshold temperature is reached, the boil will be done with the max boil output power

### Installation:

Please have a look at the [Craftbeerpi4 Documentation](https://openbrewing.gitbook.io/craftbeerpi4_support/readme/plugin-installation)

- Package name: cbpi4-PIDBoil
- Package link: https://github.com/daGrumpf-bxp/cbpi4-PIDBoil/archive/main.zip

### Parameters

- P - proportional value
- I - integral value
- D - derivative value
- SampleTime - 2 or 5 seconds -> how often the logic calculates the power setting
- Max_Output - heater power used when target is above boil threshold but current temp hasn't reached it yet
- Boil_Threshold - temperature above which boil logic activates (default: 98°C / 208F). Only active when target temp is also above this threshold.
- Max_Boil_Output - Power (%) used once boil threshold is reached (default: 85%)
- PID_DuringBoil - When boil threshold is active: `No` (default) uses fixed Max_Boil_Output / `Yes` hands control to the PID

### Changelog

- 11.05.26: (0.0.18) Lower log level from `warning` to `info` for normal lifecycle messages (start, mode/power changes). Set CBPi log level to `INFO` if you want to see them.
- 08.05.26: (0.0.17) Fix actor_on removed before loop — heater now started at 0% and power set exclusively by control logic on first iteration; fix heat_percent_old initialized to -1 to force first power update
- 08.05.26: (0.0.14) Fix `Boil_Threshold` GUI value not used in control logic (hardcoded 98°C was used instead); smart logging — log only on mode/power change or every 10 iterations
- 08.05.26: (0.0.10) Fix incorrect boil threshold condition (target_temp was not evaluated); fix `PID_DuringBoil` property read (NameError); fix bitwise `&` replaced with boolean `and`; add `PID_DuringBoil` parameter
- 29.12.22: (0.0.9) Fixed Bug related to Boil Threshold Parameter
- 10.05.22: (0.0.8) Updated README (removed cbpi add)
- 10.05.22: (0.0.7) Removed cbpi dependency
- 01.12.21: (0.0.6) If current kettle power is different from kettle logic, logic will overrule kettle power setting
- 21.11.21: (0.0.5) Adapted to cbpi4 4.0.0.45 to accommodate actor power settings incl. the PWM Actor
- 13.10.21: (0.0.4) Added Power setting for Boil
- 13.10.21: (0.0.3) Improvement of actor toggling in case of 0% or 100% heating
- 12.10.21: (0.0.2) Bug fixing MashStep Automode Issue
- 19.08.21: (0.0.1) Initial commit
