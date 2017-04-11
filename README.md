# Huion-610-Pro
driver to graphical tablet Huion 610 Pro

how to use huion h610 pro buttons in ubuntu linux

SOLUTION:

Installing digimend-kernel-drivers-6 from source followings the instructions.
Creating 52-tablet.conf because it didn't exist:
cd /etc/X11
sudo mkdir xorg.conf.d 
cd xorg.conf.d 
sudo gedit 52-tablet.conf 
Copy and paste the following in that file:
Section "InputClass"
Identifier "Huion on wacom"
# MatchIsTablet "on"
MatchProduct "HUION"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
EndSection
Saving the file and restart.

Open the terminal and put the following: xsetwacom --list
You should see something like this:

HUION PenTablet Pad pad id: 13 type: PAD
HUION PenTablet Pen stylus id: 14 type: STYLUS
The buttons are: 1,2,3,8,9,10,11,12.

Put this in the terminal, defining the desired keys for each button (Top-down on the tablet Huion H610 Pro):

xsetwacom --set "HUION PenTablet Pad pad" Button 1 "key +ctrl +z -z -ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 2 “key e” <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 3 "key +ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 8 "key +" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 9 "key -" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 10 "key [" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 11 "key ]" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 12 "key space" <br>
