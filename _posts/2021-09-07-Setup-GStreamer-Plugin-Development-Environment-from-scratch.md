---
layout: post
title: >
    Setup GStreamer Plugin Development Environment from scratch
hide_title: false
tags: []
excerpt_separator: <!--more-->
---
Install any packages required.

sudo apt update

sudo apt install meson

sudo apt install ninja\-build

From [https://askubuntu.com/questions/723723/is\-it\-possible\-to\-install\-gstreamer\-gstreamer\-core\-and\-plugins\-1\-6\-3\-stable\-rele](https://askubuntu.com/questions/723723/is-it-possible-to-install-gstreamer-gstreamer-core-and-plugins-1-6-3-stable-rele). The steps are old so follow the following steps.

First, install some dependencies.

sudo apt\-get update

sudo apt\-get install autoconf automake libtool build\-essential ubuntu\-restricted\-extras autopoint flex bison gtk\-doc\-tools

Download latest gstreamer sourcecode.

wget http://gstreamer.freedesktop.org/src/gstreamer/gstreamer\-1.19.2.tar.xz

Extract the package.

tar xvf gstreamer\-1.19.2.tar.xz

cd gstreamer\-1.19.2

Now follow the README in the file. I have mentioned the steps for your clarity.

meson build

If you want to install it \(not required, but what you usually want to do\), run

ninja \-C build install

Try out a simple test:

gst\-launch\-1.0 \-v fakesrc num\_buffers=5 \! fakesink

If it outputs a bunch of messages from fakesrc and fakesink, everything is ok.

Follow steps in [https://gstreamer.freedesktop.org/documentation/plugin\-development/basics/boiler.html?gi\-language=c](https://gstreamer.freedesktop.org/documentation/plugin-development/basics/boiler.html?gi-language=c)

Unlike given, give name of plugin in all lowercase like "atif" without quotes. This will prevent build errors.

shell $ git clone https://gitlab.freedesktop.org/gstreamer/gst\-template.git

shell $ cd gst\-template/gst\-plugin/src

shell $ ../tools/make\_element atif

run inside gst\-template folder

meson build

ninja \-C build

Following command will vary based on where your gst\-template has been cloned.

export GST\_PLUGIN\_PATH=/usr/lib/x86\_64\-linux\-gnu/gstreamer\-1.0:~/Desktop/gst\-docs/examples/tutorials/pluginDevelopment/gst\-template/build/gst\-plugin

Finally,

gst\-inspect\-1.0 atif

gst\-launch\-1.0 autovideosrc \! atif \! autovideosink

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.

I'm plugged, therefore I'm in.
**NOTE:**

If you have a older version of gstreamer installed.

gst\-inspect\-1.0 \-\-version

Then do this at start.

sudo apt\-get \-\-purge remove gstreamer1.0

//////////////////////////

To check if your plugin has been blacklisted, run

gst\-inspect\-1.0 \-b

//////////////////////////

If the following command does not show autovideosink details

gst\-inspect\-1.0 autovideosink

From [https://stackoverflow.com/questions/54097034/gst\-good\-plugins\-installed\-but\-no\-element\-autovideosink](https://stackoverflow.com/questions/54097034/gst-good-plugins-installed-but-no-element-autovideosink)

export GST\_PLUGIN\_SYSTEM\_PATH\_1\_0=$GST\_PLUGIN\_SYSTEM\_PATH\_1\_0:/usr/lib/x86\_64\-linux\-gnu/gstreamer\-1.0

echo $GST\_PLUGIN\_SYSTEM\_PATH\_1\_0

//////////////////////////

You may need to install other packages from [https://gstreamer.freedesktop.org/documentation/installing/on\-linux.html?gi\-language=c](https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c).

sudo apt\-get install libgstreamer1.0\-dev libgstreamer\-plugins\-base1.0\-dev libgstreamer\-plugins\-bad1.0\-dev gstreamer1.0\-plugins\-base gstreamer1.0\-plugins\-good gstreamer1.0\-plugins\-bad gstreamer1.0\-plugins\-ugly gstreamer1.0\-libav gstreamer1.0\-doc gstreamer1.0\-tools gstreamer1.0\-x gstreamer1.0\-alsa gstreamer1.0\-gl gstreamer1.0\-gtk3 gstreamer1.0\-qt5 gstreamer1.0\-pulseaudio

//////////////////////////





