Title: System Program on Linux
Date: 2017-3-15 20:20
Category: System Program
Tags: Yee, Yeee

## `gcc`

Options:

`-pg`: Used for gprofile analysis.

`--static`: Includes the libraries used by the program into itself. So, if a program used this option to compile, it can be run anywhere. Also, it may run slightly faster because the system don't have to link the libraries dynamically during runtime. The downside is that it will have a larger size than usual.

## `gprofile`


## `strace`

Inspect programs' system call during runtime.

After compiling with `-static`

example: `strace ./hello`

## man 2 brk
