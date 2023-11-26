---
layout: post
title: >
    Automating Indentation of GStreamer code
hide_title: false
tags: []
excerpt_separator: <!--more-->
---
Currently a lot of time is spent on code formatting in code reviews.

We can automate this rather than doing this manually.
# Option 1 \(VS Code\)

We can use VS code auto indentation which is graphical and live. Setup steps at [https://mdsheraj123.blogspot.com/2022/08/linux\-remote\-gstreamer\-execution\-setup.html](https://mdsheraj123.blogspot.com/2022/08/linux-remote-gstreamer-execution-setup.html).
# Option 2 \(gst\-indent\)

The other option for GStreamer code is to use gst\-indent which is recommended by GStreamer [https://gstreamer.freedesktop.org/documentation/frequently\-asked\-questions/developing.html\#what\-is\-the\-coding\-style\-for\-gstreamer\-code](https://gstreamer.freedesktop.org/documentation/frequently-asked-questions/developing.html#what-is-the-coding-style-for-gstreamer-code).

The steps to use gst\-indent are


1\) Download gst\-indent script from the mainline [https://gitlab.freedesktop.org/gstreamer/gstreamer/\-/blob/main/scripts/gst\-indent](https://gitlab.freedesktop.org/gstreamer/gstreamer/-/blob/main/scripts/gst-indent).

2\) Paste the gst\-indent file near your code.

3\) Do runtime permissions to the gst\-indent script.
```
$ chmod 777 <path>/gst-indent
```

4\) Install indent package.
```

$ sudo apt-get update -y
$ sudo apt-get install -y indent
```

5\) Run gst\-indent like this.
```
$ <path>/gst-indent <gstreamer_filename>.c
```

  

You can see all the indentation changes in your file via git diff.
# Conclusion

If you find many indentation corrections in your code with default settings, I would suggest to push all suggestions at once and use this gst\-indent from now on.

Probably modifying gst\-indent to support other coding styles and C\+\+ code might be a good idea.
