Current and Postponed tasks
===========================

Completed tasks are marked [Ｘ]. Postponed tasks are marked [Ｏ].

:strong:`Contents`:

* `To be done immediately`_
* `On-going`_
* `Done`_
* `Abandoned items`_
* `Summary of the break between the two halves of my batch`_


To be done immediately
----------------------


Upcoming
--------

VisiData
^^^^^^^^

* [　] Meet with Saul Pwanson to learn about current process-based testing workflow and then begin documenting it.
* [　] Meet with Saul Pwanson to learn about coloring tools and then begin documenting them.
* [　] Play with unit tests and document how to write them.
* [　] Write fresh pull-requests on some of the small TODO items in the docstring commits.
* [　] Clean up code in `addons` directory. Submit these as discrete pull-requests.
* [Ｏ] Write up VisidData decisions and set up documentation-notes repo.

IPython and Jupyter
^^^^^^^^^^^^^^^^^^^

* [　] Get practice with Jupyter and current Ipython configuration settings. See `IPython project page <ipython.rst>`_.

Regular coding practice
^^^^^^^^^^^^^^^^^^^^^^^

* [　] Examine coding practice sites:
 
  * CareerCup
  * TopCoder
  * GeeksforGeeks
  * Sphere Online Judge (SPOJ)
  * Project Euler
  * HackerRank
  * LeetCode Online Judge
  * [Exercism](exercism.io)

* [Ｏ] Find possible pairing partner for interview coding practice. (20170525) Two people I've asked today don't seem to have time. I suspect it will be easier to work on my own and ask for Crit or Code Review feedback. I should aim for more statistical projects. (20170605) This seems pointless — the people I've approached tentatively seem to want other things. I am on my own.


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

----

On-going
--------

Sphinx
^^^^^^

* Practice reStructuredText by rewriting some Markdown content. 


Unix knowledge
^^^^^^^^^^^^^^

* Read in Eric S. Raymond, :emphasis:`The Art of Unix Programming`. Existence of `website <http://www.catb.org/esr/writings/taoup/html/>`_ should allow easy recording of :emphasis:`bon mots`.
 
  * 20170605: Am finished with Sec. 5.2.6. It remains interesting, but it's also clear how little adhereance there is to Unix values in the field generally.
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
----

RC people
^^^^^^^^^

* [Ｘ] Two long rounds of corrections to prospective Python blog-post by Katie Allen. (20170604-5)
* [Ｘ] Long conversation with Adriel Arsenault about preparing for jobs. (20170526)
* [Ｘ] Helped Nicole Orchard with initial Python set-up. (20170525)
* [Ｘ] Asked Alex Leeds if he would meet Sean Travis Taylor. (20170522) Done, and Alex's details conveyed to Sean.
* [Ｘ] Signed up for in-person check-ins and mentioned in the Zulip ``checkins`` stream. (20170522). Parthiv and Logan Buckley showed up the first day (20170523) and I described to them something of the history of check-ins and 

Sphinx
^^^^^^

* [Ｘ] Installed `sphinx` in order to have access to `rst2html.py` for converting reST to HTML. (20170527)
* [Ｘ] Converted all my in-progress notes on Chao wenyan grammar from Markdown to reST. (20170527) This allows me to render my markup locally; `grip` for GitHub-Flavored Markdown involved a call to GitHub itself.
* [Ｘ] Practiced reStructuredText by rewriting some Markdown content. (20170526) Began with this "Current and Postponed tasks" file. 

  * One nice thing is that GitHub does not reformat ``[　]`` as a checkbox in reST the way it does in Markdown. More generally, GitHub does not have a proprietary and arbitrary version of reST, the way it does of Markdown; reST is essentially still a single standard.
  * One unpleasant thing is that marking section headers takes more time and space than in Markdown (which allows just a prefixed :literal:`###\ `, for instance, instead of a separate line of ``#`` at least equal in length to the number of characters in the heading.

* [Ｘ] Begin learning Sphinx (http://www.sphinx-doc.org/en/stable/tutorial.html). (20170524)
* [Ｘ] Begin learning reStructured Text (http://www.sphinx-doc.org/en/stable/rest.html). (20170524)
* [Ｘ] Read two of the longer reST doumentation collections. (http://docutils.sourceforge.net/rst.html) (20170524)

VisiData
^^^^^^^^

* [Ｘ] Eight commits, adding about 300 docstrings and some other miscellaneous changes, to the VisiData add-ons and to the `vd.py` file. (20170602-5) Discussion with Saul Pwanson about principles of this work and next steps. (20170605)

* [Ｘ] Meet with Saul to discuss my role in the project. 20170524: Saul was too busy to do this. 20170525: Saul was too busy to do this today again. He gave a workshop today and published a brief user guide, but he never had a chance to work with me on these things as we had planned. 20170526: Made appointment. Had half-hour disussion — covered running locally, where to place notes, where to place docs, setting up GitHub organization, DPB's title and use on résumé, Sphinx, Nose or Pytest for testing.

* [Ｘ] Reported errors installing VisiData via ``git`` cloning and via ``pip`` on Debian. (20170523) On the possibility that the problem is due to my Debian installation, am considering trying an Ubuntu/Python3.4 Vagrant container on my Mac. (Later:) Vagrant now has trouble working with VirtualBox, so that option was not possible. However, I tried using an Ubuntu installation on a remote server and on Mac OS 10.9.5 itself. Neither the version cloned from Git (``develop`` or ``stable`` branches) or the version installed by ``pip`` worked. Finally, only the ``testpypi`` version (``pip install -i https://testpypi.python.org/pypi visidata``) worked correctly. But this will not allow me to work on the project — that has to be done via Git.
* [Ｘ] Get Chinese data suitable for use by VisiData and send it to Saul. (20170522-23). 
* [Ｘ] Issue posted to VisiData GitHub account about the low visibility of ``curses.BLUE``. (20170521)

Grammar
^^^^^^^

* [Ｘ] Chao Grammar: added notes for sections involving inversion of object or subject: 2.3.2, 2.10.8, 5.4.7, 8.1.2.2. (20170528)

Environment
^^^^^^^^^^^

* [Ｘ] Get non-ASCII working on the ``debian-test`` chroot — it doesn't work at all now. (20160524) Did this using ``dpkg-reconfigure locales`` and (incompletely) by getting Chinese fonts working. 
* [Ｘ] Install ``reportbug`` and report the ``xorg`` issue. (20170523) Done — had to use `-y` option on installation, because ``crosh`` terminal window suddenly would not accept ``CR`` to confirm apt installation. 
* [Ｘ] Documented Maté problem, showing that it is the upgrading of ``xorg`` and ``xserver-xorg`` from v. 7.7+18 to v. 7.7+19 that causes an error when looking for `/dev/tty0`. (20170522) Learned about using ``sudo apt list --upgradable`` and then ``sudo apt --only-upgrade install <package>`` for selective Debian upgrades.

Jobs
^^^^

* [Ｘ] Submitted a number of technical writing samples to Jane Street, at their request. (20170531)
* [Ｘ] Prepare résumé for technical writing positions. 20170525: Wrote to RC Jobs to discussion position and whether application should go through RC or not; no response yet. 20170530: Résumé prepared and submitted to RC Jobs.
* [Ｘ] Wrote to Jobs about Jane Street position. (20170530)
* [Ｘ] Lunch conversation with TwoSigma technical writer. (20170523) Relatively more technical contracting position may be available right now; will hear back. Discussed some ethical issues with RMKA.

----

Abandoned items
---------------

Kaggle (abandoned)
^^^^^^^^^^^^^^^^^^

* [Ｘ] Set up private repo for Kaggle project and invited the four other participants.

After today's (20170525) Kaggle meeting the five of us agreed that we would work first on an Instagram challenge, leaving a more interesting Quora challenge for private reading. I was to set up a private repository, giving eachmember access (which I did). Other plans for were learn IPython independently and read the kaggle.com wiki independently. There was also supposed to be an additional meeting at 1500h, to review some past challenges, but if it took place then I was never notified. 

Although I would like to learn this material, I think it's too much for the five remaining weeks. Three of us are quite inexperienced and two have somewhat more data-science experience; I think it is infeasible to work on this together productively in the remaining time. I would, however, like to get practice with Jupyter and current Ipython configuration settings, so I will create an item for myself to do that.

It would be a good idea to spend some of my coding time working on simple statistics problems.

EMACS (abandoned)
^^^^^^^^^^^^^^^^^

* [　] Look at the Emacs introduction in `Clojure for the Brave and True <http://www.braveclojure.com/basic-emacs/>`_, recommended by Stacey and Logan.
* [Ｘ] Retrieve old EMACS notes and find recommended EMACS intro. (20170522)

As of today (20170526) I think working with EMACS will complicate unnecessarily the rest of my work. RMKA called this "cutting your hands while working".

----

Summary of the break between the two halves of my batch
-------------------------------------------------------

(From my diary)

 I have had a two-week break in the midst of my batch. I gained a lot from it — one thing I did was to transcribe the whole :emphasis:`Tsyrchyuan` of Yang Shuhdar (all the definitions), which meant that I read the whole thing carefully. The other was to put my RC experience in better focus — both the MongoDB interview experience and the changes to RC's self-description have had a big effect on me, and the latter has been building since I worked writing referral letters for RC.

[end]
