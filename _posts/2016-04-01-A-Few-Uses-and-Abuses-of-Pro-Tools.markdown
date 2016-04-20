--- 
layout: post 
title: A Few Uses and Abuses of Pro Tools 
date: 2016-4-1 8:40 
description: Presentation to UW Madison Sound Design Classes 
thumbnail: /img/proToolsImages/ptIcon.png 
comments: True
---
These are notes for two guest lectures I gave to Professor Joseph Koykkar's sound design classes at UW Madison on March 14, 2016. Various ways of generating sound from simple building blocks like sine waves and pink noise are explored: beating sine waves, filtered noise, extreme pitch shifting and time stretching, and the application of delay, reverb and modulation. Along the way, a variety of useful Pro Tools routing and automation techniques are applied, and a number of standard plugins are put to use. Various helpful key commands are demonstrated as well. I have included a number of audio examples.

The material is broken into six sections:


<A HREF="#SECTION_1">Beating Sine Waves, </A>
<A HREF="#SECTION_2">Filtered Noise, </A>
<A HREF="#SECTION_3">Automation, </A>
<A HREF="#SECTION_4">Elastic Audio Mangulation of a Sine Wave, </A>
<A HREF="#SECTION_5">Elastic Audio Mangulation of a Square Wave, </A>
<A HREF="#SECTION_6">Elastic Audio Mangulation of a Drum Loop.</A>

<A NAME="SECTION_1">
	
<H1><A NAME="SECTION_1">
Beating Sine Waves</A>
</H1>
No sine waves were harmed in the preparation of this presentation.  

<div align="center"><br/><audio controls><source src="/audio/jkClass/sineWavesBeat.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>Make two sine wave clips with different frequencies</LI>
<UL>
<LI>When heard together, the two tones will "beat" at the difference frequency</LI>
<LI>i.e. 264 - 261 = 3 Hz beat frequency</LI>
</UL>
<LI>Make an empty selection</LI>
<LI><STRONG>Start End Length</STRONG> fields can be useful for making exact selections</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Four second selection</CAPTION>
<TR>
<TD>
<br/>
<IMG WIDTH="197" HEIGHT="106" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/startEndLength2.png" ALT="Image startEndLength2"></IMG> 
</TD>
</TR>
</TABLE><br/>
<UL>
<LI>Audiosuite Signal Generator - select signal type, set frequency and level, <STRONG>Render</STRONG></LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Audiosuite Signal Generator</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="241" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/sigGen.png" ALT="Image sigGen"></IMG> 
</TD></TR>
</TABLE><br/>

<UL>
<LI>Use "New Track" for quick and easy routing</LI>
<UL>
<LI>Select all tracks you want to route</LI>
<LI>Hold down <STRONG>Option + Shift</STRONG></LI>
<LI>Click on the output of one of the tracks to be routed</LI>
</UL></UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Route to New Track - Output Path Selector</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="203" HEIGHT="152" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/newTrack.png" ALT="Image newTrack"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Select "New Track"</LI>
<LI>Choose Track Type and Name</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Route to New Track - Select Track</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="784" HEIGHT="131" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/newTrack2.png" ALT="Image newTrack2"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI><STRONG>Audio Track</STRONG> allows you to "print" to a new audio file</LI>
<LI><STRONG>Aux Track</STRONG> is good for further processing</LI>
</UL>
End result:



<TABLE>
<CAPTION ALIGN="BOTTOM">Source tracks routed and recorded</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="435" HEIGHT="337" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/swBeat.png" ALT="Image swBeat"></IMG> 
</TD></TR>
</TABLE><br/>

<UL>
<LI>A few useful commands</LI>
<UL>
<LI><STRONG>Option + F</STRONG> zoom a selection to screen width</LI>
<LI><STRONG>Command + [ or ]</STRONG> Horizontal zoom</LI>
<LI><STRONG>Option + Command + [ or ]</STRONG> Vertical zoom</LI>
<LI><STRONG>Option Click</STRONG> - set control to default</LI>
<LI><STRONG>Tab to Transient</STRONG> - very useful, can be combined with option and shift keys</LI>
</UL></UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Tab to Transient Enabled</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="110" HEIGHT="68" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/tt.png" ALT="Image tt"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI><STRONG>Commands Focus Mode:</STRONG>Provides single-key "hotkey" commands</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Commands Focus Mode</CAPTION>
	<TR>
		<TD>
			<IMG  WIDTH="120" HEIGHT="112" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/cfMode.png" ALT="Image cfMode"></IMG>
		</TD>
	</TR>
</TABLE><br/>


<UL>
<LI><STRONG>A</STRONG> key trims from clip start to cursor</LI>
<LI><STRONG>S</STRONG> key trims from cursor to clip end</LI>
<LI><STRONG>P and ;</STRONG> move selection up and down. Very useful.</LI>
<LI><STRONG>Shift + S, M, R</STRONG> - solo, mute, record enable all tracks where cursor resides</LI>
<LI><STRONG>Option Drag</STRONG> drags a copy of a clip, plug-in or send</LI>
</UL>

<H1>
<A NAME="SECTION_2">Filtered Noise</A>
</H1>
Interesting pitched sounds can be created by applying very sharp filters to noise signals:

<div align="center"><br/><audio controls><source src="/audio/jkClass/filteredNoise1.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>Audiosuite Signal Generator : Select desired length, Pink or White noise at -6dB, Render</LI>
<LI>Air Vintage filter</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Air Vintage Filter</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="422" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/vintageFilter.png" ALT="Image vintageFilter"></IMG> 
</TD></TR>
</TABLE><br/>


<UL>
<LI>Set cutoff to desired frequency</LI>
<LI>Set resonance to around 90 </LI>
<LI>Mode: BP (Bandpass Filter)</LI>
<LI>Option drag plug-in to put two or more in series</LI>
<LI>Duplicate tracks - Option Shift D (or right-click) </LI>
<LI>Fancy: set frequencies to chord notes:</LI>
</UL>
		
<TABLE CELLPADDING="3" BORDER="1">
<TR><TD ALIGN="CENTER">Interval</TD>
<TD ALIGN="CENTER">Ratio</TD>
<TD ALIGN="CENTER">Multiplier</TD>
<TD ALIGN="CENTER">Example</TD>
</TR>
<TR><TD ALIGN="CENTER">Unison</TD>
<TD ALIGN="CENTER">1:1</TD>
<TD ALIGN="CENTER">1</TD>
<TD ALIGN="CENTER">440 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Major second</TD>
<TD ALIGN="CENTER">9:8</TD>
<TD ALIGN="CENTER">1.125</TD>
<TD ALIGN="CENTER">495 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Minor Third</TD>
<TD ALIGN="CENTER">32:27</TD>
<TD ALIGN="CENTER">1.185</TD>
<TD ALIGN="CENTER">521 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Major Third</TD>
<TD ALIGN="CENTER">81:64</TD>
<TD ALIGN="CENTER">1.2656</TD>
<TD ALIGN="CENTER">557 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Fourth</TD>
<TD ALIGN="CENTER">4:3</TD>
<TD ALIGN="CENTER">1.333</TD>
<TD ALIGN="CENTER">587 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Tritone</TD>
<TD ALIGN="CENTER">1024:729</TD>
<TD ALIGN="CENTER">1.405</TD>
<TD ALIGN="CENTER">618 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Fifth</TD>
<TD ALIGN="CENTER">3:2</TD>
<TD ALIGN="CENTER">1.5</TD>
<TD ALIGN="CENTER">660 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Minor Sixth</TD>
<TD ALIGN="CENTER">128:81</TD>
<TD ALIGN="CENTER">1.58</TD>
<TD ALIGN="CENTER">695 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Major Sixth</TD>
<TD ALIGN="CENTER">27:16</TD>
<TD ALIGN="CENTER">1.6875</TD>
<TD ALIGN="CENTER">743 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Minor Seventh</TD>
<TD ALIGN="CENTER">16:9</TD>
<TD ALIGN="CENTER">1.778</TD>
<TD ALIGN="CENTER">782 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Major Seventh</TD>
<TD ALIGN="CENTER">243:128</TD>
<TD ALIGN="CENTER">1.898</TD>
<TD ALIGN="CENTER">835 Hz</TD>
</TR>
<TR><TD ALIGN="CENTER">Octave</TD>
<TD ALIGN="CENTER">2:1</TD>
<TD ALIGN="CENTER">2</TD>
<TD ALIGN="CENTER">880 Hz</TD>
</TR>
</TABLE><br/>

<H1>
<A NAME="SECTION_3">Automation</A>
</H1>

Automation can be used for almost anything imaginable in Pro Tools. Here we will change the pitch of one of the filtered noise tracks for a musical effect.

<div align="center"><br/><audio controls><source src="/audio/jkClass/filteredPinkNoise.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>"Power Claw" (<STRONG>Control + Option + Command</STRONG>) - click on a parameter (Cutoff in this example) to quickly automate it</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Power Claw</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="313" HEIGHT="148" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/powerClaw.png" ALT="Image powerClaw"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Set ruler to Bars Beats</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">BarsBeats Ruler</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="163" HEIGHT="78" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/ruler.png" ALT="Image ruler"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Set track to "Ticks" (more on this in a moment</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Tick-based</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="297" HEIGHT="195" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/ticks.png" ALT="Image ticks"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Set grid to 1 Bar</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Grid set to 1 Bar</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="173" HEIGHT="63" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/grid.png" ALT="Image grid"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Select Grid Mode (press F2)</LI>
<LI>Make a 1 bar selection, use Smart Tool, mouse up, drag cutoff frequency to 695, 782, 743</LI>
<LI>Hold down the <STRONG>Command</STRONG> key while mousing for finer contro</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Paste Special</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="626" HEIGHT="317" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/pasteSpecial.png" ALT="Image pasteSpecial"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI><STRONG>Multiple Automation Lanes</STRONG></LI>
<UL>
<LI>Click on small triangle at lower left corner of track, automation "lane" will appear</LI>
<LI>Click on + or - buttons to add more lanes or remove unwante</LI>
</UL></UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Automation Lanes</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="449" HEIGHT="117" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/autoLanes.png" ALT="Image autoLanes"></IMG>	
</TD></TR>
</TABLE><br/>
<UL>
<LI>Select desired parameter in the pulldow</LI>
<LI>Use Edit : Paste Special : To Current Automation Type to paste to other tracks</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Plug-In Automation</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="474" HEIGHT="226" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/auto1.png" ALT="Image auto1"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Make a tempo change - since track has been set to "Tick Based," automation will follow tempo</LI>
<LI>Note - The "Conductor" (Window Menu : Transport - the blue box) has to be <STRONG>on</STRONG> for tempo events to work</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Conductor</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="162" HEIGHT="102" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/conductor.png" ALT="Image conductor"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Click on the "+" sign just to the left of the <STRONG>Tempo</STRONG> rule</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Tempo Event at Bar 9</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="683" HEIGHT="296" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/tempoChange.png" ALT="Image tempoChange"></IMG> 
</TD></TR>
</TABLE><br/>

<STRONG>Air Talkbox Effect:</STRONG> Interesting Vocoder type sounds:

<TABLE>
<CAPTION ALIGN="BOTTOM">Air Talkbox Effect</CAPTION>
<TR><TD>
<IMG  WIDTH="467" HEIGHT="332" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/talkbox.png" ALT="Image talkbox"></IMG> 
</TD></TR>
</TABLE><br/>


<H1>
<A NAME="SECTION_4">Elastic Audio Mangulation of a Sine Wave</A>
</H1>
By repeatedly shifting a sine wave down in pitch until it is out of the audible range, and then shifting it back up, interesting sounds can result. Making the track tick-based and playing with tempo events allows for varispeed effects.

<div align="center"><br/><audio controls><source src="/audio/jkClass/sineWaveExtremePitch.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>Create a 1 kHz sine wave at -6 dB</LI>
<LI>Enable Elastic Audio - Polyphonic (the tiny "upside-down Y" button</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Elastic Audio Polyphonic Mode</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="235" HEIGHT="161" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/elastic.png" ALT="Image elastic"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Clip Menu : Elastic Properties Floating Windo</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Elastic Audio Properties Floating Window</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="318" HEIGHT="183" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/elasticPitch.png" ALT="Image elasticPitch"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Select clip and set Pitch Shift to -24 (Pitch is now down two octaves to 250 Hz)</LI>
<LI>Consolidate with <STRONG>Option + Shift + 3</STRONG> </LI>
<LI>Repeat - Pitch is now 62 Hz</LI>
<LI>Repeat - Pitch is now 16 Hz - Pro Tools will get confused...</LI>
<LI>Pitch up + 24 two more times, we're back to 250 Hz, in theory...</LI>
<LI>Repeat the entire process again...</LI>
<LI>Set track to tick-based</LI>
<LI>Select clip</LI>
<LI>Change Elastic Audio to "Varispeed"</LI>
<LI>Event Menu : Tempo Operations : Linear - set ending tempo to 240, or 60..</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Event Menu : Tempo Operations : Linear</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="518" HEIGHT="163" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/linearTempoChange.png" ALT="Image linearTempoChange"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Try slowing the tempo way down (as in 5 BPM) and then changing the Elastic Audio plug-in to "Rhythmic." Interesting..</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Tempo Operations Window</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="324" HEIGHT="283" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/linearTempoChange2.png" ALT="Image linearTempoChange2"></IMG> 
</TD></TR>
</TABLE><br/>

<H1>
<A NAME="SECTION_5">Elastic Audio Mangulation of a Square Wave</A>
</H1>

Square waves have - in theory at least - infinitely many odd harmonic overtones. Pitch shifting them up by many octaves pushes the overtones out of the range of the digital system. Pitch shifting them back into range results in a sound with altered harmonics. The Mod Delay plug in can then be applied to create vibrato effects and beyond.

<div align="center"><br/><audio controls><source src="/audio/jkClass/extremeMod.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>Create a 1 kHz square wave at -6dB</LI>
<LI>Enable Elastic Audio - Polyphonic</LI>
<LI>Clip Menu : Elastic Properties Floating Window</LI>
<LI>Select clip and set Pitch to +24 (Pitch is now 4 kHz)</LI>
<LI>Consolidate with <STRONG>Option + Shift + 3</STRONG> </LI>
<LI>Repeat - Pitch is now 16 kHz</LI>
<LI>Consolidate </LI>
<LI>Now reverse the process, shifting the pitch down until you get a sound you like</LI>
<LI>Insert A Mod Delay</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Mod Delay Used as a Vibrato</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/vibrato.png" ALT="Image vibrato"></IMG> 
</TD></TR>
</TABLE><br/>

<UL>
<LI>Interesting Alteration #1</LI>
<UL>
<LI>Increase <STRONG>feedback</STRONG> to +/- 50 (or more)</LI>
<LI>Increase <STRONG>Delay Time</STRONG> in small increments (you can type in as little as .1 milliseconds), listen to the difference</LI>
<LI>Play with the low pass filter</LI>
</UL></UL>
<UL>
<LI>Interesting Alteration #2</LI>
<UL>
<LI>Try these settings</LI>
</UL></UL>
<TABLE>
<CAPTION ALIGN="BOTTOM">Mod Delay Used as an Extreme Vibrato</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/vibrato2.png" ALT="Image vibrato2"></IMG> 
</TD></TR>
</TABLE><br/>
<UL
><LI>Use the "Power Claw" trick to automate the <STRONG>Depth</STRONG> control</LI>
<LI><STRONG>Control Command</STRONG> click on the Depth control to switch to its automation playlist</LI>
<LI>Select the Pencil  Triangle Too</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Pencil Triangle Tool</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="176" HEIGHT="158" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/triTool.png" ALT="Image triTool"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Set the grid to <STRONG>1 Bar</STRONG></LI>
<LI>Draw automation with the triangle too</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Automation with the Pencil Triangle Tool</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="778" HEIGHT="97" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/triAuto.png" ALT="Image triAuto"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Try changing the rate (it often interacts with the frequency of the source tone in interesting ways) </LI>
<LI>Put some echo or delay on it..</LI>
</UL>

<H1>
<A NAME="SECTION_6">Elastic Audio Mangulation of a Drum Loop</A>
</H1>

<div align="center"><br/><audio controls><source src="/audio/jkClass/drumLoopExtremeStretch.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>

<UL>
<LI>Oasis Chorus 2 Loop - 140 BPM, 4 Bar Loop</LI>
<LI>Identify Beat - set Pro Tools tempo to 14</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Identify Beat</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="326" HEIGHT="350" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/idbeat.png" ALT="Image idbeat"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>"Conductor" has to be <STRONG>on</STRONG></LI>
<LI>Set Elastic Audio plug-in to <STRONG>Monophonic</STRONG></LI>
<LI>Use <STRONG>TCE Trim tool,</STRONG> stretch loop to 40 Bar</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">10x Stretch</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="505" HEIGHT="269" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/10xStretch.png" ALT="Image 10xStretch"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Apply excessive compressio</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Excessive Compression</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="542" HEIGHT="425" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/compress.png" ALT="Image compress"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Apply Sans Amp distortio</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Sans Amp Distortion</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="581" HEIGHT="210" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/sansAmp.png" ALT="Image sansAmp"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Apply Phase Shifte</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Phase Shifter</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="387" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/phaser.png" ALT="Image phaser"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Sounds a bit "buzzy" - let's tame it with some eq</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Low Pass Filter, -18 dB/Octave at 2.45 kHz</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="470" HEIGHT="289" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/lpf.png" ALT="Image lpf"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Let's smooth it out even more with another compressor, this time with less agressive settings</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM"></CAPTION>
<TR><TD>
<br/><IMG  WIDTH="542" HEIGHT="425" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/comp2.png" ALT="Image comp2"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>Add some delay to make it sound more ethereal</LI>
<LI>Click on a send selector, use "New Track" again, create an Aux track called "Ambience"</LI>
<LI>A new send window will appear <STRONG>Option click</STRONG> the fader to set it to zero, or adjust it by ear</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM">Create an Ambience Send and Return</CAPTION>
<TR><TD>
<IMG  WIDTH="896" HEIGHT="245" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/ambSend.png" ALT="Image ambSend"></IMG> 
</TD></TR>
</TABLE>
<UL>
<LI>Put a Mod Delay on the return track</LI>
<LI>I like to make the left and right a little different - note the settings</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM"></CAPTION>
<TR><TD>
<IMG  WIDTH="805" HEIGHT="403" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/modDelay.png" ALT="Image modDelay"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>And just for good measure, a little Plate reverb to smooth things out a bit more:</LI>
</UL>


<TABLE>
<CAPTION ALIGN="BOTTOM"></CAPTION>
<TR><TD>
<br/><IMG  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/verb.png" ALT="Image verb"></IMG> 
</TD></TR>
</TABLE><br/>
<UL>
<LI>The plug-ins plus the send and return look like this</LI>
</UL>

<TABLE>
<CAPTION ALIGN="BOTTOM">Plug-in Chain, Send and Return</CAPTION>
<TR><TD>
<br/><IMG  WIDTH="212" HEIGHT="288" ALIGN="BOTTOM" BORDER="0" SRC="/img/proToolsImages/plugChain.png" ALT="Image plugChain"></IMG> 
</TD></TR>
</TABLE><br/>

<div align="center">The original drum loop:<br/><audio controls><source src="/audio/jkClass/drumLoopClean.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>
<div align="center">The processed drum loop:<br/><audio controls><source src="/audio/jkClass/drumLoopMangled.mp3" type="audio/mp3" preload="auto">Your browser does not support the audio tag.</audio></div><br/>


