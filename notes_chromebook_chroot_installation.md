## Notes

### Debian installation

Activate "developer mode" by holding down ESC and REFRESH and then briefly pressing the power button; once a white screen is displayed, press `ctrl-d` to bring up another white screen; then hit ENTER and developer mode should begin to be activated. When the computer beeps, press `ctrl-d` again to reboot -- on this reboot, developer mode will be activated.

Open Chrome "shell" (Crosh, highly restricted pseudo-shell) with `ctrl-alt-t`. Enter `shell` to get basic native ChromeOS prompt.

Add some basic tools to `~/.bashrc`:

```bash
export EDITOR=vi
export HISTSIZE=''
set -o vi
alias i3='sudo enter-chroot -n debian-i3 xinit'
```

Create a user password, using `passwd`.

Download Crouton (to ~/Downloads) by pointing Chrome browser to https://goo.gl/fd3zc.

Initial installation (note that Debian `stretch` is needed; `jessie` seems to have a bug that prevents i3 from opening in Debian under the current version of Chrome OS:

```bash
sudo sh ~/Downloads/crouton -n debian-i3 -r stretch -t x11,extension,keyboard,cli-extra,gtk-extra
```

(Source: http://craig-russell.co.uk/2015/07/13/cromebook-debian-i3.html, accessed 20170303.)

You will be asked for a password if you have not already set one up.

### Environment

Enter the chroot by means of the `i3` alias added to the Chrome OS earlier.

Add some basic tools to `~/.bashrc`:

```bash
export EDITOR=vi
export HISTSIZE=''
export TERM='xfce4'
set -o vi
```
Install `i3`:

```bash
sudo apt install i3
```

Configure `.xinitrc`:

```
exec i3
setxkbmap -layout us
```

Configure `/etc/default/keyboard`:

```
XKBMAP="chromebook"
```

Configure `i3` so that no mouseclick is needed to exit, by commenting out the existing line mentioning `exit` and adding to `/mnt/stateful_partition/crouton/chroots/debian-i3/home/dpb/.config/ie/config` the line:

```bash
bindsym $mod+Shift+e exit
```

and restarting.

---

### Software for the chroot

In the chroot, install

 * `git firefox-esr-dev curl`
 * `xfce4-terminal`: Apparently provides the best terminal emulator.
 * `xclip`: Copy command-line to/from clipboard.

Clone the vim_configuration repo: https://github.com/brannerchinese/vim_configuration.

Clone the crouton installation notes file (includes this file).

In the Chrome OS, create a link to that file, so that it can be accessed outside of the chroot (below, assuming `dpb` is the your username.

```bash
ln -s /mnt/stateful_partition/crouton/chroots/debian-i3/home/dpb/crouton_installation_notes/notes.md notes
```

### Software for the Chrome OS

It may be possible to use Git outside of developer mode if the [Git-Browser](https://chrome.google.com/webstore/detail/git-browser/cladogmhjppclibenkdbnjcogiaifnbd) Chrome extension is installed. (This has yet to be tested.)

In order to get `crosh` to run a script automatically, follow the instructions [here](https://groups.google.com/a/chromium.org/d/msg/chromium-os-discuss/rdzA2gfTMWM/KROV8m19wZ0J):

```bash
# 1. Remove rootfs verification
sudo /usr/share/vboot/bin/make_dev_ssd.sh --remove_rootfs_verification #eventually add --partitions n

# 2. Reboot and remount
sudo crossystem dev_boot_signed_only=0
sudo mount -o remount,rw /

# 3. Edit /usr/bin/crosh:
# Add `cmd_shell` right before the `repl` call.

[end]
