Mobash.sh
=========

A simplistic modular bash "compiler"

Mobash allows you to modularize and simplify your bash code, in order to make it more reusable and understandable.  Mobash provides three constructs that you can take advantage of to break out your code:

*	*Config files:* Mobash allows you to put the config and info section of your script in a seperate file, keeping it out of the way of any code.  Config files are defined with '#@config <filename>', and are put at the top of the compiled bash script.
*	*Included files:*  Mobash lets you include other source files with the '#@include <filename>' tag.  These files generally contain functions used in the project that there's no reason to share with other scripts.  Included files are inserted into the script before the main file, and should not contain any code besides functions.
*	*Imported files:* 
