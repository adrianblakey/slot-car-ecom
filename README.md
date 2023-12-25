# Adrian and Richard's (AART's) Slot Car eCom

This repo contains a KiCad design, built binaries (bootloader and firmware) and help for a slot car brushless motor electronic commutator or "eCom", also known as an Electronic Speed Controller (ESC).

Please note this is a prototype design and is being manufactured. It has yet to be tested. Once it is, the information in this repository shall be updated to reflect that change in development status.

All the intellectual property is released under a [creative commons license](https://creativecommons.org/share-your-work/cclicenses/#:~:text=Creative%20Commons%20licenses%20give%20everyone,creative%20work%20under%20copyright%20law.). Under the terms of this license you are free to use everything you find here and make your own eCom from the distributed files. We hope that by doing so we'll stimulate innovation and experimentation. If you have suggestions for improvement please file a bug report and tell us about it. We'll provide some other feedback mechanisms as we go on and build a community. Also a good place to get help is the [ESCape32 slot car discord channel.](https://discord.com/invite/aed6xdSM5Y) ESCape32 is the firmware we have used to flash and test this eCom it's also open source and you'll find it on [github too.](https://github.com/neoxic/ESCape32)

There is obviously nothing stopping you from making your own versions of this part, calling it your own and selling it as a finished product. If you want to do that we only ask that you negotiate a small royalty payment with us. Some income from this effort would help to defray our development costs and any extra income will be put back into the hobby.

We also ask that nothing here is used for military purposes. This applies to the ESCape32 firmware too.

# A Bit of Background

After taking up slot car racing for the second time in late 2022 my attention was quickly caught by the introduction of small brushless drone motors to slot car racing. There are [several links this being one ...](http://slotblog.net/topic/100990-designer-of-the-brushless-slot-car-speed-controller/) Three people deserve credit for this, namely: Pete Smits, Bob Budge and Richard Mack. Pete Smits is the developer of open source esc firmware called AM32. Bob and Richard are UK slot car racers with the vision and determination to upend the status quo.

They came up with a slot-car specific ESC (the Smits-Budge-Mack SBM) that they named an Electronic Commutator or eCom, that has been in the marketplace for just over a year. It is not the only one out there but it has set the standard by being small, reliable, relatively inexpensive and functional.

It's hard to do better than this, however when we started out we took a look at it and decided we could do better since it does suffer from a few drawbacks, namely:

It's closed - despite the [AM32 firmware](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) being readily available the SBM gets a custom build of this code and there's no information to explain how a hobbyist might want to make similar updates, to not only the code but also the hardware design. And there's no clarity around the intellectual property ownership.

The hardware design is good however we wanted something that could respond faster, and operate from a lower starting voltage, andoperate at higher voltages and current. These capabilities are all captured in the [requirement's document](https://github.com/adrianblakey/slot-car-ecom/blob/main/docs/slot-car-ecom-requirements.ods) that you'll find in the "docs" directory.

Its cost is still a little too much for most people. The cost of electronics is a function of the parts' costs. A good rule of thumb is that the final cost of a part is about 4 times the constituent parts cost. Therefore, by making informed parts choices that might say save a cent or two while still optimizing performance, a much more cost effective design can be produced. We think we have done this.

# The Files

In this repo you'll find the complete set of KiCad files for the design in the directory AART11-2023-12-13_115145. The AART is our partnership acronym. In the same way Pete/Bob/Richard called theirs SBM - we've given ours the catchy name: Adrian And Richard's Technology (AART) and I suppose it reflects the fact that it really is a work of art.

The board itself is called a Remora. I named our first prototype this because it was a little add-on board for a commercial drone ESC (HAKRC BLHeli_32 Bit 35A 2-5S ESC) that clung to the top - a bit like the [remora fish](https://en.wikipedia.org/wiki/Remora) clings to a shark. Richard liked the name and persuaded me to keep it for the product - cause it sort of sticks to a slot car chassis I suppose. It's printed on the PCB - if you don't like it - well I hope you know what to do :-)

There is also a [binary directory called "bin"](https://github.com/adrianblakey/slot-car-ecom/tree/main/bin) in which you'll find ESCape32 binaries built specifically for the part. There is a custom bootloader _BOOT3_FAST-rev2.bin and a firmware build _SLOTCAR-rev8.bin - you should not need the non-bin files - but they are there for completeness.

Needless to say you can download the sources of ESCape32 and build them yourself assuming you have a suitable machine on which to do so. We build ours on an Arch-Linux laptop - it only takes a few seconds to do.

# Obtaining One For Yourself

If you want one of these - you have a few choices, namely:

  1. Ask us (nicely) for one.
  2. Make one yourself.
  3. And hopefully sometime in the future - call your favorite slot car parts vendor - maybe Betta in the UK and maybe do-slot in Germany and in the USA(?)

We should have a few flashed, tested and inventoried for our own use and to give to friends and family (neither Richard nor I have family that slot car race :-) - so I suppose half of that is a lie) If you are very nice to us and you are willing to be a tester and provide constructive feedback and suggestions I am pretty sure you'll get one. At some point the supply will run out and we might well have moved on to working on V2, V3 ... (there will be innovations)

You can make one yourself. Everything is here to do that. It not hard to do and you'll have some fun doing it and learn some new skills. If you want to make a lot and sell them - please do ... The basic steps to do so are: create an account on JLCPCB, upload some files from the production directory, possibly order missing parts, wait a while, optionally build a version of the firmware, flash the part with your own build or the one we supply.

We hope that some of the vendors want to get involved and see an opportunity to make and sell these at a profit. As you'll see there is some effort and cost involved for them to do that, so expect to pay a premium for a finished item.

Once I can figure out how to create a proper WiKi on git - we'll provide some more detailed instructions for doing all this.

# ESCape32 Build Options

We have decided  to use the ESCape32 firmware for the device. There are a number of good reasons for doing so, namely:

  - Writing the code and getting it right, is difficult.
  - It's open source.
  - It's supported and maintained.
  - There is a community and Arseny specifically created a Discord channel for slot-cars (yeah).
  - It's lovely, readable code.
  - I can't say enough good things about Arseny, its developer, who's been helpful and supportive of our efforts.

If you want to build and flash your own version of the firmware the best place to study the settings is here:

https://github.com/neoxic/ESCape32/wiki/Configuration#settings

Include the ANALOG option if you don't want CLI access for configuration, however better just to enable it by leaving the option out.

Setting these targets in the CMakeLists.txt will enable both CLI and Analog throttle:

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

# Misc. Notes

## The F421 Startup Delay

If there is one downside to our design it might be the choice of mcu. We relize that it has a small start up delay which we think might be caused by memory copying. This article explains something about this issue for other chips https://hackaday.com/2020/10/22/stm32-clones-the-good-the-bad-and-the-ugly/ Search for "boot-up delay" to get to the piece. Artery chips are not the same, although it might be something similar.

The AT32F421 startup delay is measured at ~4.2ms.

After startup, there's a little bit of extra time needed to switch clock source, lock PLL, calibrate ADC, etc. For the STM32G071, it all stays within about 1ms altogether. On the other hand, it takes another extra ~1ms for the AT32F421. Not too bad, but since there's an inevitable extra 4.2ms boot delay, it all comes down to ~5.5ms that Richard witnessed in his analysis.

We chose the Artery F421 mcu because of cost and speed so that we had a fast enough clock speed to commutate a 12 pole motor at very high rpm, say 180,000 rpm+. As motor technogology matures we might need to revist this decision and it's an obvious change to the design that should be fairly simple to make. If you do that, please contribute it back.

## To Start a 10,000kV

There are several parameters to the ESCape32 firmware that can be adjusted to alter motor function.

When a motor spins up, maximum duty cycle is limited at 10% by default before a full synchronized revolution is reached, i.e. 6 sync'ed commutations have commenced. This value can be overridden by the DUTY_SPUP build option. The maximum value is 25%. Please note that allowing even higher DUTY_SPUP values is possible, but generally it is dangerous as a stuck rotor will lead to instant motor overheating. Higher values also degrade smooth spinup most of the times because the motor tends to desync right away and stutters longer. Another option is FREQ_MIN which is 24kHz by default. Setting FREQ_MIN to 48 can help reduce current ripple.

The default acceleration ramp DUTY_RAMP value is 25 (conservative 2.5%/ms) which leads to 100/2.5=40ms from 0% to 100% throttle. This can be easily increased. The maximum value is 100, i.e. 10%/ms.

It's important that increased DUTY_SPUP has much less effect under load. In a real life situation, a motor with a relatively significant load simply can't reach maximum RPM in just 40ms. Increased acceleration ramping might speed it up a bit, but with a progressively diminishing effect, so care must be taken. On the other hand, too rapid power increase often leads to desyncs in some bigger motors (not our case). That is why the default value of 2.5%/ms is somewhat conservative as a one size fits all value.

Why would you want to override DUTY_SPUP? Is it not alright for a motor to sync on moderate power? Why and how would you want to override DUTY_RAMP? Is it not alright for a motor to reach its maximum RPM in 40ms (with no load)? If it's not, then what time is okay? 30ms, 20ms? Do the calcualation and go from there.

All motors and loads are different. You can't know beforehand, so you can't really have some bleeding edge values in the hope they will work with all motors and in all conditions. Hence, the default settings.

An ideal commutation should happen when the rotor is at 90 degrees to the field, so torque is maximized.

But in reality, this is barely feasible because a slight deviation, and you get a desync. Therefore timing is advanced so commutation delay is reduced. With more timing advance you get further and further away from the ideal 90 degrees between the rotor and the field.

The timing setting of n equates to: 3.75 x n degrees

The default is 4, or 15 degrees. The value can be set to between 1 and 7.

In testing, a 1105 10000KV motor desyncs on 3S (S means the number of LiPo RC batteries in series. 2S is about 7.4VDC, 3S is about 11.1VDC)  with the default settings. Increased timing helps get rid of desyncs, nothing else. The same 10000KV motor with 22.5 degree timing (timing=6) instead of the default 15 degrees (timing=4).

  set timing 6  
  set freq_min 48  
  set freq_max 96  
  set duty_rate 15  

In case of the 10000KV motor, set duty_rate to 15 (1.5%/ms). The latest code doesn't slow down anything too much because it's doubled above 60K ERPM.

And also it's sometimes not even necessary under load.

## 100% duty cycle

In the ESCape32 code the PWM duty cycle is always one MCU clock cycle less than 100%. If allowed to be 100%, two problems arise. First, there is a very pronounced step between 100%-1 and full 100% duty cycle. Second, the charge pump capacitor becomes starved, i.e. has no time to charge. These two issues are interconnected. So if more output is needed, simply supply more voltage.

The ESCape32 firmware is deliberately set to not run at 100% duty cycle. If you want a 100% dc you need to modify the code and all bets are off :-) it's not supported and a very bad idea for small motors because any (high or low) PWM frequency is meaningless at 100% dc.

If you really want to try it - change this line: https://github.com/neoxic/ESCape32/blob/master/src/main.c#L616 to:
    
    IM1_ARR = arr - 1;  

## Default Drag Brake Setting 75%

The default value is not a random value. When a motor is driven using complementary PWM (so called damped mode) it's literally braking while running. In other words, its two energized phases are either connected to rail and ground (driving) or both connected to ground (braking). When duty cycle is close to 100%, the energized phases spend most of the time in driving state (connected to opposite polarities) giving 0% braking. When duty cycle is close to 0%, the energized phases spend most of the time in braking state (connected to ground) yielding a rough equivalent of 66% drag brake force. Deadtime obviously slightly reduces running brake by introducing an unconnected gap between transitions from driving to braking.

So with the default 75% drag brake the transition from running brake to drag brake is already quite smooth.

But if you need a more abrupt brake, higher than 75%, try setting it, it won't be smooth.

# Flashing

It you want to flash the the part yourself you need a USB device to do so. We use a Powerwriter PWLINK2 that has the capability to flash the Artery F421 mcu as well as several other types of mcu. If you want to flash an STM mcu you can use their device the STLINK. There is more information on the [ESCape32 WiKi about flashing](https://github.com/neoxic/ESCape32/wiki/Installation)

To use the PWLINK2 you'll need a Windows computer on which to run the Powerwriter software. You can obtain it from [this link](https://docs.powerwriter.com/en/docs/powerwriter_for_arm/software/install/) If you run it from Chrome it'll offer to translate from Chinese to English - useful I'd say.

Here's the process I use:
  Run the software, accept the "Yes" to run in admin mode to access the devices.   
  Plug in the PWLINK2 dongle, and run driver installs and updates.  
  If Powerwriter itself offers an update - accept the offer, and wait a bit until it provides the update.  
  Click on the Writer Setting tab.  
  In Chip Select:  
  Click on MCU model:  
  For the Artery - use the menus to select AT32F421x8  
  Set the following:  
    Erase type: Don't erase  
    Interface level 3.3v  
    Speed: 10M hz  
    OptionByte: Factory=>Custom  
    Note: Don't change the Write function configuration  
  Hit the Save button at the top and save the configuration as a pkg file - it'll save you time later to reload this configuration instead of setting everything again next time you run the program. It asks for a password - (why?) ...  
  In Communication configuration:  
    Click on Refresh  
    It'll update the Device dropdown - on my machine I see COM6 and COM7 - with the dongle on COM7  
  Hit Connect - the log window on the right should show you that it has successfully connected to the dongle  
  Select the Option bytes tab  
  Only if you are flashing an esc/mcu for the first time, you need to disable the RDP read protection, otherwise it's not possible to update the firmware.  
  Click on the RDP line and ensure it says read protection off  
  Wire up the dongle to the "stab pins" (or connectors you are using to connect the dongle to the board - you could solder some wires on but ...) to connect the dongle to the swdio/clk pins.  
  Connect a ground wire from the 2 dongle gnd pins to -ve on your power supply (psu).  
  Connect the psu to the red/black of the eCom  
  If the eCom has already been flashed with firmware, yu might want to disconnect the motor from the eCom otherwise the motor might run when you turn power on. (not the case if you use the default firmware)  
  Power on - give it about 8VDC
  (It will beep if it's a drone esc with a buzzer running Beliheli32)  
  If it's running the ESCape32 default binaries - no beep.
  Note: If you are flashing the prototype (HAKRC) drone eCom and the shunt is in place on the HAKRC and it's running the default ESCape32 binary, you can connect a serial terminal to the white and black control cable of the esc - see the ESCap32 wiki. https://github.com/neoxic/ESCape32/wiki  
  Load up the binaries into Powerwriter.  
  Select the Program Memory tab  
  Click on + Add firmware  
  Locate the bootstrap binary - _BOOT3_FAST-rev2.bin - this is a custom build target and not a default binary - it's in the bin directory of this repo  
  Accept the default memory location 08000000  
  Click OK  
  Again - click on + Add firmware  
  Locate the motor commutator binary - _SLOTCAR_rev8.bin  
  Give it the location 08001000 - there is a bug in Powerwriter that truncates a zero from the end of the address - just add it.  
  Hit the checkmark Apply button  
  You are now ready to flash  
  Touch the SWD pins from the dongle on to the pads on the eCom.  
  Just for good measure, go into the writer settings and hit disconnect/connect - check the log  
  If this is a new mcu - select: Option byte  
  Hit the "Write" button - this should disable the write protection on the mcu  
  Select the Program Memory tab  
  If this has already been flashed - you must first erase the current flash before writing the new flash  
  With the swd pins connected, hit erase - it take about 2 secs  
  Hit "Write" - again takes about 2 sec  
  Power off the eCom  
  Attach a motor  
  Power on at say 4v - restraining the motor  
  This is where it's useful to have a command line or a WiFi dongle attached to enable you to change any compiled-in settings ...
