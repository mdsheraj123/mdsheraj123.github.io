---
layout: post
title: >
    Linux remote server GStreamer execution setup in Windows VS Code host
hide_title: false
tags: []
excerpt_separator: <!--more-->
---
## Motivation


Our goal is to run VS Code in Windows host to browse code and be able to build the GStreamer pipelines code located on a Linux server. I have found it to be the most optimal, free GStreamer development environment.

VS Code will allow code browsing, formatting, execution, and debugging support along with live git diff preview, revert, and stage changes in VS Code itself.

Linux server will allow easy setup of GStreamer, more storage and computation power, backup, and full target builds.

## Steps

The steps to follow are \(tested on Windows host and Ubuntu server\):

1\) We will install GStreamer on Linux

Follow the steps in [https://gstreamer.freedesktop.org/documentation/installing/on\-linux.html?gi\-language=c](https://gstreamer.freedesktop.org/documentation/installing/on-linux.html?gi-language=c).

Basically,

Install GStreamer on Ubuntu or Debian

Run the following command:

apt\-get install libgstreamer1.0\-dev libgstreamer\-plugins\-base1.0\-dev libgstreamer\-plugins\-bad1.0\-dev gstreamer1.0\-plugins\-base gstreamer1.0\-plugins\-good gstreamer1.0\-plugins\-bad gstreamer1.0\-plugins\-ugly gstreamer1.0\-libav gstreamer1.0\-doc gstreamer1.0\-tools gstreamer1.0\-x gstreamer1.0\-alsa gstreamer1.0\-gl gstreamer1.0\-gtk3 gstreamer1.0\-qt5 gstreamer1.0\-pulseaudio

For Ubuntu 16.04, follow [https://github.com/mavlink/qgroundcontrol/issues/4303](https://github.com/mavlink/qgroundcontrol/issues/4303).

Basically, run

list=$\(apt\-cache \-\-names\-only search ^gstreamer1.0\-\* | awk '\{ print $1 \}' | grep \-v gstreamer1.0\-hybris\)

sudo apt\-get install $list

For Ubuntu 16.04, you can also follow [https://github.com/jackersson/env\-setup/blob/master/gst\-ubuntu\-16\-py/Dockerfile](https://github.com/jackersson/env-setup/blob/master/gst-ubuntu-16-py/Dockerfile).

2\) Make sure gst\-launch\-1.0 videotestsrc \! videoconvert \! fakesink is working.

3\) Setup ssh server on your Linux host machine.

4\) Install VS Code on windows.

5\) Install [https://marketplace.visualstudio.com/items?itemName=ms\-vscode\-remote.remote\-ssh](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh).

Press F1 and run the Remote\-SSH: Open SSH Host... command.

Enter your user and host/IP in the following format in the input box that appears and press enter: user@host\-or\-ip or user@domain@host\-or\-ip. Mine was ssh://username@username\-linux.

Then choose the first option. Then click connect on the popup in the bottom right

Click the bottom left green button and choose your ssh host.

Choose Linux in select the platform of the remote host. Continue with the fingerprint when prompted.

Click on the blue details link in the setting up popup in the bottom right corner and put your password. Press enter.

Open the folder and browse to your folder.

Click on the blue details link in the setting up popup in the bottom right corner and put your password. Press enter.


6\) Trust all authors

You can now browse the code.

7\) You need to set up VS code to support debugging and code highlighting with IntelliSense.

Make a folder named .vscode in the root of the folder you opened and add the following files:
**.vscode/c\_cpp\_properties.json**

\(got it from running pkg\-config \-\-cflags \-\-libs gstreamer\-video\-1.0 gtk\+\-3.0 gstreamer\-1.0 in terminal for all libraries\)

\{

    "configurations": \[

        \{

            "name": "Linux",

            "includePath": \[

                "$\{workspaceFolder\}/\*\*",

                "/usr/lib/x86\_64\-linux\-gnu/glib\-2.0/include",

                "/usr/include/glib\-2.0",

                "/usr/lib/x86\_64\-linux\-gnu/gstreamer\-1.0/include/",

                "/usr/include/gstreamer\-1.0",

                "/usr/lib/x86\_64\-linux\-gnu/dbus\-1.0/include",

                "/usr/include/gtk\-3.0",

                "/usr/include/at\-spi2\-atk/2.0",

                "/usr/include/at\-spi\-2.0",

                "/usr/include/dbus\-1.0",

                "/usr/include/gio\-unix\-2.0",

                "/usr/include/cairo",

                "/usr/include/pango\-1.0",

                "/usr/include/harfbuzz",

                "/usr/include/atk\-1.0",

                "/usr/include/pixman\-1",

                "/usr/include/uuid",

                "/usr/include/freetype2",

                "/usr/include/gdk\-pixbuf\-2.0",

            \],

            "defines": \[\],

            "compilerPath": "/usr/bin/gcc",

            "cStandard": "gnu11",

            "cppStandard": "gnu\+\+14",

            "intelliSenseMode": "linux\-gcc\-x64",

            "configurationProvider": "ms\-vscode.cmake\-tools"

        \}

    \],

    "version": 4

\}

**.vscode/launch.json**

\{

    // Use IntelliSense to learn about possible attributes.

    // Hover to view descriptions of existing attributes.

    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387

    "version": "0.2.0",

    "configurations": \[

        \{

            "name": "gcc \- Build and debug active file",

            "type": "cppdbg",

            "request": "launch",

            "program": "$\{fileDirname\}/$\{fileBasenameNoExtension\}",

            "args": \[

                "\-e", "playbin", "uri=https://www.freedesktop.org/software/gstreamer\-sdk/data/media/sintel\_trailer\-480p.webm"

            \],

            "stopAtEntry": false,

            "cwd": "$\{workspaceFolder\}",

            "environment": \[\],

            "externalConsole": false,

            "MIMode": "gdb",

            "setupCommands": \[

                \{

                    "description": "Enable pretty\-printing for gdb",

                    "text": "\-enable\-pretty\-printing",

                    "ignoreFailures": true

                \}

            \],

            "preLaunchTask": "C/C\+\+: gcc build active file",

            "miDebuggerPath": "/usr/bin/gdb"

        \}

    \]

\}

**.vscode/settings.json**

  
  
  
  
\{

    "C\_Cpp.clang\_format\_fallbackStyle": "\{ BasedOnStyle: GNU, IndentWidth: 2, ColumnLimit: 0, BreakBeforeBraces: Linux\}",

    "files.associations": \{

        "string": "c",

        "gst.h": "c",

        "gstdio.h": "c",

        "gprintf.h": "c",

        "gstbin.h": "c",

        "gstbuffer.h": "c",

        "gstbufferpool.h": "c"

    \},

    "C\_Cpp.errorSquiggles": "Enabled"

\}

**.vscode/tasks.json**


\{

    "tasks": \[

        \{

            "type": "cppbuild",

            "label": "C/C\+\+: gcc build active file",

            "command": "/usr/bin/gcc",

            "args": \[

                "\-g",

                "$\{file\}",

                "\-o",

                "$\{fileDirname\}/$\{fileBasenameNoExtension\}",

                "`",

                "pkg\-config",

                "\-\-cflags",

                "\-\-libs",

                "gstreamer\-1.0",

                "gstreamer\-audio\-1.0",

                "gstreamer\-video\-1.0",

                "gtk\+\-3.0",

                "gstreamer\-pbutils\-1.0",

                "`"

            \],

            "options": \{

                "cwd": "$\{workspaceFolder\}"

            \},

            "problemMatcher": \[

                "$gcc"

            \],

            "group": \{

                "kind": "build",

                "isDefault": true

            \},

            "detail": "Task generated by Debugger."

        \}

    \],

    "version": "2.0.0"

\}


8\) Install VS Code extension [https://code.visualstudio.com/docs/languages/cpp](https://code.visualstudio.com/docs/languages/cpp) on host.

I recommend you to also optionally install VS Code extension [https://marketplace.visualstudio.com/items?itemName=ms\-vscode.cpptools\-extension\-pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools-extension-pack) on host.

Ctrl \+ Shift \+ B to build

Open new terminal. Browse to path of C\+\+ file.

then ./executable. Your gstreamer app should start running.

If prompted select 

Search for kits

Install in host

9\) You can find usages of variables and functions in your code by Ctrl\+Click on the desired symbol.

10\) You can auto indent by running alt\+shift\+f. You can modify auto indent options from **.vscode/settings.json**.

11\) You can debug code by putting breakpoints and pressing F5. While debugging you can put variables in watch and change variable values to anything at runtime to prevent multiple executions.

12\) You can see the diff between your changes if you have opened a git folder and can revert and stage changes in VS Code itself.

13\) Close VS code. Everytime you open VS Code again:

Open recents and look for your ssh folder.

Click details to add password and continue.

14\) Install any other extensions in VS Code as you like and have fun\! Try to standardize the settings in your team\!\!\!


