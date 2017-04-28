## Notes: MongoDB features

 * Solution to object-relational impedance mismatch (will@mongolab, ["Why is MongoDB wildly popular? It’s a data structure thing"](https://blog.mlab.com/2012/08/why-is-mongodb-wildly-popular/), 20120802, accessed 20170427):
 
   > While MongoDB may have ridden onto the scene under the banner of scalability with the rest of the NoSQL database technologies,  the disproportionate success of MongoDB is largely based on its innovation as a data structure store that lets us more easily and expressively model the 'things' at the heart of our applications. For this reason MongoDB, or something very like it, will become the dominant database paradigm for operational data storage, with relational databases filling the role of a specialized tool.
   >
   > …
   >
   > many of the entities that back most modern web-apps:
   >
   > * **CMS**: the flexible schema of MongoDB is great for heterogeneous collections of content types
   > * **Location based data**: MongoDB understands geo-spatial coordinates and natively supports geo-spatial indexing
   > * **System configuration**: just a nice **object graph** of configuration values, which is very natural in MongoDB
   > * **Form data**: MongoDB makes it easy to evolve the structure of form data over time

 * Uses JSON, rather than requiring a parser for syntax. (anonymous, ["Why is JSON so popular? Developers want out of the syntax business"](https://blog.mlab.com/2011/03/why-is-json-so-popular-developers-want-out-of-the-syntax-business/), 20110330, accessed 20170427)

 * Compatible with Agile-style fast iteration (Matt Asey, ["Why MongoDB Is Popular"](https://www.mongodb.com/blog/post/why-mongodb-popular), 20130712, accessed 20170427)

### Also note

 * Close relationship with Meteor. [1](https://www.meteor.com/articles/what-is-mongodb), [2](https://guide.meteor.com/collections.html).
 * [Quasar](https://github.com/quasar-analytics/quasar) (formerly [SlamData](https://blog.mlab.com/2014/10/run-sql-queries-on-mongolab/)), for running SQL queries on MongoDB.

[end]