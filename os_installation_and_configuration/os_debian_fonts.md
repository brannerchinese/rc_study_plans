## Chinese fonts in Debian

### Current installation instructions

I have been following https://www.blackmoreops.com/2014/07/31/install-fonts-on-linux/ (accessed 20170524).

 1. First, for clarity, I removed all other CJK fonts.
 1. Copy fonts to `/usr/share/fonts`. I am trying to use the TrueType [HanaMin 花園明朝 fonts](www.fonts.jp/hanazono/), so I have copied them into `/usr/share/fonts/truetype/hanamin`. Other possible locations are
 
    * `/usr/share/X11/fonts`
    * `/usr/local/share/fonts`
    * `~/.fonts`
 
 1. `fc-cache -fv`: Build font information cache files. Confirm that the fonts have been made available using `fc-list`.
 1. `sudo dpkg-reconfigure fontconfig-config`: Allow system to configure fonts.
 1. Then reboot.

At this point, I have two slightly different fonts displaying all high and low CJK codepoints I'm aware of, within the terminal running on the Maté desktop, but not in the Crosh shell window.

Problems:

 1. How to get high codepoints to display in the Crosh shell winow? That probably requires the font to be added to Chrome rather than the Debian chroot.
 1. High codepoint characters are being displayed in a serifed font that is probably HanaMin, but those in the Basic Multilingual Plane appear in a non-serif font, and the mismatch is noticeable. 
 2. Also, it appears that even normal ASCII text is now (20170524) being displayed in the same font as the Basic Multilingual Plane characters, and so there are kerning issues.

What other fonts should I try to resolve these issues?

### Other

 * Fonts to be considered
 
   * [Quivera](http://www.quivira-font.com/), described here: http://www.metafilter.com/110330/Quivera-a-fairly-complete-Unicode-font)
   * [GNU FreeFont](http://www.gnu.org/software/freefont/). Not for CJK but for most other things.
   * [Source Han Super OTC](https://github.com/adobe-fonts/source-han-super-otc)

 * Fonts available through `apt`:

   * ttf-ancient-fonts
   * fonts-arphic-uming fonts-arphic-ukai
   * [xfonts-intl-chinese](https://packages.debian.org/search?keywords=xfonts-intl-chinese)

 * Reference:
 
   * [note on selective anti-aliasing](https://gideontsang.wordpress.com/2007/07/16/chinese-fonts-in-linux-blur-when-antialias-is-true/)
   * Overview of tools: [Fonts in Debian](https://wiki.debian.org/Fonts)
   * [2005 post](http://forums.debian.net/viewtopic.php?f=6&t=2563) on Chinese font-problems in Linux
    
[end]
