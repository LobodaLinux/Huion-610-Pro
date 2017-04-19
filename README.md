# Huion-610-Pro<br>
<br>
How to use graphical tablet Huion 610 Pro buttons in ubuntu / debian / linux mint / deepin etc. linux<br>
          <h2>SOLUTION:</h2>
<ul>
<li>Installing <strong><a href="https://github.com/LobodaLinux/Huion-610-Pro/blob/master/digimend-dkms_6_all.deb" target="blank">digimend-kernel-drivers-6</a></strong> from deb file using gdebi or synaptic or terminal.</li>
<li>Creating 52-tablet.conf because it didn't exist:</li>
open terminal Ctrl+Alt+T then type:
</ul>
<pre><code>cd /etc/X11
sudo mkdir xorg.conf.d 
cd xorg.conf.d 
sudo gedit 52-tablet.conf 
</code></pre>
<ul>
<li>Copy and paste the following in that file:</li>
</ul>
<pre><code>Section "InputClass"
Identifier "Huion on wacom"
# MatchIsTablet "on"
MatchProduct "HUION"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
EndSection
</code></pre>
<ul>
<li>
<p>Saving the file and restart.</p>
</li>
<li>
<p>Open the terminal and put the following: <code>xsetwacom --list</code><br>
You should see something like this:</p>
<blockquote>
<p>HUION PenTablet Pad pad           id: 13  type: PAD<br>
HUION PenTablet Pen stylus          id: 14  type: STYLUS</p>
</blockquote>
</li>
</ul>
<p>The buttons are: 1,2,3,8,9,10,11,12.</p>
<ul>
<li>Put this in the terminal, defining the desired keys for each button (Top-down on the tablet Huion H610 Pro) :</li>
</ul>
<pre><code>xsetwacom --set "HUION PenTablet Pad pad" Button 1 "key +ctrl +z -z -ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 2 "key e" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 3 "key +ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 8 "key +" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 9 "key -" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 10 "key [" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 11 "key ]" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 12 "key space" <br>

</code></pre>
<h1>And ready, the buttons will function. :)</h1>
<br><br>
a) You can automate it by making script file that autoruns every time you open a session. For example, my script is called Huion.Default.sh and I like bebop from AskUbuntu's button scheme:<br>
<br>
<pre><code>#!/bin/sh<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 1 "key +ctrl +z -z -ctrl"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 2 "key e"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 3 "key b"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 8 "key +"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 9 "key -"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 10 "key ]"<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 11 "key ["<br>
xsetwacom --set 'HUION PenTablet Pad pad' Button 12 "key p"<br></code></pre>
<br>
b) Don't forget to give the script execution permission:<br>
<pre><code>chmod +x Huion.Default.sh<br></code></pre>
<br>
c) You can make different scripts and button schemes for the different Apps you use with the tablet. When making lauchers, you can make those scripts lauch before you launch the apps themselves. You do this by editing the Command in the laucher or desktop file. For example: Command: ~/./GIMP-tablet-scheme.sh && /usr/bin/gimp <br>	
