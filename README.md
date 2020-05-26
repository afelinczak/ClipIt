Introduction
===============================================================================

ClipIt is a lightweight GTK+ clipboard manager.

This repository is a fork for building patched version for ppa.
 
Project website: https://github.com/CristianHenzel/ClipIt


ClipIt - Lightweight GTK+ Clipboard Manager
===============================================================================

Copyright (C) 2010-2019 by Cristian Henzel <oss@rspwn.com>

Copyright (C) 2011 by Eugene Nikolsky <pluton.od@gmail.com>

forked from parcellite, which is

Copyright (C) 2007-2008 Gilberto "Xyhthyx" Miralla <xyhthyx@gmail.com>


How to compile and install clipit
===============================================================================


#### Requirements:
* gtk+ >= 2.10.0 (>= 3.0 for gtk+3)
* xdotool - for automatic paste functionality

sudo apt-get install build-essential git automake xdotool autoconf intltool autopoint checkinstall gtk+-3.0

#### Download the clipit source code, then:
    tar zxvf clipit-x.y.z.tar.gz
    cd clipit-x.y.z
    ./autogen.sh
    ./configure --with-gtk3 
    make
    sudo checkinstall

Documentation
===============================================================================

#### Default keybindings:

| Action       | Key combination |
| ------------ | --------------- |
| History      | Ctrl + Alt + h  |
| Actions      | Ctrl + Alt + a  |
| Menu         | Ctrl + Alt + p  |
| Search       | Ctrl + Alt + f  |
| Offline mode | Ctrl + Alt + o  |
