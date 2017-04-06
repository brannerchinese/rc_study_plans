## Chinese Input Methods for Linux

### General

There are Ibus instructions at https://wiki.debian.org/I18n/ibus, but Maté is not listed. 

On **Rime**, see [these Arch Linux instructions](https://wiki.archlinux.org/index.php/Rime_IME).
 
**`m17n`**: 

 * [manual](http://www.nongnu.org/m17n/)
 * [this brief discussion](https://en.wikipedia.org/wiki/Intelligent_Input_Bus#ibus-m17n) of `ibus-m17n`
 * There is other IBus information at http://home.uchicago.edu/~alexlee/projects/m17n-classical/, but perhaps it is intended for a Windows environment?

**IBus-chewing** instructions here: https://github.com/definite/ibus-chewing/blob/maater/USER-GUIDE. I haven't learned these yet. 

Under Maté, within Vim, I can use `ctrl-U` rather than `ctrl-v u` to enter by code point.

Must remove most of the fonts —  there are too many (and perhaps other things) that I don't need. 

### `i3`

**20170405**: In the `i3` window manager for the Debian `chroot`, running Ibus at the command line gets an error "Can't connect to IBus." (Also reported for Fedora: http://forums.fedoraforum.org/showthread.php?t=309058.) This is the same as in the Chrome OS browser tab environment. In Firefox, whose UI opens successfully in `i3`, the input method doesn't start, and I also can't get `ctrl-U` to accept manual code-point entry. Chinese character display at the command line, including pasted-in characters (from Chinese websites) is very good; within Vim it is also good but characters already existing within a page are displayed as multi-byte ASCII substitutes. 

However, `ibus-daemon` (with or without following `&`) appears to succeed, and the first time I did it a little modal appeared, saying that the "super" key was now the hotkey for Ibus. I may have remapped the "super" key to caps lock, or I may not. 

In the Chrome tab environment, `ibus-daemon` followed by other `ibus` commands also succeed, although again nothing happens when I hit `ctrl-space` or the super key and space. The same `.md` file (the present one) in which pre-existing Chinese does not display correctly in Vim under `i3` displays correctly here. But pasting in does not! So it is the reverse of the situation under `i3`! There may be `i3` settings that I haven't gotten right yet.

Something else that doesn't work well in `i3` but does work well in the Chrome terminal tab is `ctrl-v` code point-entry in Vim. I've placed `:inoremap <C-u> <Nop>` in the `.vimrc` file to see if that frees up `ctrl-v` in Vim (and the command line, which uses Vim bindings). I think I will need to restart in order to test it.

I need to read about the use of the super key in `i3`.

 * **This looks promising**: http://unix.stackexchange.com/questions/277692/getting-ibus-working-with-tiling-window-manager
 * Super key generally: https://help.gnome.org/users/gnome-help/stable/keyboard-key-super.html.en
 * Seems to involve Fedora and a GUI desktop, so perhaps not pertinent. https://desktopi18n.wordpress.com/2012/05/28/customize-shortcut-keys-for-ibus-1-5/


**20170328: It appears that what I am using is Chrome's own built-in input methods. I never installed a Debian input method and it seems unnecessary.**

 1. Intelligent Input Bus (IBus)
 
    > The Intelligent Input Bus (IBus, pronounced as I-Bus) is an input method (IM) framework for multilingual input in Unix-like operating-systems. The name "Bus" comes from its bus-like architecture. (https://en.wikipedia.org/wiki/Intelligent_Input_Bus, accessed 20170217)
    
    * [documentation](https://wiki.debian.org/I18n/ibus, accessed 20170217); [Arch Linux user-guide](https://wiki.archlinux.org/index.php/IBus)
    
    * input methods
    
      `ibus-cangjie` seems the best documented, followed by `ibus-chewing`. 
    
      * Juhin 注音
    
        LibZhuyin has a better reputation, but Chewing is much better documented.
    
        * [`ibus-libzhuyin`](https://github.com/libzhuyin/ibus-libzhuyin)
        * [`ibus-chewing`](https://github.com/definite/ibus-chewing), [user guide](https://github.com/definite/ibus-chewing/blob/master/USER-GUIDE)
        
        > [`ibus-m17n`](https://github.com/phuang/ibus-m17n) and [`ibus-anthy`](https://github.com/phuang/ibus-anthy) both provide BoPoMoFo input methods. (http://askubuntu.com/a/281820/41401, accessed 20170217)
    
      * Pin'in 漢語拼音
    
        > Pinyin is the transcription of the spoken Chinese language in Latin characters. Each character has a tone which can be entered via the keyboard's various layers. E.g. on a German keyboard, buttons for `'` and <code>&#96;</code> are available which allows to write the second (e.g. _m√°_) and fourth tone (e.g. _m√†_). The first tone can be composed by holding `<alt gr> + <shift> + <+>` then the character (e.g. _mƒÅ_), the third by `<alt gr> + <shift> + <√§>` then the character (e.g. _m«é_).  (https://wiki.debian.org/gnome-chinese-input, accessed 20170217)
    
        * [`ibus-libpinyin`](https://github.com/libpinyin/ibus-libpinyin)
        * [`ibus-pinyin`](https://github.com/ibus/ibus-pinyin)
      
      * Tsangjye 倉頡
    
        * [`ibus-cangjie`](https://github.com/Cangjians/libcangjie), [documentation](http://cangjians.github.io/projects/ibus-cangjie/documentation/)

      * Gwoyeu Romatzyh 國語羅馬字
    
        Consider trying to prepare, using `ibus-table`? Only good for an initial, syllable-by-syllable approach. For connected words, there is logic required.
      
        > `ibus-table`, developed by Yu Wei Yu, is an IME that loads tables of input methods which do not need complicated logic to select words. Many structure-based Chinese input methods such as Cangjie and Wubi are supported this way. (https://en.wikipedia.org/wiki/Intelligent_Input_Bus#ibus-table, accessed 20170217)

 1. [Review of options generally](https://blogs.gnome.org/happyaron/2011/01/15/linux-input-method-brief-summary/), including SCIM.

[end]
