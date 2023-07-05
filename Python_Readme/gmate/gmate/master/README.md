# GMate

This package contains some gedit improvements to make it more similar to
TextMate. The package contain code snippets, plugins, and an automatic
registration of rails-related files.

If you have issues with one of the plugins included in Gmate or have suggestions
please fill an issue in <http://github.com/gmate/gmate/issues>

## Install

### Ubuntu

1. Add Ubuntu on Rails PPA:

        sudo apt-add-repository ppa:ubuntu-on-rails/ppa
        sudo apt-get update

   *Note:* on Karmic use `add-apt-repository` instead of `apt-add-repository`.
2. Install gedit-gmate package:

        sudo apt-get install gedit-gmate

### Other Linux

1. Install all dependencies:
    * `python-webkitgtk` for Todo-List plugin and Find in Project plugin, see
      <http://code.google.com/p/pywebkitgtk>
    * `python-sexy` for Go to File plugin
    * `pyinotify` for Gedit Open Files and SnapOpen plugins.
    * `ack-grep` for faster search in Find in Project. (optional)

   **Note:** Dependencies have slightly different names in Fedora Linux (`pywebkitgtk`, `python-sexy`, `python-inotify` and `ack`).

2. Download gmate sources or clone git repository:

        git clone git://github.com/gmate/gmate.git
        cd gmate

3. And run install script:

        sh install.sh

   **Note:** Some commands will expect you enter your sudo password.

## GMate package include

### Plugins

#### gedit2:

* **Advanced Bookmarks**. Highlight, remenber and toggle bookmarks in your
  files.
* **Align columns**. Align text blocks into columns separated by pipe ( | )
* **Classbrowser**. A Classbrowser (depends of ctags, I use exuberant-ctags).
* **Encoding**. Reopen the document in a different encoding
* **Embedded Terminal**. Terminal with multiple windows
* **File Search**. This is a search plugin for Gedit to search for a text inside
  a directory. <https://github.com/oliver/gedit-file-search>
* **Find in Project**. Search in the project with ack/grep.
  <http://github.com/eggegg/find-in-project>
* **Fuzzy Open**. Quick way to open file in project.
  <http://github.com/eggegg/fuzzyopen>
* **Gedit Open File**. Regex based file open (like textmate Go to file…).
* **Gedit Todo**. Find Todo Marks in source files (integrated with filebrowser).
* **Gemini**. Pair complete for quotes and braces.
* **Highlight Edited Lines**. Highlights lines changed during your edit session.
  <http://1dan.org/gedit-plugins/highlight-edited-lines/>
* **Indent Converter**. Converts tabs to spaces and spaces to tabs.
* **Line Tools**. comment toggle, duplicate, selection, add semi-colon.
* **Multi Edit**. Check it out at author's page
  <http://jon-walsh.com/journal/multi-edit>
* **Macropy**. Record and execute macros.
  <https://github.com/eguaio/gedit-macropy>
* **Open URI Context Menu**. Adds context menu item to open an URI at the
  pointer position.
  <http://www.jpfleury.net/en/software/open-uri-context-menu.php>
* **Pair Character Completion**. Pair complete for quotes and braces, that
  also wrap selected text. <http://code.google.com/p/gedit-pair-char-autocomplete>
* **Pastie**. Paste a selection of code or a source file to pastie.org directly
  from editor <http://github.com/ivyl/gedit-pastie>
* **Quickhighligthmode**. Fast change current highlight mode.
* **Rails Extract Partial**. Extract selected region of rhtml as a partial.
* **Rails Hotcommands**. Execute Rails Commands (such rake tasks).
* **Rails Hotkeys**. Navigation in Rails Project Files.
* **Regex Search Replace**. Search and replace with regular expressions.
* **Reopen Tabs**. Saves opened tabs on exit to restore them on next run.
* **Simple Folding**. Collapse selected text.
* **Smart Indent**. Smart Indentation regex based.
* **Tabulation**. Auto set tabs and spaces based on file type.
* **TextMate Style Autocompletion**. Better autocompletion. Tap `Esc` to cycle
  through the available completions.
* **Text Map**. Navigatable thumbnail of the entire file
  <http://1dan.org/gedit-plugins/textmap/>
* **Text Tools**. Some text manipulation improvements (adapted from line tools).
* **Trailsave**. Remove trailing spaces before save a document.
* **Word Completion**. Word completion plugin.
* **Zen Coding**. Tools for faster HTML/CSS coding
  <http://github.com/mikecrittenden/zen-coding-gedit>
* **Zoom**. Adds the ability to change the text size.
  <http://github.com/algorich/gedit-zoom>

#### gedit3:
	**NOTE:** gedit3.8+, at least in Ubuntu expects python3 while earlier versions
	did not. For now Python plugins that have been updated may not work in version
	3.0-3.6. If you have a desire for backwards compatibility create an issue.
* **Advanced Find/Replace**. Search and replace in all documents/tabs
* **Gemini**. Pair complete for quotes and braces.
* **Line Tools**. comment toggle, duplicate, selection, add semi-colon.
* **Simple Folding**. Collapse selected text.
* **Snap Open**. Opens files by regex
* **Zen Coding**. Tools for faster HTML/CSS coding
* **And More...**

**Note:** Multi Edit plugin is not enabled by default GMate installation.


Refer to each plugin source code and readme file to get information about
specific plugin licensing and copyright.

### Language Improvements and Mime Types

* Basic YAML Syntax Highlight
* CoffeeScript Syntax Highlight
* ColdFusion Syntax Highlight
* Cucumber Syntax Highlight
* Groovy/Grails/Gradle improvements
* HAML Syntax Highlight
* Markdown Syntax Highlight
* reStructuredText Syntax Highlight
* rhtml/erb Syntax Highlight
* Ruby on Rails improvements
* SASS and Stylus Syntax Highlight
* Jade and Eco templates Highlight

### Themes/Styles

* Active4d (Converted from Textmate)
* All Hallow's Eve (Converted from Textmate)
* Ambiance
* Ambiance Dark
* Amy (Converted from Textmate)
* Argonaut  (Converted from Textmate)
* barf (Converted from Textmate)
* BBEdit (Converted from Textmate)
* Blackboard (Converted from Textmate)
* Black Pearl (Converted from Textmate)
* Black Pearl II (Converted from Textmate)
* Blue Dream
* Boys & Girls 0.1 (Converted from Textmate)
* Briliance Black (Converted from Textmate)
* Briliance Dull (Converted from Textmate)
* Chela Light
* choco (Converted from Textmate)
* Classic Modified (Mac classic)
* CodeZone (New!)
* Cool Glow (Converted from Textmate)
* Daltonism (Converted from Textmate)
* Darkmacs
* Darkmate
* Desert
* Dawn (Converted from Textmate)
* Desert
* Django (Converted from Textmate)
* Django (Smoothy) (Converted from Textmate)
* Dreamweaver
* eclips3.media (ECLM) (Converted from Textmate)
* Eiffel (Converted from Textmate)
* Emacs
* Emacs Dark (Converted from Textmate)
* Emacs Strict (Converted from Textmate)
* Expresso Libre (Converted from Textmate)
* Fade to Grey (Converted from Textmate)
* Flarp
* Fluffy
* ForLaTeX (Converted from Textmate)
* Fruity
* Github (Converted from Textmate)
* GlitterBomb (Converted from Textmate)
* IDLE (Converted from Textmate)
* idleFingers (Converted from Textmate)
* iLife 05 (Converted from Textmate)
* iPlastic (Converted from Textmate)
* IR_Black (Converted from Textmate)
* Ironman
* IR_White (Converted from Textmate)
* Jellybeans (Converted from VIM)
* Kate
* LAZY (Converted from Textmate)
* Lowlight (Converted from Textmate)
* Mac Classic (Converted from Textmate)
* MacMoose (Converted from Textmate)
* MagicWB (Amiga) (Converted from Textmate)
* Matrix (Converted from Textmate)
* Merbivore (Converted from Textmate)
* Merbivore Soft (Converted from Textmate)
* Midnight (Converted from Textmate)
* minimal Theme (Converted from Textmate)
* monoindustrial (Converted from Textmate)
* Monokai (Converted from Textmate)
* Mustang (Converted from VIM)
* Neopro (Converted from Textmate)
* Notepad 2 (Converted from Textmate)
* Overcast (Converted from Textmate)
* Pastels on Dark (Converted from Textmate)
* PlasticCodeWrap (Converted from Textmate)
* Plum Dump (Converted from Textmate)
* Railscasts (Converted from Textmate)
* Railscasts Improved
* RDark (Converted from Textmate)
* Ruby Blue (Converted from Textmate)
* Rubycius
* RubyRobot (Converted from Textmate)
* Ryan Light (Converted from Textmate)
* Slate (Converted from Textmate)
* Slush & Poppies (Converted from Textmate)
* Slush and Poppies (Mod)
* Smurfy (Converted from Textmate)
* SpaceCadet (Converted from Textmate)
* SpaceCadet Pro (Converted from Textmate)
* Spetacular (Converted from Textmate)
* Stoneship (Converted from Textmate)
* Solarized
* Sunburst (Converted from Textmate)
* Swyphs II (Converted from Textmate)
* Tango (Converted from Textmate)
* Tek (Converted from Textmate)
* Text Ex Machina (Converted from Textmate)
* Textmate (mac classic) (Converted from Textmate)
* Tinge
* Tomorrow
* Travis Jeffery (Converted from Textmate)
* Twilight (Converted from Textmate)
* Twilight Modified
* Vibrant Fun
* Vibrant Ink (Converted from Textmate)
* Vibrant Nerd
* Vitamins (Converted from VIM)
* Warm Grey
* Why's Poingnant (Converted from Textmate)
* Wombat
* Zenburn
* Zenburnesque (Converted from Textmate)

