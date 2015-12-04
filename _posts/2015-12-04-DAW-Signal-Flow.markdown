---
layout: post
title: Pro Tools Signal Flow
date: 2015-12-04 01:24 
description: Making sense of Pro Tools signal flow 
comments: True
---


In Pro Tools, the visual layout of a track doesn't correspond to the way signal flows, and this can be confusing. Looking at a track in the mix window, it's reasonable to think that signal should flow from the top down, but this is not the case. Leaving aside the fact that signal does not actually flow at all in the screen image, which is merely a control interface, we can still use what we see onscreen to understand what is happening "under the hood."

Here's a diagram to help identify the relevant parts:

![record.png](/img/DAWSignalFlow/labels.png)<sub>figure 1</sub>

The most common misunderstanding I run into is the idea that the effect of a plug-in on a track that is recording ends up in the recorded file. Visually, this makes sense, but the signal path from the interface doesn't pass through the inserts. You hear the effect of the plug-in, but that is because it is in the playback path. Have a look:  

![record.png](/img/DAWSignalFlow/record.png)<sub>figure 2</sub>

It is possible to record the effect of a plug-in into a track, but it requires an aux track and more complicated routing. More on that in another post.

I included a pre-fader send because in this case what you see in the Pro Tools mix window corresponds with signal flow, which goes through the insert first, then the send, then on to the fader. Be aware, though, that sends are only in the signal path in the sense that they "tap" the signal at a certain point in order to send it somewhere else in your pro tools session. They do not alter the signal passing through the track they are on in any way. 

Another confusing point is the role of the input path selector. On audio tracks, its setting really only matters if the track is recording. In that case, whatever is being fed into the input is what ends up in the file on disk. If you aren't recording, the input path selector is ignored, and Pro Tools simply plays back the clips (files) that are in the timeline on that particular track. In this case, the signal flow is somewhat more intuitive - it runs top to bottom, although it skips over the input and output path selectors to pass through the fader, and then goes to the output.

![playback.png](/img/DAWSignalFlow/playback.png)<sub>figure 3</sub>

A couple of caveats. The foregoing only applies to audio tracks, not to aux tracks or master faders. To keep the diagrams from becoming overly complicated, I have only shown the inserts as pre-fader. 

