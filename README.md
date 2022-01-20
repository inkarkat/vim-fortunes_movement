FORTUNES_MOVEMENT
===============================================================================
_by Ingo Karkat_

DESCRIPTION
------------------------------------------------------------------------------

This filetype plugin provides movement commands and text objects for email
fortunes, i.e. blocks of text delimited by /^-- \\?$/.

USAGE
------------------------------------------------------------------------------

                            Move around fortunes:
    ]]                      Go to [count] next start of a fortune.
    ][                      Go to [count] next end of a fortune.
    [[                      Go to [count] previous start of a fortune.
    []                      Go to [count] previous end of a fortune.

    if                      "inner fortune" text object, select [count] fortunes,
                            excluding the fortune separator.
    af                      "a fortune" text object, select [count] fortunes, including
                            the preceding fortune separator.

INSTALLATION
------------------------------------------------------------------------------

The code is hosted in a Git repo at
    https://github.com/inkarkat/vim-fortunes_movement
You can use your favorite plugin manager, or "git clone" into a directory used
for Vim packages. Releases are on the "stable" branch, the latest unstable
development snapshot on "master".

This script is also packaged as a vimball. If you have the "gunzip"
decompressor in your PATH, simply edit the \*.vmb.gz package in Vim; otherwise,
decompress the archive first, e.g. using WinZip. Inside Vim, install by
sourcing the vimball or via the :UseVimball command.

    vim fortunes_movement*.vmb.gz
    :so %

To uninstall, use the :RmVimball command.

### DEPENDENCIES

- Requires Vim 7.0 or higher.
- Requires the CountJump plugin ([vimscript #3130](http://www.vim.org/scripts/script.php?script_id=3130)), version 1.30.

CONFIGURATION
------------------------------------------------------------------------------

The commands and text objects are only active when 'filetype' is set to
"fortunes".
You need to make sure that the filetype is properly detected, for example via
the following fragment in .vim/filetype.vim:

    augroup filetypedetect
        " Fortunes files.
        autocmd BufNewFile,BufRead fortunes.txt,*/fortunes/*.txt setf fortunes
    augroup END

or manually set the filetype every time via

    :setf fortunes

If you want to use this plugin also for other filetypes, e.g. "txt", create a
file ftplugin/txt\_movement.vim in your 'runtimepath' (usually ~/.vim) with the
following contents:

    runtime! ftplugin/fortunes_movement.vim

This is more maintainable than simply renaming fortunes\_movement.vim.

CONTRIBUTING
------------------------------------------------------------------------------

Report any bugs, send patches, or suggest features via the issue tracker at
https://github.com/inkarkat/vim-fortunes_movement/issues or email (address
below).

HISTORY
------------------------------------------------------------------------------

##### 1.10    18-Dec-2010
- Switched definition of motion mappings from patterns to begin and end to a
region of continguous lines defined by a non-matching pattern (representing the
fortune separator line). This should make it more correct with corner cases.
Requires CountJump version 1.30.

##### 1.00    03-Aug-2010
- First published version.

##### 0.01    03-Oct-2009
- Started development.

------------------------------------------------------------------------------
Copyright: (C) 2009-2022 Ingo Karkat -
The [VIM LICENSE](http://vimdoc.sourceforge.net/htmldoc/uganda.html#license) applies to this plugin.

Maintainer:     Ingo Karkat &lt;ingo@karkat.de&gt;
