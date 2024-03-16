# The Remora - Slot Car eCom

This repo contains a [KiCad](https://www.kicad.org/) design, built binaries (bootloader and firmware) and documentation for a slot car brushless motor electronic commutator or "eCom", also known as an Electronic Speed Controller (ESC).

All the intellectual property herein is released under a [creative commons license](https://creativecommons.org/share-your-work/cclicenses/#:~:text=Creative%20Commons%20licenses%20give%20everyone,creative%20work%20under%20copyright%20law.). Under the terms of this license you are free to use everything you find here and make your own eCom from the distributed files. We hope that by doing so we'll stimulate innovation and experimentation. If you have suggestions for improvement please file a bug report and tell us about it. We'll provide some other feedback mechanisms as we go on and build a community. Also a good place to get help is the [ESCape32 slot car discord channel.](https://discord.com/invite/aed6xdSM5Y) ESCape32 is the firmware we have used to flash and test this eCom it's also open source and you'll find it on [github too.](https://github.com/neoxic/ESCape32)

There is nothing stopping you from making your own copies of this eCom, calling it your own and selling it as a finished product. If you want to do that we only ask that you negotiate a small royalty payment with us. If it's out there in the marketplace we'll obviously know about it because it's a small world - so just be up front about it. Some income from this effort would help to defray our development costs and any extra income will be put back into the hobby and improving this part.

We also ask that nothing here is used for military purposes. This also applies to the ESCape32 firmware.

# A Bit of Background

After taking up slot car racing for the second time in late 2022 my attention was quickly caught by the introduction of small brushless drone motors to slot car racing. There are [several links this being one ...](http://slotblog.net/topic/100990-designer-of-the-brushless-slot-car-speed-controller/) Three people deserve credit for this, namely: Pete Smits, Bob Budge and Richard Mack. Pete Smits is the developer of open source esc firmware called AM32. Bob and Richard are UK slot car racers with the vision and determination to upend the status quo.

They came up with a slot-car specific ESC (the Smits-Budge-Mack SBM) that they named an Electronic Commutator or eCom, that has been in the marketplace for just over a year. It is not the only one out there but it has set the standard by being small, reliable, relatively inexpensive and functional.

It's hard to do better than this, however when we started out we took a look at it and decided we could do better since it does suffer from a few drawbacks, namely:

It's closed - despite the [AM32 firmware](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) being readily available the SBM gets a custom build of this code and there's no information to explain how a hobbyist might want to make similar updates, to not only the code but also the hardware design. And there's no clarity around the intellectual property ownership.

The hardware design is good however we wanted something that could respond faster, and operate from a lower starting voltage, and operate at higher voltages and current. These capabilities are all captured in the [requirements document](https://github.com/adrianblakey/slot-car-ecom/blob/main/docs/slot-car-ecom-requirements.ods) that you'll find in the "docs" directory.

Its cost is still a little too much for most people. The cost of electronics is a function of the parts' cost. A good rule of thumb is that the final cost of an assembled board is about 4 times the constituent parts' cost. Therefore, by making informed parts choices that might say save a cent or two while still optimizing performance, a much more cost effective design can be produced. We think we have done this.

# Slot Car Racing

We want the slot car hobby to flourish and not die. We see brushless motors as a lower cost option to brushed motors that are close to (and soon) shall exceed the performance of brushed motors. One obstacle to running brushless is the eCom - we hope by providing a very competetive one at very low cost, we can remove if not eliminate that obstacle. 

Slot car racing has always represented a way to practically learn some new skills.

The traditional route (that I and others followed) was to go from having had fun with the Scalextric toy, to club racing, motivted by wanting to go faster and compete. This involved finding a club track close by - which back in the late 60's and early 70's was not too hard to do. 

This led on to building chassis out of brass and piano wire - which taught soldering skills, and basic metal working skills; winding and tuning motors - which taught some electricity and magnetism lessons (Lenz's law, Ohm's law etc. ) (there's more ...)

These days the bar has been raised, as has the skill set. To be a competetive DIY slot car racer you need to understand how to design and build an EDM-cut spring steel chassis - using mechanical CAD skills; master the motor skills and know how to design and build an eCom - using eCAD. 

We hope by providing an open solution for the latter we've moved things along a bit and opened the door for more people to learn and innovate, and hopefullly bring the hobby back to its roots a bit.

Now, all we need (lol) are some open designs for motors and chassis :-)

# Naming

The AART is our partnership acronym. In the same way Pete/Bob/Richard called theirs SBM - we've given ours the catchy name: Adrian And Richard's Technology (AART) and it reflects the fact that it really is a work of art. Since Arseny (of ESCape32) had a large influence in the design it is also be an acronym for "Adrian, Arseny, (and) Richard's Technology".

The board itself is called a Remora1 - Remora version 1. Our first prototype was called "Remora" because it was a little add-on board for a commercial drone ESC (HAKRC BLHeli_32 Bit 35A 2-5S ESC) that clung to the top - a bit like the [remora fish](https://en.wikipedia.org/wiki/Remora) clings to a shark. Richard liked the name and persuaded me to keep it for the product - cause it sort of stuck and sticks to a slot car chassis I suppose. It's printed on the PCB - if you don't like it - well I hope you know what to do :-)

# Github Repo Organization

In this repo. you'll find:  

  [AART11-2023-12-13_115145](https://github.com/adrianblakey/slot-car-ecom/tree/main/AART11-2023-12-13_115145) - A KiCad design for the board  
  [KiCad_ESP32Mini_interface](https://github.com/adrianblakey/slot-car-ecom/tree/main/KiCad_ESP32Mini_interface) - A KiCad design for an adapter board  
  [Simetrix_simulation](https://github.com/adrianblakey/slot-car-ecom/tree/main/Simetrix_simulation) - A Simetrix simulation for the board  
  [bin](https://github.com/adrianblakey/slot-car-ecom/tree/main/bin) - Firmware binaries (bootloader and commutator)  
  [docs](https://github.com/adrianblakey/slot-car-ecom/tree/main/docs) - Documentation

# The Board Design Files

In this repo you'll find the complete set of KiCad files for the design in the directory AART11-2023-12-13_115145. We chose KiCad because it's freely available and there's plenty of information to describe how to use it.

It's quite simple to send this automated design to the JLCPCB to get the boards manufactured. The process to generate the files to send to them is: 

  Download and install KiCad on a computer.   
  Open the software and use the plugin installer to install "Fabrication Toolkit".  
  Use git to clone the slot-car-ecom git repo.  
  Navigate to the KiCad files.  
  Click on the project file to open them in KiCad. 
  Open the pcb editor.
  Use the Fabrication Toolkit icon to generate the gerber, bom and placement files.

 Note: There are a couple of defects in this plugin that incorrectly swaps the columns around in the placement and bom files. The corrected files are checked in to repo. in the "production" directory.

If you run the design through the design rules checker it'll give warning messages. I was always told "a warning is an error" - and needs to be addressed. Despite this advice you may ignore them - unless of course you'd like to provide us with a fix that'll correct the issues :-) 

There are 2 types of vias used in the pcb design. They differ in size to differentiate one type from the other. We asked JLCPCB about this before submitting the design because their order input only allows you to specify one type of via. 

The solution to this is to annotate the order in the PCB remarks field with something like: "0.3mm via holes are standard through-hole vias, namely: "Via Covering" Tented.
The 11 vias with 0.35mm holes are the via-in-pad ones, namely: "Via Covering" Epoxy Filled & Capped".

You also should select the option: "Confirm Production file" - as this puts the information in front of a real person for review.

We chose to fabricate a 1mm rather than the standard 1.6mm board.

## Binaries 

There is also a [binary directory called "bin"](https://github.com/adrianblakey/slot-car-ecom/tree/main/bin) in git in which you'll find ESCape32 binaries built specifically for the part. There is a custom bootloader BOOT3_PA2_AUX_FAST_EXIT-rev2.bin and firmware build REMORA-rev0.bin.

You can download the sources of ESCape32 and build them yourself assuming you have a suitable machine on which to do so. We build ours on an Arch Linux laptop - it only takes a few seconds to do. There are other Linux distros. that'll work fine and (guessing ... you can either: install cygwin on Windows or the [Linux Subsystem for Windows](https://learn.microsoft.com/en-us/windows/wsl/install) or suitable packages using brew on MacOS). 

Note: the CMake is configured to use the gnu arm cross compiler and it assumes it's running on an Intel machine despite the binary targets being for an arm binary. I made a half hearted effort to try to get it to run on a Apple Silcon Mac without the cross compiler - but failed. I am told it can run be run in a [UTM](https://mac.getutm.app/) virtual machine on MacOS - but I haven't tried yet. If you have success doing this we'd like instructions - please file a defect and tell us how, or submit a pull request in git.

# Obtaining One For Yourself

Once we get past some initial testing, if you want one of these - you have a few choices, namely:

  1. Ask us (nicely) for one.
  2. Make one yourself.
  3. And hopefully sometime in the future - call your favorite slot car parts vendor - maybe Betta in the UK, and maybe do-slot in Germany and in the USA(?)

We should have a few flashed, tested and inventoried for our own use and to give to friends and family (neither Richard nor I have family that slot car race :-) - so I suppose half of that is a lie) If you are very nice to us and you are willing to be a tester and provide constructive feedback and suggestions I am pretty sure you'll get one. At some point the supply will run out and we might well have moved on to working on V2, V3 ... (there will be innovations).

You can make one yourself. Everything is here to do that. It is not hard to do and you'll have some fun doing it and learn some new skills. If you want to make a lot and sell them - please do ... The basic steps to do so are: create an account on JLCPCB, upload some files from the production directory, possibly order missing parts, wait a while, optionally build a version of the firmware, flash the part with your own build or the one we supply, test it, put it in a chassis.

We hope that some of the vendors want to get involved and see an opportunity to make and sell these at a profit. As you'll see there is some effort and cost involved for them to do that, so expect to pay a premium for a finished item. There's also maybe an opportunity say to create a third party marketplace for custom binaries, an eCom tester, a flashing jig etc.

Once I can figure out how to create a proper WiKi on git - we'll provide some more detailed instructions for doing all this.

# The ESCape32 Firmware

The Remora1 is programmed using the ESCape32 firmware. There are a number of good reasons for doing so, namely:

  - Writing a brushless motor driver and getting it right, is difficult.
  - The skills to do it are hard to find and acquire.
  - It's open source.
  - It's supported and maintained.
  - There is a community and Arseny specifically created a [Discord channel for slot-cars](https://discord.com/channels/1103745257046278144/1151565789984469144) (yeah).
  - It's lovely, readable code.
  - We can't say enough good things about Arseny, its developer, who is helpful and supportive of our efforts.
  - It's fully configurable from a command line and WiFi dongle so you do not need to compile custom binaries to make configuration changes - once it's flashed.

There are no code changes or patches to the ESCape32 firmware to run the Remora1. Although the ESCape32 build for it has a specific configuration as it does for other drone ESC's.

In comparison to a commercial drone ESC, the board has some additional features that are not normally found on other ESC's - like the reverse polarity protection, and low voltage operation - that are overkill for a drone ESC. Interestingly, it also supports a digital interface that could theorectically allow it to be used in combination with a controller.

## Provided Binaries

In order to flash the board you need 2 binary files. Namely:

  - the bootloader
  - the driver

We have provided the bootloader binary and a build of the driver. You only really need one binary, because once it's installed you can change its parameters using a WiFi Link dongle. If a updated binary is released this can also be installed using the dongle and a browser.

In the bin directory you'll find the following binaries: 

    BOOT3_PA2_AUX_FAST_EXIT-rev2.bin   
    REMORA-rev10.bin  
 
They are built on Linux from the ESCape32 sources. 

The following build options are used:

For the bootloader:

    add_target(BOOT3_PA2_XF STM32F0 AT32F4 IO_PA2 IO_AUX FAST_EXIT) 

For the firmware:

    add_target(REMORA AT32F421 DEAD_TIME=66 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=200 ANALOG_MAX=2218)

The firmware build is more complex, there's an explanation below which describes the parameters, there is a complete description of all the build options on the [ESCape32 WiKi.]([https://githib.comneoxic/ESCape32/wiki](https://github.com/neoxic/ESCape32/wiki/BuildOptions)).


The REMORA-rev10 binary is built from sources for ESCape32 Rev 10, it has default values and no ramping with a minimum analog voltage of ~1.1v to ~12.2v. We have been using this for our prototype testing. To use this you'll probably need to attach a WiFi dongle to eCom and set some specific values to suit your precise needs.

The firmware has not been compiled with the "ANALOG" option so that the board and ESCape32 can be configured either by connecting a computer serial interface, or a WiFi "dongle" to the signal pins.

There is a complete explanation about how to connect a computer and use the [command line interface (CLI) on the ESCape32 WiKi.](https://github.com/neoxic/ESCape32/wiki/WiFiLink)

It's also possible to connect a WiFi dongle to the same interface and use a Web browser to make configuration changes. The [WiFi link](https://github.com/neoxic/ESCape32/wiki/WiFiLink) is also described on the github WiKi.

Either you can obtain a "WiFi Link" board from Arseny, or you can buy a very inexpensive (~$5) ESP S3 board from Amazon or Ebay and flash a supplied image onto it. The only significant difference between the two is some additional protection circuitry on the WiFi Link board. Until we can provide some similary interface circuit - you must **limit the supplied voltage to the Remora to 3.3v if you have the ESP S2 dongle attached**.

# Building the Firmware

If you want to build and flash your own version of the firmware the best place to study the settings is here:

https://github.com/neoxic/ESCape32/wiki/Configuration#settings

Include the ANALOG option if you ***DON'T*** want CLI access for configuration, however better just to enable it by leaving the option out.

You need to build 2 custom binaries, namely:

  - the boot loader  
  - the driver  

Setting these targets in the CMakeLists.txt will enable both CLI and Analog throttle:

In ESCape32/boot/CMakeLists.txt  
  
    add_target(BOOT3_PA2_XF STM32F0 AT32F4 IO_PA2 IO_AUX FAST_EXIT)  

In ESCape32/CMakeLists.txt  

    add_target(REMORA AT32F421 DEAD_TIME=66 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=200 ANALOG_MAX=2218)  

## Ducty Cycle Ramping and Drag Brake

The ANALOG_MIN value sets the voltage below which the drag brake takes effect and where pulse width modulation duty cycle ramping take effect.

There will be a quadratic throttle curve when both voltage level and pwm duty cycle are applied. For example: motor voltage is 1/4 at 1/2 "throttle" voltage.

The drag brake determines the duty cycle of the eneergized phases when the analog voltage drops below ANALOG_MIN. In effect the phases act like a brake, how much of this is applied is determined by the duty drag setting.

The duty drag is set by default in the firmware to 0 and is an alterable parameter that can be set by means of the WiFi dongle or command line.

The calculated and measured voltage to which the circuit will operate down to is 1.1VDC. The calculated and measured starting voltage is 1.3VDC. These voltages are a result of adding the buck booster circuit to the board.

The ANALOG_MIN value that's compiled in to the distributed firmware is 200, corresponding to about 1.1VDC, hence there is no room for the drag brake to turn on and have an effect.

Therefore if it's important to be able to set the drag brake to something other than 0, it's necessary to compile the firmware with an ANALOG_MIN value of something higher than the current setting of 200.

Calculating the ANALOG_MIN/MAX values: 

  1) Let's assume the minimum input voltage is ~2.2VDC, and the maximum input voltage is 10VDC. This corresponds roughly at the low end to the smallest "useful" track voltage to get the motor running and where we want to start ramping up the duty cycle (dc), and below which we want to apply motor drag brakes. At the top end this is a track voltage at which we want to hit 100% duty cycle (we choose 10VDC not 12.4VDC say because often we run low voltage club race nights and still want 100% dc at this maximum voltage)
  2) A 10K/2.2K ohm voltage divider circuit on the back EMF of each pole is used to detect the voltages in the mcu. Using the formula r2/(r1+r2), we get a factor of 2.2/(10 + 2.2) = .18 
  3) So 2.2VDC translates to 2.2 * .18 = 397mV, 10VDC translates to 10 * .18 = 1803mV on the voltage divider pin, so we'd set the following options:  
  
    ANALOG_MIN=397  
    ANALOG_MAX=1803  

## Options

     REMORA = name of the binary  
     AT32F421 = specify the Artery F421 mcu  
     DEAD_TIME = microseconds to wait for the high/low side switching(?) 
     COMP_MAP = Comparator map. Maps the A/B/C (U/V/W) phase back emf signals to mcu pins PA0, PA4, PA5, namely 1, 2, 3 
     ANALOG_MIN = the voltage at which the pwm duty cycle starts ramping up, 200 is about 1.1VDC  
     ANALOG_MAX = the voltage at which the duty cycle reaches 99% = 2218 is about 12.2VDC  
     ANALOG_PIN - assign analog throttle to pin 6 on the AT32F421 MCU.  
     ARM=1  
     VOLUME=0 turn off sounds - the board does not have sound :-)  
     INPUT_MODE=1 - Analog  
     FREQ_MIN = lowest pwm frequency  
     FREQ_MAX = highest pwm frequency  
     DUTY_DRAG = duty cycle for braking, to enable say 70% dc, set this to 70. 
     IO_AUX = detect whether on not full duplex signal IO

The REMORA-REV10 binary is built uing the following target in the CMakeLists.txt file

    add_target(REMORA AT32F421 DEAD_TIME=66 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=200 ANALOG_MAX=2218)   

The ANALOG_MIN is set to a minimum voltage of about 1.1v, which is below the voltage the board theoretically powers up. You'll note that ANALOG_MIN and ANALOG_MAX need to be compiled in to the firmware and are not setable parameters. 

If for example you want the eCom to always run at 100% duty cycle from its starting voltage with no ramp up in the duty cycle, then you need to attach a WiFi link dongle to set and save duty_min to 100, this is the first non-zero duty cycle. When throttle becomes non-zero (voltage above 1.1VDC in our case), it's applied after synchronization. If you wanted 100% throttle at every voltage, change throt_set=100. See https://github.com/neoxic/ESCape32/wiki/Settings#throt_set-0 Note: throt_set is the minimum throttle value in analog mode and it's what ANALOG_MIN translates to. When you set it to some non-zero value, you'll get that throttle value at ANALOG_MIN voltages and lower. 

We usually run in analog mode set by INPUT_MODE=1. In digital mode, throt_set is just an initial value that the throttle is set to upon startup. If it's not changed (say, you have no input), it remains at that value. Hence you can get fixed throttle mode out of it.

In analog mode, it also serves as the minimum throttle value. Thus you can get two distinct modes - when you have zero-throttle and when you don't. 

When you connect via a WiFi link and change the throttle using a slider control in the browser, it disables analog throttle. That is to make it possible to save settings.

Once a throttle value is established, duty_min and duty_max start playing a role mapping throttle [1...2000] to the duty cycle.

In analog mode, it also serves as the minimum throttle value. Thus you can get two distinct modes - when you have zero-throttle and when you don't.

Also note that DUTY_DRAG is defaulted to 0. Therefore if you want a specific brake setting you'll need to access the firmware through the WiFi link dongle and set it.

Normally you can't disable arming (arm=0) in analog mode (unless you build with ANALOG which disables that). This is because it becomes impossible to distinguish between digital high level and analog high level. But in with ANALOG_PIN overriding the default analog throttle pin (the same as the digital input pin), it becomes possible.

ANALOG_PIN forces the firmware to sample analog throttle values on a different pin. By default, it's the same pin, e.g. PA2 or PA6. However in our case, PA2 is digital input and PA6 is analog. Since they are separated, there's no aforementioned problem, hence no there is no restriction on arming.

# Misc. Notes

## The F421 Startup Delay

If there is one downside to our design, it might be the choice of MCU. When prototyping the design we realized that it has a small start up delay which we think might be caused by memory copying. [This article in HackaDay](https://hackaday.com/2020/10/22/stm32-clones-the-good-the-bad-and-the-ugly/) explains something about this issue for other chips. Search for "boot-up delay" to get to the piece. Artery chips are not the same, although it might be something similar.

The AT32F421 startup delay is measured at ~4.2ms.

After startup, there's a little bit of extra time needed to switch clock source, lock PLL, calibrate ADC, etc. For the STM32G071, it all stays within about 1ms altogether. On the other hand, it takes another extra ~1ms for the AT32F421. Not too bad, but since there's an inevitable extra 4.2ms boot delay, it all comes down to ~5.5ms that Richard witnessed in his analysis.

We chose the Artery F421 MCU because of its (low) cost and (high) speed so that we had a fast enough clock speed to commutate a 12 pole motor at very high rpm, say 180,000 rpm+. As motor technogology matures we might need to revist this decision and it's an obvious change to the design that should be fairly simple to make. If you do that, please contribute it back.

## To Start a 10,000+K<sub>v</sub> Motor (say)

There are several parameters to the ESCape32 firmware that can be adjusted to alter motor function.

When a motor spins up, maximum duty cycle is limited at 10% by default before a full synchronized revolution is reached, i.e. 6 sync'ed commutations have commenced. This value can be overridden by the DUTY_SPUP build option. The maximum value is 25%. Please note that allowing even higher DUTY_SPUP values is possible, but generally it is dangerous as a stuck rotor will lead to instant motor overheating. Higher values also degrade smooth spinup most of the time because the motor tends to desync right away and stutters longer. Another option is FREQ_MIN which is 24kHz by default. Setting FREQ_MIN to 48 can help reduce current ripple.

The default acceleration ramp, DUTY_RATE value is 25 (conservative 2.5%/ms) which leads to 100/2.5=40ms from 0% to 100% throttle. This can be easily increased. The maximum value is 100, i.e. 10%/ms.

It's important that increased DUTY_SPUP has much less effect under load. In a real life situation, a motor with a relatively significant load simply can't reach maximum RPM in just 40ms. Increased acceleration ramping might speed it up a bit, but with a progressively diminishing effect, so care must be taken. On the other hand, too rapid a power increase often leads to desyncs in some bigger motors (not our case). That is why the default value of 2.5%/ms is somewhat conservative as a one size fits all value.

Why would you want to override DUTY_SPUP? Is it not alright for a motor to sync on moderate power? Why and how would you want to override DUTY_RATE? Is it not alright for a motor to reach its maximum RPM in 40ms (with no load)? If it's not, then what time is okay? 30ms, 20ms? Do the calcualation and go from there.

[This blog post](https://www.miniquadtestbench.com/brushless-drive-and-esc-basics.html) is a good primer and might provide some more insight. 

### Timing Advance 

All motors and loads are different. You can't know beforehand, so you can't really have some bleeding edge values in the hope they will work with all motors and in all conditions. Hence, the default settings.

An ideal commutation should happen when the rotor is at 90 degrees to the field, so torque is maximized.

But in reality, this is barely feasible because a slight deviation, and you get a desync. Therefore timing is advanced so commutation delay is reduced. With more timing advance you get further and further away from the ideal 90 degrees between the rotor and the field.

The timing setting of n equates to: 3.75 x n degrees

The default is 4, or 15 degrees. The value can be set to between 1 and 7.

In testing, a 1105 10000K<sub>v</sub> motor desyncs on 3S (S means the number of LiPo RC batteries in series. 2S is about 7.4VDC, 3S is about 11.1VDC, obviously this varies as a battery discharges) with the default settings. Increased timing helps get rid of desyncs, nothing else. The same 10000K<sub>v</sub> motor with 22.5 degree timing (timing=6) instead of the default 15 degrees (timing=4).

  set timing 6  
  set freq_min 48  
  set freq_max 96  
  set duty_rate 15  

An alternative setting that can be used to limit power based on RPM is duty_ramp (not to be confused with duty_rate). Read the code :-)

You might witness timing effects in a car that won't leave the line smoothly on full power - it'll stutter and "cog". This might be because the motor is not under load because the wheels are spinning (!) due to too much torque from the motor - drone motors have a lot of torque - maybe too much. There are some [technical articles ... ](https://www.miniquadtestbench.com/motors-and-torque.html#:~:text=Torque%20itself%20is%20simply%20a,power%20%3D%20torque%20*%20angular%20velocity.) 

## Drag Brake Setting

When a motor is driven using complementary PWM (so called damped mode) it's literally braking while running. In other words, its two energized phases are either connected to rail and ground (driving) or both connected to ground (braking). 

When the duty cycle is close to 100%, the energized phases spend most of the time in the driving state (connected to opposite polarities) giving 0% braking. When duty cycle is close to 0%, the energized phases spend most of the time in the braking state (connected to ground) yielding a rough equivalent of 66% drag brake force. Deadtime obviously slightly reduces running brake by introducing an unconnected gap between transitions from driving to braking.

So with a drag brake setting of 75%, the transition from running brake to drag brake is quite smooth.

But if you need a more abrupt brake, higher than 75%, try setting it, it won't be smooth.

# Flashing the Board

It you want to flash the the part yourself you'll need:

   - a computer running Windows or Linux.
   - a USB serial interface or "dongle" (different from the WiFi dongle to change the operating parameters) - we use the [PWLINK2.](https://www.powerwriter.com/index/index/products.html?p=5&c=description). Do a search to find them. You can pck one up from EBay for about $12.
   - connectors to connect the dongle to the board - we use spring loaded pin connectors (pictures and links to come). These probably come from [Farnell](https://uk.farnell.com/) in the UK.
   - computer software to flash the board using the dongle - for Windows use [Power Writer](https://www.powerwriter.com/index/index/products.html?p=5&c=description) or [the OpenOCD fork for Artery MCU's](https://github.com/ArteryTek/openocd)

To use the PWLINK2 you'll either need a Windows computer on which to run the Powerwriter software, or a Linux/macOS machine to run the OpenOCD software.

Power Writer PWLINK2 that has the capability to flash the Artery F421 MCU as well as several other types of MCU. The ESCape32 WiKi mentions the STLINK device however it's only useful for flashing STM MCU's and we are using the Artery. There is more information on the [ESCape32 WiKi about flashing](https://github.com/neoxic/ESCape32/wiki/Installation)

To connect the PWLINK2 to the board we have some connectors that have very fine spring loaded pins on the ends to touch down on the single wire debug pads on the board (look at the picture in the [test document](https://github.com/adrianblakey/slot-car-ecom/blob/main/docs/Remora1ProductionTests.odt) in the docs directory to find these on the board). They are fiddly to use and I don't yet have a link to where to obtain them. If you find a link to buy them - please file a defect and tell us :-). Obviously a better flashing solution is needed.

Power Writer has options to flash a board that has existing software on it. If you are flashing for the first time and do not need to reset the option bytes OpenOCD is a good solution. The official [OpenOCD fork for Artery MCU's is in github.](https://github.com/ArteryTek/openocd) I haven't tried using it yet therefore if you do please file a defect and provide some explicit instructions.

Since we built our prototype from an existing drone ESC we used Power Writer. You can obtain Power Writer from [this link](https://docs.powerwriter.com/en/docs/powerwriter_for_arm/software/install/) If you run it from Chrome it'll offer to translate from Chinese to English - useful I'd say.

Here's the process we used:
  - Run the software, accept the "Yes" to run in admin mode to access the devices.   
  - Plug in the PWLINK2 dongle, and run driver installs and updates.  
  - If PowerWriter offers an update - accept the offer, and wait a bit until it provides the update.  
  - Click on the Writer Setting tab.  
  - In Chip Select:  
  - Click on MCU model:  
  - For the Artery - use the menus to select AT32F421x8  
  - Set the following:  
     Erase type: Don't erase  
     Interface level 3.3v  
     Speed: 10M hz  
     OptionByte: Factory=>Custom  
     Note: Don't change the Write function configuration  
  - Hit the Save button at the top and save the configuration as a pkg file - it'll save you time later to reload this configuration instead of setting everything again next time you run the program. It asks for a password - (why?) ...  
  - In Communication configuration:  
  - Click on Refresh  
  - It'll update the Device dropdown - on my machine I see COM6 and COM7 - with the dongle on COM7  
  - Hit Connect - the log window on the right should show you that it has successfully connected to the PWLINK2 dongle  
  - Select the Option bytes tab  
  - Only if you are flashing an ESC/MCU for the first time, you need to disable the RDP read protection, otherwise it's not possible to update the firmware.  
  - Click on the RDP line and ensure it says read protection off  
  - Wire up the dongle to the "stab pins" (or connectors you are using to connect the dongle to the board - you could solder some wires on but ...) to connect the dongle to the swdio/clk pins.  
  - Connect a ground wire from the 2 dongle gnd pins to -ve on your power supply (psu).  
  - Connect the psu to the red/black of the eCom  
  - If the eCom has already been flashed with firmware, you might want to disconnect the motor from the eCom otherwise the motor might run when you turn power on. (not the case if you use the default firmware)  
  - Power on - give it about 8VDC (It will beep if it's a drone esc with a buzzer running Beliheli32)  
  - If it's running the ESCape32 default binaries - no beep.
  - Note: If you are flashing the prototype (HAKRC) drone eCom and the shunt is in place on the HAKRC and it's running the default ESCape32 binary, you can connect a serial terminal to the white and black control cable of the esc - see the ESCap32 wiki. https://github.com/neoxic/ESCape32/wiki  
  - Load up the binaries into Powerwriter.  
  - Select the Program Memory tab  
  - Click on + Add firmware  
  - Locate the bootstrap binary - _BOOT3_FAST-rev2.bin - this is a custom build target and not a default binary - it's in the bin directory of this repo  
  - Accept the default memory location 08000000  
  - Click OK  
  - Again - click on + Add firmware  
  - Locate the motor commutator binary - _SLOTCAR_rev8.bin  
  - Give it the location 08001000 - there is a bug in Powerwriter that truncates a zero from the end of the address, just add it.  
  - Hit the checkmark Apply button  
  - You are now ready to flash  
  - Touch the SWD pins from the dongle on to the pads on the eCom.  
  - Just for good measure, go into the writer settings and hit disconnect/connect - check the log  
  - If this is a new mcu - select: Option byte  
  - Hit the "Write" button - this should disable the write protection on the mcu  
  - Select the Program Memory tab  
  - If this has already been flashed - you must first erase the current flash before writing the new flash  
  - With the swd pins connected, hit erase - it take about 2 secs  
  - Hit "Write" - again takes about 2 sec  
  - Power off the eCom  
  - Attach a motor  
  - Power on at say 4v - restraining the motor  
  - This is where it's useful to have a command line or a WiFi dongle attached to enable you to change any compiled-in settings ...

# The WiFi Dongle

## Flashing an ESP 2 WiFi Dongle

Follow the link in the [ESCape32 Wiki](https://github.com/neoxic/ESCape32/wiki/WiFiLink) and install the tooling. Connect the board to a computer using a USB-C cable. Make sure you can see the device in the computer's USB device list. I had issues getting it to appear in Linux and resorted to using a Mac. We have also flashed the device using Windows.

Download the [binary](https://github.com/neoxic/ESCape32-WiFi-Link/releases/tag/1.1) from git. 

Before you flash the device connect the device to your computer using a suitable USB-C cable. Then, reset the device by following this process:  

  Hold the board between thumb and index finger in left hand.  
  Plug the USB-C cable at right.  
  With right index finger hold the "0" button in.  
  With thumb, press RST button and relese it.  
  Release the "0" button.  

On a Mac, use the esptool python program to flash it. Detect the correct USB port by listing the devices before and after plugging it in, using this command from a terminal window:

  ls -alt /dev/cu*
  
Plug it in and reset it using the process above. Then from a terminal window run something like this (substitute your device).
 
  esptool.py -p /dev/cu.usbmodem01 write_flash 0x00000 ESCape32-WiFi-Link-1.1-ESP32-S2.bin  

To flash it on Windows download the flash tools from here: https://www.espressif.com/en/support/download/other-tools. Install it by extracting the contents from the zip file. Read the instructions in the associated pdf file entitled "Regular Download Example". It's intuitive to use but it does have a couple of "gotchas".

  - Attach the device and reset it.   
  - Run the utility.  
  - Complete the popup window:  
    - ChipType ESP32-S2   
    - WorkMode Develop   
    - LoadModu'le USB   
  - Hit OK  
  - Another window is displayed with a single tab lableed SPIDownload  
  - In the top line, navigate to the binary (ESCape32-WiFi-Link-1.1-ESP32-S2.bin) by clicking on the elipise "..."   
  - After the "@" enter "0x00000"  
  - Check the box to the left of the file name - the whole line then should be highlighted in green.  
  - You can just use the default values - or, I like to set SPI Speed to 20MHz. Note clicking on "Default" resets all of these values.  
  - Click on the COM: drop down on the right - you should only see a single COM port listed - select this.  
  - Click "START". The window shows an advancing green bar.  
  - The console window should now say something like:  
  - Changing baud rate to 115200  
      Changed    
      SPI_BOOT_CRYPT_CNT 0    
      SECURE_BOOT_EN False    
      Compressed 858688 bytes to 525693...    
      
      is stub and send flash finished    

Reboot it by plugging/unplugging the USB cable.

Check it's flashed by attaching to its WiFI AP - named: ESCape32-WiFi-Link

Browse: [http://escape32.local](http://escape32.local)

Power it off and follow the ESCape32 Wiki to connect its signal, ground and power to the Remora, you'll optionally need a diode for full duplex.  

Apply power (at least 4v) to the eCom. Browse the link again - you should see the current setting values.

## Connecting a WiFi dongle to the Remora

If you look very closely at the Remora you'll see a very small .6mm, 4 pin connector on the top of the board. This exports 4 connections, namely:

   - +3.3 vdc
   - GND
   - PA1
   - PA15

These need to be connected to the equivalent pins of an ESP S2 or ESCape32 WiFi link. 

### The ESP S2 Adapter

If you wish to use an off-the-shelf ESP S2 board flashed with the equivalent ESCape32-provided firmware you need to exercise some care because these boards are powered from their 3.3v power connector from power output from the Remora1.

If you choose to connect the two together directly just using a cable then you **MUST** ensure you do not apply more than 3.3v to the Remora1.

You may also choose to interface them with an adapter board which contains a protection circuit. The KiCad design for these boards is located here [https://github.com/adrianblakey/slot-car-ecom/tree/main/KiCad_ESP32Mini_interface](https://github.com/adrianblakey/slot-car-ecom/tree/main/KiCad_ESP32Mini_interface)

Send these off to JLCPCB to get parts made - we made 20 for about $75.

The final part is connected to the Remora1 by means of a connector cable.

The connector system is by JST and is the XSR series. Obtain the cable assembly from these suppliers:

Farnell: (£10 delivery for orders < £40)

[https://uk.farnell.com/jst-japan-solderless-terminals/04xsrxsr36l100/lead-100mm-xsr-rcpt-36awg-4way/dp/2347802](https://uk.farnell.com/jst-japan-solderless-terminals/04xsrxsr36l100/lead-100mm-xsr-rcpt-36awg-4way/dp/2347802)  
[https://uk.farnell.com/help-delivery-information](https://uk.farnell.com/help-delivery-information)  

RS: (£7 for orders < £50, but no stock, & the headline says 1.5m long but the text description says 150mm)

[https://uk.rs-online.com/web/p/wire-to-board-cables/8201686](https://uk.rs-online.com/web/p/wire-to-board-cables/8201686)  
[https://uk.rs-online.com/web/content/support/all-articles/delivery](https://uk.rs-online.com/web/content/support/all-articles/delivery)  


Digikey: (£12 delivery for orders < £33)

[https://www.digikey.co.uk/en/products/detail/jst-sales-america-inc/A04XSR04XSR36R152A/6194782](https://www.digikey.co.uk/en/products/detail/jst-sales-america-inc/A04XSR04XSR36R152A/6194782)  
[https://www.digikey.co.uk/en/help-support/delivery-information/delivery-time-and-cost](https://www.digikey.co.uk/en/help-support/delivery-information/delivery-time-and-cost)  

## The ESP32 WiFi Link

These boards are an amalgam of the ESP32 and the adapter circuit. They can be ordered from Arseny directly for about $15.

He advertises them on EBay: [https://www.ebay.ca/itm/126321893290](https://www.ebay.ca/itm/126321893290)


## Saving Values inm the UI

You can't save settings if the motor is spinning.

Use the throttle slider at the bottom to stop it first.

Then save.

## The Simulation

We have provided five SIMetrix simulations in the repo: [https://github.com/adrianblakey/slot-car-ecom/tree/main/Simetrix_simulation](https://github.com/adrianblakey/slot-car-ecom/tree/main/Simetrix_simulation)

All run using the demo version of SIMetrix which is available from: https://www.simetrix.co.uk/

These are for anyone who wants to understand more about Remora1 hardware operation and might perhaps want to test and compare working hardware.

They provide voltages and currents at any point you want to probe.

They all run and give some key waveforms by just pressing F9 on the computer keyboard.

BLDCmotor_PowerStage_BackEMFsense.wxsch gives some brief instructions about using SIMetrix.

# Building the sources on Windows

Install wsl - follow this: https://learn.microsoft.com/en-us/windows/wsl/install

Install wsl with Ubuntu. You'll need to reboot a couple of times and take the advice to install the Windows Terminal.

Go to the Windows store https://apps.microsoft.com/ and download Arch linux. It's hosted here: https://github.com/VSWSL/Arch-WSL

When it's finished downloading launch it to open a terminal window and create a Arch userid and password. You'll then be at a Linux command prompt.

Get the latest sources by typing:  

   git clone git clone https://github.com/neoxic/ESCape32.git   

Then use pacman the package installer to install the dependencies:   
  
   sudo pacman -Syu cmake arm-none-eabi-gcc arm-none-eabi-binutils arm-none-eabi-newlib libopencm3 stlink   
   
When it asks for the password use the one you created for the id you just created.

Note right mouse implements cut/paste and you can edit the command line using the emacs key bindings (lol) and cursor keys.

Try building all the targets to see if this has succeeded.

    cd ESCape32   
    cmake -B build   
    cd build   
    make   

Open the VSCode editor: 

    code CMakeLists.txt
   
Move to the bottom and remove the targets you do not need and add the one and only target for REMORA e.g.

    add_target(REMORA AT32F421 DEAD_TIME=0 COMP_MAP=123 ANALOG_PIN=6 ARM=0 VOLUME=0 INPUT_MODE=1 IO_AUX ANALOG_MIN=200 ANALOG_MAX=2218)  

Hint: ctl-C to copy the line above, select the add_target lines in the editor and ctl-V to replace them. ctl-S to save it. 

Use the File->Open->Arch/home/nnn/boot/CMakeLists.txt and do the same - remove all targets and replace with:
 
    add_target(BOOT3_PA2_XF STM32F0 AT32F4 IO_PA2 IO_AUX FAST_EXIT)

Then build the files:

    cd ~/ESCape32/build   
    make clean  
    make  

You'll find the binaries in: 

    ~/ESCape32/build   
    ~/ESCape32/build/boot   
  




