The Gramps Project ( https://gramps-project.org )
===================
[![GitHub CI](https://github.com/gramps-project/gramps/actions/workflows/gramps-ci.yml/badge.svg?event=push&branch=master)](https://github.com/gramps-project/gramps/actions/workflows/gramps-ci.yml?query=branch%3Amaster)
[![codecov.io](https://codecov.io/github/gramps-project/gramps/coverage.svg?branch=master)](https://app.codecov.io/gh/gramps-project/gramps/branch/master)
[![Translation status](https://hosted.weblate.org/widgets/gramps-project/-/gramps/svg-badge.svg)](https://hosted.weblate.org/engage/gramps-project)

We strive to produce a genealogy program that is both intuitive for hobbyists and feature-complete for professional genealogists.

Please read the **COPYING** file first.

Please read the **INSTALL** file if you intend to build from source.

Requirements
============
The following packages **MUST** be installed in order for Gramps to work:

* **Python** 3.8 or greater - The programming language used by Gramps. https://www.python.org/
* **GTK** 3.24 or greater - A cross-platform widget toolkit for creating graphical user interfaces. http://www.gtk.org/
* **pygobject** 3.12 or greater - Python Bindings for GLib/GObject/GIO/GTK+ https://wiki.gnome.org/Projects/PyGObject

The following three packages with GObject Introspection bindings (the gi packages)

* **cairo** 1.14.0 or greater - a 2D graphics library with support for multiple output devices. http://cairographics.org/
* **Pycairo** 1.13.3 or greater - GObject Introspection bindings for cairo. https://github.com/pygobject/pycairo
* **pango** - a library for laying out and rendering of text, with an emphasis on internationalization. http://www.pango.org/
* **pangocairo** - Allows you to use Pango with Cairo http://www.pango.org/

* **librsvg2** - (SVG icon view) a library to render SVG files using cairo. http://live.gnome.org/LibRsvg
* **bsddb3** - Python bindings for Oracle Berkeley DB https://pypi.python.org/pypi/bsddb3/
* **sqlite3** - Python bindings for SQLite Database library

The following package is needed for full translation of the interface
to your language:

*   **language-pack-gnome-xx**

 Translation of GTK elements to your language, with
 xx your language code; e.g. for Dutch you need
 language-pack-gnome-nl. The translation of the
 Gramps strings is included with the Gramps source.


The following packages are **STRONGLY RECOMMENDED** to be installed:
--------------------------------------------------------------------
*  **osmgpsmap**

 Used to show maps in the geography view.
 It may be osmgpsmap, osm-gps-map, or python-osmgpsmap,
 but the Python bindings for this must also be present, so gir1.2-osmgpsmap-1.0.
 Without this the GeoView will not be active, see
 https://gramps-project.org/wiki/index.php?title=Gramps_5.1_Wiki_Manual_-_Categories#Geography_Category

* **Graphviz**

  Enable creation of graphs using Graphviz engine.
  Without this, three reports cannot be run.
  Obtain it from: http://www.graphviz.org or try graphviz and python3-pygraphviz from your packages.

* **PyICU**

 Improves localised sorting in Gramps. In particular, this
 applies to sorting in the various views and in the
 Narrative Web output. It is particularly helpful for
 non-Latin characters, for non-English locales and on MS
 Windows and Mac OS X platforms. If it is not available,
 sorting is done through built-in libraries. PyICU is
 fairly widely available through the package managers of
 distributions. See http://pyicu.osafoundation.org/
 (These are Python bindings for the ICU package
 https://pypi.python.org/pypi/PyICU/).

* **Ghostscript**

  Used by Graphviz reports to help create PDF files.

The following packages are optional:
------------------------------------
* **gtkspell**

 Enable spell checking in the notes. Gtkspell depends on
 enchant. A version of gtkspell with gobject introspection
 is needed, so minimally version 3.0.0.

* **rcs**

 The GNU Revision Control System (RCS) can be used to manage
 multiple revisions of your family trees. See info at
 https://gramps-project.org/wiki/index.php?title=Gramps_5.1_Wiki_Manual_-_Manage_Family_Trees#Archiving_a_Family_Tree
 Only rcs is needed, NO python bindings are required.

* **PIL**

 Python Image Library (PILLOW) is needed to crop
 images and also to convert non-JPG images to
 JPG so as to include them in LaTeX output.
 (For Python3 a different source may be needed,
 python-imaging or python-pillow or python3-pillow).

* **GExiv2**

 Enables Gramps to manage Exif metadata embedded in your
 media. Gramps needs version 0.5 or greater.
 See https://www.gramps-project.org/wiki/index.php?title=GEPS_029:_GTK3-GObject_introspection_Conversion#GExiv2_for_Image_metadata

* **ttf-freefont**

 Provides genealogical symbols and more fonts for reports

* **geocodeglib**

 A library use to associate a geographical position (latitude, longitude)
 to a place name. This is used if you already have osmgpsmap installed.
 If installed, when you add or link a place from the map, you have a red line
 at the end of the table for selection.
 Debian, Ubuntu, ... : gir1.2-geocodeglib-1.0
 Fedora, Redhat, ... : geocode-glib
 openSUSE            : geocode-glib
 ArchLinux           : geocode-glib
 ...

* **fontconfig**

 Python bindings of fontconfig are required for displaying
 genealogical symbols

* **magic**

 Python magic bindings required to have better performances with image
 processing.
 If this module is not available, we continue to use Gdk.
 This avoid to load the image in memory. This is a real improvement
 when we have many big images.
 Used in odfdoc, rtfdoc and webreport and tested with png, gif, jpeg, bmp, tiff
 #
 #            file size     with magic  without (Gdk)   ratio
 # example 1 :     256k        0.00080        0.00575       7
 # example 2 :      21M        0.00171        0.55860     326

 Debian, Ubuntu, ... : python3-magic
 Fedora, Redhat, ... : python3-magic
 openSUSE            : python-magic
 ArchLinux           : python-magic

Optional packages required by Third-party Addons
------------------------------------------------

**Third-party Addons are written by users and developers and unless stated are not officially part of Gramps.**
For more information about Addons see:  https://gramps-project.org/wiki/index.php?title=Third-party_Plugins

Prerequistes required for the following Addons to work:

* **Family Sheet** - Requires: PIL (Python Imaging Library) or PILLOW.
( https://gramps-project.org/wiki/index.php?title=Family_Sheet )

* **Graph View** - Requires: PyGoocanvas and Goocanvas (python-pygoocanvas, gir1.2-goocanvas-2.0).
( https://gramps-project.org/wiki/index.php?title=Graph_View )

* **Network Chart** - Requires: networkx and pygraphviz
( https://gramps-project.org/wiki/index.php?title=NetworkChart )

* **PedigreeChart** - Can optionally use - numpy if installed
( https://gramps-project.org/wiki/index.php?title=PedigreeChart )

No longer needed:
-----------------
* Since Gramps 5.2:
   **xdg-utils**

* Since Gramps 4.2:
   **gir-webkit**

* Since Gramps 4.0:
   **pygoocanvas, pygtk, pyexiv2**

* Since Gramps 3.3:
   **python-enchant Enchant**

* Since Gramps 3.2:
   **python glade bindings**

* Since Gramps 3.1:
   **yelp** -             Gnome help browser. No offline help is shipped see Gramps website for User manual

Documentation
-------------
The User Manual is maintained on the Gramps website:

* https://www.gramps-project.org/wiki/index.php?title=User_manual

Issue Tracker
-------------
Gramps bug and issue tracker can be found [here](https://gramps-project.org/bugs/my_view_page.php).

Translation
-------------
Gramps uses Hosted Weblate for its translations:

* https://hosted.weblate.org/engage/gramps-project
