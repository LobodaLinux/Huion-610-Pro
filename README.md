# Huion-610-Pro<br>
<br>
How to use graphical tablet Huion 610 Pro buttons in ubuntu linux<br>

SOLUTION:<br>

Installing digimend-kernel-drivers-6 from source followings the instructions.<br>
Creating 52-tablet.conf because it didn't exist: <br>
    <i>cd /etc/X11<br>
    sudo mkdir xorg.conf.d <br>
    cd xorg.conf.d <br>
    sudo gedit 52-tablet.conf <br>
    Copy and paste the following in that file:<br>
    Section "InputClass"<br>
    Identifier "Huion on wacom"<br>
    # MatchIsTablet "on"<br>
    MatchProduct "HUION"<br>
    MatchDevicePath "/dev/input/event*"<br>
    Driver "wacom"<br>
    EndSection<br></i>
Saving the file and restart.<br>

Open the terminal and put the following: xsetwacom --list<br>
You should see something like this:<br>

HUION PenTablet Pad pad id: 13 type: PAD<br>
HUION PenTablet Pen stylus id: 14 type: STYLUS<br>
The buttons are: 1,2,3,8,9,10,11,12.<br>

Put this in the terminal, defining the desired keys for each button (Top-down on the tablet Huion H610 Pro):<br>

xsetwacom --set "HUION PenTablet Pad pad" Button 1 "key +ctrl +z -z -ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 2 “key e” <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 3 "key +ctrl" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 8 "key +" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 9 "key -" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 10 "key [" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 11 "key ]" <br>
xsetwacom --set "HUION PenTablet Pad pad" Button 12 "key space" <br>
