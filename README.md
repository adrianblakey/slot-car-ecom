# Slot Car eCom

This repo contains a KiCad design, built binaries (bootloader and firmmware) and help for a slot car brushless motor electronic commutator or "eCom", also kown as an electronic speed controller (esc).

Please note this is a prototype design and has yet to be manufactuered and tested. Once it is, the information in this repository shall be updated to reflect that change in development status.

All the intellectual property is released under a creative commons license. You are free to use everything you find here and make your own eCom from the distributed files. We hope that by doing so we'll stimulate innovation and experimentation. If you have suggestions for improvement please file a bug report and tell us about it. I am sure we'll provide some other feedback mechanisms as we go on and build a community.

There is obviously nothing stopping you from making your own versions of this part, calling it your own and selling it as a finished product. If you want to do that we only ask that you negotiate a small royalty payment with us. Some income from this effort would help to defray our development costs and extra income could be put to use to help the hobby.

We also ask that nothing here is used for miltary purposes. This applies to the firmware too.

# A Bit of Background

After taking up slot car racing for the second time in late 2022 my attention was quickly caught by the introduction of small brushless drone motors to slot car racing. There are [several links this being one ...] (http://slotblog.net/topic/100990-designer-of-the-brushless-slot-car-speed-controller/) Three people deserve credit for this, namely: Pete Smits, Bob Budge and Richard Mack. Pete Smits is the developer of open source esc firmware called AM32. Bob and Richard are UK slot car racers with the vision and detemrination to upend the status quo.

They came up with a slot-car specfic ESC (the SBM) that they named an eCom, that has been in the marketplace for just over a year. It has set the standard by being reliable, relatively in-expensive and functional.

It's hard to do better than this however it does suffer from a few drawbacks, namely:

It's closed - despite the [AM32 firmware] (https://github.com/AlkaMotors/AM32-MultiRotor-ESC-firmware) being readily available the SBM gets a custom build of this code and there's no information to explain how a hobbyist might want to make changes, to not only the code but also the hardware design. There's no clarity around the intellectual property ownership.

The hardware design is good but after taking a close look at it we believe it was possible to do better, by creating something that could respond faster, and operate from a lower starting voltage, operate at higher voltages and current. These ideas capabilities are all captured in the requirements document that you'll find in the "docs" directory.

It's still too much money for most people which is a function of the parts. I am told a good rule of thumb is that the final cost of a part is a bout 4 times the parts cost. Therefore by making informed parts choices that might say save a cent or two but while still optimizing performance a much more cost effective design can be produced.

