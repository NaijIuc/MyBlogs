---
title: Tim's homework 2 performed with R
author: Jian.C
date: '2020-09-01'
slug: tim-s-homework-performed-with-r
categories:
  - R
  - Teaching
tags: []
---

1.  In _Gödel, Escher, Bach: An Eternal Golden Braid_, Douglas Hofstadter describes a property of integers:

>We begin with your number, and if it is ODD, we triple it and add 1.  If it is EVEN, we take half ofit.  Then we repeat the process.  Call a number which eventually reaches 1 this way a WONDROUSnumber, and a number which doesn’t, an UNWONDROUS number.

Write a Python script called `wondrous.py` that reads a positive integer from the command line and calculateswhether it’s wondrous.  If it is, the program tells the number of steps needed to reach 1. It should have thefollowing behavior:

```bash
$ python wondrous.py 15

15 is wondrous.  It converges in 17 steps.

$python wondrous.py bacon

‘bacon’ is not an integer.
```
What happens if the program is given an UNwondrous number?



2.  Analternating permutationof the set{1,2,3, . . . N}is a permutation in which each element is alternativelygreater than or less than the previous element.  That is, ifn1is the first element,n2the second, etc., theneither

$$\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi$$

$ n1> n2< n3> n4< n5. . . $

or

$ n1< n2> n3< n4> n5. . . $

Write a program called `zigzag.py` that determines the probability that a random permutation of the integers1 throughNwill be alternating.  It should return the number of alternating permutations, the total numberof permutations, and their ratio:

```bash
$python zigzag.py 3
4 6 0.666667

$python zigzag.py 3.7
3.7 is not an integer.
```

3.  Write a program called `mtxvec.py` that reads anN×Nmatrix from a tab-delimited file, places the elementsof its upper triangle into the vector~v1,  the elements of its lower triangle into the vector~v2,  and calculatestheir dot product.  For example, if the input matrix is

```bash
$cat data.tsv
1 2 3 
4 5 6 
7 8 9
```
the output would be

```bash
$python mtxvec.py data.tsv
v1 = 1 2 3 5 6 9
v2 = 1 4 5 7 8 9
v1.v2 = 188
```


4.  DNA uses four different nucleobases, abbreviated as A, C, T, and G, to code protein amino acid sequences.The _genetic code_ maps  codons  –  nucleobase  triplets  –  to  amino  acids.   For  example,  the  nucleobase  triplet CAT is  a  codon  for  the  amino  acid  histidine.   There  are  $4^3=  64$  codons,  or  three-letter  words  that  can  be constructed from a four-letter alphabet.  In general, there are $k^n$n-letter words that can be constructed from a _k_-letter alphabet.  Write a program called `nkwords.py` that takes in two integers, _k_ and _n_, and prints all _n_-letter words that can be constructed with the first _k_ letters of the alphabet.  For example:

```bash
$python nkwords.py 2 3
AAA
AAB
ABA
ABB
BAA
BAB
BBA
BBB
```

The words don’t need to be printed in any particular order.  Your code should include controls to catch invalidinput.