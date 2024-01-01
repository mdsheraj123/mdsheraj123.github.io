---
layout: post
title: >
    Installing Ubuntu 22.04 LTS on a Intel MacBook air 2018 with T2 chip.
hide_title: false
tags: []
excerpt_separator: <!--more-->
---

Follow [https://wiki.t2linux.org/](https://wiki.t2linux.org/).

For T2 mac, you need to enable boot from non secure media and set secure boot to no security or else your bootable usb won't work.

Keep in mind that setting secure boot to no security is tricky. You cannot do it from any regular recovery mode. You need to specifically reboot, press Ctrl\+R and then go into recovery mode to do this. If you don't do this, the secure boot would revert to medium security \(only mac and windows\) without telling you after you leave the menu.

Follow [https://youtu.be/KIgxEEzT9ek?feature=shared](https://youtu.be/KIgxEEzT9ek?feature=shared) to see how to create the partitions for dual boot.

**Faced issues:**

1\) Suspend does not work so we need to reassign lid close action. [https://ubuntuhandbook.org/index.php/2020/05/lid\-close\-behavior\-ubuntu\-20\-04/](https://ubuntuhandbook.org/index.php/2020/05/lid-close-behavior-ubuntu-20-04/)

Open issue: [https://github.com/t2linux/T2-Ubuntu-Kernel/issues/53](https://github.com/t2linux/T2-Ubuntu-Kernel/issues/53).

**Fixed issues:**


1\) Keyboard back fixed in latest updates. The backlight can be controlled manually too.

sudo apt install brightnessctl

brightnessctl \-l

sudo brightnessctl \-\-device='apple::kbd\_backlight' s 32

sudo brightnessctl \-\-device='apple::kbd\_backlight' s 0

2\) To fix webcam, this works [https://devicetests.com/fix\-webcam\-issues\-ubuntu\-macbook\-air](https://devicetests.com/fix-webcam-issues-ubuntu-macbook-air).

3\) To fix the microphone, follow [https://wiki.t2linux.org/guides/audio\-config/](https://wiki.t2linux.org/guides/audio-config/). Go to settings and change the default microphone to "MacBook Pro T2 DSP Mic" which works.
