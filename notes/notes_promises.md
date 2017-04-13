## Promises

Paul Morris. Recurse Center JS/Webstack Topics workshop, 20170412.

Many comments by AJ Jordan.

 * Used for asynchronous programming (instead of callbacks)
 * Something like a wrapper for a value that is not yet available —  status may be pending or settled; settled comprises fulfilled and rejected
 * Has a method `then()`: takes "`onSuccess`" function (which can be chained to make a pipeline of functions depending on promises)
 * Has a method `catch()`: takes "`onFailure`" function (which can be chained to `then`)
 * Things you can do with a promise:

   * return it from a function
   * call `then` or `catch` on it
   * `all`
   * `race`, for multiple arguments

 * Unlike callbacks, promises have automatic error handling, avoiding the need for `if (error) {throw error}`.
 * new JS things implemented with promises:

   * `await` in `axync` function calls
   * generators

 * The biggest advantage of promises is that they represent a standard interface for a callback-like behavior.

[end]
