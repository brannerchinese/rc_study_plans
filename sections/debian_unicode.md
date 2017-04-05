## Debian and Unicode

 * `showconsolefont`: outputs the current console font to stdout. The option -v prints additional information, while the option -V prints the program version number. On Linux 2.6.1 and later, the option -C allows one to indicate the console involved. Its argument is a path-name.
 
   Without any arguments we get error: "Couldn't get a file descriptor referring to the console"

 * Running `sudo dpkg-reconfigure console-setup` puts me through choices for language support, but Chinese is not offered and Unicode is still not supported. Perhaps we must reboot first.

 * `$LOCALE` is not yet set -- how do we set it?

[end]
