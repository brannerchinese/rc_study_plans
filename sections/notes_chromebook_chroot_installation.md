## Notes

### Debian installation

Activate "developer mode" by holding down ESC and REFRESH and then briefly pressing the power button; once a white screen is displayed, press `ctrl-d` to bring up another white screen; then hit ENTER and developer mode should begin to be activated. When the computer beeps, press `ctrl-d` again to reboot -- on this reboot, developer mode will be activated.

Open Chrome "shell" (Crosh, highly restricted pseudo-shell) with `ctrl-alt-t`. Enter `shell` to get basic native ChromeOS prompt.

Add some basic tools to `~/.bashrc`:

```bash
export EDITOR=vi
export HISTSIZE=''
set -o vi
alias d='sudo enter-chroot -n debian-i3'
# alias i3='sudo enter-chroot -n debian-i3 xinit' # Note 20170328: I uninstalled i3; Running separate Debian processes in separate Chrome windows is sufficient for my needs.
```

Create a user password, using `passwd`.

Download Crouton (to ~/Downloads) by pointing Chrome browser to https://goo.gl/fd3zc.

Initial installation (note that Debian `stretch` is needed; `jessie` seems to have a bug that prevents i3 (initially part of my installation) from opening in Debian under the current version of Chrome OS:

```bash
sudo sh ~/Downloads/crouton -n debian-i3 -r stretch -t x11,extension,keyboard,cli-extra,gtk-extra
```

(Source: http://craig-russell.co.uk/2015/07/13/cromebook-debian-i3.html, accessed 20170303.)

You will be asked for a password if you have not already set one up.

### Environment

Enter the chroot by means of the `d` alias added to the Chrome OS earlier.

Add some basic tools to `~/.bashrc`:

```bash
export EDITOR=vi
export HISTSIZE=''
export TERM='xfce4'
set -o vi
```


Configure `/etc/default/keyboard`: (**EDIT**: Is this part of `i3`? If so, delete.)

```
XKBMAP="chromebook"
```

### Software for the chroot

In the chroot, install

 * `git firefox-esr-dev curl`
 * `xfce4-terminal`: Apparently provides the best terminal emulator.
 * `xclip`: Copy command-line to/from clipboard.

Clone the vim_configuration repo: https://github.com/brannerchinese/vim_configuration.

Clone the `rc_study_plans` repo, which includes the present file.

In the Chrome OS, create a symlink to that file, so that it can be accessed outside of the chroot (below, assuming `dpb` is the your username.

```bash
ln -s /mnt/stateful_partition/crouton/chroots/debian-i3/home/dpb/repos_rc_study_plans/sections notes
```

Make a similar symlink in Debian.

### Software for the Chrome OS

It may be possible to use Git outside of developer mode if the [Git-Browser](https://chrome.google.com/webstore/detail/git-browser/cladogmhjppclibenkdbnjcogiaifnbd) Chrome extension is installed. (This has yet to be tested.)

There is a `chromebrew` Ruby script that aims to serve as a _de facto_ package manager.

In order to get `crosh` to run a script automatically, it may be possible to follow the instructions [here](https://groups.google.com/a/chromium.org/d/msg/chromium-os-discuss/rdzA2gfTMWM/KROV8m19wZ0J). However, doing this may put the filesystem at risk of corruption, and I haven't done this yet.

```bash
# 1. Remove rootfs verification
sudo /usr/share/vboot/bin/make_dev_ssd.sh --remove_rootfs_verification #eventually add --partitions n

# 2. Reboot and remount
sudo crossystem dev_boot_signed_only=0
sudo mount -o remount,rw /

# 3. Edit /usr/bin/crosh:
# Add `cmd_shell` right before the `repl` call.

---

## Improvements 20170329

 1. Keep from dropping SSH connections

    Edit `.ssh/config` and insert:

    ```
    Host *
       ServerAliveInterval 300
       ServerAliveCountMax 2
    ```

 2. Configure locales for UTF-8

    To `/etc/locale.gen/ add

    ```
# This file lists locales that you wish to have built. You can find a list
# of valid supported locales at /usr/share/i18n/SUPPORTED. Other
# combinations are possible, but may not be well tested. If you change
# this file, you need to rerun locale-gen.
#
# XXX GENERATED XXX
#
# NOTE!!! If you change this file by hand, and want to continue
# maintaining manually, remove the above line. Otherwise, use the command
# "dpkg-reconfigure locales" to manipulate this file. You can manually
# change this file without affecting the use of debconf, however, since it
# does read in your changes.
    ```

    However, I have no program `dpkg-reconfigure` available.

    Then install `locales` with `apt` and run `/usr/sbin/locale-gen` as root.

[end]
