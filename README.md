brett.schellenberg@gmail.com

Introduction
============
Welcome to wordindex, a command line utility for indexing arbitrary text by word. Default output is a summary of unique words, the occurance count of each, and the list of lines the word is found in. Note that there may be fewer lines than occurances, due to a word being repeated in the same line.

"Words" are defined by groups of `[A-Za-z0-9_']` characters separated by other characters.

.txt files with line endings of either `\n` or `\r\n` are supported. (Or indeed any combination of `\r` and `\n` ending with an `\n`.) This is accomplished by simply using `\n` as a line separator and then trimming off any remaining `\r` and `\n`.


Installation
============
required perl modules

Name              | Location  | Description
------------------|-----------|------------|
`Getopt/Long.pm`  | CPAN      | for parsing command line options


Graph utility
=============
Also included is a simple command line graphing utility. It accepts input in the style of
uniq -c's output and creates a bar graph of the results. It's a great visual aid for simple count information. The graph utility requires two additional perl modules: Term::ReadKey and POSIX. POSIX should be installed on most systems already and Term::ReadKey is available on CPAN.


Usage
=====
Use the --help option to display detailed usage information

    > wordindex --help

    Usage: ./wordindex <filename> [options]
     Index a file by words

     <filename>                   text file to index. defaults to samples/california.txt

     --normalize                  normalize words by lowercasing. defaults to true.
     --nonormalize                turns off normalizing behavior

     --graph-format               changes output to be in the style of uniq -c, for piping into graph

     --help                       display this message

    typical usage cases:
    What are the most frequently used words and their contexts?
    ./wordindex | less

    Show a graph of the 25 most frequently used words.
    ./wordindex --graph-format | graph | head -25


Examples
========

Show a graph of the 25 most used words in the Declaration of Independence:
    > wordindex samples/declaration.txt --graph-format | graph | head -25
    of             : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (78)
    the            : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (78)
    to             : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (65)
    and            : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (56)
    for            : xxxxxxxxxxxxxxxxxxxxxxxxxx (29)
    our            : xxxxxxxxxxxxxxxxxxxxxxx (26)
    their          : xxxxxxxxxxxxxxxxxx (20)
    in             : xxxxxxxxxxxxxxxxxx (20)
    has            : xxxxxxxxxxxxxxxxxx (20)
    he             : xxxxxxxxxxxxxxxxx (19)
    a              : xxxxxxxxxxxxxx (16)
    them           : xxxxxxxxxxxxxx (15)
    that           : xxxxxxxxxxxx (13)
    these          : xxxxxxxxxxxx (13)
    by             : xxxxxxxxxxxx (13)
    us             : xxxxxxxxxx (11)
    we             : xxxxxxxxxx (11)
    have           : xxxxxxxxxx (11)
    is             : xxxxxxxxx (10)
    which          : xxxxxxxxx (10)
    people         : xxxxxxxxx (10)
    all            : xxxxxxxxx (10)
    be             : xxxxxxxx (9)
    his            : xxxxxxxx (9)
    laws           : xxxxxxxx (9)


Copyright
=========
Copyright (c) 2016 Brett Schellenberg <brett.schellenberg@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.
