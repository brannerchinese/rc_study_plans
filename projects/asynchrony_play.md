## Asynchrony play

### Idea

 * Produce some objects that have to be processed in some time-consuming way —  large integers to be factored, or URLs of aggregator sites. 
 * Display them one per line in the browser and send them asynchronously for processing.
 * Delete them after they have been processed.
 * Later:

   * animate the processing

### Iterations

 * 1: basic structure; use factorization of large numbers as asynchronous task.

### Reference

 1. Large numbers. Use `Math.random`. What is the largest integer JS can handle? `Number.MAX_SAFE_INTEGER` (= 9007199254740991).

[end]
