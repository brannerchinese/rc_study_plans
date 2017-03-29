## 20170329. Reading Kyle Simpson, _You Don't Know JavaScript: Up & Going_

 * Void operator

 * Fn that returns no value can set variable to `"undefined"`

 * `typeof`

 * type of `null` is `"undefined"`

 * "Properties": object's elements. Also called "keys" when accessed by bracket operator.

 * Arrays and functions are subtypes of the object.

 * "Native": object wrapper around a primitive type. Capitalized.

 * "boxing": conversion of a primitive type to a native type.

 * Empty objects are `true`, not `false`.

 * Difference between `==` and `===`: `==` includes type coercion and `===` does not.
 
 * Author considers widespread preference for `==` "shortsighted". Avoid using when either value is `true`, `false`, `0`, `""`, or `[]`.
 
 * In comparisons, arrays are coerced to `,`-separated strings.
 
 * "Hoisting": moving a variable declaration to the top of its scope. Most commonly used with functions and their declarations. Hoisting can be prevented (ES6) with `let`, which restricts a variable to "block scoping".
 
 * `switch`/`case`/`default` and the need for `break` to prevent "fall through"; utility of "fall through"
 
 * IIFEs
 
 * closures as "modules" for data privacy

 * `this` in reference to objects or the global object 

 * prototypes: not classal inheritance but "behavior delegation" — tool for "fallback" suppletion of properties.
 
 * polyfilling: checking for existence of a newer feature and defining it for use by browsers that lack it. Author recommends use of standard ES5/6 shims rather than writing one's own polyfills.
 
 * transpiling: polyfilling for new syntax. Has the added bonus of making explicit the implementation of the newer syntax. Author recommends Babel and Traceur.

 * DOM API (not part of JS)

### Questions

 * How can I see what something will be coerced to?

[end]
