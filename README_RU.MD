# Huion-610-Pro <br>
<br>
Как использовать графические кнопки Huion 610 Pro в ubuntu / debian / linux mint / deepin и т. Д. Linux <br>
          <H2> РЕШЕНИЕ: </ h2>
<ul>
<li> Установка <strong> <a href="https://github.com/LobodaLinux/Huion-610-Pro/blob/master/digimend-dkms_6_all.deb" target="blank"> digimend-kernel-drivers- 6 </a> </ strong> из файла deb, используя gdebi или Synaptic или терминал. </li>
<li> Создайте 52-tablet.conf, потому что его нет в системе: </li>
Откройте терминал Ctrl + Alt + T и введите:
</ul>
<pre><code>cd /etc/X11
sudo mkdir xorg.conf.d 
cd xorg.conf.d 
sudo gedit 52-tablet.conf 
</code></pre>
<ul>
<li> Скопируйте и вставьте в этот файл следующее: </li>
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
<P> Сохранените файл и перезагрузутесь. </P>
</li>
<li>
<P> Откройте терминал и введите следующее: <code>xsetwacom --list</code><br>
You should see something like this:</p>
<blockquote>
<p>HUION PenTablet Pad pad           id: 13  type: PAD<br>
HUION PenTablet Pen stylus          id: 14  type: STYLUS</p>
</blockquote>
</li>
</ul>
<P> Кнопки: 1,2,3,8,9,10,11,12. </P>
<ul>
<li> Поместите это в терминал, определив нужные клавиши для каждой кнопки (считая кнопки сверху вниз на планшете Huion H610 Pro):</li>
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
<H1> И готово, кнопки будут работать. :) </H1>
<br> <br>
A) Вы можете автоматизировать процесс, сделав файл сценария, который будет запускаться каждый раз, когда вы открываете сессию. Например, мой скрипт называется Huion.Default.sh<br>
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
Б) Не забудьте дать разрешение на выполнение скрипта: <br>
<pre><code>chmod +x Huion.Default.sh<br></code></pre>
<br>
В) Вы можете создавать разные сценарии и схемы кнопок для различных приложений, которые вы используете с планшетом. Вы можете запускать эти скрипты перед запуском самих приложений, просто обавив их в лаунчеры. Это можно сделать отредактировав команду в файле laucher или desktop. Например: Команда: ~/./GIMP-tablet-scheme.sh && /usr/bin/gimp <br>
