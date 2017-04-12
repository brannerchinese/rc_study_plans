## "Hànbûn-columns" coding project

 1. Hànbûn tool. (JS). Input text and have computer set it in right-to-left columns. Further items:
 
    1. Must wrap and scroll properly. 
    1. Instead of text, allow link to news site?

 1. Features:
 
    1. iteration: Make resizable frame no larger than open window/viewport.
    1. iteration: Within frame, create columnar subframes that wrap right-left.
    1. iteration: Populate subframes with characters, one to a row.
    1. iteration: Load page into iframe from elsewhere.

 1 Reference:

    * style: `unicode-bidi`. 
    
      * Stands for "bidirectional". Allows developer to control display of bidirectional text in a single document. Probably not needed here.
      * https://developer.mozilla.org/en-US/docs/Web/CSS/unicode-bidi
      * https://www.w3schools.com/cssref/pr_text_unicode-bidi.asp

    * style: `direction`. 
    
      * https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/direction
      * https://developer.mozilla.org/en-US/docs/Web/CSS/direction
      * https://www.w3schools.com/cssref/pr_text_direction.asp

    * style: `column-count` and `column-gap` (note: `-moz` and `-webkit` prefixes are needed). 
    
      * https://developer.mozilla.org/en-US/docs/Web/CSS/column-count
      * https://developer.mozilla.org/en-US/docs/Web/CSS/column-gap
      * http://learnlayout.com/column.html

[end]
