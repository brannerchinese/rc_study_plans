## Current and Postponed tasks

Postponed tasks are marked [Ｏ].

### To be done immediately

 * [　] Pack fuller mihmaa sheet in bag.

#### EMACS

 * [　] Look at the Emacs introduction in [Clojure for the Brave and True](http://www.braveclojure.com/basic-emacs/), recommended by Stacey and Logan.

#### Environment

 * [　] Learn what the difference between `/dev/tty0` and `/dev/tty` actually is, and why `/dev/tty0` is being sought in the `xorg` upgrade.
 * [　] Get non-ASCII working on the `debian-test` chroot — it doesn't work at all now.

#### Jobs

 * [　] Prepare résumé for technical writing positions.
 * [　] Begin learning Sphinx (http://www.sphinx-doc.org/en/stable/)

#### VisiData


---

### On-going

### Unix knowledge

 * Read in Eric S. Raymond, _The Art of Unix Programming_. [Website](http://www.catb.org/esr/writings/taoup/html/) should allow easy recording of _bon mots_.
 
   * 20170522: Have reached Sec. 4.4, starting at the beginning.

#### Things learned

 * `shred`
 * `sudo apt list --upgradable`
 * `sudo apt --only-upgrade install <package>`

---

### Done

#### RC people

 * [Ｘ] Ask Alex Leeds if he would meet Sean Travis Taylor. (20170522) Done, and Alex's details conveyed to Sean.
 * [Ｘ] Signed up for in-person check-ins and mentioned in the Zulip `checkins` stream. (20170522). Parthiv and Logan Buckley showed up the first day (20170523) and I described to them something of the history of check-ins and 

#### VisiData

 * [Ｘ] Reported errors installing VisiData via `git` cloning and via `pip` on Debian. (20170523) On the possibility that the problem is due to my Debian installation, am considering trying an Ubuntu/Python3.4 Vagrant container on my Mac. (Later:) Vagrant now has trouble working with VirtualBox, so that option was not possible. However, I tried using an Ubuntu installation on a remote server and on Mac OS 10.9.5 itself. Neither the version cloned from Git (`develop` or `stable` branches) or the version installed by `pip` worked. Finally, only the `testpypi` version (`pip install -i https://testpypi.python.org/pypi visidata`) worked correctly. 
 * [Ｘ] Get Chinese data suitable for use by VisiData. (20170522-23). 
 * [Ｘ] Issue posted to VisiData GitHub account about the low visibility of `curses.BLUE`. (20170521)

#### Environment

 * [Ｘ] Install `reportbug` and report the `xorg` issue. (20170523) Done — had to use `-y` option on installation, because `crosh` terminal window suddenly would not accept `CR` to confirm apt installation. 
 * [Ｘ] Documented Maté problem, showing that it is the upgrading of `xorg` and `xserver-xorg` from v. 7.7+18 to v. 7.7+19 that causes an error when looking for `/dev/tty0`. (20170522) Learned about using `sudo apt list --upgradable` and then `sudo apt --only-upgrade install <package>` for selective Debian upgrades.

#### EMACS

 * [Ｘ] Retrieve old EMACS notes and find recommended EMACS intro. (20170522)

#### Jobs

 * [Ｘ] Lunch conversation with TwoSigma technical writer. (20170523) Relatively more technical contracting position may be available right now; will hear back. Discussed some ethical issues with RMKA.

---

### Summary of the break between the two halves of my batch

(From my diary)

> I have had a two-week break in the midst of my batch. I gained a lot from it — one thing I did was to transcribe the whole _Tsyrchyuan_ of Yang Shuhdar (all the definitions), which meant that I read the whole thing carefully. The other was to put my RC experience in better focus — both the MongoDB interview experience and Nancy's suggestion that I take Myer-Briggs had a big effect on me.



---

[end]
