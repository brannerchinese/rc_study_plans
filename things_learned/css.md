## Things learned: CSS

 * Centering `div`s. There are two principal ways:

   1. inner objects:  

      ```css
      display: block;
      margin: auto;
      width: <actual>;
      ```
      I've thought about supplying the actual width from a measurement of that object itself, in JS.

   1. outer object:

      ```css
      text-align: center;
      ```

      inner object:

      ```css
      display: inline;
      ```

      An idea suggested [here](http://stackoverflow.com/a/114549/621762) is to use `display: table;` instead of `width` in the first example. There are several dozen suggestions about centering `div`s on that page.

 * Difference between `display:inline-block` and `display:inline`
 
   * > Elements with `display:inline-block` are like `display:inline` elements, but they can have a width and a height. That means that you can use an inline-block element as a block while flowing it within text or other elements. (http://stackoverflow.com/a/14033814/621762, accessed 20170412)
   * > `display: inline;` is a display mode to use in a sentence. For instance, if you have a paragraph and want to highlight a single word…  **Comment**:  If you want to resize `inline` elements you could be using `inline-block` as the display type. (http://stackoverflow.com/a/8969466/621762, accessed 20170412)
   * `block` forces a newline after it.

   * What different properties do these styles have?

[end]
