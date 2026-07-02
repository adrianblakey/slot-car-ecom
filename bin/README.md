This repo contains experimental binaries - USE AT YOUR OWN RISK.

We know that high Kv motors are easier to commutate using higher pwm frequencies. The off-the-shelf ESCape32 binaries place restrictions on the values for pwm_min/max - probably because several ESCape32-targetted mcu's run at slower clocks than the F421 and the "market" for this firmware is more conservative drone motors - not outrageous (22,000Kv) slot car motors. 

These binaries expand and raise the pwm limits to values that are just below the possible theoretical values supported by the Artery F421 peripherals. The pwm_min limit is more critical that the pwm_max limit. Also, the 2:1 ratio in the ESCape32 firmware is removed allowing you to pick values yourself.

Also know that we only use pwm during the start and synchronization of a motor, and not once it's running when it's turned off and effectively running at 100% duty cycle (with pwm off).

If you are curious to see the chnages they are in a fork of the EScape32 repo in my own repo e.g. https://github.com/adrianblakey/ESCape32/blob/master/src/util.c#L435

And eh, yes they were Vibe-coded using claude.ai - so use at your own risk and report bugs :-)
