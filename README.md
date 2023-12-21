# Adrian and Richard's (AART's) Slot Car eCom

This repo contains a KiCad design, built binaries (bootloader and firmware) and help for a slot car brushless motor electronic commutator or "eCom", also known as an Electronic Speed Controller (ESC).

Please note this is a prototype design and has yet to be manufactured and tested. Once it is, the information in this repository shall be updated to reflect that change in development status.

All the intellectual property is released under a [creative commons license](https://creativecommons.org/share-your-work/cclicenses/#:~:text=Creative%20Commons%20licenses%20give%20everyone,creative%20work%20under%20copyright%20law.). Under the terms of this license you are free to use everything you find here and make your own eCom from the distributed files. We hope that by doing so we'll stimulate innovation and experimentation. If you have suggestions for improvement please file a bug report and tell us about it. We'll provide some other feedback mechanisms as we go on and build a community. Also a good place to get help is the [ESCape32 slot car discord channel.](https://discord.com/invite/aed6xdSM5Y) ESCape32 is the firmware we have used to flash and test this eCom it's also open source and you'll find it on [github too.](https://github.com/neoxic/ESCape32)

There is obviously nothing stopping you from making your own versions of this part, calling it your own and selling it as a finished product. If you want to do that we only ask that you negotiate a small royalty payment with us. Some income from this effort would help to defray our development costs and extra income could be put to use to help the hobby.

We also ask that nothing here is used for military purposes. This applies to the ESCape32 firmware too.

# A Bit of Background

After taking up slot car racing for the second time in late 2022 my attention was quickly caught by the introduction of small brushless drone motors to slot car racing. There are [several links this being one ...](http://slotblog.net/topic/100990-designer-of-the-brushless-slot-car-speed-controller/) Three people deserve credit for this, namely: Pete Smits, Bob Budge and Richard Mack. Pete Smits is the developer of open source esc firmware called AM32. Bob and Richard are UK slot car racers with the vision and determination to upend the status quo.

They came up with a slot-car specific ESC (the Smits-Budge-Mack SBM) that they named an eCom, that has been in the marketplace for just over a year. It has set the standard by being reliable, relatively inexpensive and functional.

It's hard to do better than this, however it does suffer from a few drawbacks, namely:

It's closed - despite the [AM32 firmware](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) being readily available the SBM gets a custom build of this code and there's no information to explain how a hobbyist might want to make similar updates, to not only the code but also the hardware design. There's no clarity around the intellectual property ownership.

The hardware design is good but after taking a close look at it we believed it was possible to do better, by creating something that could respond faster, and operate from a lower starting voltage, operate at higher voltages and current. These capabilities are all captured in the requirements document that you'll find in the "docs" directory.

The cost is still a little too much for most people. The cost of electronics is a function of the parts' costs. A good rule of thumb is that the final cost of a part is a bout 4 times the parts cost. Therefore by making informed parts choices that might say save a cent or two while still optimizing performance, a much more cost effective design can be produced. We think we have done this.

# The Files

In this repo you'll find the complete set of KiCad files for the design in the directory AART11-2023-12-13_115145. The AART is our partnership acronym. In the same way Pete/Bob/Richard called theirs SBM - we've given ours the catchy name: Adrian And Richard Technology (AART) and I suppose it reflects the fact that it really is a work of art :-) The board itself is called a Remora. I named our first prototype this because it was a little add-on board for a commercial drone ESC that clung to the top - a bit like the remora fish clings to a shark. Richard liked the name and persuaded me to keep it for the product - cause it sort of sticks to a slot car chassis I suppose. It's printed on the PCB - if you don't like it - well I hope you know what to do :-)

There is also a binary directory called "bin" in which you'll find ESCape32 binaries build specifically for the part. There is a custom bootloader and two different versions of the firmware.

Needless to say you can download the sources of ESCape32 and build them yourself assuming you have a suitable machine on which to do so. We build ours on an Arch-Linux laptop - it only takes a few seconds to do.

# Obtaining One For Yourself

If you want one of these - you have a few choices, namely:

  1. Ask us (nicely) for one.
  2. Call your favorite slot car parts vendor - maybe Betta in the UK and maybe do-slot in Germany and in the USA(?)
  3. Make one yourself.

We should have a few flashed, tested and inventoried for our own use and to give to friends and family (neither Richard nor I have family that slot car race :-) - so I suppose half of that is a lie) If you are very nice to us and you are willing to be a tester and provide constructive feedback and suggestions I am pretty sure you'll get one. At some point the supply will run out and we might well have moved on to working on V2, V3 ... (there will be innovations)

We hope that some of the vendors want to get involved and see an opportunity to make and sell these at a profit. As you'll see there is some effort and cost involved for them to do that, so expect to pay a reasonable premium for a finished item.

Also you can make one yourself. It not hard to do and you'll have some fun doing it and learn some new skills. If you want to make a lot and sell them - please do ... The basic steps to do so are: create an account on JLCPCB, upload some files from the production directory, possibly order missing parts, wait a while, optiionally build a version of the firmware, flash the part with your own build or the one we supply.

We'll provide detailed instructions for doing that are below.

# ESCape32 Build Options
The best place to study the settings is here:
https://github.com/neoxic/ESCape32/wiki/Configuration#settings

Include the ANALOG option if you don't want CLI access for configuration, however better just to enable it by leaving the option out.

Setting these target in the CMakeLists.txt will enable both CLI and Analog throttle:

In ESCape32/boot/CMakeLists.txt
  add_target(_BOOT3_FAST STM32F0 IO_PA2 USARTv1 FAST_EXIT)

In ESCape32/CMakeLists.txt

  dd_target(_SLOTCAR AT32F421 DEAD_TIME=66 COMP_MAP=213 ANALOG_MIN=200 ANALOG_MAX=909 ANALOG_PIN=3 ARM=0 VOLUME=0 INPUT_MODE=1 FREQ_MIN=48 FREQ_MAX=96 DUTY_DRAG=70)


To assign analog throttle to pin PA3 on the AT32F421 MCU, you use the ANALOG_PIN=3  option.

  1) Let's assume your figures - the minimum input voltage is 2.5V, the maximum input voltage is 10V.
  2) For a 10K/1K divider, we get a factor of 1/(10+1)=1/11.
  3) 2.5V translates to 2.5/11=227mV, 10V translates to 10/11=909mV on the voltage divider pin, so we set the following options:
  ANALOG_MIN=227
  ANALOG_MAX=909

There will be a quadratic throttle curve when both voltage level and pwm duty cycle are applied. Motor voltage is 1/4 at 1/2 "throttle" voltage, for example.

To enable 100% drag brake, you use the DUTY_DRAG=100  option.

  _SLOTCAR = name
  AT32F421 = specify the Artery F421 mcu
  DEAD_TIME
  COMP_MAP
  ANALOG_MIN = the voltage at which the pwm duty cycle starts ramping up 200 is about 2.2vDC
  ANALOG_MAX = the voltage at which the duty cycle reaches 99% = 909 is about 10vDC
  ANALOG_PIN
  ARM
  VOLUME=0 turn off sounds
  INPUT_MODE
  FREQ_MIN = lowest pwm frequency
  FREQ_MAX = highest pwm frequency
  DUTY_DRAG = duty cycle for braking

# Odd Notes

## The F421 Startup Delay

https://hackaday.com/2020/10/22/stm32-clones-the-good-the-bad-and-the-ugly/ Search for "boot-up delay" to get to the piece. Artery chips are not the same - it might be something similar.

AT32F421 startup delay is ~4.2ms.

After startup, there's a little bit of extra time needed to switch clock source, lock PLL, calibrate ADC, etc. For the STM32G071, it all stays within about 1ms altogether. On the other hand, it takes another extra ~1ms for the AT32F421. Not too bad, but since there's an inevitable extra 4.2ms boot delay, it all comes down to ~5.5ms that Richard witnessed in his analysis.

## To Start a 10,000kV

When the motor spins up, maximum duty cycle is limited at 10% by default before a full synchronized revolution is reached, i.e. 6 sync'ed commutations have commenced. This value can be overridden by the DUTY_SPUP build option. The maximum value is 25%. Please note that allowing even higher DUTY_SPUP values is possible, but generally it is dangerous as a stuck rotor will lead to instant motor overheating. Higher values also degrade smooth spinup most of the times because the motor tends to desync right away and stutters longer. Another unused option is FREQ_MIN which is 24kHz by default. Setting FREQ_MIN to 48 might help reduce current ripple.

The default acceleration ramp DUTY_RAMP value is 25 (conservative 2.5%/ms) which leads to 100/2.5=40ms from 0% to 100% throttle. This can be easily increased. The maximum value is 100, i.e. 10%/ms.

It's important that increased duty_spup has much less effect under load. In a real life situation, a motor with a relatively significant load simply can't reach maximum RPM in just 40ms. Increased acceleration ramping might speed it up a bit, but with a progressively diminishing effect, so care must be taken. On the other hand, too rapid power increase often leads to desyncs in some bigger motors (not our case). That is why the default value of 2.5%/ms is somewhat conservative as a one size fits all value.

Why would you want to override DUTY_SPUP? Is it not okay for a motor to sync on moderate power? Why and how would you want to override DUTY_RAMP? Is it not okay for a motor to reach its maximum RPM in 40ms (with no load)? If it's not, then what time is okay? 30ms, 20ms? And you go from there.

All motors and loads are different. You can't know beforehand, so you can't really have some bleeding edge values in hopes they will work with all motors and in all conditions. Hence, the default settings.

An ideal commutation should happen when the rotor is at 90 degrees to the field, so torque is maximized.

But in reality, this is barely feasible because a slight deviation, and you get a desync. Therefore timing is advanced so commutation delay is reduced. With more timing advance you get further and further away from the ideal 90 degrees between the rotor and the field.

The timing setting of n equates to: 3.75 x n degrees

The default is 4, or 15 degrees. The value can be set to between 1 and 7.

In testing a 1105 10000KV motor desyncs on 3S with the default settings. Increased timing helps get rid of desyncs, nothing else. The same 10000KV motor with 22.5 degree timing (timing=6) instead of the default 15 degrees (timing=4).

  set timing 6
  set freq_min 48
  set freq_max 96
  set duty_rate 15

In case of the 10000KV motor, set duty_rate to 15 (1.5%/ms). The latest code doesn't slow down anything too much because it's doubled above 60K ERPM.

And also it's sometimes not even necessary under load.

## 100% duty cycle

PWM duty cycle is always one MCU clock cycle less than 100%. If allowed to be 100%, two problems arise. First, there's a very pronounced step between 100%-1 and full 100% duty cycle. Second, the charge pump capacitor becomes starved, i.e. has no time to charge. I guess these two problems are interconnected. So if more output is needed, simply supply more voltage.

The ESCape32 firmware is deliberately set to not run at 100% duty cycle. It maxes out at 99% to leave a clock cycle for ... If you want a 100% dc you need to modify the code and all bets are off :-) it's not supported and a very bad idea for small motors because any (high or low) PWM frequency is meaningless at 100% dc.

Change this line: https://github.com/neoxic/ESCape32/blob/master/src/main.c#L616
    IM1_ARR = arr - 1;

## Default Drag Brake Setting 75%

The default value is not a random value. When a motor is driven using complementary PWM (so called damped mode) it's literally braking while running. In other words, its two energized phases are either connected to rail and ground (driving) or both connected to ground (braking). When duty cycle is close to 100%, the energized phases spend most of the time in driving state (connected to opposite polarities) giving 0% braking. When duty cycle is close to 0%, the energized phases spend most of the time in braking state (connected to ground) yielding a rough equivalent of 66% drag brake force. Deadtime obviously slightly reduces running brake by introducing an unconnected gap between transitions from driving to braking.

So with the default 75% drag brake the transition from running brake to drag brake is already quite smooth.

But if you need more abrupt brake higher than 75%, then yes, it won't be smooth of course.

