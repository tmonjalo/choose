choose: a shell menu
====================

Description
-----------

_choose_ is a shell script which allows an interactive choice on stderr among lines from stdin and returns the result on stdout.

    multiple lines         menu          one line
                   --->   choose   --->
          stdin     TTY input / stderr     stdout

It is nearly the same goal as the shell builtin _select_ with fancy I/O more.


Usage
-----

A choice can be preselected as parameter. In cursor mode, it falls back to the first line if there is no default choice.

When the key ENTER is pressed, the selected choice is validated.

* In cursor mode (the default), the selection can be moved with the keys UP and DOWN.

* In numerated mode, a number matching a list item can be entered.

When the choice is done, the menu can disappeared (quiet option), be replaced by the chosen line (default), or be kept as is (verbose option).

If you don't want it tampers your TTY with alternative settings and special characters, use _-nav_ options (numerated mode with arrow and keep verbose). It disables all "advanced" features.


Example
-------

    # answer=$(echo "yes\nno" | choose -av)
    =>  yes
        no
    # echo $answer
    yes
