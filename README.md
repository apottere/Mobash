Mobash.sh
=========

Cloning
-------

After cloning, make sure you run `git submodule update --init --recursive` in the root diretory to pull bashlib to the import directory.

Usage
-----

A simplistic modular bash "compiler"

Mobash allows you to modularize and simplify your bash code, in order to make it more reusable and understandable.  Mobash provides multiple constructs that you can take advantage of to break out your code:

*	*Config files:* Mobash allows you to put the config and info section of your script in a seperate file, keeping it out of the way of any code.  Config files are defined with `#@config <filename>`, and are put at the top of the compiled bash script, and all comments and formatting is preserved.
*	*Included files:*  Mobash lets you include other source files with the `#@include <filename>` tag.  These files generally contain functions used in the project that there's no reason to share with other scripts.  Included files are inserted into the script before the main file, and should not contain any code besides functions.  The filename should not be absolute or relative, and will be recursively found under the source root.
*	*Imported files:*  Imports are defined with the syntax `#@import library.function`, where `library_function` is a function declared in the file `library.shm`, which exists somewhere under the defined import path.
*	*Color codes:* Color variables can be injected into the script with `#@color VAR <color definition>`.  Examples can be found at the top of mobash.shs

When building a script, mobash looks initially for a `script_name.shs` file.  This is the base source file for your script.  From here, it parses the included files for all imports and colors.  This means that imports can be declared in included files for the functions that they include, rather than cluttering up the main source file.

All of the imports so far are encapsulated in [Bashlib](https://github.com/apottere/bashlib), but feel free to define your own libraries.  The only required syntax is `#@function module.function: dependency1 dependency2...`

There's another script source bundled with it that shows some basic concepts.  It can be found under `source/example`, and can be compiled with `bin/mobash example`