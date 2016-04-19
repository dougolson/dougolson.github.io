---
layout: post
title: A Few Uses and Abuses of Pro Tools
date: 2016-4-1 8:40 
description: Presentation to UW Madison Sound Design Classes
thumbnail: /img/proToolsImages/ptIcon.png
comments: True
---



<DIV CLASS="ABSTRACT">
These are notes for two guest lectures I gave to Professor Joseph Koykkar's sound design classes at UW Madison on March 14, 2016. Various ways of generating sound from simple building blocks like sine waves and pink noise are explored: beating sine waves, filtered noise, extreme pitch shifting and time stretching, and the application of delay, reverb and modulation. Along the way, a variety of useful Pro Tools routing and automation techniques are applied, and a number of standard plugins are put to use. Various helpful key commands are demonstrated as well. I have included a number of audio examples.

The material is broken into six sections:


<A HREF="#SECTION_1">Beating Sine Waves, </A>
<A HREF="#SECTION_2">Filtered Noise, </A>
<A HREF="#SECTION_3">Automation, </A>
<A HREF="#SECTION_4">Elastic Audio Mangulation of a Sine Wave, </A>
<A HREF="#SECTION_5">Elastic Audio Mangulation of a Square Wave, </A>
<A HREF="#SECTION_6">Elastic Audio Mangulation of a Drum Loop.</A>



</DIV>
<P>
<H1>

<A NAME="SECTION_1">Beating Sine Waves</A>

</H1>
No sine waves were harmed in the preparation of this presentation.  
	
<UL>
<LI>Make two sine wave clips with different frequencies
		
<UL>
<LI>when heard together, the two tones will "beat" at the difference frequency
</LI>
<LI>i.e. 264 - 261 = 3 Hz beat frequency
		
</LI>
</UL>
</LI>
<LI>Make an empty selection
</LI>
<LI><strong>Start End Length</strong> fields can be useful for making exact selections
		
<DIV ALIGN="CENTER"><A NAME="30"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Four second selection</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="197" HEIGHT="106" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/startEndLength2.png"
 ALT="Image startEndLength2"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Audiosuite Signal Generator - select signal type, set frequency and level, <strong>Render</strong>
		
<DIV ALIGN="CENTER"><A NAME="37"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Audiosuite Signal Generator</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="241" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/sigGen.png"
 ALT="Image sigGen"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Use "New Track" for quick and easy routing 
		
<UL>
<LI>Select all tracks you want to route
</LI>
<LI>Hold down <strong>Option + Shift</strong>
</LI>
<LI>Click on the output of one of the tracks to be routed
			
<DIV ALIGN="CENTER"><A NAME="45"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Route to New Track - Output Path Selector</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="203" HEIGHT="152" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/newTrack.png"
 ALT="Image newTrack"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Select "New Track"
</LI>
<LI>Choose Track Type and Name
			
<DIV ALIGN="CENTER"><A NAME="51"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Route to New Track - Select Track</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="784" HEIGHT="131" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/newTrack2.png"
 ALT="Image newTrack2"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI><strong>Audio Track</strong> allows you to "print" to a new audio file
</LI>
<LI><strong>Aux Track</strong> is good for further processing
</LI>
<LI>End result:
			
<DIV ALIGN="CENTER"><A NAME="59"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Source tracks routed and recorded</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="435" HEIGHT="337" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/swBeat.png"
 ALT="Image swBeat"> 
					
</DIV></TD></TR>
</TABLE></br>
<p><audio controls><source src="/audio/jkClass/sineWavesBeat.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> </p>
</DIV>
</LI>
</UL>
</LI>
<LI>A few useful commands:
		
<UL>
<LI><strong>Option + F</strong> zoom a selection to screen width
</LI>
<LI><strong>Command + [ or ]</strong> Horizontal zoom
</LI>
<LI><strong>Option + Command + [ or ]</strong> Vertical zoom
</LI>
<LI><strong>Option Click</strong> - set control to default
</LI>
<LI><strong>Tab to Transient</strong> - very useful, can be combined with option and shift keys
			
<DIV ALIGN="CENTER"><A NAME="72"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Tab to Transient</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="110" HEIGHT="68" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/tt.png"
 ALT="Image tt"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>
			
</LI>
<LI><strong>Commands Focus Mode:</strong> single key "hotkey" commands 
			
<DIV ALIGN="CENTER"><A NAME="79"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Commands Focus Mode</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="120" HEIGHT="112" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/cfMode.png"
 ALT="Image cfMode"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

<UL>
<LI><strong>A</strong> key trims from clip start to cursor
</LI>
<LI><strong>S</strong> key trims from cursor to clip end
</LI>
<LI><strong>P and ;</strong> move selection up and down. Very useful.
</LI>
<LI><strong>Shift + S, M, R</strong> - solo, mute, record enable all tracks where cursor resides
</LI>
<LI><strong>Option Drag</strong> drags a copy of a clip, plug-in or send
			
</LI>
</UL>
</LI>
</UL>
</LI>
</UL>
<H1><A NAME="SECTION_2">
Filtered Noise</A>
</H1>
Interesting pitched sounds can be created by applying very sharp filters to noise signals
	
<UL>
<LI>Audiosuite Signal Generator : Select desired length, Pink or White noise at -6dB, Render
</LI>
<LI>Air Vintage filter 
		
<DIV ALIGN="CENTER"><A NAME="96"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Air Vintage Filter</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="422" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/vintageFilter.png"
 ALT="Image vintageFilter"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

<UL>
<LI>Set cutoff to desired frequency
</LI>
<LI>Set resonance to around 90 
</LI>
<LI>Mode: BP (Bandpass Filter)
</LI>
<LI>Option drag plug-in to put two or more in series
		
</LI>
</UL>
</LI>
<LI>Duplicate tracks - Option Shift D (or right-click) 
</LI>
<LI>Fancy: set frequencies to chord notes...</LI>
	
<DIV ALIGN="CENTER"><audio controls><source src="/audio/jkClass/filteredNoise1.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/><br/> </DIV>	


| Interval      | Ratio    | Multiplier | Example |
|:-------------:|:--------:|:----------:|:-------:|
| Unison        | 1:1      | 1          | 440 Hz  |
| Major second  | 9:8      | 1.125      | 495 Hz  |
| Minor Third   | 32:27    | 1.185      | 521 Hz  |
| Major Third   | 81:64    | 1.2656     | 557 Hz  |
| Fourth        | 4:3      | 1.333      | 587 Hz  |
| Tritone       | 1024:729 | 1.405      | 618 Hz  |
| Fifth         | 3:2      | 1.5        | 660 Hz  |
| Minor Sixth   | 128:81   | 1.58       | 695 Hz  |
| Major Sixth   | 27:16    | 1.6875     | 743 Hz  |
| Minor Seventh | 16:9     | 1.778      | 782 Hz  |
| Major Seventh | 243:128  | 1.898      | 835 Hz  |
| Octave        | 2:1      | 2          | 880 Hz  |


</br></br>

<H1><A NAME="SECTION_3">
Automation</A>
</H1>
Automation can be used for almost anything imaginable in Pro Tools. Here we will change the pitch of one of the filtered noise tracks for a musical effect.
	
<UL>
<LI>"Power Claw" (<strong>Control + Option + Command</strong>) - click on a parameter (Cutoff in this example) to quickly automate it 
		
<DIV ALIGN="CENTER"><A NAME="112"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
"Power Claw" click on Cutoff knob</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="313" HEIGHT="148" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/powerClaw.png"
 ALT="Image powerClaw"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Set ruler to Bars Beats 
		
<DIV ALIGN="CENTER"><A NAME="118"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
BarsBeats Ruler</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="163" HEIGHT="78" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/ruler.png"
 ALT="Image ruler"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Set track to "Ticks" (more on this in a moment)
		
<DIV ALIGN="CENTER"><A NAME="124"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Tick-based</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="297" HEIGHT="195" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/ticks.png"
 ALT="Image ticks"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>set grid to 1 Bar:
		
<DIV ALIGN="CENTER"><A NAME="130"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Grid set to 1 Bar</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="173" HEIGHT="63" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/grid.png"
 ALT="Image grid"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Select Grid Mode (press F2)
</LI>
<LI>Make a 1 bar selection, use Smart Tool, mouse up, drag cutoff frequency to 695, 782, 743
</LI>
<LI>Hold down the <strong>Command</strong> key while mousing for finer control
		
<DIV ALIGN="CENTER"><A NAME="137"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Paste Special</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="626" HEIGHT="317" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/pasteSpecial.png"
 ALT="Image pasteSpecial"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI><strong>Multiple Automation Lanes</strong>
			
<UL>
<LI>click on small triangle at lower left corner of track, automation "lane" will appear
</LI>
<LI>click on + or - buttons to add more lanes or remove unwanted
				
<DIV ALIGN="CENTER"><A NAME="145"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Automation Lanes</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="449" HEIGHT="117" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/autoLanes.png"
 ALT="Image autoLanes">
						
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Select desired parameter in the pulldown
			
</LI>
</UL>
</LI>
<LI>Use Edit : Paste Special : To Current Automation Type to paste to other tracks 
		
<DIV ALIGN="CENTER"><A NAME="152"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Plug-In Automation</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="474" HEIGHT="226" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/auto1.png"
 ALT="Image auto1"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

<DIV ALIGN="CENTER"><audio controls><source src="/audio/jkClass/filteredPinkNoise.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/><br/> </DIV>
</LI>
<LI>Make a tempo change - since track has been set to "Tick Based," automation will follow tempo
</LI>
<LI>Note - The "Conductor" (Window Menu : Transport - the blue box) has to be <strong>on</strong> for tempo events to work 
			
<DIV ALIGN="CENTER"><A NAME="159"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Conductor</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="162" HEIGHT="102" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/conductor.png"
 ALT="Image conductor"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Click on the "+" sign just to the left of the <strong>Tempo</strong> ruler
		
<DIV ALIGN="CENTER"><A NAME="166"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Tempo Event at Bar 9</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="683" HEIGHT="296" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/tempoChange.png"
 ALT="Image tempoChange"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>
</LI>
</UL>
	<strong>Air Talkbox Effect:</strong> Interesting Vocoder type sounds
	
<DIV ALIGN="CENTER"><A NAME="174"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Air Talkbox Effect</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="332" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/talkbox.png"
 ALT="Image talkbox"> 
			
</DIV></TD></TR>
</TABLE></br>
</DIV>

<H1><A NAME="SECTION_4">
Elastic Audio Mangulation of a Sine Wave</A>
</H1>
By repeatedly shifting a sine wave down in pitch until it is out of the audible range, and then shifting it back up, interesting sounds can result. Making the track tick-based and playing with tempo events allows for varispeed effects.
	
<UL>
<LI>Create a 1 kHz sine wave at -6 dB
</LI>
<LI>Enable Elastic Audio - Polyphonic (the tiny "upside-down Y" button)
			
<DIV ALIGN="CENTER"><A NAME="183"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Elastic Audio Polyphonic Mode</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="235" HEIGHT="161" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/elastic.png"
 ALT="Image elastic"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Clip Menu : Elastic Properties Floating Window
			
<DIV ALIGN="CENTER"><A NAME="189"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Elastic Audio Properties Floating Window</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="318" HEIGHT="183" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/elasticPitch.png"
 ALT="Image elasticPitch"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Select clip and set Pitch Shift to -24 (Pitch is now down two octaves to 250 Hz)
</LI>
<LI>Consolidate with <strong>Option + Shift + 3</strong> 
</LI>
<LI>Repeat - Pitch is now 62 Hz
</LI>
<LI>Repeat - Pitch is now 16 Hz - Pro Tools will get confused...
</LI>
<LI>Pitch up + 24 two more times, we're back to 250 Hz, in theory...
</LI>
<LI>Repeat the entire process again...
</LI>
<LI>Set track to tick-based
</LI>
<LI>Select clip
</LI>
<LI>Change Elastic Audio to "Varispeed"
</LI>
<LI>Event Menu : Tempo Operations : Linear - set ending tempo to 240, or 60...
			
<DIV ALIGN="CENTER"><A NAME="196"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Event Menu : Tempo Operations : Linear</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="518" HEIGHT="163" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/linearTempoChange.png"
 ALT="Image linearTempoChange"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Try slowing the tempo way down (as in 5 BPM) and then changing the Elastic Audio plug-in to "Rhythmic." Interesting...
			
<DIV ALIGN="CENTER"><A NAME="202"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Tempo Operations Window</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="324" HEIGHT="283" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/linearTempoChange2.png"
 ALT="Image linearTempoChange2"> 
					
</DIV></TD></TR>
</TABLE></br>
<p><audio controls><source src="/audio/jkClass/sineWaveExtremePitch.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> </p>
</DIV>
</LI>
</UL>
<H1><A NAME="SECTION_5">
Elastic Audio Mangulation of a Square Wave</A>
</H1>
Square waves have loads of odd harmonic overtones. Pitch shifting them up by many octaves pushes the overtones out of the range of the digital system. Pitch shifting them back into range results in a sound with altered harmonics. The Mod Delay plug in can then be applied to create vibrato effects and beyond. Similar unusual sounds can be generated by pitch shifting and processing pink or white noise.

<UL>
<LI>Create a 1 kHz square wave at -6dB
</LI>
<LI>Enable Elastic Audio - Polyphonic
</LI>
<LI>Clip Menu : Elastic Properties Floating Window
</LI>
<LI>Select clip and set Pitch to +24 (Pitch is now 4 kHz)
</LI>
<LI>Consolidate with <strong>Option + Shift + 3</strong> 
</LI>
<LI>Repeat - Pitch is now 16 kHz
</LI>
<LI>Consolidate 
</LI>
<LI>Now reverse the process, shifting the pitch down until you get a sound you like
</LI>
<LI>Insert A Mod Delay 
	
<DIV ALIGN="CENTER"><A NAME="212"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Mod Delay Used as a Vibrato</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/vibrato.png"
 ALT="Image vibrato"> 
			
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Interesting Alterations
	
<UL>
<LI>Increase <strong>feedback</strong> to +/- 50(or more)
</LI>
<LI>Increase <strong>Delay Time</strong> in small increments (you can type in as little as .1 milliseconds), listen to the difference
</LI>
<LI>Play with the low pass filter
	
</LI>
</UL>
</LI>
<LI>Extra Fancy
	
<UL>
<LI>Try these settings:
		
<DIV ALIGN="CENTER"><A NAME="223"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Mod Delay Used as an Extreme Vibrato</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/vibrato2.png"
 ALT="Image vibrato2"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Use the "Power Claw" trick to automate the <strong>Depth</strong> control
</LI>
<LI><strong>Control Command</strong> click on the Depth control to switch to its automation playlist
</LI>
<LI>Select the Pencil  Triangle Tool
		
<DIV ALIGN="CENTER"><A NAME="231"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Pencil Triangle Tool</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="176" HEIGHT="158" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/triTool.png"
 ALT="Image triTool"> 
				
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Set the grid to <strong>1 Bar</strong>
</LI>
<LI>Draw automation with the triangle tool
		
<DIV ALIGN="CENTER"><A NAME="238"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Automation with the Pencil Triangle Tool</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="778" HEIGHT="97" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/triAuto.png"
 ALT="Image triAuto"> 
				
</DIV></TD></TR>
</TABLE></br>
<p><audio controls><source src="/audio/jkClass/extremeMod.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> </p>
</DIV>

</LI>
<LI>Try changing the rate (it often interacts with the frequency of the source tone in interesting ways) 
</LI>
<LI>Put some echo or delay on it, or a flanger, or all three...
	
</LI>
</UL>
</LI>
</UL>
<H1><A NAME="SECTION_6">
Elastic Audio Mangulation of a Drum Loop</A>
</H1>
	
<UL>
<LI>Oasis Chorus 2 Loop - 140 BPM, 4 Bar Loop
</LI>
<LI>Identify Beat - set Pro Tools tempo to 140
			
<DIV ALIGN="CENTER"><A NAME="248"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Identify Beat</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="326" HEIGHT="350" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/idbeat.png"
 ALT="Image idbeat"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>"Conductor" has to be <strong>on</strong>
</LI>
<LI>Set Elastic Audio plug-in to <strong>Monophonic</strong>
</LI>
<LI>Use <strong>TCE Trim tool,</strong> stretch loop to 40 Bars
			
<DIV ALIGN="CENTER"><A NAME="257"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
10x Stretch</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="505" HEIGHT="269" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/10xStretch.png"
 ALT="Image 10xStretch"> 
					
</DIV></TD></TR>
</TABLE></br>
<p><audio controls><source src="/audio/jkClass/drumLoopExtremeStretch.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio><br/> </p>
</DIV>

</LI>
<LI>Apply excessive compression
			
<DIV ALIGN="CENTER"><A NAME="263"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Excessive Compression</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="542" HEIGHT="425" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/compress.png"
 ALT="Image compress"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Apply Sans Amp distortion
			
<DIV ALIGN="CENTER"><A NAME="269"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Sans Amp Distortion</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="581" HEIGHT="210" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/sansAmp.png"
 ALT="Image sansAmp"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Apply Phase Shifter
			
<DIV ALIGN="CENTER"><A NAME="275"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Phase Shifter</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="387" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/phaser.png"
 ALT="Image phaser"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Sounds a bit "buzzy" - let's tame it with some eq
			
<DIV ALIGN="CENTER"><A NAME="281"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Low Pass Filter, -18 dB/Octave at 2.45 kHz</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="470" HEIGHT="289" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/lpf.png"
 ALT="Image lpf"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>Let's smooth it out even more with another compressor, this time with less agressive settings
			
<DIV ALIGN="CENTER"><A NAME="287"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="542" HEIGHT="425" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/comp2.png"
 ALT="Image comp2"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>
  
</LI>
<LI>Add some delay to make it sound more ethereal
</LI>
<LI>Click on a send selector, use "New Track" again, create an Aux track called "Ambience"
</LI>
<LI>A new send window will appear <strong>Option click</strong> the fader to set it to zero, or adjust it by ear
			
<DIV ALIGN="CENTER"><A NAME="294"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Create an Ambience Send and Return</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="896" HEIGHT="245" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/ambSend.png"
 ALT="Image ambSend"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>
 
</LI>
<LI>Put a Mod Delay on the return track
</LI>
<LI>I like to make the left and right a little different - note the settings
			
<DIV ALIGN="CENTER"><A NAME="300"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="805" HEIGHT="403" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/modDelay.png"
 ALT="Image modDelay"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>
 
</LI>
<LI>And just for good measure, a little Plate reverb to smooth things out a bit more: 
			
<DIV ALIGN="CENTER"><A NAME="306"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="467" HEIGHT="403" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/verb.png"
 ALT="Image verb"> 
					
</DIV></TD></TR>
</TABLE></br>
</DIV>

</LI>
<LI>The plug-ins plus the send and return look like this:
		
<DIV ALIGN="CENTER"><A NAME="312"></A>
<TABLE>
<CAPTION ALIGN="BOTTOM">
Plug-in Chain, Send and Return</CAPTION></br>
<TR><TD>
<DIV ALIGN="CENTER">
</br><IMG
  WIDTH="212" HEIGHT="288" ALIGN="BOTTOM" BORDER="0"
 SRC=" /img/proToolsImages/plugChain.png"
 ALT="Image plugChain"> 
				
</DIV></TD></TR>
</TABLE></br>
</br>
<p>Drum loop before:</p><audio controls><source src="/audio/jkClass/drumLoopClean.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio>
</br></br><p>Drum loop after:</p><audio controls><source src="/audio/jkClass/drumLoopMangled.mp3" type="audio/mp3" preload="auto">
Your browser does not support the audio tag.
</audio>
</DIV>
</LI>
</UL>

