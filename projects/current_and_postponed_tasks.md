## Current and Postponed tasks

Postponed tasks are marked [Ｏ].

### **JS track**

#### **[B-tree implementation](b-trees.md)**

 * [　] Finish writing code.
 * [　] Learn SVG and begin adding SVG to working code.
 * [　] Explore [Treant.js](http://fperucic.github.io/treant-js/)
 * [　] Explore [Graph.js](https://github.com/mhelvens/graph.js)
 * [　] Explore [Sigma.js](http://sigmajs.org/)
 * [　] Explore [Gun.js](http://gun.js.org/#step1)
 * [Ｏ] Try out the preferred TDD options for JavaScript: UnitJS and SinonJS. 

#### **[Color-match project](color-match.md)**

 * [　] Color-match iteration 10: Describe dimensions of circle relative to viewport, rather than absolutely.
 * [　] Color-match iteration 11: Can you display hues of individual channel-fields? After this, time to work on actual color-match game.
 * [　] Color-match iteration: Try on other browsers.

 * [Ｏ] Color-match iteration: add a graphical picker (try for three linear sliders, one for each of RGB). This seems a lot more complicated than I had thought. Study the W3Schools implementation:

   * page: https://www.w3schools.com/colors/colors_picker.asp
   * JS: https://www.w3schools.com/lib/w3color.js
   
   and try to construct something simpler

 * [Ｏ] Color-match iteration: after graphical picker has been added, allow user to toggle numeric display on and off for learning.

#### **[Hànbûn columns project](hanbun-columns.md)**

This shouldn't take more than two good days of work.

 * [　] Hànbûn columns iteration: Make resizable frame no larger than open window/viewport.
 * [　] Hànbûn columns iteration: Within frame, create columnar subframes that wrap right-left.
 * [　] Hànbûn columns iteration: Populate subframes with characters, one to a row.
 * [　] Hànbûn columns iteration: Load page into iframe from elsewhere.

#### Reading and workshops

 * [Ｘ] Start reading about major JS graphical libraries of interest, beginning with list made earlier. **Disposition**: Under way with D3.js and SVG/SVG.js. Also, look at Treat.js and Sigma.js.

 * [　] Read about the peer-to-peer browser networking that Be Birchal described in in-person check-ins on 20170424.

 * [　] Read the [MDN article-series on Accessibility](https://developer.mozilla.org/en-US/docs/Learn/Accessibility) (note that the second-to-last item has a broken link to the last item)

   * [　] (Part of the above). Read about [ARIA](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics).

 * [　] Read the [MDN article-series on Client-side web APIs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs) (incomplete; "Video and audio APIs" is still in draft, and "Device APIs" and "Client-side storage APIs" are not posted)
 
   * [　] (Part of the above). Read the [MDN article on manipulating DOM elements](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents).

 
 * [　] Read next chapter in JS books.
 * [Ｏ] Read Coulman's Ramda.JS blogposts. **Postponed** after completing two. It's too early to be spending time with these.

### **Database infrastructure/Raft track**

 * [　] Review SQL
 * [　] Review NoSQL
 * [　] Read more about MongoDB specifically
 * [　] Read about networking terminology. 
 * [Ｘ] Explored differences between Raft algorithm and MongoDB's "replica set" model. Sources:
 
   * Kingsbury/Jepson, [critical paid review of MongoDB replication protocols 0 and 1](../materials/Kyle_Kingsbury_Jepsen_MongoDB_3.4.0-rc3_review_of_protocols_0_and_1.pdf), 20170207 ([original here](https://jepsen.io/analyses/mongodb-3-4-0-rc3))
   * "Stennie" (MongoDB employee) [comparison of Raft and MongoDB protocol 0 on StackOverflow](../materials/Stennie_on_StackOverflow,_Raft_vs_MongoDB_Primary_Election.pdf), 20140110 on StackOverflow ([original here](http://stackoverflow.com/a/21048400/621762))
   * Spencer Brody (MongdoDB employee) slide show ["Distributed Consensus in MongoDB":  Replication Election and Consensus Algorithm Refinements for MongoDB 3.2](../materials/Spencer_Brody,_Distributed_Consensus_in_MongoDB.pdf), 20150605 ([original here](https://www.slideshare.net/mongodb/replication-election-and-consensus-algorithm-refinements-for-mongodb-32))
   * Ankur Raina, ["MongoDB: The Latest Features-Replication" (description of protocolVersion 1), 20160426](../materials/Ankur_Raina,_MongoDB_The_Latest_Features-Replication.pdf) ([original here](http://info.tricoresolutions.com/blog/mongodb-the-latest-features-replication))
   * Reuben Bond, ["MongoDB Replication: The Journal Journal, The Global Lock, & Durability" (20140419)](Reuben_Bond,_MongoDB_Replication-The_Journal_Journal,_The_Global_Lock,_&_Durability.pdf) ([original here](http://daprlabs.com/blog/blog/2014/04/19/mongodb/))
 
 * [Ｘ] Implementing `JOIN`s in code: suggest generating cartesian product and filtering (but maybe there is a more efficient way):
 
   ```
   >>> dicts1 = ({'surname': 'Wilde', 'type': 'q'},
             {'surname': 'Smith', 'type': 'r'},
             {'surname': 'Irrelevant', 'type': 'z'})
   >>> dicts2 = ({'id': 1, 'name': 'Wilde'},
             {'id': 2, 'name': 'Jonson'},
             {'id': 3, 'name': 'Smith'})
   >>> tuple((d1, d2) for d1 in dicts1 
                  for d2 in dicts2
                  if d1['surname'] == d2['name'])
   (({'surname': 'Wilde', 'type': 'q'}, {'name': 'Wilde', 'id': 1}),
    ({'surname': 'Smith', 'type': 'r'}, {'name': 'Smith', 'id': 3}))
   ```

 * [Ｘ] Looked into MongoDB's recent implementation of an operator (`$lookup`) equivalent to the SQL `LEFT OUTER JOIN`; why no `INNER JOIN`?

 * [Ｏ] List made of items of interest. It seems likely that most of this work will be reading rather than implementation. In any  case, there is nothing more to do now but slowly assemble references.

### **Raft track**

 * [　] Implement a display of Raft, beginning with pseudocode.

### **RC togetherness**


### **Work-search**

 * [　] Do a one-day Flask project, putting stress on full-stack skills rather than the Python back-end.
 * [　] Fix code-issues in blog — including list of past entries (long postponed)


### **Python metaprogramming review**

 * [Ｘ] Reviewed examples of built-in decorators:
 
   * use-case of `@property` to produce protected variables
   * use-case of `@classmethod` for "alternate constructor" (i.e., bypassing `__init__`, though `__init__` is not exactly a constructor)
   * user-defined decorators: examined those used in PyMongo's sourcecode, but they're all built-ins or from `unittest`.
 * [Ｘ] Reviewed use of `inspect` for defining function signatures.

### **Technical writing**

 * [　] One or two of the documents in the repo may be suitable for quick rewriting as blog posts.

### **Environment track**

 * [　] Read the long `strace` discussion under the `mate-screenshot` script https://github.com/mate-desktop/mate-utils/issues/37#issuecomment-252103551.
 * [　] Read about Plan 9, a strongly file-oriented UNIX successor mentioned by AJ Jordan at in-person check-ins on 20170425.
 * [　] Find out what sorts of things are stored in `/etc`. Among many others, `/etc/debian_version` is there.
 * [Ｏ] Install current Firefox via command line and document process in installation notes. **Disposition**: adding the Mozilla PPA failed to change the version numbers of the Firefox candidate for installation.
 * [Ｘ] Discovered that my long efforts to use regex within `grep` were failing because I was not using `egrep`.
 
### Non-batch work

**"Face" book**

My collaborator feels well enough that on 20170407 she began criticizing my English again, for the first time in several years, and nagging me to get the book finished.

 * [　] Draft chapter on parts of speech and other conventions

 * [　] Pick up refactoring of old Python code: LaTeX-formatting of entries; handling of sentences; ordering of entries.


[end]
