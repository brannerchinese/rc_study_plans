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

**Below are notes I initially took in order to prepare for batch.**

---

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
