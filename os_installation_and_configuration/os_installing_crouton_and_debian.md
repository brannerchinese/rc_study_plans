## Steps in installing Crouton and Debian on Acer Chromebook for Work

Choose Chromebook model from [this list](http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices). I was brought to [this page for generic models](http://www.chromium.org/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/generic).

 * Invoke "Recovery mode" by holding down ESC and "Refresh" (F3) keys and quickly press the Power button. Keep ESC and F3 held down until you see a mostly white screen that is not the normal Chromebook start-up screen.
 * Press `ctrl-d` and you should see a message about pressing ENTER to turn off OS verification and restart the system.
 * Hit Return and press `ctrl-d` again. You should be taken to a white screen that says "Preparing system for Developer Mode." This process takes many minutes but the machine will eventually restart.
 * When it restarts you will seem to be booting into the regular Chrome desktop, but after start-up and log-in are complete, hitting `ctrl-alt-t` will bring up `crosh`, the Chrome OS developer shell.
 * (In the future, when you switch between standard Chrome and Developer Mode, you will see a message "Your system is transitioning to Developer Mode", and then "Preparing system for Developer Mode.")

Download Crouton using the browser.

In the developer shell, enter `shell` to bring up a real shell.

To install Debian (rather than Ubuntu, which is the default) type

```bash
sh ~/Downloads/crouton -r debian -t kde -n debian
```

[end]