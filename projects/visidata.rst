20170531 VisiData talk

Bugs fixed.

New features.

Examples using ``sample.tsv``.

#. Pivot: ``!`` changes key column, set aggregator (manually or with ``+``) as the main field; ``W`` for Pivot, produces an aggregated sheet.

#. Edit log: ``D`` lists all commands that have been run in this session. Undo steps with backspace (under the hood, replays full list of commands except the last one).

#. Mass edit: ``ge`` change everything in a selected row and field to a certain value.

#. Freeze: ``g'`` makes a new sheet containing the source sheet; this allows you not to have to wait while updating is being done.

----

Dev guide is not posted to ``visidata.readthedocs.io``.

----

Columns are effectively functions that take a row and return a value. (Views.)

Classes:

.. highlight::python
   def open_bar(p):
       vs = Sheet(name, *sources)
       vs.columns = [
           Column(name(type), (work)
                  getter=lambda r:r[0]),
                  ...
           ]
       vs.rows = list(range(0, 1000))
       vd().push(vs)

Note that a column has a getter, which is typically a ``lambda``. 

----

Ways of extending VisiData:

* Your own commands.

* Your own data sources.

* Your own sheets.

* Your own applications.

* Import VisiData into a Python program

Function names ending in `_bar`... ?

----

.. highlight:: python
    class Subsheet(Sheet):
        def __init__(self, ...)
            super()init(name, source)
            self.columns = []
            self.command(...)
    
        def reload(self): # 
            self.rows = []
    
        command('T', 'vd.push(Subsheet())', '')

We discuss code for `StaticCopy` (key: `g'`).

We discuss code for `SheetPivor` (key: `W`).

----

``@async``: runs function on a separate thread

``rowidx``: 

.. highlight:: python

   rows = [
           ((k1, k2), {"pivot value": [rows]...}
   ]

----

Goal is really to use VisiData for workflow integrations, rather than more and more math packages. Navigating APIs, e.g. 

[end]
