Here is a parser that converts GEDCOM files to a _de facto_ object model.

De Facto object model
---------------------

_De Facto_ means _"In fact or in practice; in actual use or existence,
regardless of official or legal status."_

The parser converts GEDCOM files to an object model that includes all of the
information found in the vast majority of GEDCOMs in the wild.
The model includes additional tags over those in the official GEDCOM standard,
because they are commonly used in GEDCOM files, and excludes a few tags from
the official GEDCOM standard that are never or only rarely used.

Further, most of the information from GEDCOMs that cannot be represnted directly
in the model is represented as _extensions_ so it is not lost.

The object model is able to represent all of the information found in 96%
of the roughly 7000 GEDCOMs submitted to [WeRelate.org](http://www.werelate.org),
over the past five years, with the exception of four software-specific _schema_ tags:
_SCHEMA, _EVENT_DEFN, _PLAC_DEFN, and _EVDEF, generated by _Family Tree Maker_,
_Personal Ancestral File_, _Legacy_, and _RootsMagic_ respectively.

These schema tags and more are represented by a built-in extension that stores
additional tags on the objects of the schema.  With this extension, the object
model is able to represent all of the information found in 99% of the GEDCOMs
submitted to WeRelate.

For more information about the object model, see the doc directory (coming soon).

Extensible
----------

Developers can add custom extensions to the model.  An extension might annotate
people with warnings about suspicious dates for example.

Three parsers and GEDCOM export
-------------------------------

The project includes three parsers:

* from GEDCOM to object model.  This object model can be saved as a json file.

* from GEDCOM to a general tree-based object model that captures everything
within the GEDCOM file.  This tree-based object model can also be saved as a json file.

* from json to the object model or the tree-based object model.

as well as a GEDCOM export tool:

* from object model to GEDCOM

Round-trippable
---------------

It is possible to do a round-trip: read a GEDCOM file into the object model,
save it to json, read it back from json, and save it back to GEDCOM, without
any loss of information for the vast majority (99%) of GEDCOM files.

The round-trip capability allows anyone to create programs that read gedcom files,
do interesting things like generate warnings for suspicious dates in the GEDCOM,
allow the user to correct the warnings, and save the information back as a GEDCOM
file without loss of information from the original GEDCOM.

Roadmap
-------

This project was posted only recently.  It may have bugs.  Use at your own risk.
If you find bugs, please report them.