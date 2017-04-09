## 20170329. Reading Kyle Simpson, _You Don't Know JavaScript: _Types & Grammar_

### "Types", ch. 3

 * Data contained in natives

 * `argument` now deprecated p. 45

 * Sparse array p. 45

 * `apply` p. 47

 * term: "footgun'ish" p. 48

 * Properties have to be added to natives by one p.49

 * `eval()` is preferable to `Function()` p. 49

 * `RegExp()` is useful because patterns can be defined dynamically. But literal regexes are precompiled before code execution. P. 49

 * `Date()` is useful for constructing dates. P. 49

 * `Error()` is useful for capturing the function call stack. `new` is optional. P. 50.

 * Primary use case of `Symbol()` is as a private variable, although not actually private. P. 52.

 * Prototypes for natives have shorthand: `<Native>#property` for `<Native>.prototype.property` p. 52

 * "Prototype delegation" p. 53

 * `<Native>.prototype` is an instance of `<Native>`. So these can be used as empty values: `a = x || Array.prototype`. But modifying one of these modifies the prototype. P. 53-55.

### "Grammar", ch. 5

 * Capture and assign completion value of a statement using eval. Dangerous. ES7's proposed do accomplishes the same thing. Pp 124-5.

 * Side effects: changes other than returned value.

 * Example of side-effect: `b = a++`. `++` operator acts only after assignment to `b`. To assign side-effect value, need to use `b = (a++, a)`. Pp. 125-9.

 * Example of side-effect: delete. Returns boolean but may alter a value. P. 128.

 * DPB: try `a = b++ = c++ = 5`. (Doesn't work.)

 * "Jump": 1. continue statement transferring control from an inner for loop to a labelled outer for loop. P. 132. 2. Break statement breaking out of labelled and bracketed code block or outer for loop. Pp. 133-4. DPB: item 2 seems the main case.

 * Json is a subset of JS syntax but not a "proper" subset because it can't always run as written. P. 134)

 * JSON-P: wrap JSON data (read via script tag) in a function call to make it usable. P. 134

 * Object destructuring: ES6 syntax for returning only the values of an object. Pp. 135-6.

 * `else if` is not a single expression but the compounding of `else` and `if`. Pp. 136-7

 * `&&` has precedence over `||`. Pp. 137-40.

 * Nested `?...:` is right-associative. Pp. 142-3.

 * Coerce to boolean with `!!`. P. 159

 * The "global object" is the browser window. P. 172

[end]
