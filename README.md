arandr-indicator
================

Quick and simple tray icon menu for changing the monitor layout. A great companion to ARandR tool.

Demonstration video on YouTube:

[![YouTube demonstration](http://img.youtube.com/vi/xqpF6RrYUmo/0.jpg)](http://youtu.be/xqpF6RrYUmo)


Requirements
------------

* [ARandR](http://christian.amsuess.com/tools/arandr/) (optional!)
* Python 2.x
* [PyGTK](http://www.pygtk.org/)
* [python-appindicator](https://launchpad.net/libappindicator)
* [PyXDG](http://freedesktop.org/wiki/Software/pyxdg/)
* Some kind of UI that supports [Unity indicators](https://unity.ubuntu.com/projects/appindicators/), should work on Gnome, KDE, Unity, LXDE…


How to use
----------

1. Run `arandr`.
2. Configure the monitor layout the way you like.
3. Save the layout.
    * ARandR tool will save the layout as a simple one-line shell script that calls `xrandr` with the appropriate commands. The script will be saved in `~/.screenlayout/`.
4. Magic! All layout scripts from that directory will automatically show up in the menu!


Installation
------------

1. `sudo apt-get install python-appindicator python-gtk2 python-xdg arandr`
2. Download [`arandr-indicator.py`](https://raw.githubusercontent.com/denilsonsa/arandr-indicator/master/arandr-indicator.py) and save it anywhere.
3. `chmod +x arandr-indicator.py` to make it executable.
4. `./arandr-indicator.py` to execute it.
5. Add it to autostart, so it runs whenever you login.


Credits
-------

The need for this tool started with my girlfriend.

The code organization was inspired by [indicator-chars](https://github.com/tobyS/indicator-chars), written by [Tobias Schlitt](mailto:toby@php.net).


Further hints and tips
----------------------

Since the files in `~/.screenlayout/*.sh` are just shell scripts, they can do more than calling `xrandr` to setup the monitors. They can also configure PulseAudio to redirect audio to the HDMI port. Try the following commands:

* To set audio output to HDMI: `pacmd set-card-profile 0 output:hdmi-stereo+input:analog-stereo`
* To set audio output to analog speakers: `pacmd set-card-profile 0 output:analog-stereo+input:analog-stereo`
* To see the available cards and profiles in your system: `pacmd list-cads`
* Nice GUI to configure PulseAudio: `pavucontrol`

Read more:

* https://wiki.archlinux.org/index.php/PulseAudio/Examples
* http://askubuntu.com/questions/63599/configuring-hdmi-audio-via-command-line
* http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line
