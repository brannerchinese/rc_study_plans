## Ubuntu Installation

On 20170405 I installed Ubuntu in a chroot, parallel to Debian, in order to explore configuration problems on Debian by comparison. I left only the following note.

### Locale

 * Using `export LOCALE=UTF-8` gives error `xfce4-terminal-WARNING **: Locale not supported by C library.` when `i3` runs. We can list available locales via `locale -a`, and I think `C.UTF-8` is to be preferred.

[end]
