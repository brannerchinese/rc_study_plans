## Database Internals

### Articles

 * [Christophe Kalenzaga, "How does a relational database work?"](../materials/Christophe_Kalenzaga,_How_does_a_relational_database_work.pdf) (**[external link](http://coding-geek.com/how-databases-work/)**) **[Notes](notes_kalenzaga_relational_database.md)**

 * [Hellerstein, Stonebraker, and Hamilton, "Architecture of a Database System"](../materials/Hellerstein,_Stonebraker,_and_Hamilton,_Architecture_of_a_Database_System.pdf) (**[external link](https://db.cs.berkeley.edu/papers/fntdb07-architecture.pdf)**)

 * [Conrad Muller, "A Brief Explanation of How Database Software Works"](../materials/Conrad_Muller,_A_Brief_Explanation_of_How_Database_Software_Works.pdf) (**other references [on this site](http://www.databasezone.com/techdocs/)**)

 * [Will Hartung, response on StackOverflow 172925-621762 to "How do databases work internally?"](../materials/Will_Hartung,_response_on_StackOverflow_172925-621762_How_do_databases_work_internally?.pdf) (**[external link](http://stackoverflow.com/a/172992/621762)**)

#### Indexing and B+ trees

 * [Jeremy Cole, "The physical structure of InnoDB index pages"](Jeremy_Cole,_The_physical_structure_of_InnoDB_index_pages.pdf) (**[external link](https://blog.jcole.us/2013/01/07/the-physical-structure-of-innodb-index-pages/)**)
 
 * [Jeremy Cole, "B+ Tree index structures in InnoDB"](../materials/Jeremy_Cole,_B+Tree_index_structures_in_InnoDB.pdf) (**[external link](https://blog.jcole.us/2013/01/10/btree-index-structures-in-innodb/)**)

 * [Goetz Graefe, "Modern B-Tree Techniques"](../materials/Goetz_Graefe,_Modern_B-Tree_Techniques.pdf) (**[external link](http://dl.acm.org/citation.cfm?id=2185842)**)

#### Query-optimization

 * Algorithms: [Stoyan Vellev, "Review of Algorithms for the Join Ordering Problem in Database Query Optimization"](../materials/Stoyan_Vellev,_Review_of_Algorithms_for_the_Join_Ordering_Problem_in_Database_Query_Optimization.pdf) (**[external link](http://www.acad.bg/rismim/itc/sub/archiv/Paper6_1_2009.PDF)**)

 * In DB2: [Guy M. Lohman, "DB2 for Linux, UNIX, and Windows Optimizer"](../materials/Guy_M._Lohman,_DB2_for_Linux,_UNIX,_and_Windows_Optimizer.pdf) (**[external link](http://infolab.stanford.edu/~hyunjung/cs346/db2-talk.pdf)**)

 * In Postgres: [Bruce Momjian, "Explaining the Postgres Query Optimizer"](../materials/Bruce_Momjian,_Explaining_the_Postgres_Query_Optimizer.pdf) (**[external link](https://momjian.us/main/writings/pgsql/optimizer.pdf)**)

 * In SQLite
 
   * general: [SQL documentation: "The SQLite Query Planner"](../materials/SQL_documentation_The_SQLite_Query_Planner.pdf) (**[external link](https://www.sqlite.org/optoverview.html)**)

   * NGQP: [SQL documentation: "The Next-Generation Query Planner"](../materials/SQL_documentation_The_Next-Generation_Query_Planner.pdf) (**[external link](https://www.sqlite.org/queryplanner-ng.html)**)

 * Statistics in: [PostgreSQL 9.4.11 Documentation, Chapter 61. "How the Planner Uses Statistics"](../materials/PostgreSQL_9.4.11_Documentation_Chapter_61_How_the_Planner_Uses_Statistics.pdf) (**[external link](https://www.postgresql.org/docs/9.4/static/row-estimation-examples.html)**)

 * Cost-based optimization (CBO): [Selinger et al., "Access Path Selection in a Relational Database Management System"](../materials/Selinger_et_al.,_Access_Path_Selection_in_a_Relational_Database_Management_System.pdf) (**[external link](https://www.cs.berkeley.edu/~brewer/cs262/3-selinger79.pdf)**)

#### Transaction management

 * multiversion concurrency control in PostgreSQL: [Bruce Momjian, "Mvcc Unmasked"](../materials/Bruce_Momjian,_Mvcc_Unmasked.pdf) (**[external link](https://momjian.us/main/writings/pgsql/mvcc.pdf)**)

 * locks and latches: [Goetz Graefe, "A Survey of B-Tree Locking Techniques"](../materials/Goetz_Graefe,_A_Survey_of_B-Tree_Locking_Techniques.pdf) (**[external link](http://dl.acm.org/citation.cfm?id=1806908)**)

### Links to blogs

 * [Craig Freedman, 2008-10](https://blogs.msdn.microsoft.com/craigfr/)
 * [Kalen Delaney on SQLblog.com, 2006-16](http://sqlblog.com/search/SearchResults.aspx?q=Kalen+Delaney)

[end]
