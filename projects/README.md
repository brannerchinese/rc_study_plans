## Prospective coding projects for RC batch Spring 2 '17

### Current

 1. Color-matching functionality. (JS). Computer selects a random color and user must select a color that, added to the computer's color, comes as close as possible to white. Further items:
 
    1. Randomly select RGB separately, for `rgb`.
    1. In order to practice storage algorithms, keep track of colors with poorest performance and report stats?
 
    Versions:

    * 1: Produce randomly selected background color on each reload of page.
    * 2: Produce randomly selected background color on button click.
    * 3: Add two submit buttons and have the form submit without reloading page.
    * 4: Submit three form fields and confirm that you've received them.
    * pending: process content of form fields, including validation.

    Reference:

    * [color picker tool](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Colors/Color_picker_tool)
    * [`Math.random()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
    * [`rgb`](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#rgb). Note: this is CSS, not JS; convert in JS to string for application to CSS.
    * Docstring-like behavior in JS. 
    * use `document.forms[n]` for the `n`th form and `document.forms[n].element[i]` for it's `i`th element.
    * Associative arrays do not have `length`.

      * Discussion on StackOverflow: [1](http://stackoverflow.com/questions/10126310/does-javascript-have-a-standard-for-commenting-functions), [2](http://stackoverflow.com/questions/34205666/utilizing-docstrings)
      * [JSDoc](http://usejsdoc.org/index.html)
      * Javadoc

    * It appears that a default function argument can be a functional call (same is true in Python). But I think this is brittle; if the function call fails for some reason, we have `undefined`, so I set the default argument explicitly in code, instead.
    * [Form `<input>` types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
    * [Color state in `input` elements](https://www.w3.org/TR/html5/forms.html#color-state-%28type=color%29)

    * When a form is submitted, the function it calls must explicitly `return false` in order to prevent the page from reloading.
    * `this` can be used to refer to variables declared in the global namespace.

    Terms:

    * **channel**: one of the three components in RGB or the one component in greyscale; 8-bit.

### Future

 1. Color-matching game. (JS). Use earlier functionality to make a game — player is confronted with object (eventually, objects) of random color, and must "match to white" as above in order to neutralize it. Further items:
 
    1. Make into a distributed game?

 0. B+ tree. (JS). Use a graphical library to show it. Further items:
 
    1. Can we show its construction, step by step?
 
 1. Hànbûn tool. (JS). Input text and have computer set it in right-to-left columns. Further items:
 
    1. Must wrap and scroll properly. 
    1. Instead of text, allow link to news site?

 1. Unicode codepoint-by-character-name look-up tool to the projects list for JS.

### Past

[end]
