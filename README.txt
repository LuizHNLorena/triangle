Matthieu Latapy
March 2006
http://www-rp.lip6.fr/~latapy/
matthieu.latapy@lip6.fr

This README file describes succintly the triangle computation
program provided at the author's webpage above.

The program is a C source file 'tr.c'. It is provided 'as is'
with no warranty. You may use and distribute it, provided you
cite the web page above, and the paper:
 Fast and Compact Algorithms for Triangle Problems in Very
  Large (Sparse (Power-Law)) Graphs
 Matthieu Latapy,
 Submitted,
 2006.
(A preprint is available on my web page.)
The program is designed for Linux/Unix systems but may be
compiled on any 'reasonable' platform. See below.

Please write me an e-mail if you find it useful, if you find
some bugs or have any idea to improve it.


* QUICKSTART *
**************
1. Compile the program:
  gcc -O3 tr.c -o tr
2. Run it:
  ./tr -c -cc -cf < data_file
  for use of the 'compact forward' algorithm (see paper above), or
  ./tr -c -cc -n 100 < data_file
  for use of the new algorithm proposed in the paper above.


* INPUT FORMAT *
****************
The program reads plain text; the first line must be the number n
of nodes ; then comes a series of lines of the form 'i j' meaning
that node 'i' has degree 'j', and then a series of lines of the
form 'u v' meaning that nodes 'u' and 'v' are linked together.
There *must* be no duplicate lines, and 'u v' also stands for 'v u'.
The nodes must be numbers from 0 to n-1. There must be no loop 'u u'.
The program makes basic verifications but may crash or give wrong
answers if the input is incorrect.
Example :
3
0 2
1 2
2 2
0 1
0 2
2 1
(3 nodes, thus numbered from 0 to 2, node 0 has degree 2, node 1
has degree 2, and node 2 has degree 2 too, and the links are 0 1,
0 2 and 2 1)


* COMMAND LINE OPTIONS *
************************
The program supports basic options to specify the computation
method one wants to use (edge-iterator, forward, compact forward,
or the new one, see the paper above and the reference therein),
and to specify the output (number of triangles (-c), clustering
coefficients (-cc) and/or number of triangles containing each
node (-p)). Calling the program with wrong options (or with no
option)  makes it print out the list of possible options and
their use.


* OUTPUT *
**********
The program writes the results on the standard output. Thus,
if you want to save them you should redirect it, using
typically './tr -p -n 1000 < data_file > result_file'.
Moreover, the program writes some information on what it is
doing on the standard error output. You may want to discard
or redirect this to a file.


* PORTABILITY *
***************
The program is mainly written in ANSI C, with standard libraries.
Some of them however are typical of Linux/Unix systems and may
be absent on other systems. They are *not* used for the triangle
computations, but mainly to measure the execution time. They may
therefore be removed; the concerned lines are indicated in the
source file.


