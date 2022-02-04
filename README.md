homebrew-mspgcc
===============

The [Homebrew][] formulae of GCC toolchain for MSP430, also known as
[MSPGCC][] which is based on [GNU GCC][] 4.7. This repository includes
`binutils-msp430`, `headers-msp430`, `gcc-msp430`, `libc-msp430`,
`gdb-msp430`.

To get everything, execute the following commands.

    $ brew tap tgtakaoka/mspgcc
    $ brew install libc-msp430 gdb-msp430

You may want to install `mspdebug-head` by the following commands.

    $ brew tap tgtakaoka/tinyos-msp430
    $ brew install --HEAD mspdebug-head

Version:

    binutils-msp430-2.22-20120911_4
    headers-msp430-20130321_3
    gcc-msp430-4.7.0-20120911_2
    libc-msp430-20120716_2
    gdb-msp430-7.2a-20111205_1

[Homebrew]: https://brew.sh/
[MSPGCC]: https://sourceforge.net/projects/mspgcc/
[GNU GCC]: https://gcc.gnu.org/

## Installation on Apple M1

This formula does not work, for the moment, on Homebrew arm64 native installation. However, this formula was tested to work under Rosetta 2. The native Homebrew install location on Apple M1 is in `/opt/homebrew`, while x86_64 Homebrew install location is in `/usr/local`. They both can run side-by-side.

Having both arm64 and x86_64 on the same machine, the call to `brew` command goes to native installation (it is first in the path). The call to x86_64 installation requires its full path:

    $ arch --x86_64 /usr/local/bin/brew install <package>

Native Homebrew Installation:

    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    
x86_64 Homebrew Installation:

    $ arch --x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## Troubleshooting

When you encounter error permission to write into directories, like the following:

    Error: An exception occurred within a child process:
      Errno::EPERM: Operation not permitted @ dir_s_mkdir - /usr/local/lib/msp430

run these on x86_64 Homebrew installation:

    mkdir /usr/local/lib/msp430
    mkdir /usr/local/lib/msp430/lib  
    mkdir /usr/local/include/msp430  
    mkdir /usr/local/include/msp430/include

or run these on native Homebrew installation:

    mkdir /opt/homebrew/lib/msp430
    mkdir /opt/homebrew/lib/msp430/lib  
    mkdir /opt/homebrew/include/msp430  
    mkdir /opt/homebrew/include/msp430/include
