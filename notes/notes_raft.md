## Raft algorithm

Primary source: [Diego Ongaro and John Osterhout paper, "In Search of an Understandable Consensus Algorithm (Extended Version)"](../materials/Ongaro_and_Osterhout,_In_search_of_an_understandable_consensus_algorithm_(extended_version).pdf). Published May 20, 2014, at https://ramcloud.stanford.edu/raft.pdf and also at https://ramcloud.stanford.edu/wiki/download/attachments/11370504/raft.pdf (accessed 20170421). This paper is a revision of Ongaro and Osterhout, "In search of an understandable consensus algorithm. In Proc ATC’14, USENIX Annual Technical Conference (2014), USENIX. (Paper and video of presentation [here](https://www.usenix.org/conference/atc14/technical-sessions/presentation/ongaro).) 

### Algorithm

(Blank)

### Notes

I was pleased to see a proof by contradiction in Sec. 5.4.3. I haven't seen one of those since I was in school. I suppose corrupt logs or intentional errors in transmission (evil man-in-middle) could up-end the proof.

Diego Ongaro [explains](https://groups.google.com/d/msg/raft-dev/95rZqptGpmU/cfH4N7reBQAJ) the origin of the name Raft.

> People ask me why it's called "Raft" every now and then, and I didn't have anything public on that until now. I wrote this up earlier in the year in a private email. I want a URL for it, so I'm sending it here and spamming all of you.
>
> There's a few reasons we came up with the name Raft:
>
> * It's not quite an acronym, but we were thinking about the words 'reliable', 'replicated', 'redundant', and 'fault-tolerant'.
> * We were thinking about logs and what can be built using them.
> * We were thinking about the island of Paxos and how to escape it.
>
> As a plus, we were using the randomly generated name Cheesomi in the paper before we came up with the name Raft in September 2012. The name appeared just over 100 times in our paper submission back then, so switching to the shorter name actually helped shrink the paper down quite a bit.

**Abstract**

> In order to enhance understandability, Raft separates the key elements of consensus, such as leader election, log replication, and safety, and it enforces a stronger degree of coherency to reduce the number of states that must be considered.

**1. Introduction**

> Raft separates leader election, log replication, and safety

**2. Replicated state machines**

> Consensus algorithms typically arise in the context of **replicated state machines**.
>
> Replicated state machines are typically implemented using a replicated log.
>
> Keeping the replicated log consistent is the job of the consensus algorithm.

Properties:

 1. **safety**: never returning an incorrect result
 1. functional: **available**, as long as any majority of the servers are operational and can communicate with each other and with clients
 1. do not depend on timing to ensure the consistency of logs
 1. a command can complete as soon as a majority of the cluster has responded to a single round of remote procedure calls

**3. What's wrong with Paxos**

Hard to understand

**4. Designing for understandability**

> In Raft we separated leader election, log replication, safety, and membership changes.
> 
> Logs are not allowed to have holes, and Raft limits the ways in which logs can become inconsistent with each other.
>
> Randomized approaches introduce nondeterminism, but they tend to reduce the state space by handling all possible choices in a similar fashion

**5. The Raft consensus algorithm**

> Raft implements consensus by first electing a distinguished **leader**, then giving the leader complete responsibility for managing the replicated log. The leader accepts log entries from clients, replicates them on other servers, and tells servers when it is safe to apply log entries to their state machines. 
> 
> * Leader election: a new leader must be chosen when an existing leader fails.
> * Log replication: the leader must accept log entries from clients and replicate them across the cluster, forcing the other logs to agree with its own.
> * Safety: the key safety property for Raft is the State Machine Safety Property: if any server has applied a particular log entry to its state machine, then no other server may apply a different command for the same log index.

**5.1 Raft basics**

> At any given time each server is in one of three states: **leader**, **follower**, or **candidate**.
>
> Each term begins with an **election**, in which one or more candidates attempt to become leader.
>
> Terms act as a logical clock in Raft, and they allow servers to detect obsolete information such as stale leaders.
>
> Each server stores a **current term** number, which increases monotonically over time.
> 
> Current terms are exchanged whenever servers communicate; if one server’s current term is smaller than the other’s, then it updates its current term to the larger value. If a candidate or leader discovers that its term is out of date, it immediately reverts to follower state. If a server receives a request with a stale term number, it rejects the request.
>
> Raft servers communicate using remote procedure calls (RPCs), and the basic consensus algorithm requires only two types of RPCs:
> * `RequestVote` RPCs are initiated by candidates during elections
> * `AppendEntries` RPCs are initiated by leaders to replicate log entries and to provide a form of heartbeat
> *  [`InstallSnapshot`]: a third RPC for transferring snapshots between servers.
> 
> Servers retry RPCs if they do not receive a response in a timely manner, and they issue RPCs in parallel for best performance.

**5.2 Leader election**

> heartbeat mechanism: heartbeats (`AppendEntries` RPCs that carry no log entries)
>
> If a follower receives no communication over a period of time called the **election timeout**, then it assumes there is no viable leader and begins an election to choose a new leader.
>
> To begin an election, a follower increments its current term and transitions to candidate state.
>
> Once a candidate wins an election … it then sends heartbeat messages to all of the other servers to establish its authority and prevent new elections.
>
> While waiting for votes, a candidate may receive an `AppendEntries` RPC from another server claiming to be leader. If the leader’s term (included in its RPC) is at least as large as the candidate’s current term, then the candidate recognizes the leader as legitimate and returns to follower state. If the term in the RPC is smaller than the candidate’s current term, then the candidate rejects the RPC and continues in candidate state.
>
> Split vote: When this happens, each candidate will time out and start a new election by incrementing its term and initiating another round of Request-Vote RPCs. However, without extra measures split votes could repeat indefinitely.
>
> randomized election timeouts: This spreads out the servers so that in most cases only a single server will time out; it wins the election and sends heartbeats before any other servers time out. … Each candidate restarts its randomized election timeout at the start of an election, and it waits for that timeout to elapse before starting the next election

**5.3 Log replication**

> Once a leader has been elected, it begins servicing client requests. Each client request contains a command to be executed by the replicated state machines. The leader appends the command to its log as a new entry, then issues `AppendEntries` RPCs in parallel to each of the other servers to replicate the entry. When the entry has been safely replicated (as described below), the leader applies the entry to its state machine and returns the result of that execution to the client. If followers crash or run slowly, or if network packets are lost, the leader retries `AppendEntries` RPCs indefinitely (even after it has responded to the client) until all followers eventually store all log entries.
>
> The leader decides when it is safe to apply a log entry to the state machines; such an entry is called **committed**.
>
> Once a follower learns that a log entry is committed, it applies the entry to its local state machine (in log order).
>
> simple consistency check performed by `AppendEntries`. When sending an `AppendEntries` RPC, the leader includes the index and term of the entry in its log that immediately precedes the new entries.
>
> Leader crashes can leave the logs inconsistent.
>
> The leader handles inconsistencies by forcing the followers’ logs to duplicate its own. This means that conflicting entries in follower logs will be overwritten with entries from the leader’s log.
>
> To bring a follower’s log into consistency with its own, the leader must find the latest log entry where the two logs agree, delete any entries in the follower’s log after that point, and send the follower all of the leader’s entries after that point. All of these actions happen in response to the consistency check performed by `AppendEntries`.
>
> The leader maintains a **nextIndex** for each follower, which is the index of the next log entry the leader will send to that follower. When a leader first comes to power, it initializes all nextIndex values to the index just after the last one in its log.
>
> A leader never overwrites or deletes entries in its own log.

**5.4 Safety**

> This section completes the Raft algorithm by adding a restriction on which servers may be elected leader.

**5.4.1 Election restriction**

> Log entries only flow in one direction, from leaders to followers, and leaders never overwrite existing entries in their logs.
>
> A candidate must contact a majority of the cluster in order to be elected, which means that every committed entry must be present in at least one of those servers. 
>
> Raft determines which of two logs is more up-to-date by comparing the index and term of the last entries in the logs.

**5.4.2 Committing entries from previous terms**

> A leader knows that an entry from its current term is committed once that entry is stored on a majority of the servers.
>
> Raft never commits log entries from previous terms by counting replicas.
>
> Raft incurs this extra complexity in the commitment rules because log entries retain their original term numbers when a leader replicates entries from previous terms.

**5.4.3 Safety argument**

Proof by contradiction: 

> The leaders of all terms greater than T must contain all entries from term T that are committed in term T.

**5.5 Follower and candidate crashes**

> If a follower or candidate crashes, then future RequestVote and AppendEntries RPCs sent to it will fail. Raft handles these failures by retrying indefinitely; if the crashed server restarts, then the RPC will complete successfully. If a server crashes after completing an RPC but before responding, then it will receive the same RPC again after it restarts.
>
> Raft RPCs are idempotent, so this causes no harm.

**5.6 Timing and availability**

> If message exchanges take longer than the typical time between server crashes, candidates will not stay up long enough to win an election
>
> The broadcast time should be an order of magnitude less than the election timeout so that leaders can reliably send the heartbeat messages required to keep followers from starting elections; given the randomized approach used for election timeouts, this inequality also makes split votes unlikely.

**6. Cluster membership changes**

> In order to ensure safety, configuration changes must use a two-phase approach. There are a variety of ways to implement the two phases.

**7. Log compaction**

> Snapshotting is the simplest approach to compaction.
>
> Incremental approaches to compaction, such as log cleaning and log-structured merge trees, are also possible.
>
> The leader uses a new RPC called `InstallSnapshot` to send snapshots to followers that are too far behind.
>
> This snapshotting approach departs from Raft’s strong leader principle, since followers can take snapshots without the knowledge of the leader.
>
> state machines built with functional data structures naturally support copy-on-write techniques so that new updates can be accepted without impacting the snapshot being written.

**8. Client interaction**

> Clients of Raft send all of their requests to the leader. When a client first starts up, it connects to a randomly chosen server. If the client’s first choice is not the leader, that server will reject the client’s request and supply information about the most recent leader it has heard from (`AppendEntries` requests include the network address of the leader). If the leader crashes, client requests will time out; clients then try again with randomly-chosen servers.

**9. Performance**

—

**10. Related work**

> Log entries in Raft flow in only one direction: outward from the leader in `AppendEntries` RPCs.
>
> Raft has only 4 message types (two RPC requests and their responses).

### Other materials

There are other Raft-related documents here: https://ramcloud.atlassian.net/wiki/display/RAM/RAMCloud+Presentations (accessed 20170421).

 * [Ongaro and Ousterhout, "Designing for Understandability- the Raft Consensus Algorithm" (20160829)](../materials/Ongaro_and_Ousterhout,_Designing_for_Understandability-_the_Raft_Consensus_Algorithm_20160829.pdf)
 * There are useful "quiz" questions in Appendix A of Diego Ongaro's thesis: [Ongaro thesis, Consensus- Bridging theory and practice 20141029](../materials/Ongaro_thesis,_Consensus-_Bridging_theory_and_practice_20141029.pdf) (original at https://ramcloud.stanford.edu/~Eongaro/thesis.pdf, accessed 20170421), along with good summary material about Paxos. (Document created 20140829, accessed 20170421.)
 * [Ongaro, "Leader Election RAMCloud Lunch Talk" (20131212)](../materials/Ongaro,_Leader_Election_RAMCloud_Lunch_Talk_20131212.pdf)
 * [Ongaro and Ousterhout, "The Raft Concensus Algorithm" (20131030)](../materials/Ongaro_and_Ousterhout,_The_Raft_Concensus_Algorithm_20131030.pdf)

---

 * https://github.com/jepsen-io/maelstrom. Most useful for me for testing; see also Ongaro's thesis.

[end]
