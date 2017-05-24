## Chinese fonts in Debian

I have been following https://www.blackmoreops.com/2014/07/31/install-fonts-on-linux/ (accessed 20170524).

 1. Copy fonts to `/usr/share/fonts`. I am trying to use the TrueType [HanaMin 花園明朝 fonts](www.fonts.jp/hanazono/), so I have copied them into `/usr/share/fonts/truetype/hanamin`. Other possible locations are
 
    * `/usr/share/X11/fonts`
    * `/usr/local/share/fonts`
    * `~/.fonts`
 
 1. `fc-cache -fv`: Build font information cache files. Confirm that the fonts have been made available using `fc-list`.
 1. `sudo dpkg-reconfigure fontconfig-config`: Allow system to configure fonts.

**20170328: I have not yet dealt with fonts and so far don't feel the need to do so.**

 * ttf-ancient-fonts
 * fonts-arphic-uming fonts-arphic-ukai
 * [xfonts-intl-chinese](https://packages.debian.org/search?keywords=xfonts-intl-chinese)
 * [note on selective anti-aliasing](https://gideontsang.wordpress.com/2007/07/16/chinese-fonts-in-linux-blur-when-antialias-is-true/)
 * [fonts in Debian](https://wiki.debian.org/Fonts)
 * [2005 post](http://forums.debian.net/viewtopic.php?f=6&t=2563) on Chinese font-problems in Linux
    
[end]
