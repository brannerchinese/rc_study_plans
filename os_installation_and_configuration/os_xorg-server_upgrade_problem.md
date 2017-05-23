I am running Debian release 9.0 "stretch" in a chroot, populated via Crouton, on a Chromebook. Debian has been loading satisfactorily, and I have been using the Maté desktop without obvious problems.

After a recent upgrade of `xorg` and `xorg-server` I find the Maté desktop no longer loads.

The first error line is `parse_vt_settings: Cannot open /dev/tty0 (No such file or directory)`. Before the upgrade, we already have a file `/dev/tty` but no `/dev/tty0`, so I created a symbolic link from `/dev/tty0` to `/dev/tty`. After that, and after upgrading, the error became `parse_vt_settings: Cannot find a free VT: Inappropriate ioctl for device`. 

The error message is as below:


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

Normally, running `xinit` looks like this:

```
xinit

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
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Mon May 22 20:50:19 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
method return time=1495500620.273049 sender=:1.13 -> destination=:1.299 serial=3917 reply_serial=2
   boolean true
crouton: version 1-20170315143304~master:95589555
release: stretch
architecture: amd64
xmethod: xorg
targets: x11,extension,keyboard,cli-extra,gtk-extra
host: version 9334.69.0 (Official Build) stable-channel lars 
kernel: Linux localhost 3.18.0-13985-g8bf2eb2 #1 SMP PREEMPT Wed May 10 18:47:50 PDT 2017 x86_64 GNU/Linux
freon: yes

(process:22673): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root
gnome-keyring-daemon: insufficient process capabilities, unsecure memory might get used
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
mate-session[22673]: WARNING: Unable to find provider '' of required component 'dock'

(process:22709): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Window manager warning: Locale not understood by C library, internationalization will not work

(marco:22713): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(mate-panel:22730): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Window manager warning: Log level 16: g_object_set_valist: object class 'MetaFrames' has no property named 'type'
[1495500623,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the application

(caja:22754): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(process:22761): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
gnome-keyring-daemon: insufficient process capabilities, unsecure memory might get used

(process:22764): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(polkit-mate-authentication-agent-1:22761): polkit-mate-1-WARNING **: Unable to determine the session we are in: No session for pid 22761
/usr/bin/xbindkeys_autostart: line 24: CONF: unbound variable

(process:22760): xfce4-terminal-WARNING **: Locale not supported by C library.
GNOME_KEYRING_CONTROL=/home/dpb/.cache/keyring-984J0Y
SSH_AUTH_SOCK=/home/dpb/.cache/keyring-984J0Y/ssh

(mate-power-manager:22772): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(process:22760): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
gnome-keyring-daemon: insufficient process capabilities, unsecure memory might get used
GNOME_KEYRING_CONTROL=/home/dpb/.cache/keyring-984J0Y
SSH_AUTH_SOCK=/home/dpb/.cache/keyring-984J0Y/ssh
gnome-keyring-daemon: insufficient process capabilities, unsecure memory might get used
GNOME_KEYRING_CONTROL=/home/dpb/.cache/keyring-984J0Y
SSH_AUTH_SOCK=/home/dpb/.cache/keyring-984J0Y/ssh

(process:22797): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
TI:20:50:23     TH:0x564deffa4590       FI:gpm-manager.c        FN:gpm_manager_systemd_inhibit,1754
 - Error connecting to dbus - Error calling StartServiceByName for org.freedesktop.login1: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback:
        mate-power-manager(+0x1900f) [0x564def93f00f]
        mate-power-manager(+0x11dcc) [0x564def937dcc]
        /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x20b) [0x7a6e4c35c36b]
        /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x151fb) [0x7a6e4c33e1fb]
        /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x1dd) [0x7a6e4c33fc0d]
        /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_new+0x104) [0x7a6e4c3403c4]
        mate-power-manager(+0x120e2) [0x564def9380e2]
        mate-power-manager(+0x7c42) [0x564def92dc42]
        /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf1) [0x7a6e4b7762b1]
        mate-power-manager(+0x7fba) [0x564def92dfba]
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
Initializing caja-image-converter extension

(blueman-applet:22781): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Initializing caja-open-terminal extension
** Message: Initializing gksu extension...
blueman-applet version 2.0.4 starting

(xfce4-terminal:22760): Gtk-WARNING **: Allocating size to GtkScrollbar 0x5ef9fda864b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 175, in activate_name_owner
    return self.get_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 361, in get_name_owner
    's', (bus_name,), **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.bluez': no such name

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/blueman-applet", line 121, in <module>
    BluemanApplet()
  File "/usr/bin/blueman-applet", line 63, in __init__
    self.Plugins.Load()
  File "/usr/lib/python3/dist-packages/blueman/main/PluginManager.py", line 90, in Load
    __import__(self.module_path.__name__ + ".%s" % plugin, None, None, [])
  File "/usr/lib/python3/dist-packages/blueman/plugins/applet/DBusService.py", line 12, in <module>
    from blueman.main.applet.BluezAgent import AdapterAgent
  File "/usr/lib/python3/dist-packages/blueman/main/applet/BluezAgent.py", line 23, in <module>
    from blueman.bluez.Agent import Agent, AgentMethod
  File "/usr/lib/python3/dist-packages/blueman/bluez/Agent.py", line 48, in <module>
    class Agent(dbus.service.Object):
  File "/usr/lib/python3/dist-packages/blueman/bluez/Agent.py", line 56, in Agent
    @AgentMethod
  File "/usr/lib/python3/dist-packages/blueman/bluez/Agent.py", line 38, in AgentMethod
    if BlueZInterface.get_interface_version()[0] < 5:
  File "/usr/lib/python3/dist-packages/blueman/bluez/BlueZInterface.py", line 16, in get_interface_version
    obj = dbus.SystemBus().get_object('org.bluez', '/')
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python3/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1

(mate-panel:22730): Gtk-WARNING **: Allocating size to PanelToplevel 0x5cc90c539ef0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?

(process:22954): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
mate-session[22673]: WARNING: Could not connect to Systemd: Could not get owner of name 'org.freedesktop.login1': no such name
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
Running exit commands...
/usr/bin/xinit: connection to X server lost

waiting for X server to shut down Hangup
Hangup
Hangup
method return time=1495500629.171478 sender=:1.13 -> destination=:1.300 serial=3919 reply_serial=2
   boolean true
(II) Server terminated successfully (0). Closing log file.

```

Running `sudo apt list upgradable` before the problem installation returned:

```
xorg/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
xserver-xorg/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
xserver-xorg-input-all/testing 1:7.7+19 amd64 [upgradable from: 1:7.7+18]
```

(All other upgrades had been done manually, and `xinit` loaded the Maté desktop, which ran without a hitch. On `sudo apt --only-upgrade install xorg` and then logging out, `xinit` then produced the error message above.
