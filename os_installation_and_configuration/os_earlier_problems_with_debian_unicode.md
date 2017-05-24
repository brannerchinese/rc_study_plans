## Debian and Unicode

This page describes some issues early in installation. I have resolved them, however.

### Possible xterm problem

 * Possibly `xterm` itself doesn't allow non-ASCII input. See http://unix.stackexchange.com/questions/280466/how-do-i-type-arbitrary-unicode-characters-in-xterm (201605). Are there other terminal emulators to use? https://lists.freebsd.org/pipermail/freebsd-questions/2010-March/213717.html suggests rxvt-unicode.

 * "gucharmap and UMap are tools to select and paste any Unicode character into your application." (https://www.cl.cam.ac.uk/~mgk25/unicode.html). Under section "UTF-8 cut and paste" it seems there are still problems with this.

 * See `xterm` FAQ: http://invisible-island.net/xterm/xterm.faq.html#xterm_select_clipboard.

### Possible Debian problem

 * Error described for Debian in 201402 and reported still current in 201602. Non-ASCII characters pasting in correctly (https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=737989).

### Possible Chrome OS problem.

 * `showconsolefont`: outputs the current console font to stdout. The option -v prints additional information, while the option -V prints the program version number. On Linux 2.6.1 and later, the option -C allows one to indicate the console involved. Its argument is a path-name.
 
   Without any arguments we get error: "Couldn't get a file descriptor referring to the console". Using option `-C` and various `tty` values (`tty0`, `tty7`, etc.) it says it can't open that console.

### Possible configuration problem

 * Running `sudo dpkg-reconfigure console-setup` puts me through choices for language support, but Chinese is not offered and Unicode is still not supported. Perhaps we must reboot first.
 
   On reboot, still does not accept upper ASCII.

   Also run `sudo dpkg-reconfigure fontconfig-config`, but this does not involve CJK, either.

 * `$LOCALE` is not yet set -- how do we set it?

   Added `export` lines to `.bashrc`:

   ```
   export LANG=en_US.UTF-8
   export LOCALE=UTF-8
   ```

   and now some upper ASCII and other Unicode characters appear correctly if they are already in a file (though not all of them), but not those input. 

### Fonts

 * To list installed packages, use `dpkg-query -l`. Fonts installed via `apt`:

   * `fonts-noto-cjk`: "No Tofu" font families with large Unicode coverage (CJK)
   * `xfonts-intl-chinese`: International fonts for X -- Chinese
   * `xfonts-intl-chinese-big`: International fonts for X -- large Chinese
   * `fonts-arphic-bkai00mp`: "AR PL KaitiM Big5" Chinese TrueType font by Arphic Technology
   * `fonts-arphic-bsmi00lp`: "AR PL Mingti2L Big5" Chinese TrueType font by Arphic Technology
   * `fonts-arphic-gbsn00lp`: "AR PL SungtiL GB" Chinese TrueType font by Arphic Technology
   * `fonts-arphic-gkai00mp`: "AR PL KaitiM GB" Chinese TrueType font by Arphic Technology
   * `fonts-vlgothic`: Japanese TrueType font from Vine Linux

 * How do we determine what font is used in the terminal?

[end]
