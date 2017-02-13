## The Graph abstract data-type and the Tree data-structure

 1. **Wirth**. Niklaus Wirth, _Algorithms + Data Structures = Programs_. Englewood Cliffs, NJ: Prentice-Hall, Inc., 1976.
    
    Examples are written in **PASCAL**, with a parser introduced in Chapter 5 for **PL/0**. Topics of immediate interest:
    
    * Chapter 4, "Dynamic Information Structures"
    
      * 4.4 "Tree Structures"
      * 4.5 "Multiway Trees"

    * Chapter 5, "Language Structures and Compilers"
    
      * 5.3 "Constructing a Syntax Graph"

 1. **Aho et al**. Alfred V. Aho, John E. Hopcroft, and Jeffrey D. Ullman, _Data Structures and Algorithms_. Reading, Mass.: Addison-Wesley Publishing Company, 1983.
    
    Examples are written in "**super Pascal**", a superset of Pascal with three additional features: non-numeric labels, return statements, and expressions as names of types. Topics of interest to me are integrated with the treatment of sets, but the chapters of immediate interest to me are:
    
    * Chapter 3, "Trees"
    * Chapter 5, "Advanced Set Representation Methods" (includes binary search trees, tries, balanced tree implementations of sets)
    * Chapter 6, "Directed Graphs"
    * Chapter 6, "Undirected Graphs"
    
 1. **Esakov and Weiss**. Jeffrey Esakov and Tom Weiss, _Data Structures: An advanced approach using C_. Englewood Cliffs, New Jersey: Prentice Hall, 1989.
 
    Examples are written in C. This book features several concrete applications that may be useful as project-ideas. Chapters of immediate interest:
    
    * Chapter 7, "Trees and Graphs"
 
 1. **Gamma et al**. Erich Gamma, Richard Helm, Ralph E Johnson, and John Vlissides, _Design Patterns_. Boston: Addison-Wesley, 1995.
 
    Examples are in C++ and sometimes Smalltalk (see pp. 3-4). Index is useless. Sections of immediate interest:
     
    * "Visitor": pp. 331-44
    
      > Represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.

    * "Iterator" (or "cursor"): pp. 257-71
    
      > Provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation.

    * "Adapter": pp. 139-50. Includes discussion of "`TreeDisplay` widget that can display tree structures graphically":
     
      > Consider a TreeDisplay widget that can display tree structures graphically. If this were a special-purpose widget for use in just one application, then we might require the objects that it displays to have a specific interface; that is, all must descend from a Tree abstract class. But if we wanted to make TreeDisplay more reusable (say we wanted to make it part of a toolkit of useful widgets), then that requirement would be unreasonable. Applications will define their own classes for tree structures. They shouldn't be forced to use our Tree abstract class. Different tree structures will have different interfaces.
      >
      > In a directory hierarchy, for example, children might be accessed with a GetSubdirectories operation, whereas in an inheritance hierarchy, the corresponding operation might be called GetSubclasses. A reusable TreeDisplay widget must be able to display both kinds of hierarchies even if they use different interfaces. In other words, the TreeDisplay should have interface adaptation built into it.

    * "Composite: pp. 163-73

      > Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly.

    * "Interpreter": pp. 243-55

      > Given a language, define a represention for its grammar along with an interpreter that uses the representation to interpret sentences in the language.

    * "Abstract Factory" (or "kit"): pp. 87-95

      > Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

 
 1. **Kleinberg and Tardos**. Jon Kleinberg and Éva Tardos, _Algorithm Design_, Boston: Pearson/Addison Wesley, 2006.
 
    Examples are in pseudocode. Sections of immediate interest:
    
    * Chapter 3: "Graphs"
    * Section 4.4: "Shortest Paths in a Graph"
    * Section 4.5: "The Minimum Spanning Tree Problem"
    * Section 4.6: "Implementing Kruskal's Algorithm"
    * Section 4.7: "Clustering"
    * Section 4.8: "Huffman Codes and Data Compression"
    * Section 4.8: "Minimum-Cost Arborescences"
    * Section 6.8: "Shortest Paths in a Graph"
    * Section 6.9: "Shortest Paths and Distance Vector Protocols"
    * Section 6.10: "Negative Cycles in a Graph"
    * Chapter 7: "Network Flow"
    * Chapter 10: "Extending the Limits of Tractability"

 1. **Cormen et al**. Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, and Clifford Stein, _Introduction to Algorithms_.  Third edition. Cambridge, Mass.: MIT Press, 2009.
 
    Examples are in pseudocode (revised in third edition) to use `=` for assignment and `==` for equality (conventions are listed on pp. 20-22). Sections of immediate interest:
    
    * Chapter 12: "Binary Search Trees"
    * Chapter 13: "Red-Black Trees"
    * Chapter 14: "Augmenting Data Structures"
    * Section 16.3: "Huffman codes"
    * Section 16.4: "Matroids and greedy methods"
    * Section 16.5: "A task=-scheduling problem as a matroid"
    * Chapter 18: "B-Trees"
    * Chapter 19: "Fibonacci Heaps"
    * Chapter 20: "van Emde Boas Trees"
    * Chapter 21: "Data Structures for Disjoint Sets"
    * Chapter 22: "Elementary Graph Algorithms"
    * Chapter 23: "Minimum Spanning Trees"
    * Chapter 24: "Single-Source Shortest Paths"
    * Chapter 25: "All-Pairs Shortest Paths"
    * Chapter 26: "Maximum Flow"
    * Chapter 35: "Approximation Algorithms"
    * Appendix B.4: "Graphs"
    * Appendix B.5: "Trees"

[end]