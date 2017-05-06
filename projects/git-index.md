## Git-index

Index all the keywords and options (including symbols) occurring in the Git man pages. 

Goal: to make it easier to study the structure of the whole system. 

Examples:

 * When is a "ref" used and when is a "refspec" used? What is the difference?
 * What do symbols such as `^` and `@` and `--` and `{1}` mean?
 * What is the difference between `..` and `...`?

Points to think about in implementation:

 * Commands are documented in distinct text files on https://github.com/git/git/tree/master/Documentation. Links to the files seem to be tagged with `class=js-navigation-open`.
 
 * Files are `.txt` but seem to be in a kind of simple markdown. There are derived HTML versions at https://github.com/git/htmldocs, but I suspect the text is easier to work with (and it's primary).
 
 * Based on the use of single-quotes for italics and back-ticks for monospace, the markdown appears to be AsciiDoc. [AsciiDoc's (brief) chapter on man pages](http://asciidoc.org/chunked/ch24.html) makes it sound as though there is a standard "manpage roff format", but I don't see that listed elsewhere.
 
   * Items for discussion begin at the left margin and end with `::`. Several of these can be consecutive (one per line) and apparently all apply to the following explanation.
   * Indented explanation-text under an item for discussion begins with a tab (one per line) or with `+` (one per paragraph).
   * Monospace is marked with backticks.
   * Italics are marked with single-quotes.
   * Links are marked `linkgit:<name>[<n>]` where 
   
     * `linkgit` seems to be replaced with an `a href` tag in HTML and with a link to `<name>.html` in the same directory
     * the text for the link is rendered as `<name>(<n>)`.

   * The Synopsis section seems always to contain `[verse]` as the first line. This "style" is a form of quotation, but unlike `[quote]` it preserves line-breaks.
   
   * The Synopsis generally is not as pared-down as it could be. It tries to show all possible options, but that makes it harder to take in the whole format quickly.

[end]

