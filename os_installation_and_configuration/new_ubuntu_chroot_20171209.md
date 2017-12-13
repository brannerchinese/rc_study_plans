## New Ubuntu chroot, 20171212

### Desktop

The best choice at present is Ubuntu with Unity. This is the least interesting options, but Chinese is the best supported here. Install with

```
sudo sh ~/Downloads/crouton -n unity -t unity
```

Software to install:

```
vim firefox tree xfce4-terminal
rxvt-unicode-256color
xclip
trash-cli
torbrowser-launcher
```

Follow other instructions from Spring, 2017.

**Important**: in order to get the Terminal to respect Unicode, you must adjust the locales.

```
$ locale -a                       # List available locales 
C
C.UTF-8
POSIX
$ sudo locale-gen en_US.UTF-8     # Must generate en_US.UTF-8
Generating locales (this might take a while)...
  en_US.UTF-8... done
Generation complete.
$ sudo update-locale LANG=en_US.UTF-8 LANGUAGE=en.UTF-8
$ locale -a                       # Now we should be able to display Unicode
C
C.UTF-8
en_US.utf8
POSIX
```


Enter using:

```
sudo startunity
```

Don't forget to create an alias (such as `g`).

### CLI along with desktop

Install `crouton integration` extension in Chrome browser.

Update crouton:

```
sudo sh ~/Downloads/crouton -u -n unity -t extension,xiwi,cli-extra
```

(Most recently, omitted `extension` and `xiwi`, because desktop doesn't load properly. Also omitted Chinese packages.

Enter using:

```
sudo startcli -n unity
```

Don't forget to create an alias (such as `gcli`).

[end]
