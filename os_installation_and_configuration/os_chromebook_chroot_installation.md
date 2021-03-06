## Notes on Chromebook chrooted Debian installation

### Chrome OS preparation

 1. Activate "developer mode" by holding down ESC and REFRESH and then briefly pressing the power button; once a white screen is displayed, press `ctrl-d` to bring up another white screen; then hit ENTER and developer mode should begin to be activated. When the computer beeps, press `ctrl-d` again to reboot -- on this reboot, developer mode will be activated.

 1. Open Chrome "shell" (Crosh, highly restricted pseudo-shell) with `ctrl-alt-t`. Enter `shell` to get basic native ChromeOS prompt.

 1. Add some basic tools to `~/.bashrc`:

    ```bash
    export EDITOR=vi
    export HISTSIZE=''
    set -o vi
    alias d='sudo enter-chroot -n debian'
    ```

    Note that after Maté is installed and configured, `xinit` can be added to the `d` alias, so that Maté starts up immediately. But doing this seems to prevent Unicode input (using `ctrl-U` followed by the codepoint) from working correctly in Vim, so I am not doing it.

 1. Create a user password, using `passwd`.

### Debian installation

 1. Download Crouton (to ~/Downloads) by pointing Chrome browser to https://goo.gl/fd3zc.

 1. Do initial installation. Note that Debian `stretch` is needed; `jessie` seems to have a bug that prevents i3 (initially part of my installation) from opening in Debian under the current version of Chrome OS:

    ```bash
    sudo sh ~/Downloads/crouton -n debian -r stretch -t x11,extension,keyboard,cli-extra,gtk-extra
    ```

    (Source: http://craig-russell.co.uk/2015/07/13/cromebook-debian-i3.html, accessed 20170303.)

    You will be asked for a password if you have not already set one up.

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

 1. In the Linux chroot, install the following packages:

    * `vim git firefox-esr-dev curl`
    * `software-properties-common dirmngr`: The former includes `apt-add-repository`, needed for adding a Personal Package Archive (PPA). The latter is a dependency of `apt-add-repository`.
    * `mate-desktop mate-desktop-environment*`: Currently chosen desktop and all environment files.
    * `xfce4-terminal`: "XForms Common Environment". Apparently provides the best terminal emulator.
    * `rxvt-unicode-256color`: "ouR X Virtual Terminal, unicode". Recommended by Saul Pwanson for best font-control in a terminal emulator.
    * `xclip`: Copy command-line to/from clipboard.
    * `trash-cli`: See [installation details](https://github.com/andreafrancia/trash-cli).
    * `ibus ibus-qt4 ibus-gtk ibus-chewing ibus-libzhuyin ibus-m17n ibus-pinyin ibus-libpinyin`
    * `torbrowser-launcher`
    * `tree`
    * `reportbug`: Needed to report unexpected behavior on upgrade of`xorg`.
    * `emacs`
    * `python3 python3-venv`
    * `debconf`: Make available `dpkg-reconfigure` (which is only accessible with root permissions).

    * For Firefox:

      ```
      sudo apt install pkg-mozilla-archive-keyring
      sudo apt-add-repository ppa:mozillateam/firefox-next
      ```

      In addition, a GPG key is needed; this still has to be done and docmented.
    
    * For Google Chrome:

      Following http://www.tecmint.com/install-google-chrome-in-debian-ubuntu-linux-mint/ (accessed 20170403).
      
      ```
      wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
      sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
      sudo apt-get update
      sudo apt-get install google-chrome-stable
      ```


 1. Add some basic tools to `~/.bashrc`:

    ```bash
    export EDITOR=vi
    export HISTSIZE=''
    export TERM='xterm-256color' # We use `xterm` even though xfce4 is what we are installing.
    set -o vi
    export LANG=en_US.UTF-8
    export LOCALE=C.UTF-8

    # For Mate
    export GTK_IM_MODULE=ibus
    export XMODIFIERS=@im=ibus
    export QT_IM_MODULE=ibus
    ```

 1. Keep from dropping SSH connections

    Edit `.ssh/config` and insert:

    ```
    Host *
       ServerAliveInterval 300
       ServerAliveCountMax 2
    ```

 1. Configure `/etc/default/keyboard`:

    ```
    XKBMAP="chromebook"
    ```

 1. Configure `~/.xinitrc`:

    ```
    exec mate-session
    setkxbmap -layout us
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

 1. Following [GitHub's instructions](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/), enerate a new public SSH key for the new installation and add it to the appropriate GitHub accounts so that needed repositories can be cloned.


### More Software for Chrooted Linux

 1. Fonts will be needed. Right now we are using `fonts-noto-cjk`; can get all available No-Tofu fonts using `sudo apt install fonts-noto-*`. We also had to use `xfontsel fonts-noto-cjk`, but this has not been documented yet.

 1. Make a directory `repos` and `cd` into it; clone all repositories there.

 1. Clone the [vim_configuration repo](https://github.com/brannerchinese/vim_configuration), using `--depth=1` in order to keep the repository small, and configure following instructions there.
 
    Remember to change `.vimrc` to reflect the fact that the repository is located inside `repos`.
    
    Add `:inoremap <C-U> <Nop>`, though I'm not sure if it's needed now.

 1. Clone the `rc_study_plans` repo (using `--depth=1`), which includes the present file.

    In the Chrome OS, create a symlink to that file, so that it can be accessed outside of the chroot (below, assuming `dpb` is the your username.

    ```bash
    ln -s /mnt/stateful_partition/crouton/chroots/debian-i3/home/dpb/repos_rc_study_plans/sections notes
    ```

    Make a similar symlink in Debian.

### Desktop environment

 1. Run and set up `Maté`

    I am using `Maté` because earlier efforts to use `i3` and to avoid using a desktop at all ran into problems with Unicode support and Chinese input method support. These are described in a [separate document](what_went_wrong_with_i3_and_chrome_terminal_tabs.md)

    Set up background and Terminal. 

    For background, go to `System => Preferences => Look and Feel => Appearance`
    
    For terminal, go to `System =>  Preferences =>  Personal => Startup Application` and add:

    * `xfce4-terminal`

    I use `xfce4` rather than the `Maté` Terminal becaus copying and pasting seems to work better and because accented characters cause the font fewer problems when I'm in Vim.
    
    The terminal can be configured with `xfce4-settings-manager` and there are related commands. Configure it to use Noto Sans Mono CJK TC Reg 14 font. 
    
    Need to find a font-spread that supports Upper code-points. Must look into what fonts are actually needed and what characters a font supports, see http://stackoverflow.com/questions/4458696/finding-out-what-characters-a-font-supports.

 1. Within `Maté` set up IBus

    For IBus, go to `System =>  Preferences =>  Personal => Startup Application` and add:

    * `ibus-daemon`

    As long as `ibus-daemon` runs first (and it must run in `Maté`, not in the Chrome terminal tab before `Maté` starts), then IBus is running. You can run `ibus-setup` from thee command line or you can select `System => Preferences => Other => IBus preferences`, to configure. set "Next input method" to `<Control>space`. IBus is not ideal, because the characters in the selection panel are very small, but it's usable.
    
 1. `Maté` configuration
 
    The configuration file is in `~/.config/dconf` and can be accessed with `dbus dump <path>` and installed with `dbus load`.
    
 1. Chinese fonts
 
    See the [separate page on Chinese fonts in Debian](os_debian_fonts.md).

 1. Configure locales for UTF-8

    * To `/etc/locale.gen/` add

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

    * Install `locales` with `apt` and run `/usr/sbin/locale-gen` as root.
    
    * Run `dpkg-reconfigure locales` and follow the directions.



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

[end]
