## Chinese Pinyin input and Unicode code-points on Chrome OS

To enter Unicode characters on Linux, enter `ctrl-shift-u` and the codepoint, and then return or space. It seems I can drop any number of initial zeros, so I've done so below. Vim has, built-in, a command `ctrl-v` which can be followed by `u` and a hexidecimal codepoint to the same effect.

Since there appears to be no unified "keyboard" driver that contains all of these things, I will have to learn by heart the codepoints of the characters I use most often. 

 * 　: 3000
 * Ｘ: ff38

### Pīnyīn diacritic-ed vowels

There are enough patterns here that Mnemosyne has a few crutches for her work. Capital forms are either 0x1 or 0x20 less than their small forms — macron and caron are 0x20; acute and grave are 0x1 less.

| macron | acute | caron | grave |
|--------|-------|-------|-------|
| ā: 101 | á: e1 | ǎ: 1ce | à: e0
| Ā: 100 | Á: c1 | Ǎ: 1cd | À: c0
| | | | |
| ē: 113 | é: e9 | ě: 11b | è: e8
| Ē: 112 | É: c9 | Ě: 11a | È: c8
| | | | |
| ī: 12b | í: ed | ǐ: 1d0 | ì: ec
| Ī: 12a | Í: cd | Ǐ: 1cf | Ì: cc
| | | | |
| ō: 14d | ó: f3 | ǒ: 1d2 | ò: f2
| Ō: 14c | Ó: d3 | Ǒ: 1d1 | Ò: d2
| | | | |
| ū: 16b | ú: fa | ǔ: 1d4 | ù: f9
| Ū: 16a | Ú: da | Ǔ: 1d3 | Ù: d9
| | | | |
| ǖ: 1d6 | ǘ: 1d8 | ǚ: 1da | ǜ: 1dc
| Ǖ: 1d5 | Ǘ: 1d7 | Ǚ: 1d9 | Ǜ: 1db

### Other Unicode codepoints

See the [Unicode Character Name Index](http://www.unicode.org/charts/charindex.html) (which is not complete, by design).

 * Ł: 141: LATIN CAPITAL LETTER L WITH STROKE (not on Unicode Consortium page but lapse reported) 
 * ł: 142: LATIN SMALL LETTER L WITH STROKE
 * û: fb: U WITH CIRCUMFLEX, LATIN SMALL LETTER
 * Û: db: U WITH CIRCUMFLEX, LATIN CAPITAL LETTER
 * …: 2026: HORIZONTAL ELLIPSIS
 * —: 2014: EM DASH
 * ⸺: 2e3a: TWO-EM DASH
 *  : a0: NON-BREAKING SPACE

---

### Older efforts

 * [Discussion of common non-ASCII characters](http://sites.hanovernorwichschools.org/techsupport/howtos/google/chromebook-accent-characters)

   This makes it look as though at least two different keyboards are needed to get both umlaut and the acute and grave accent marks, and macron and caron are not listed. **EDIT** 20170409: That is so; it doesn't appear that the Chromebook is currently prepared for robust input of Pīnyīn with diacritics.

 * [UTF-8 extension](https://chrome.google.com/webstore/detail/utf-8-and-unicode-charact/fcemphgmjnjpmmdhcedhjiegickfbiia/related?hl=en)

   This appears to supply mostly emoji.

[end]
