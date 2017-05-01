## B⁺-tree coding project

 1. Tricky ideas:
 
    1. Fundamentally a B⁺-tree is not a tree but a linked list. However, the list-nodes' values are indexed by means of a tree.

    1. Pointers needed to create the doubly linked list of leaves are not added in a separate traversal of the tree; they are available immediately at the moments when nodes are ramified from other nodes. Only the "ripple up" (Aho) or "propagation up" (Wirth) of merging and deletion involves some amount of traversal after `search`.
    
    1. "Balancing" of pages can be done during search. This is most clearly discussed in Knuth and Cormen. Wirth describes this:
    
       > … page splitting should be delayed in the same way that page merging is delayed, by first attempting to balance neighboring pages.
    
    1. In the published descriptions, a "branch" node is a sandwich of values (for navigation only) and pointers to children, in alternation. Perhaps this came more naturally in pointer-based languages; for modeling it in JS, suggest using different datatypes for data and pointers, and hard-code:
    
       1. the invariants defining sorted order
       2. insertion without allowing duplicates
       3. counting values alone
       4. counting pointers alone
       5. handling mergers and splits.

 1. Can we show its construction, step by step? Initially I thought I would try this with [d3.js](https://github.com/d3/d3/wiki). But now I'm leaning toward SVG, which seems a more useful general skill and is the foundation of d3.

 1. Names
 
    1. "Multiway Tree" (Knuth, Wirth, Aho) is the general type of which a B-tree is a subvariety.
    1. B-tree. Comer (p. 123):
    
       > The origin of "B-tree" has never been explained by the authors.  As we shall see, "balanced," "broad," or "bushy" might apply. Others suggest that the "B" stands for Boeing [DPB: Bayer and McCreight were Boeing engineers at the time of their 1972 paper]. Because of his contributions, however, it seems appropriate to think of B-trees as "Bayer"-trees.
       
       Gräfe:
       
       > This design has been called B⁺-tree but it is nowadays the default design when B-trees are discussed.

 1. Components (pseudocode has now been moved to working repository and coded over):

    1. `Window` globals (still don't have a satisfactory way of handling these)
    1. `Node`
    1. `search`
    2. `insert`
    2. `delete`
    2. `checkOverflow`
    2. `checkUnderflow`
    2. `split`
    2. `merge` (Goodrich: "fusion")
    2. helper functions

 1. Extra elements in the Wikipedia article:

    1. prefix-key compression — add this later
    2. bulk-loading — this involves finding a range; there are other terms for it in some of the other presentations.

### References:

#### B⁺-tree

 1. Cormen et al., 3rd ed., p. 481:
 
    > Because disks operate much more slowly than random-access memory, we measure the performance of B-trees not only by how much computing time the dynamic-set operations consume but also by how many disk accesses they perform. For each B-tree operation, the number of disk accesses increases with the height of the B-tree, but B-tree operations keep the height low.

    The full text of the first edition is on line at [the University of Science and Technology of China](http://staff.ustc.edu.cn/~csli/graduate/algorithms/book6/toc.htm); the B-tree section is numbered [Chapter 19](http://staff.ustc.edu.cn/~csli/graduate/algorithms/book6/chap19.htm) there.

 1. Donald Knuth, "Multiway Trees", _The Art of Computer Programming_ (2nd ed.), Sec. 6.2.4 (Vol. 3, pp. 481-9, n.b. exercises pp. 490-1). The main discussion of B-trees ("*B*-trees"; Knuth is very particular about typography\*) specifies (p. 483):
 
    > …A "leaf" is a terminal node, one with no children. Since the leaves carry no information, we may regard them as external nodes that aren't really in the tree, so that Λ is a pointer to a leaf. [DPB: In this book Λ stands for "pointer to null address", Sec. 2.1, Vol. 1, p. 234.]
    
    But the B⁺-tree is covered under subsection "Refinements and variations" (Vol. 3, pp. 486-9), and Knuth modifies the general definition (p. 486):

    > We might use a completely different node format in each level of the tree, and we might also store information in the leaves. Sometimes the keys form only a small part of the records in a file, and in such cases it is a mistake to store the entire records in the branch nodes near the root of the tree; this would make *m* too small for efficient multiway branching.
    > 
    > We can therefore reconsider Fig. 30, imagining that all the records of the file are now stored in the leaves, and that only a few of the keys have been duplicated in the branch nodes. Under this interpretation, the leftmost leaf contains all records whose key is ≤ 011; the leaf marked *A* contains all records whose key satisfies
    >
    > 　　　　　　439 < *K* ≤ 449;　　　　(8)
    >
    > and so on. Under this interpretation the leaf nodes grow and split just as the branch nodes do, except that a record is never passed up from a leaf to the next level. Thus the leaves are always at least half filled to capacity. A new key enters the nonleaf part of the tree whenever a leaf splits. If each leaf is linked to its successor in symmetric order [DPB: I think this means a doubly-linked list], we gain the ability to traverse the file both sequentially and randomly in an efficient and convenient manner. This variant has become known as a *B⁺*-tree. [DPB: This last sentence is all that was added from the first edition of the text.]
    
    I've been puzzling about this for some time — wouldn't linking leaves symmetrically always require some further traversal of the tree, whenever a leaf is inserted or deleted? But none of the descriptions I've seen include this traversal. Why?
    
    Thinking about it for a while, I now see that every insertion begins as the splitting of an existing leaf into either two leaves or its conversion into a branch node and spawning of new leaves. In either case, all the pointers needed are already to hand. No new traversal of the tree is needed. Deletions, too, require no new traversal of the tree — all the pointers needed are already to hand.

    \* On p. 489 of this section, Knuth remarks that "Two of the most interesting developments of the basic *B*-tree strategy have unfortunately been given almost [DPB: !] identical names: "*SB*-trees" and "SB-trees".

 1. [Visualization on David Galles' site](http://www.cs.usfca.edu/~galles/visualization/BPlusTree.html). Questions:
 
    * It accepts duplicate keys; I think that is an error.
    * Because it accepts duplicate keys, finding a key that is a duplicate returns only one such key, not all of them. It's not clear which one is found.
    * Perhaps because it accepts duplicate keys, deleting one of those duplicates sometimes leaves branch nodes without content. It's not clear how traversal goes in such a case or which one is deleted.
    * After branch nodes cease to have content, adding another duplicate proceeds in a different way than when there were no empty branch nodes.
 
 1. [Wikipedia article](https://en.wikipedia.org/wiki/B+_tree)
 1. [Douglas Comer, "The Ubiquitous B-Tree,"](https://github.com/tpn/pdfs/blob/master/The%20Ubiquitous%20B-Tree%20-%201979%20%28comer-b-tree%29.pdf) ACM _Computing Surveys_, Vol ll, No 2, June 1979, pp. 121-37. [Local copy here](../materials/Douglas_Comer,_The_Ubiquitous_B-Tree.pdf).

    > The author thanks the referees, especially for providing contacts regarding the history of B-trees, and IBM Corporation for cheerfully making available detailed information on its B-tree based access method when none of its competitors would reveal theirs. (p. 136)

    TODO: Write up notes on reading.

 1. Steve S. Skiena, _Algorithm Design Manual_. Ch. 12 "Data Structures", Sec. 12.1 "Dictionaries". P. 370:
 
    > The idea behind a B-tree is to collapse several levels of a binary search tree into a single large node, so that we can make the equivalent of several search steps before another disk access is needed. With B-tree we can access enormous numbers of keys using only a few disk accesses. To get the full benefit from using a B-tree, it is important to understand how the secondary storage device and virtual memory interact, through constants such as page size and virtual/real address space. Cache-oblivious algorithms (described below) can mitigate such concerns.

 1. [Amruta Kudale, "B⁺ tree preference over B trees"](http://www.academia.edu/11575258/B_tree_preference_over_B_trees) [Local copy here](../materials/Amruta_Kudale,_B_tree_preference_over_B_trees.pdf). This paper is poorly proofread but seems to be a survey of main ideas: summarizes special features of B⁺ trees (Sec. III.C) and their advantages over ordinary B trees (Sec. IV.A).

 1. Gräfe.

    The Gräfe book says (Sec. 2.1, p. 213):
    
    > The original design for B-trees has user data in all nodes. The design used much more commonly today holds user data only in the leaf nodes. The root node and the branch nodes contain only separator keys that guide the search algorithm to the correct leaf node. These separator keys may be equal to keys of current or former data, but the only requirement is that they can guide the search algorithm.
    >
    > This design has been called B⁺-tree but it is nowadays the default design when B-trees are discussed. The value of this design is that deletion can affect only leaf nodes, not branch nodes and that separator keys in branch nodes can be freely chosen within the appropriate key range.
    
    There are two key differences between a vanilla B-tree and a B⁺-tree:
    
    * As mentioned, B⁺-tree holds data only the leaf nodes; the branch nodes are used for navigation only.
    
    * In a B⁺-tree, the leaf nodes are a linked list independent of the branch nodes. Comer explains:
     
      > In particular, leaf nodes are usually linked together left-to-right, as shown. The linked list of leaves is referred to as the sequence set. Sequence set links allow easy sequential processing.
    
    Nowhere that I can see does Gräfe discuss this linking of leaves. However, Gräfe does discuss something called a "Bˡⁱⁿᵏ-tree", involving a pointer between two nodes on the same level (Sec. 4.6, pp. 283-86). However, as far as I can see, this is used only for load-balancing between branch nodes (Comer's "index nodes") in the case of overflow.

    In the Gräfe article he repeats (p. 16:4) that he uses "B-tree" to mean what Comer calls a "B⁺-tree". And he adds (p. 16:4): 
    
    > We also ignore many other variations of B-trees here. This includes what Comer [1979], following Knuth, calls B\*-trees, that is, attempting to merge an overflowing node with a sibling rather than splitting it immediately. We ignore whether or not underflow is recognized and acted upon by load balancing and merging nodes, whether or not empty nodes are removed immediately or ever, **whether or not leaf nodes form a singly or doubly linked list** using physical pointers (page identifiers) or logical boundaries (fence keys equal to separators posted in the parent node during a split), whether suffix truncation is employed when posting a separator key [Bayer and Unterauer 1977], whether prefix truncation or any other compression is employed on each page, and the type of information associated with B-tree keys. **Most of these issues have little or no bearing on locking in B-trees, with the exception of sibling pointers, as indicated in the following where appropriate.**
    
    But the only place where "sibling pointers" are mentioned is this (p. 16:9):
    
    > … **"pointer chasing" applies not only to parent-child pointers but also to neighbor pointers, such as, in a chain of leaf pages during a range scan or while searching for the key to lock in key range locking** (see the following). 
    
    and "the following" turns out to be, again, a reference to "Bˡⁱⁿᵏ-trees".  So that leaves only range scans, and they are basically not treated in either article or book.

 1. [David Lomet, "The Evolution of Effective B-tree: Page Organization and Techniques- A Personal Account"](../materials/David_Lomet,_The_Evolution_of_Effective_B-tree-_Page_Organization_and_Techniques-_A_Personal_Account.PDF). Not very useful, but contains a series of approaches to B-tree efficiency

 1. [Rudolf Bayer and Karl Unterauer, "Bayer and Unterauer, Prefix B-trees"](../materials/Bayer_and_Unterauer,_Prefix_B-trees.pdf)
 
    TODO: Write up notes on reading.

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

 1. Aho, Hopcroft, and Ullman, _Data Structures and Algorithms_ (1983), Sec. 11.4 "External Search Trees," pp. 368-74. Notes:

    * Used to "represent external files".
    * Special type of "multiway search tree" (_q.v._)
    * lookup: within a node can use linear search or, if there are many keys, binary search
    * splitting blocks: if inserting a new leaf violates the invariants, "the effects of this insertion can **ripple up** (p. 370) through the ancestors of [the leaf] back to the root, along the path that was traced by the original lookup procedure."
    * combining blocks: if deleting a leaf violates the invariants, parents may need to be combined, rippling up to the root
    * cf. "Comparison of Methods" (pp. 373-74)

 1. Wirth, _Algorithms + Data Structures = Programs_ (1976), Sec. 4.5.1 "B-Trees," pp. 245-64. Notes:

    * Special type of "multiway tree" (_q.v._)
    * Cf. binary b-trees
    * relaxation of stricture that tree must be "perfectly balanced", due to Bayer and McCreight (1972).
    * If each node is a memory access, then the number of memory accesses in minimized, as long as there is a "schema for controlled growth", in order to prevent the tree from growing "at random."
    * search: as in binary search tree, only not binary
    * distinguish "special nodes" (pp. 191-92) from leaves; I don't understand the distinction
    * "root page is best allocated permanently in the primary store because each query proceeds necessarily from the root page" (p. 250)
    * "balancing" two pages: "annecting" a key: borrowing it from an adjacent page
    * Merging may "propagate" all the way up to the root
    * TODO: unfinished — both addition of matter and editing of what is already here.

[end]
