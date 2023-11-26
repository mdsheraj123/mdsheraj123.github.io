---
layout: post
title: >
    Custom Video Composition logic
hide_title: false
tags: []
excerpt_separator: <!--more-->
---

How to do Video Composition in OpenGLES2?
[This](https://www.edn.com/portable-and-scalable-solution-for-off-screen-video-frame-composition-and-decomposition-using-opengl-es-part-2/) is a good reference, basically, we draw the number of times the input is there.

I have implemented a custom logic in our app ‘Qmedia’ for Kona LA to fit any number of video frames onto a rectangular output with given width and height. I could not find any industry standard for the logic so developed my own.

I am using OpenGL ES to achieve the same. Basically, we use \-
**GLES20.glViewport\(wOffset, hOffset, rectWidth, rectHeight\);**

To set the location of the input frame on the output frame. We do for each input frame \- 
**GLES20.glDrawArrays\(GLES20.GL\_TRIANGLE\_STRIP, 0, 4\);**

The logic is based on four core principles.

1\)	Use the entire space available in the output frame.

2\)	The only transformation of the input will be to change location, width, and height.

3\)	Use the aspect ratio of the output frame for most inputs keeping 4\) in mind.

4\)	Any change in aspect ratio will be spread out amongst the most inputs possible.

Based on my logic inputs that are not perfect squares like 1,4,9 will be stretched. Secondary principle:

1\)	Videos will be filled horizontally \(along width as usually more\) first.

My logic goes like this \-

1\)	Find the gridSize which is ceil of √inputs.

2\)	numberVertically is inputs/gridSize.

3\)	Extra grids we must cover is gridSize\*numberVertically\-inputs.

4\)	baseHeight is totalHeight /numberVertically.

5\)	baseWidth is totalWidth/gridSize. baseWidthShared is totalWidth/\(gridSize\-1\).

6\)	We start filling the grids along width from bottom up taking note on which row we are.

7\)	We give priority to clearing one Extra grid per row. Till they are cleared, we use baseWidthShared.

I am making sure to round up or down the final coordinates of the input on the output frame to cover the most area and hence avoid unfilled areas.

Finally using SufaceView we can fit the output on any display.
[
{% include image.html url="/assets/img/posts/AVvXsEhipHk2ArVDi5aBDAScJtRxoIFi4XznNiwRn8ckgA0FUdpc8ojuWY1QtirlCLTrONPCUj9c8YU0utGXyIXUaLqxOQv7o9e-Wu3okeZiQxEBJy8ZJ8ynfdWcR4jFY23bKjlO6dtxJE4D3s2goHslVC5ZyIMgKAXZ1VnJWdQT03CnItOcZs651iPxmD9Ygg=s400" caption="](https://blogger.googleusercontent.com/img/a/AVvXsEhipHk2ArVDi5aBDAScJtRxoIFi4XznNiwRn8ckgA0FUdpc8ojuWY1QtirlCLTrONPCUj9c8YU0utGXyIXUaLqxOQv7o9e-Wu3okeZiQxEBJy8ZJ8ynfdWcR4jFY23bKjlO6dtxJE4D3s2goHslVC5ZyIMgKAXZ1VnJWdQT03CnItOcZs651iPxmD9Ygg=s1001)Figure 1: 4 inputs[" alt="" %}
{% include image.html url="/assets/img/posts/AVvXsEjjctJJZjGSby8Xxs_Z-GBRyfjCM-fV92SpV27sN3iwJwZONLW-As1TQtElw6bc1s_jtfOosn-ABJ4EAD7DqWG9lSPMMtBdp48TA_ItzXti3djvCa-fSaQn7rd_vHD8vOa5jg3ocDkMognfo9TACrTHzpMSwn2PIe1KWIr0V4N3070IttWSQes8dR4iXw=s400" caption="](https://blogger.googleusercontent.com/img/a/AVvXsEjjctJJZjGSby8Xxs_Z-GBRyfjCM-fV92SpV27sN3iwJwZONLW-As1TQtElw6bc1s_jtfOosn-ABJ4EAD7DqWG9lSPMMtBdp48TA_ItzXti3djvCa-fSaQn7rd_vHD8vOa5jg3ocDkMognfo9TACrTHzpMSwn2PIe1KWIr0V4N3070IttWSQes8dR4iXw=s999)Figure 2: 8 inputs[" alt="" %}
{% include image.html url="/assets/img/posts/AVvXsEh0qsnAgiaieYCKyVHkAFVh3iO5EbIpSC7buEK8Cfv5HupIniDt1yaznGaQNW6BG1Bfq-A0va_9joXlTcEOzdcrOnhe83RrbmQgt8PMKjN4akYV_viQ1SLy8STTquHlMJT-mv6KYHI4KMMPjzmalKB5aYPgtz3ZpnKoamYCz8bAvg3RgbgoI5poFDqoMQ=s400" caption="](https://blogger.googleusercontent.com/img/a/AVvXsEh0qsnAgiaieYCKyVHkAFVh3iO5EbIpSC7buEK8Cfv5HupIniDt1yaznGaQNW6BG1Bfq-A0va_9joXlTcEOzdcrOnhe83RrbmQgt8PMKjN4akYV_viQ1SLy8STTquHlMJT-mv6KYHI4KMMPjzmalKB5aYPgtz3ZpnKoamYCz8bAvg3RgbgoI5poFDqoMQ=s1297)Figure 2: 10 inputs" alt="" %}