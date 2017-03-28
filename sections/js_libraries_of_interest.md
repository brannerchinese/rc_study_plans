## JS specialized libraries of interest

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
