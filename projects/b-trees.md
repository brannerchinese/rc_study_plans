## "B+-tree coding project

 1. B+ tree. (JS). Use a graphical library to show it. Further items:
 
    2. Can we show its construction, step by step? It would be nice to try this with [d3.js](https://github.com/d3/d3/wiki).  

 1. Components:

    2. search
    2. insertion
    2. deletion

 1. Extra elements in the Wikipedia article:

    2. prefix-key compression
    2. bulk-loading

### References:

#### B+ tree

 1. [Visualization on David Galles' site](http://www.cs.usfca.edu/~galles/visualization/BPlusTree.html)
 1. [Wikipedia article](https://en.wikipedia.org/wiki/B+_tree)
 1. [Douglas Comer, "The Ubiquitous B-Tree,"](https://github.com/tpn/pdfs/blob/master/The%20Ubiquitous%20B-Tree%20-%201979%20%28comer-b-tree%29.pdf) ACM _Computing Surveys_, Vol ll, No 2, June 1979, pp. 121-37. [Local copy here](../materials/Douglas_Comer,_The_Ubiquitous_B-Tree.pdf).

    > The author thanks the referees, especially for provid- ing contacts regarding the history of B-trees, and IBM Corporation for cheerfully making available detailed information on its B-tree based access method when none of its competitors would reveal theirs. 

 1. [Amruta Kudale, "B+ tree preference over B trees"](http://www.academia.edu/11575258/B_tree_preference_over_B_trees) [Local copy here](../materials/Amruta_Kudale,_B_tree_preference_over_B_trees.pdf). Survey of main ideas: summarizes special features of B+ trees (Sec. III.C) and their advantages over ordinary B trees (Sec. IV.A).

#### B-tree

These are generally discussed as memory-efficiencies. Rather than storing data _per se_, they generally store memory locations, 

 1. Goodrich et al., _Data Structures and Algorithms in Python_, sec. 15.3.2, p. 714, "B-Trees". Notes:

    * Special type of `(a,b)` tree (_q.v._)
    * "I/O complexity"

      > … We refer to the transfer of a block between secondary memory and primary memory as a **disk transfer**. Recalling the great time difference that exists between main memory accesses and disk access, **the main goal of maintaining such a collection in external memory is to minimize the number of disk transfers** needed to perform a query or update. (p. 711)
    
    * handling overflow and underflow
    * fusion operation
    * cf. inefficient external-memory representations
    * cf. `(a,b)` trees

 1. Aho, Hopcroft, and Ullman, _Data Structures and Algorithms_, Sec. 11.4 "External Search Trees," pp. 368-74. Notes:

    * Used to "represent external files".
    * Special type of "multiway search tree" (_q.v._)
    * lookup: within a node can use linear search or, if there are many keys, binary search
    * splitting blocks: if inserting a new leaf violates the invariants, "the effects of this insertion can **ripple up** through the ancestors of [the leaf] back to the root, along the path that was traced by the original lookup procedure."
    * combining blocks: if deleting a leaf violates the invariants, parents may need to be combined, rippling up to the root
    * cf. "Comparison of Methods" (pp. 373-74)

 1. Wirth, _Algorithms + Data Structures = Programs_, Sec. 4.5.1 "B-Trees," pp. 245-64. Notes:

    * Special type of "multiway tree" (_q.v._)
    * Cf. binary b-trees
    * relaxation of stricture that tree must be "perfectly balanced", due to Bayer and McCreight (1972).
    * If each node is a memory access, then the number of memory accesses in minimized, as long as there is a "schema for controlled growth", in order to prevent the tree from growing "at random."
    * search: as in binary search tree, only not binary
    * distinguish "special nodes" (pp. 191-92) from leaves; I don't understand the distinction
    * "root page is best allocated permanently in the primary store bedcause each query proceeds necessarily from the root page" (p. 250)
    * "annecting" a node: borrowing it from an adjacent page
    * (unfinished qqq)

[end]
