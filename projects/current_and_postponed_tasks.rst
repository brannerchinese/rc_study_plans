Current and Postponed tasks
===========================

Completed tasks are marked [Ｘ]. Postponed tasks are marked [Ｏ].

:strong:`Contents`:

* `To be done immediately`_
* `On-going`_
* `Done`_
* `Summary of the break between the two halves of my batch`_


To be done immediately
----------------------

* [　] Write up VisidData decisions and set up documentation-notes repo.
* [　] Write up Kaggle tasks.
* [　] Write to Jobs.

Upcoming
--------

Kaggle
^^^^^^

* [　] Get practice with Jupyter and current Ipython configuration settings.
* [　] Read on the kaggle.com wiki.
* [　] Study the Quora problem privately.
* [Ｘ] Set up private repo for Kaggle project and invited the four other participants.

EMACS
^^^^^

* [　] Look at the Emacs introduction in `Clojure for the Brave and True <http://www.braveclojure.com/basic-emacs/>`_, recommended by Stacey and Logan.

Environment
^^^^^^^^^^^

* [　] Learn what the difference between `/dev/tty0` and `/dev/tty` actually is, and why `/dev/tty0` is being sought in the ``xorg`` upgrade. See
 
  * https://unix.stackexchange.com/questions/60641/linux-difference-between-dev-console-dev-tty-and-dev-tty0
  * https://unix.stackexchange.com/questions/229530/how-linux-uses-dev-tty-and-dev-tty0

Sphinx
^^^^^^

* [　] Learn about Docutils. See http://docutils.sourceforge.net/FAQ.html.
* [　] Read `A Record of reStructuredText Syntax Alternatives <http://docutils.sourceforge.net/docs/dev/rst/alternatives.html>`_
* [　] Choose code to document with Sphinx.

Testing
^^^^^^^

* [　] Write up old PyTest materials. See https://github.com/brannerchinese/pytest_tutorial_project.
* [　] Learn about Nose. See http://nose.readthedocs.io/en/latest/testing.html.

Jobs
^^^^

* [　] Prepare résumé for technical writing positions. 20170525: Wrote to RC Jobs to discussion position and whether application should go through RC or not; no response yet.
* [　] Examine coding practice sites:
 
  * CareerCup
  * TopCoder
  * GeeksforGeeks
  * Sphere Online Judge (SPOJ)
  * Project Euler
  * HackerRank
  * LeetCode Online Judge

* [　] Find possible pairing partner for interview coding practice.

VisiData
^^^^^^^^

* [Ｘ] Meet with Saul to discuss my role in the project. 20170524: Saul was too busy to do this. 20170525: Saul was too busy to do this today again. He gave a workshop today and published a brief user guide, but he never had a chance to work with me on these things as we had planned. 20170526: Made appointment. Had half-hour disussion — covered running locally, where to place notes, where to place docs, setting up GitHub organization, DPB's title and use on résumé, Sphinx, Nose or Pytest for testing.

----

On-going
--------

Sphinx
^^^^^^

* Practice reStructuredText by rewriting some Markdown content. 


Unix knowledge
^^^^^^^^^^^^^^

* Read in Eric S. Raymond, :emphasis:`The Art of Unix Programming`. Existence of `website <http://www.catb.org/esr/writings/taoup/html/>`_ should allow easy recording of :emphasis:`bon mots`.
 
  * 20170522: Have reached Sec. 4.4, starting at the beginning.

Interesting things learned
^^^^^^^^^^^^^^^^^^^^^^^^^^

reST
""""

* "Implicit hyperlink targets" (hyperlinks to section-titles) use a reduced form of the hyperlinking syntax: :literal:`\`Done\`_` rather than :literal:`\`Done <Done>\`_`
* To put a space in a reST literal, use :literal:`:literal:\`\\\ \``.
* Although the `Docutils site <http://docutils.sourceforge.net/FAQ.html#what-s-the-standard-filename-extension-for-a-restructuredtext-file>`_ says that the extension for reST files should be ``.txt``, GitHub does not recognize ``.txt`` files as reST, requiring ``.rst`` or ``.rest``.
* Convert Markdown external links to reST with ``\[([a-z].+?)\]\((.+?)\)`` => ```\1 <\2>`_``
* reST horizontal rule: four or more section-head characters, but with a blank line before them

Command-line tools
""""""""""""""""""

``shred``
  Overwrite a file to hide its contents, and optionally delete it.

``sudo apt list --upgradable``
  List only packages that are available to upgrade.

``sudo apt --only-upgrade install <package>``
  Selectively upgrade individual packages (avoid having to upgrade all packages at once).

----

Done
--------

RC people
^^^^^^^^^

* [Ｘ] Helped Nicole Orchard with initial Python set-up. (20170525)
* [Ｘ] Asked Alex Leeds if he would meet Sean Travis Taylor. (20170522) Done, and Alex's details conveyed to Sean.
* [Ｘ] Signed up for in-person check-ins and mentioned in the Zulip ``checkins`` stream. (20170522). Parthiv and Logan Buckley showed up the first day (20170523) and I described to them something of the history of check-ins and 

Sphinx
^^^^^^

* [Ｘ] Practiced reStructuredText by rewriting some Markdown content. (20170526) Began with this "Current and Postponed tasks" file. 

  * One nice thing is that GitHub does not reformat ``[　]`` as a checkbox in reST the way it does in Markdown. More generally, GitHub does not have a proprietary and arbitrary version of reST, the way it does of Markdown; reST is essentially still a single standard.
  * One unpleasant thing is that marking section headers takes more time and space than in Markdown (which allows just a prefixed :literal:`###\ `, for instance, instead of a separate line of ``#`` at least equal in length to the number of characters in the heading.

* [Ｘ] Begin learning Sphinx (http://www.sphinx-doc.org/en/stable/tutorial.html). (20170524)
* [Ｘ] Begin learning reStructured Text (http://www.sphinx-doc.org/en/stable/rest.html). (20170524)
* [Ｘ] Read two of the longer reST doumentation collections. (http://docutils.sourceforge.net/rst.html) (20170524)

VisiData
^^^^^^^^

* [Ｘ] Reported errors installing VisiData via ``git`` cloning and via ``pip`` on Debian. (20170523) On the possibility that the problem is due to my Debian installation, am considering trying an Ubuntu/Python3.4 Vagrant container on my Mac. (Later:) Vagrant now has trouble working with VirtualBox, so that option was not possible. However, I tried using an Ubuntu installation on a remote server and on Mac OS 10.9.5 itself. Neither the version cloned from Git (``develop`` or ``stable`` branches) or the version installed by ``pip`` worked. Finally, only the ``testpypi`` version (``pip install -i https://testpypi.python.org/pypi visidata``) worked correctly. But this will not allow me to work on the project — that has to be done via Git.
* [Ｘ] Get Chinese data suitable for use by VisiData and send it to Saul. (20170522-23). 
* [Ｘ] Issue posted to VisiData GitHub account about the low visibility of ``curses.BLUE``. (20170521)

Environment
^^^^^^^^^^^

* [Ｘ] Get non-ASCII working on the ``debian-test`` chroot — it doesn't work at all now. (20160524) Did this using ``dpkg-reconfigure locales`` and (incompletely) by getting Chinese fonts working. 
* [Ｘ] Install ``reportbug`` and report the ``xorg`` issue. (20170523) Done — had to use `-y` option on installation, because ``crosh`` terminal window suddenly would not accept ``CR`` to confirm apt installation. 
* [Ｘ] Documented Maté problem, showing that it is the upgrading of ``xorg`` and ``xserver-xorg`` from v. 7.7+18 to v. 7.7+19 that causes an error when looking for `/dev/tty0`. (20170522) Learned about using ``sudo apt list --upgradable`` and then ``sudo apt --only-upgrade install <package>`` for selective Debian upgrades.

EMACS
^^^^^

* [Ｘ] Retrieve old EMACS notes and find recommended EMACS intro. (20170522)

Jobs
^^^^

* [Ｘ] Lunch conversation with TwoSigma technical writer. (20170523) Relatively more technical contracting position may be available right now; will hear back. Discussed some ethical issues with RMKA.

----

Summary of the break between the two halves of my batch
-------------------------------------------------------

(From my diary)

 I have had a two-week break in the midst of my batch. I gained a lot from it — one thing I did was to transcribe the whole :emphasis:`Tsyrchyuan` of Yang Shuhdar (all the definitions), which meant that I read the whole thing carefully. The other was to put my RC experience in better focus — both the MongoDB interview experience and the changes to RC's self-description have had a big effect on me, and the latter has been building since I worked writing referral letters for RC.

----

[end]
