# Adrian and Richard's (AART's) Slot Car eCom

This repo contains a KiCad design, built binaries (bootloader and firmware) and help for a slot car brushless motor electronic commutator or "eCom", also known as an Electronic Speed Controller (ESC).

Please note this is a prototype design and has yet to be manufactuered and tested. Once it is, the information in this repository shall be updated to reflect that change in development status.

All the intellectual property is released under a [creative commons license] (https://creativecommons.org/share-your-work/cclicenses/#:~:text=Creative%20Commons%20licenses%20give%20everyone,creative%20work%20under%20copyright%20law.). Under the terms of this license you are free to use everything you find here and make your own eCom from the distributed files. We hope that by doing so we'll stimulate innovation and experimentation. If you have suggestions for improvement please file a bug report and tell us about it. We'll provide some other feedback mechanisms as we go on and build a community. Also a good place to get help is the [ESCape32 slot car discord channel.](https://discord.com/invite/aed6xdSM5Y) ESCape32 is the firmware we have used to flash and test this eCom it's also open source and you'll find it on [github too.](https://github.com/neoxic/ESCape32)

There is obviously nothing stopping you from making your own versions of this part, calling it your own and selling it as a finished product. If you want to do that we only ask that you negotiate a small royalty payment with us. Some income from this effort would help to defray our development costs and extra income could be put to use to help the hobby.

We also ask that nothing here is used for miltary purposes. This applies to the ESCape32 firmware too.

# A Bit of Background

After taking up slot car racing for the second time in late 2022 my attention was quickly caught by the introduction of small brushless drone motors to slot car racing. There are [several links this being one ...](http://slotblog.net/topic/100990-designer-of-the-brushless-slot-car-speed-controller/) Three people deserve credit for this, namely: Pete Smits, Bob Budge and Richard Mack. Pete Smits is the developer of open source esc firmware called AM32. Bob and Richard are UK slot car racers with the vision and determination to upend the status quo.

They came up with a slot-car specfic ESC (the Smits-Budge-Mack SBM) that they named an eCom, that has been in the marketplace for just over a year. It has set the standard by being reliable, relatively inexpensive and functional.

It's hard to do better than this, however it does suffer from a few drawbacks, namely:

It's closed - despite the [AM32 firmware](https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) being readily available the SBM gets a custom build of this code and there's no information to explain how a hobbyist might want to make similar updates, to not only the code but also the hardware design. There's no clarity around the intellectual property ownership.

The hardware design is good but after taking a close look at it we believed it was possible to do better, by creating something that could respond faster, and operate from a lower starting voltage, operate at higher voltages and current. These capabilities are all captured in the requirements document that you'll find in the "docs" directory.

The cost is still a little too much for most people. The cost of electronics is a function of the parts' costs. A good rule of thumb is that the final cost of a part is a bout 4 times the parts cost. Therefore by making informed parts choices that might say save a cent or two while still optimizing performance, a much more cost effective design can be produced. We think we have done this.

# The Files

In this repo you'll find the complete set of KiCad files for the design in the directory AART11-2023-12-13_115145. The AART is our partnership acronym. In the same way Pete/Bob/Richard called theirs SBM - we've given ours the catchy name: Adrian And Richard Technology (AART) and I suppose it reflects the fact that it really is a work of art :-) The board itself is called a Remora. I named our first prototype this because it was a little add-on board for a commercial drone ESC that clung to the top - a bit like the remora fish clings to a shark. Richard liked the name and pursuaded me to keep it for the product - cause it sort of sticks to a slot car chassis I suppose. It's printed on the PCB - if you don't like it - well I hope you know what to do :-)

There is also a binary directory called "bin" in which you'll find ESCape32 binaries build specifically for the part. There is a custom bootloader and two different versions of the firmware.

Needless to say you can download the sources of ESCape32 and build them yourself assuming you have a suitable machine on which to do so. We build ours on an Arch-Linux laptop - it only takes a few seconds to do.

# Obtaining One For Yourself

If you want one of these - you have a few choices, namely:

  1. Ask us (nicely) for one.
  2. Call your favorite slot car parts vendor - maybe Betta in the UK and maybe do-slot in Germany and in the USA(?)
  3. Make one yourself.

We should have a few flashed, tested and inventoried for our own use and to give to friends and family (neither Richard nor I have family that slot car race :-) - so I suppose half of that is a lie) If you are very nice to us and you are willing to be a tester and provide constructive feedback and suggestions I am pretty sure you'll get one. At some point the supply will run out and we might well have moved on to working on V2, V3 ... (there will be ionnovations)

We hope that some of the vendors want to get involved and see an opportunity to make and sell these at a profit. As you'll see there is some effort and cost involved for them to do that, so expect to pay a reasonable premium for a finished item.

Also you can make one yourself. It not hard to do and you'll have some fun doing it and learn some new skills. If you want to make a lot and sell them - please do ... The basic stpes to do so are: create an account on JLCPCB, upload some files from the production directory, possibly order missing parts, wait a while, optiionally build a version of the firmware, flash the part with your own build or the one we supply.

We'll provide detailed instructions for doing that are below.


