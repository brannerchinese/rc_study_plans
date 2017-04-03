## Use the Chrome OS built-in browser to open local files

 1. There is an extension "Local Explorer" designed to access the file system and open files. "LocalLinks" may be another option. 

 1. `ctrl-o` opens a limited file-system browser modal, showing Google Drive, Downloads and (currently) an installed SD card. Traversing the full file system doesn't seem possible.

 1. Experiment with the file URI scheme. Not only can the chroot's file system not be accessed by the browser, but the file system of the Chrome OS shell user (chronos) also cannot. E.g., `file:///home/chronos/<hash>/Downloads/<file>` works, but the hash seems to be required and files outside of `Downloads` cannot be opened. This doesn't seem to be a matter of file permissions, since Downloads can be accessed while Lnks cannot, and permissions and groups are as follows.

    ```
    drwx--x---.  2 chronos chronos-access 4.0K Apr  3 11:45 Downloads
    drwx--x---.  2 chronos chronos-access 4.0K Apr  3 11:43 Lnks
    ```

    The error is "ERR_ACCESS_DENIED".

    I've also tried creating a symbolic link to Lnks within Downloads; the error is "ERR_FILE_NOT_FOUND". The same is true with the link's group set to `root` rather than `chronos`. Running `chgrp` on the symbolic link fails without an explicit explanation, even with root access. Anyway, the user `chronos` is a member of chronos-access, so if chronos can't change the link's owner, there must be something else going on. And `usermod` is unknown to `chronos`.

 1. Experiment with `localhost` or 127.0.0.1; but this requires running a server. What I am trying to do is open HTML files.

 1. Starting Chrome with `--allow-file-access-from-files` set is said to work. But that apparently doesn't apply to the built-in browser in Chrome OS.

 1. Simple solutions: 
 
    * Move everything I want to access into Downloads. Result: is indeed accessible.
    * Install browsers in the chroot.
                                              

[end]
