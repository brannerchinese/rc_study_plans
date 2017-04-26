## Notes on Adam Marcus, "The NoSQL Ecosystem"

[Adam Marcus, "The Architecture of Open Source Applications: The NoSQL Ecosystem"](../materials/Adam_Marcus,_The_Architecture_of_Open_Source_Applications_The_NoSQL_Ecosystem.pdf) (**[external link](http://aosabook.org/en/nosql.html)**).

### Notes (emphasis on MongoDB)

 * Tend to restrict lookups on a dataset to a single field, by key. (13.2.1)
 * Trade-off: 
 
   * Join operations "get pushed into application logic". (13.2.1)
   * Key look-up gives database "consistent query pattern". (13.2.1)

 * Major differences from the SQL model

   * NoSQL tends to favor performance over ACID guarantees, but keys are always guaranteed not to collide. (13.2.4)

     * MongoDB uses key-document stores. Documents are JSON. Keyspaces are separated into collections (mirroring tables) to avoid collisions. (13.2.1)

   * NoSQL tends to lack schema enforcement, so properties are not necessarily the same across "records". (13.2.5)

 * One of the major distinguishing features across different NoSQL systems is how single-server durability is implemented. (13.3.1)

   * Database updates can be buffered and actual writes delayed until `fsync` is called.
   * The log is the source of truth in the event of a crash, and the log is always sequential.
   * MongoDB updates documents in-place; other NoSQL systems merge data structure and log even more so.


[end]
