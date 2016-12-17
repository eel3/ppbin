ppbin
=====

Pretty-printer for binary file.

License
-------

zlib License.

Target environments
-------------------

Windows, Cygwin, Linux, Mac OS X, FreeBSD.

ppbin is Python 2.7 script, and so probably works fine on other OS.

Set up
------

1. Install Python 2.7.12 or later.
2. Put ppbin in a directory registered in PATH.

Usage
-----

Please check help message `ppbin --help`

Example
-------

    $ # -n 20 --> 20 words in 1 line
    $ # -w 1  --> 1 word == 1 octet
    $ ppbin -n 20 -w 1 test.bin
    52 49 46 46 24 00 00 00 57 41 56 45 66 6D 74 20 10 00 00 00
    01 00 02 00 44 AC 00 00 10 B1 02 00 04 00 10 00 64 61 74 61
    00 00 00 00
    $
    $ # -n 4 --> 4 words in 1 line
    $ # -w 4 --> 1 word == 4 octet
    $ ppbin -n 4 -w 4 test.bin
    52494646 24000000 57415645 666D7420
    10000000 01000200 44AC0000 10B10200
    04001000 64617461 00000000
    $
    $ # -l --> interpret as little-endian
    $ ppbin -l -n 4 -w 4 test.bin
    46464952 00000024 45564157 20746D66
    00000010 00020001 0000AC44 0002B110
    00100004 61746164 00000000
    $
    $ # -p 2 --> print 2 octet at a time
    $ # -w 4 --> 1 word == 4 octet
    $ ppbin -l -n 4 -p 2 -w 4 test.bin
    4646 4952 0000 0024 4556 4157 2074 6D66
    0000 0010 0002 0001 0000 AC44 0002 B110
    0010 0004 6174 6164 0000 0000
    $
    $ # C-style print with 2-space indentation.
    $ # -a 0x   --> add prefix `0x' to each word
    $ # -d ', ' --> delimiter is ', '
    $ # -i 2    --> indent size is 2
    $ ppbin -a 0x -d ', ' -i 2 -l -n 4 -w 4 test.bin
      0x46464952, 0x00000024, 0x45564157, 0x20746D66,
      0x00000010, 0x00020001, 0x0000AC44, 0x0002B110,
      0x00100004, 0x61746164, 0x00000000,
    $
    $ # 1-tab indentation.
    $ # -i 1 --> indent size is 1
    $ # -t   --> use tab insted of space
    $ ppbin -a 0x -d ', ' -i 1 -l -n 4 -t -w 4 test.bin
            0x46464952, 0x00000024, 0x45564157, 0x20746D66,
            0x00000010, 0x00020001, 0x0000AC44, 0x0002B110,
            0x00100004, 0x61746164, 0x00000000,
    $
    $ _
