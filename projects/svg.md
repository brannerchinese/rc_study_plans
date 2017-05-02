## SVG

The simplest options are [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) and [SVG.js](http://svgjs.com/). 

Paul Morris referred me to the Jacob Jenkov [tutorial](http://tutorials.jenkov.com/svg/index.html) on vanilla SVG. I think the best plan is to work in vanilla SVG or a while and then move to SVG.js. 

 1. Jacob Jenkov [SVG tutorial](http://tutorials.jenkov.com/svg/index.html) notes.

    1. SVG icons: Prefabricated image-tokens. Served as `img`s. SVG `viewBox` attribute specifies how much of SVG canvas is to be displayed. Samples at http://iconmonstr.com. 
    2. Coordinate system. Units include `em` (height of character in default font) and `ex` height of character "x" in default font. Default value is pixels.
    2. `svg` element: Can be nested (inner elements can have their positions specified vis-à-vis the outer element).
    2. `g` element: For grouping other elements. Styling is inherited by children.
    2. `rect` element: properties `rx`/`ry` (mirror if only one is set), `stroke`, `stroke-width`, `stroke-dasharray`, `fill`, `fill-opacity`. 
    2. `circle` element: properties `cx`/`cy`; `stroke`, `stroke-width`, `stroke-dasharray`, `fill`, `fill-opacity`.
    2. `ellipse` element: both `cx`/`cy` and `rx`/`ry`; `stroke`, `stroke-width`, `stroke-dasharray`, `fill`, `fill-opacity`. `stroke-opacity` —  do the others also have this?
    2. `polyline`: jointed straight line; and `polygon`.
    2. `path`: drawing commands initiated with `d`. Then

       * `Mx y`: move to (x, y) and set down pen
       * `Lx y`: draw straight line to (x, y); lower-case `l` is relative position; `L` is absolute position.
       * `Arx ry x-axis-rotation large-arc-flag sweep-flag x y`: !

	 * `large-arc-flag`: 0: small arc; 1: large arc
         * `sweep-flag`: 0: counter-clockwise; 1: clockwise
    
       * `Qx y`: quadratic Bezier curve; control point (intersection of two tangent lines) at (x, y)
       * `Cx1 xy x2 y2`: cubic Bezier curve; two control points
       * `Z`: close the path
       * `S`: shorthand cubic Bezier curve
       * `T`: shorthand quadratic Bezier curve

       CLosed paths can be filled.

       Markers on a path are indicated as x,y pairs after a path command.

    2. `marker`: a separate graphic element on a path. 
    2. `tspan`: used for relative positioning of multiple lines of text.
    2. `tref`: defines references to text labeled with `<text id>` tags. (Supplied code works in neither Firefox nor Chrome.)
    2. `textpath`: lays text out along a path.
    2. `switch`: allows flow control within SVG, but we can do this better with JS.
    2. `image`: incorporate existing images into SVG shapes.
    2. `a`: create links; SVG shapes themselves can be the object to which the link attaches.
    2. `def`: label items for cross-reference with `tref` or `use`.
    2. `symbol`: perhaps like `def` in that it defines items for cross-reference with `use`, but it has different attributes from `def`.
    2. `use`: allows reuse of SVG shapes; `def`, `tref` or any `id`-bearing element can be `xlink`-ed with `use`.
    2. `stroke`: fine-grained subtypes are listed in this section.
    2. `fill`: two fine-grained subtypes are listed in this section; the more interesting one is `fill-rule` and its two values: `nonzero` and `evenodd`.
    2. `viewBox`: details of how the overall SVG environment is configured.
    2. Animation. A long section, covering:

       * `set`
       * `animate`
       * `animateColor`
       * `animateTransform`
       * `animateMotion`

    2. Scripting. A long section.
    2. Transformation. A long section, covering:

       * `translate()`
       * `rotate()`
       * `scale()`
       * `skew()`
       * `matrix()`

    2. Gradients. A long section.
    2. `pattern` element: define and transform fill patterns.
    2. `clipPath` element: describe a path that masks part of another SVG image.
    2. `mask` element: use one SVG image to mask another.
    2. Filters. A long section.
 
 1. Some things encountered the first day (before reading Jenkov):

    * Be careful not to use pure JS methods when special namespaced methods are needed, such as `createElementNS`.
    * It doesn't appear that the attributes for SVG objects can be populated via CSS.
    * Where we would normally group things with a `div` element, SVG uses a `g` element that provides more functionality.
    * It appears (Firefox 45.8) that a "text node" cannot have `getBBox` called on it, while a namespaced SVG text element can.. `getBBox` is important for determining the size of a dynamically changing text element.

 1. Try the more generic [`getBoundingClientRect`](https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect) and `getClientRects` instead of SVG-native `getBBox`. The SVG-native method has a slightly tighter fit and additional properties (`top`, `right`, `bottom`, `left`), which can be calculated from the others.

    Keys in `getClientRects` have values that are not all of the same time, including a function `item()`, which cannot be coerced to string. So prefer `getBoundingClientRect`.

 1. SVG scaling principles.

    * [Amelia Bellamy-Royds, "How to Scale SVG"](https://css-tricks.com/scale-svg/)
    *  `viewBox` and `preserveAspectRatio`.

 1. Modeling edges between nodes.

[end]
