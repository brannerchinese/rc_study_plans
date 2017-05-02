## JS accessing the viewport

CSS Object Model (CSSOM) attributes

### Height and width of viewport

 1. `Element.clientWidth` and `Element.clientHeight` values

    See https://drafts.csswg.org/cssom-view/#dom-element-clientwidth.

    ```js
    var w = document.documentElement.clientWidth;
    var h = document.documentElement.clientHeight;
    ```
 2. `Window.innerWidth` and `Window.innerHeight` values

    May include scrollbars and other non-display components fo window. See https://drafts.csswg.org/cssom-view/#dom-window-innerwidth.

 3. More sophisticated approach:

    See http://stackoverflow.com/a/8876069/621762.

    ```js
    var w = Math.max(document.documentElement.clientWidth, window.innerWidth || 0);
    var h = Math.max(document.documentElement.clientHeight, window.innerHeight || 0);
    ```

  4. Examples.
  
     There is a useful page at http://ryanve.com/lab/dimensions/ (accessed 20170501). 

### Font size as a function of the viewport dimensions

Use `nvw` for `n`% of viewport width, `nvh` for `n`% of viewport height.

`nvmin` and `nvmax` are `n`% of the lesser or greater of `vw` and `vh`.

See https://css-tricks.com/viewport-sized-typography/ (accessed 20170501).

[end]
