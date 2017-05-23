After a recent upgrade of `xorg` and `xorg-server` I find the Maté desktop no longer loads.

The error message looks like this:


```
$ xinit

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root

X.Org X Server 1.19.2
Release Date: 2017-03-02
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.16.0-4-amd64 x86_64 Debian
Current Operating System: Linux localhost 3.18.0-13985-g8bf2eb2 #1 SMP PREEMPT Wed May 10 18:47:50 PDT 2017 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 3584000 verity payload=PARTUUID=ced5a43b-0938-474f-a512-e31a5c04d43f/PARTNROFF=1 hashtree=PARTUUID=ced5a43b-0938-474f-a512-e31a5c04d43f/PARTNROFF=1 hashstart=3584000 alg=sha1 root_hexdigest=acba5490b0c9fdc4f630ae704141e67910d16dc8 salt=d06ac551a951f2ac038486c9ca001398ea49f33918501caf0fdb3b343389d507" noinitrd vt.global_cursor_default=0 kern_guid=ced5a43b-0938-474f-a512-e31a5c04d43f add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic intel_idle.max_cstate=7  
Build Date: 03 March 2017  03:14:41PM
xorg-server 2:1.19.2-1 (https://www.debian.org/support) 
Current version of pixman: 0.34.0
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Mon May 22 20:31:01 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error:
(EE) parse_vt_settings: Cannot open /dev/tty0 (No such file or directory)
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: Connection refused
/usr/bin/xinit: server error
```

Running `sudo apt upgradeable` returned

```
xorg/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
xserver-xorg/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
xserver-xorg-input-all/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
```

(All other upgrades had been done manually, and `xinit` loaded the Maté desktop, which ran without a hitch. On `sudo apt --only-upgrade install xorg` and then logging out, `xinit` then produced the error message above.
