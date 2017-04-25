## JS specialized libraries of interest

### Graphical

Tool for comparing graphical libraries: http://www.jsgraphs.com/.

 1. [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) and [SVG.js](http://svgjs.com/). Paul Morris referred me to the Jacob Jenkov [tutorial](http://tutorials.jenkov.com/svg/index.html) on vanilla SVG. I think the best plan is to work in vanilla SVG or a while and then move to SVG.js. Notes in [separate file](../projects/svg.md).

 1. [p5.js](https://p5js.org/get-started/)

 1. [paper.js](http://paperjs.org/features/)

 1. [three.js](https://threejs.org/)

 1. [`canvas`](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial)

 1. [Treant.js](http://fperucic.github.io/treant-js/)
 
 1. [Graph.js](https://github.com/mhelvens/graph.js)
 
 1. [Sigma.js](http://sigmajs.org/)
 
 1. [Gun.js](http://gun.js.org/#step1)

 1. [fingertree](https://www.npmjs.com/package/fingertree); see application in [immutable-sequence](https://github.com/qiao/immutable-sequence.js). Can you visualize one of these with D3?

### Node

Network services.

### Functional

 1. **Underscore.JS**. Seems very practical, but some people say it's not as good as replacements.

 1. **Bibly.JS**. I have read the docs at https://bilby.brianmckenna.org and I like their terseness. First thoughts:
 
    * It seems to me to make no sense to start using curried functions for regular JS syntax (e.g., `strictEquals(a)(b)` for `a === b`) until I'm comfortable with the native syntax. 

    * Some of the terminology will take time to look into:
    
      * `catamorphism`
      * `polyfill`
      * `properties can be accessed without dispatching on arguments'
      * `[A trampoline] reifies continutations onto the heap, rather than the stack. Allows efficient tail calls.`

    * I like the way overriding and QuickCheck (assertion testing) work.

 1. **Ramda.JS**. Documentation appears to be fuller than for Bilby.JS.

    * Based on the [author's introductory blog post](https://buzzdecafe.github.io/code/2014/05/16/introducing-ramda), it seems that handling currying is the most important innovation in Ramda. (Other items [here](https://buzzdecafe.github.io/categories.html))
 
Norm Kabir always warns me about using libraries that don't have permanence and enough eyes on them. I'd be a lot more sanguine about Bilby and Ramda if there were fewer typos in their write-ups.


[end]
