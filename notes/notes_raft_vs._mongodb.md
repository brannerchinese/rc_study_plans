## Differences between Raft algorithm and MongoDB's "replica set" model. 

### Main points 

 * MongoDB's Protocol v. 0 was "inherently unsafe" (Jepsen) but as Protocol v. 1 it has now been improved and further patched.

 * Protocol v. 0:
 
   * [It] "does not provide consensus; it relies on synchronized clocks, and even where clocks are synchronized, can become skewed when many operations arrive at the same timestamp." (Jepsen)
   * "This is a design flaw of the v0 replication protocol itself, not a bug; there are no plans to fix it. … The solution is to switch to MongoDB's newer replication protocol: v1." (Jepsen)
 
 * Protocol v. 1 has adopted features from Raft:

   * "terms": Voting rounds now occur only once per term (Jepsen); once per election *attempt* (Brody); in v. 0 the number of votes was configurable (Stennie).

     * `optime` is now tuple `[term, timestamp]`; "term" ensures logical instead of temporal priority; timestamps still serve as log indices, unlike in Raft (Jepsen).
     * `oplog` "is, in essence, a sparse Raft log" (Jepsen).
   
   * Monitoring node status using metadata sent via existing data replication channel, rather than from every node to every other node (Brody).
   * Heartbeats now faster (Brody).
   * Asymmetric election timeouts (Brody).

 * Distinctive MongoDB replication characteristics still in place:
 
   * Operations are applied as soon as received, rather than only after committal (Jepsen).
   * effects of dirty reads are attenuated with (Jepsen):
   
     * snapshots of last committed state
     * "majority read concern": reads from committed snapshot
     * "linearizable read concern": read is done by primary from own, uncommitted state, and primary then blocks until committal

   * Candidacy of MongoDB "primary" is decided based on `priority`; in Raft any "follower" may elect to become candidate for election (Raina).
   * MongoDB has "hidden members", used for reporting and back-up but not serving queries or becoming "primaries"; they may or may not participate in an election (Raina).
   * Durability is ensured via "write concern" (level of acknowledgement for replicated data from the `oplog`) and "journaling" (write-ahead logging, on-disk) (Raina). Perhaps it is better to use only one of `oplog` and journal, not both (Bond).

### Sources
 
   * Jepsen (Kyle Kingsbury), [critical paid review of MongoDB replication protocols 0 and 1](../materials/Kyle_Kingsbury_Jepsen_MongoDB_3.4.0-rc3_review_of_protocols_0_and_1.pdf), 20170207 ([original here](https://jepsen.io/analyses/mongodb-3-4-0-rc3))
   * "Stennie" (MongoDB employee) [comparison of Raft and MongoDB protocol 0 on StackOverflow](../materials/Stennie_on_StackOverflow,_Raft_vs_MongoDB_Primary_Election.pdf), 20140110 on StackOverflow ([original here](http://stackoverflow.com/a/21048400/621762))
   * Spencer Brody (MongdoDB employee) slide show ["Distributed Consensus in MongoDB":  Replication Election and Consensus Algorithm Refinements for MongoDB 3.2](../materials/Spencer_Brody,_Distributed_Consensus_in_MongoDB.pdf), 20150605 ([original here](https://www.slideshare.net/mongodb/replication-election-and-consensus-algorithm-refinements-for-mongodb-32))
   * Ankur Raina, ["MongoDB: The Latest Features-Replication" (description of protocolVersion 1), 20160426](../materials/Ankur_Raina,_MongoDB_The_Latest_Features-Replication.pdf) ([original here](http://info.tricoresolutions.com/blog/mongodb-the-latest-features-replication))
   * Reuben Bond, ["MongoDB Replication: The Journal Journal, The Global Lock, & Durability" (20140419)](Reuben_Bond,_MongoDB_Replication-The_Journal_Journal,_The_Global_Lock,_&_Durability.pdf) ([original here](http://daprlabs.com/blog/blog/2014/04/19/mongodb/))

[end]
