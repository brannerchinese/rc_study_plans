## "Color-match" coding project

 1. Color-matching functionality. (JS). Computer selects a random color and user must select a color that, added to the computer's color, comes as close as possible to white. Further items:
 
    1. Randomly select RGB separately, for `rgb`.
    1. In order to practice storage algorithms, keep track of colors with poorest performance and report stats?
 
    Versions:

    * 1: Produce randomly selected background color on each reload of page.
    * 2: Produce randomly selected background color on button click.
    * 3: Add two submit buttons and have the form submit without reloading page.
    * 4: Submit three form fields and confirm that you've received them.
    * 5: process content of form fields, including validation.
    * 6: set up a scoring mechanism and display.
    * pending: add a graphical picker.

    Reference:

    * [color picker tool](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Colors/Color_picker_tool)
    * [`Math.random()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
    * [`rgb`](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#rgb). Note: this is CSS, not JS; convert in JS to string for application to CSS.
    * Associative arrays do not have `length`.
    * Docstring-like behavior in JS. 
    
      * Discussion on StackOverflow: [1](http://stackoverflow.com/questions/10126310/does-javascript-have-a-standard-for-commenting-functions), [2](http://stackoverflow.com/questions/34205666/utilizing-docstrings)
      * [JSDoc](http://usejsdoc.org/index.html)
      * Javadoc

    * It appears that a default function argument can be a functional call (same is true in Python). But I think this is brittle; if the function call fails for some reason, we have `undefined`, so I set the default argument explicitly in code, instead.
    * [Form `<input>` types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
    * [Color state in `input` elements](https://www.w3.org/TR/html5/forms.html#color-state-%28type=color%29)

    * When a form is submitted, the function it calls must explicitly `return false` in order to prevent the page from reloading.
    * `this` can be used to refer to variables declared in the global namespace.
    * use `document.forms[n]` for the `n`th form and `document.forms[n].element[i]` for it's `i`th element.
    * How elements are added by JS.
    * How elements are styled by JS.
    * `placeholder` and `select()` on an input form.
    * Hack for generating a "range" in JS.

    Terms:

    * **channel**: one of the three components in RGB or the one component in greyscale; 8-bit.

[end]
