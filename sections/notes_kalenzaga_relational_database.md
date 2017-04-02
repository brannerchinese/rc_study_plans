## Note on Christophe Kalenzaga, How does a relational database work?

### Indexing data structures

 1. Binary search tree: suitable for retrieving just one value
 
 1. B+ tree: suitable for doing a **range query**. 
 
    1. only leaves store information; non-leaf "decision" nodes route search to the correct leaf
    1. leaves also form a sorted linked list
    1. complexity: `log(total leaves) + |desired range|`
    1. cost: ordering and balancing (indexing more tables incurs these costs for each index)
    
 1. Hash table: advantages over an array:
 
    1. can be loaded into memory only partially
    1. memory does not have to be contiguous
    1. `O(1)` lookup by specific key

### Core components

 1. Client manager
 
    1. provides APIs
    1. handles authentication
    1. manages communications with client
 
 1. Query manager
 
    1. parses, edits, optimizes, compiles, and executes queries
    
    1. query rewriting includes;
    
       * eliminating redundancies
       * evaluating arithmetic; expanding views and subqueries

    1. query optimizer
    
       * cost-based optimization (CBO): choosing among competing chains of operations for a given query, based on 
      
         * CPU cost
         * disk I/O cost (usually the bottleneck)
         * memory requirement
      
        Choice may be aided by optimization heuristics, dynamic programming, greedy incremental algorithms.
      
       * Joins are not commutative vis-à-vis cost. `cost(a JOIN b)` != `cost(b JOIN a)`

       * different kinds of join implementations

         * Nested loop join: `O(outer * inner)`
         * Hash join : `O(outer + inner)`; Wikipedia lists several forms
         * Merge join: `O(outer * log(outer) + inner * log(inner)` (best on sorted tables, such as B+ trees)

 1. Data manager: retrieves data
 
    1. strategies: 
    
       * prefetching
       * least-recently used (LRU) buffer-replacement, sometimes with additional weighting
 
 1. Transaction manager

    1. constraints: ACID transactions
    1. concurrency control. Strategies:

       * locks
      
         * exclusive lock (for writes; must always be released after transactions)
         * shared lock (for reads)
         * deadlock: caused by cycles in the graph, which are expensive to check for, so timeouts are commonly used
         * two-phase locking: "growing" vs. "shrinking" phases, preventing a transaction from both obtaining and releasing locks at the same time
      
       * data versioning
      
         * data can be modified simultaneously by different transaction, but each transaction has a unique "version" of the data; only one modification is accepted and any others are rolled back.
         * can make heavy use of memory

 1. Log manager
 
    1. strategies for dealing with mid-transaction crashes:
    
       * shadow copies or pages
       * transaction logs (RAID disks are normal, for stability)
      
    1. Write-Ahead Logging protocol (WAL):
      
       * logging must precede writing data
       * logs must be sequential
       * commits must be logged before the transaction is considered finished

    1. Algorithms for Recovery and Isolation-Exploiting Semantics (ARIES)
    
       * modification of WAL
       * components of record:
         * log records are numbered (LSN)
         * transaction ID 
         * page ID of modified data
         * link to previous log produced by same transaction
         * how to UNDO operation (this usually means a reverse operation to restore prior state)
         * how to REDO operation

       * logging is buffered to prevent bottlenecks
       * NO-FORCE policy: actual writing to disk may occur after commit, because it is recoverable with REDO
       * STEAL policy: incremental writing to disk
       * UNDO/REDO data is stored transiently in a transaction table and a dirty table
       * writes may be punctuated by checkpoints

### Other topics not covered

 1. clustered databases and global transactions
 1. snapshots (while database is running)
 1. efficient data-storage and compression
 1. memory management

---

### Terms

  * range query
  * process vs. thread
  * page or block of storage
  * predicate: condition, "prior declaration", proviso, premise; "the thing to be affirmed or denied in the copula"; "the part of a sentence or clause containing what is said about a subject"; contingency
  * bitmap index
  * full scan (whole database)
  * unique scan (only one record)
  * inner vs. outer relation: right vs. left
  * genetic algorithm: randomly create different query plans, prune those with poor costs, repeat iteratively and finally choose the best plan.
  * buffer pool: in-memory cache of pre-fetched data
  * dirty (page): modified but not written to disk
  * latch: lock on indexes, shorter-lived than the common transaction locks on user data
  * ACID
  * phantom read
  * non-repeatable read
  * dirty read
  * exclusive lock
  * shared lock
  * deadlock
  * rollback
  * "database effect"

### Structures and algorithms

  * B+ tree (used for database index)
  * Hash join (used for lock table, buffer pool)
  * Nested loop join
  * Merge join: via merge sort
  * Nearest neighbor algorithm

[end]
