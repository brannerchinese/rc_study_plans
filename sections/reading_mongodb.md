## MongoDB

### How it works

 * https://www.slideshare.net/mdirolf/mongodb-how-it-works

 * [Manual](https://docs.mongodb.com/manual/)

 * "Somewhere in the middle" between SQL and key-value stores." Ub David Glasser, "[MongoDB queries don’t always return all matching documents!](https://blog.meteor.com/mongodb-queries-dont-always-return-all-matching-documents-654b6594a827#4ccf)".
 
   > SQL databases offer powerful transactional guarantees and a query planner that can run queries against various user-defined indexes, but you tend to lose these guarantees when you shard data in order to scale.
   > 
   > In the pursuit of scalability, key-value stores and Bigtable don’t let you change arbitrary data in a single transaction. This generally means that they don’t have built-in indexes and query planning, and it’s then your job to structure data in a way that’s efficient for the queries you need to make.
   > 
   > MongoDB is somewhere in the middle. On the one hand, the basic unit of atomicity is the single document: you can make transactional writes to a document, but not across documents. On the other hand, MongoDB does support indexes, and has a query planner that knows how to use them.
   >
   > MongoDB has a long document describing its concurrency properties. The basic gist of it is that you should only expect consistency at the single document level. So it’s not surprising that it provides “Non-point-in-time read operations”: if you modify a few documents while executing a slow query on their collection, you might see some of them in the state before the modification, and some of them as already modified.

### Criticisms

 1. MongoDB lacks `JOIN`s, which have to be implemented instead in application code. Sarah Mei, "[Why you should never use MongoDB](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/)". Describes the model as a "huge fractal data structure" and "one big denormalized nested data structure". 

 1. [Security issues in the default configuration](https://en.wikipedia.org/wiki/MongoDB#Bug_reports_and_criticisms)

 1. David Glasser, "[MongoDB queries don’t always return all matching documents!](https://blog.meteor.com/mongodb-queries-dont-always-return-all-matching-documents-654b6594a827)".

 1. Kyle Kingsbury, "[Jepsen: MongoDB stale reads](https://aphyr.com/posts/322-jepsen-mongodb-stale-reads)":
    
    > Mongo’s consistency model is broken by design: not only can “strictly consistent” reads see stale versions of documents, but they can also return garbage data from writes that never should have occurred. ... Almost all write concern levels allow data loss.


[end]
