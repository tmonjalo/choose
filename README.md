choose: a shell menu
====================

Description
-----------

_choose_ is a shell script which allows an interactive choice on stderr among lines from stdin (or arguments) and returns the result on stdout.

            multiple lines            menu            one line
                           --->      choose      --->
             args / stdin      TTY input / stderr      stdout

It is nearly the same goal as the shell builtin _select_ with fancy I/O more.


Usage
-----

A choice can be preselected as first argument. In cursor mode, it falls back to the first line if there is no default choice.

When the key ENTER is pressed, the selected choice is validated.

* In cursor mode (the default), the selection can be moved with the keys UP and DOWN.

* In numerated mode, a number matching a list item can be entered.

There are 2 styles for the selected line. It can be shown with an arrow or in a reversed font.

When the choice is done, the menu can disappeared (quiet option), be replaced by the chosen line (default), or be kept as is (verbose option).

If you don't want it tampers your TTY with alternative settings and special characters, use _-nav_ options (numerated mode with arrow and keep verbose). It disables all "advanced" features.

The environment variables _CHOOSE_INDENT_ and _CHOOSE_ARROW_ allow to customize line prefix.


Example
-------

    # answer=$(choose -av '' yes no)
    =>  yes
        no
    # echo $answer
    yes

There is a directory with more useful examples.

Bugs
----

* In cursor mode, long lines with non printable characters are smaller than the terminal width.

* In numerated mode with default verbose, clearing may be wrong if there are long lines with non printable characters.


Dependencies
------------

It should need no special tool to run. Indeed all requirements are standard and commonly available.

_choose_ runs with _/bin/sh_ which can be any POSIX shell (_ash_, _bash_, _dash_, _ksh_, _zsh_...).

It uses many basic tools from _coreutils_ (_basename_, _cat_, _head_, _cut_, _tr_, _fold_, _od_, _dd_, _seq_, _wc_, _stty_), _ncurses_ (_tput_) and _sed_.

It also needs _procfs_ (especially _/proc/?/fd/0_ to get terminal input).

It is designed for GNU/Linux but could run on other Unix.

Copyright
---------

The author disclaims copyrights, so _choose_ is in the public domain.
