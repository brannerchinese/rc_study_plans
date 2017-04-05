## Notes on Chromebook chrooted Debian installation

### Chrome OS preparation

 1. Activate "developer mode" by holding down ESC and REFRESH and then briefly pressing the power button; once a white screen is displayed, press `ctrl-d` to bring up another white screen; then hit ENTER and developer mode should begin to be activated. When the computer beeps, press `ctrl-d` again to reboot -- on this reboot, developer mode will be activated.

 1. Open Chrome "shell" (Crosh, highly restricted pseudo-shell) with `ctrl-alt-t`. Enter `shell` to get basic native ChromeOS prompt.

 1. Add some basic tools to `~/.bashrc`:

    ```bash
    export EDITOR=vi
    export HISTSIZE=''
    set -o vi
    alias d='sudo enter-chroot -n debian' # This line should be removed.
    alias i3='sudo enter-chroot -n debian-i3 xinit'
    ```

 1. Create a user password, using `passwd`.

### Debian installation

 1. Download Crouton (to ~/Downloads) by pointing Chrome browser to https://goo.gl/fd3zc.

 1. Do initial installation. Note that Debian `stretch` is needed; `jessie` seems to have a bug that prevents i3 (initially part of my installation) from opening in Debian under the current version of Chrome OS:

    ```bash
    sudo sh ~/Downloads/crouton -n debian-i3 -r stretch -t x11,extension,keyboard,cli-extra,gtk-extra
    ```

    (Source: http://craig-russell.co.uk/2015/07/13/cromebook-debian-i3.html, accessed 20170303.)
    
    But if we are doing Ubuntu, use:

    ```bash
    sudo sh ~/Downloads/crouton -n ubuntu -t x11,extension,keyboard,cli-extra,gtk-extra,xfce
    ```

    In either case, you will be asked for a password if you have not already set one up.

    When the installation is correct, the script finishes:
    
    > Here's some tips:
    > 
    > Audio from the chroot will now be forwarded to CRAS (Chromium OS audio server),
    > through an ALSA plugin.
    > 
    > Future Chromium OS upgrades may break compatibility with the installed version
    > of CRAS. Should this happen, simply update your chroot.
    > 
    > You can flip through your running chroot desktops and Chromium OS by hitting
    > Ctrl+Alt+Shift+Back and Ctrl+Alt+Shift+Forward.
    > 
    > You must install the Chromium OS extension for integration with crouton to work.
    > The extension is available here: https://goo.gl/OVQOEt
    > 
    > You can start a shell in a new VT via the startcli host command: sudo startcli
    > 
    > Unmounting /mnt/stateful_partition/crouton/chroots/debian-i3...
    > Done! You can enter the chroot using enter-chroot.

### Chrooted Linux Environment

 1. Enter the chroot by means of the `d` alias added to the Chrome OS earlier.

 1. Add some basic tools to `~/.bashrc`:

    ```bash
    export EDITOR=vi
    export HISTSIZE=''
    export TERM='xterm-256color' # We use `xterm` even though xfce4 is what we are installing.
    set -o vi
    export LANG=en_US.UTF-8
    export LOCALE=UTF-8
    ```

 1. Configure `/etc/default/keyboard`:

    ```
    XKBMAP="chromebook"
    ```

 1. Configure `~/.xinitrc`:

    ```
    exec i3
    setkxbmap -layout us
    ```

 1. How to configure `i3`? According to the [User Guide](https://i3wm.org/docs/userguide.html):
 
    > Note that when starting i3 without a config file, i3-config-wizard will offer you to create a config file in which the key positions (!) match what you see in the image above, regardless of the keyboard layout you are using. If you prefer to use a config file where the key letters match what you are seeing above, just decline i3-config-wizard’s offer and base your config on `/etc/i3/config`.

 1. Configure `~/.config/i3/config` (or whatever other config file is set up for `i3`), adding this to replace the "nagbar" line:

    ```
    bindsym $mod+Shift+e exit
    ```

 1. Configure `git`:
    
    ```
    git config --global user.name <string>
    git config --global user.email "username@users.noreply.github.com"
    git config --global core.excludesfile '~/.gitignore'
    ```
    
    Populate `~/.gitignore` with:
    
    ```
    **~
    **.swp
    **.swo
    **.db
    ```

 1. Generate a new public SSH key for the new installation and add it to the appropriate GitHub accounts so that needed repositories can be cloned.

### Software for Chrooted Linux

 1. In the Linux chroot, install

    * `git firefox-esr-dev curl`: If Ubuntu, use plain `firefox` instead of `firefox-esr-dev`.
    * `xfce4-terminal`: Apparently provides the best terminal emulator.
    * `xclip`: Copy command-line to/from clipboard.
    * `vim i3`
    * `trash-cli` See installations details at https://github.com/andreafrancia/trash-cli.

 1. Clone the [vim_configuration repo](https://github.com/brannerchinese/vim_configuration) and configure following instructions there.

 1. Clone the `rc_study_plans` repo, which includes the present file.

    In the Chrome OS, create a symlink to that file, so that it can be accessed outside of the chroot (below, assuming `dpb` is the your username.

    ```bash
    ln -s /mnt/stateful_partition/crouton/chroots/debian-i3/home/dpb/repos_rc_study_plans/sections notes
    ```

    Make a similar symlink in Debian.

### Software for Chrome OS

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
```

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

    To `/etc/locale.gen/` add

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

    I installed `debconf` and then had `dpkg-reconfigure` available. This should eventually be added to list of packages to add.

[end]
