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


Example
-------

    # answer=$(echo "yes\nno" | choose -a)
    =>  yes
        no
    # echo $answer
    yes
