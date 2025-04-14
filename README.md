CTags Modules
=============

## Purpose
Allows for easier and more precise creation of tags files using the (exuberant) `ctags` command.

Other vim-specific data is also output, namely data for inclusion in Vim's `path` variable, which makes
jumping around header files easier via the `gf` command (or other commands using the `path` variable).

## How To Use
**Running the program**: Typing `createtags <module name>` will generate a tags file for the module.

**Getting help**: `createtags` with no parameters will print out the program's help.

**Listing Available Modules**: `createtags -l` will generate a list of all the modules that are known.

**Printing the version number**: `createtags -v` will print out the version number on standard output.

**Displaying the command that WOULD have been run (dry-run mode)**: Running `createtags` with the `-n` option
will print the command to be run without actually running it.  Useful for debugging purposes.

**Display the possible return values and their meanings**: `createtags -r` will generate a human-readable list of return values and their meanings.

## Filesystem Structure
bin
---
Contains the `createtags` command.

files
---
Contains files for each standard of the C and C++ language.  Each file representing that standard contains a list of the header files, one per line, the given standard added to the previous standard.

exclude
---
Contains a file per module.  Each file lists, one per line, a pattern to pass to the --exclude option (to the underlying ctags program).  Used to exclude input files.

ignore
---
Contains a file per module.  Each file lists, one per line, a preprocessor macro to ignore.  These are passed to the -I option (to the underlying ctags program).

modules
---
Contains files defining the available modules.

tags
---
The output tags file for each module.

vim_path
---
If it exists for a given module, a file containing the directories that were searched for the input tag file generation.
Useful for adding to Vim's 'path' variable, which will allow for using Vim's 'gf', ]I, etc. to find header files for the module.
