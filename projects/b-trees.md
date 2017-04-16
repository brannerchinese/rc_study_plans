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
 1. Donald Knuth, "Multiway Trees", _The Art of Computer Programming_ (2nd ed.), Sec. 6.2.4 (pp. 481-9, n.b. exercises pp. 490-1).
 1. [Douglas Comer, "The Ubiquitous B-Tree,"](https://github.com/tpn/pdfs/blob/master/The%20Ubiquitous%20B-Tree%20-%201979%20%28comer-b-tree%29.pdf) ACM _Computing Surveys_, Vol ll, No 2, June 1979, pp. 121-37. [Local copy here](../materials/Douglas_Comer,_The_Ubiquitous_B-Tree.pdf).

    > The author thanks the referees, especially for providing contacts regarding the history of B-trees, and IBM Corporation for cheerfully making available detailed information on its B-tree based access method when none of its competitors would reveal theirs. (p. 136)
    >
    > ...
    > 
    > The origin of "B-tree" has never been explained by the authors.  As we shall see, "balanced," "broad," or "bushy" might apply. Others suggest that the "B" stands for Boeing [dpb: Bayer and McCreight were Boeing engineers at the time of their 1972 paper]. Because of his contributions, how- ever, it seems appropriate to think of B-trees as "Bayer"-trees. (p. 123)

 1. [Amruta Kudale, "B+ tree preference over B trees"](http://www.academia.edu/11575258/B_tree_preference_over_B_trees) [Local copy here](../materials/Amruta_Kudale,_B_tree_preference_over_B_trees.pdf). This paper is poorly proofread but seems to be a survey of main ideas: summarizes special features of B+ trees (Sec. III.C) and their advantages over ordinary B trees (Sec. IV.A).

 1. Gräfe.

    The Gräfe book says (Sec. 2.1, p. 213):
    
    > The original design for B-trees has user data in all nodes. The design used much more commonly today holds user data only in the leaf nodes. The root node and the branch nodes contain only separator keys that guide the search algorithm to the correct leaf node. These separator keys may be equal to keys of current or former data, but the only requirement is that they can guide the search algorithm.
    >
    > This design has been called B⁺-tree but it is nowadays the default design when B-trees are discussed. The value of this design is that deletion can affect only leaf nodes, not branch nodes and that separator keys in branch nodes can be freely chosen within the appropriate key range.
    
    There are two key differences between a vanilla B-tree and a B+-tree:
    
    * As mentioned, B+-tree holds data only the leaf nodes; the branch nodes are used for navigation only.
    
    * In a B+-tree, the leaf nodes are a linked list independent of the branch nodes. Comer explains:
     
      > In particular, leaf nodes are usually linked together left-to-right, as shown. The linked list of leaves is referred to as the sequence set. Sequence set links allow easy sequential processing.
    
    Nowhere that I can see does Gräfe discuss this linking of leaves. However, Gräfe does discuss something called a "Bˡⁱⁿᵏ-tree", involving a pointer between two nodes on the same level (Sec. 4.6, pp. 283-86). However, as far as I can see, this is used only for load-balancing between branch nodes (Comer's "index nodes") in the case of overflow.

    In the Gräfe article he repeats (p. 16:4) that he uses "B-tree" to mean what Comer calls a "B⁺-tree". And he adds (p. 16:4): 
    
    > We also ignore many other variations of B-trees here. This includes what Comer [1979], following Knuth, calls B\*-trees, that is, attempting to merge an overflowing node with a sibling rather than splitting it immediately. We ignore whether or not underflow is recognized and acted upon by load balancing and merging nodes, whether or not empty nodes are removed immediately or ever, **whether or not leaf nodes form a singly or doubly linked list** using physical pointers (page identifiers) or logical boundaries (fence keys equal to separators posted in the parent node during a split), whether suffix truncation is employed when posting a separator key [Bayer and Unterauer 1977], whether prefix truncation or any other compression is employed on each page, and the type of information associated with B-tree keys. **Most of these issues have little or no bearing on locking in B-trees, with the exception of sibling pointers, as indicated in the following where appropriate.**
    
    But the only place where "sibling pointers" are mentioned is this (p. 16:9):
    
    > … **"pointer chasing" applies not only to parent-child pointers but also to neighbor pointers, such as, in a chain of leaf pages during a range scan or while searching for the key to lock in key range locking** (see the following). 
    
    and "the following" turns out to be, again, a reference to "Bˡⁱⁿᵏ-trees".  So that leaves only range scans, and they are basically not treated in either article or book.

 1. [David Lomet, "The Evolution of Effective B-tree- Page Organization and Techniques- A Personal Account"](../materials/David_Lomet,_The_Evolution_of_Effective_B-tree-_Page_Organization_and_Techniques-_A_Personal_Account.PDF)

 1. [Rudolf Bayer and Karl Unterauer, "Bayer and Unterauer, Prefix B-trees"](../materials/Bayer_and_Unterauer,_Prefix_B-trees.pdf)

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
