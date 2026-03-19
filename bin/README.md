You'll find the [latest firmware in the github release repo for ESCape32.](https://github.com/neoxic/ESCape32/releases)

The 2 binaries in this bin directory are an experiment that are built from a fork https://github.com/adrianblakey/ESCape32 of the ESCape32 repo. They permit freq_min and freq_max to be set up to 72kHz and 144kHz respectively this might help to start high Kv motors.

The binaries in the flex-pwm directory decouple freq_min and freq_max and allow you to set min to 48 - 152 and max to min - 152.
Its build string looks like this: 

add_target(AART1X AT32F421 DEAD_TIME=0 COMP_MAP=123 ARM=0 VOLUME=0 INPUT_MODE=1 ANALOG_CHAN=6 ANALOG_MIN=0 ANALOG_MAX=1440 DUTY_MIN=100 DUTY_MAX=100  DUTY_RAMP=100 DUTY_SPUP=25 FULL_DUTY IO_RXTX)
