## Things learned about Debian

 * `dpkg-query -l`: list installed packages
 * `sudo apt list --upgradable`: Get list of all packages to be installed, without actually installing them.
 * `sudo apt --only-upgrade install <package>`: Used for upgrading packages individually.
 * Some of the `dpkg-...` tools require root permissions and without root permissions the system will claim the tools are not installed.

[end]
