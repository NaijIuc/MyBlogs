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

* In _Gödel, Escher, Bach: An Eternal Golden Braid_, Douglas Hofstadter describes a property of integers:

>We begin with your number, and if it is ODD, we triple it and add 1.  If it is EVEN, we take half of it.  Then we repeat the process.  Call a number which eventually reaches 1 this way a WONDROUS number, and a number which doesn’t, an UNWONDROUS number.

Write a Python script called `wondrous.py` that reads a positive integer from the command line and calculateswhether it’s wondrous.  If it is, the program tells the number of steps needed to reach 1. It should have thefollowing behavior:

```bash
$ python wondrous.py 15

15 is wondrous.  It converges in 17 steps.

$python wondrous.py bacon

‘bacon’ is not an integer.
```
What happens if the program is given an UNwondrous number?

**My demo:**
```r
wonder.func <- function(x){
  wonder.list <- c()
  w <- x
  while (w > 1) {
    m.fuc <- function(x){
      y = NULL
      ifelse(x %% 2 == 1, y <- x*3+1, y <- x/2)
      return(y)
    }
    
    wonder.list <- c(wonder.list, w)
    w = m.fuc(w)
  }
  
  cat("",x, "is wondrous. \n" ,
      "It converges in", length(wonder.list), "steps\n",
      "content = ", wonder.list,1)
}
```

* Analternating permutationof the set{1,2,3, . . . N}is a permutation in which each element is alternativelygreater than or less than the previous element.  That is, ifn1is the first element,n2the second, etc., theneither

 n1> n2< n3> n4< n5. . . 

or

n1< n2> n3< n4> n5. . . 

Write a program called `zigzag.py` that determines the probability that a random permutation of the integers1 throughNwill be alternating.  It should return the number of alternating permutations, the total numberof permutations, and their ratio:

```bash
$python zigzag.py 3
4 6 0.666667

$python zigzag.py 3.7
3.7 is not an integer.
```
**My Demo:**
```r
# This method looks for all the possibilities, which takes too much memory

zigzag <- function(x){

  library(e1071)
  
  all <- permutations(x)
  
  a = 1:(x-1)
  b = 2:x

  t = all[b] - all[a]
  
  t[t<=-1] = -1
  t[t>=1] = 1
  
  a <- seq(0,x-1,2)[-1]
  b <- seq(1,x-1,2)
  
  seq.1 <- NULL
  seq.1[a] <- 1
  seq.1[b] <- -1
  
  seq.2 <- NULL
  seq.2[a] <- -1
  seq.2[b] <- 1
  
  f <- sum(apply(t, 1, function(x) all(x == seq.1))+
        apply(t, 1, function(x) all(x == seq.2)))
  
  cat(f ,"\t", factorial(x), "\t", round(f/factorial(x),6))
  
  
}
```
* Write a program called `mtxvec.py` that reads an N×Nmatrix from a tab-delimited file, places the elements of its upper triangle into the vector~v1,  the elements of its lower triangle into the vector~v2,  and calculatestheir dot product.  For example, if the input matrix is

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
**My Demo:**
```r
M <- matrix(1:9, nrow = 3)

v1 <- M[upper.tri(M, diag = T)] 
v2 <- M[lower.tri(M, diag = T)]

cat("v1.v2 = ", v1 %*% v2)
```

* DNA uses four different nucleobases, abbreviated as A, C, T, and G, to code protein amino acid sequences.The _genetic code_ maps  codons  –  nucleobase  triplets  –  to  amino  acids.   For  example,  the  nucleobase  triplet CAT is  a  codon  for  the  amino  acid  histidine.   There  are  $4^3=  64$  codons,  or  three-letter  words  that  can  be constructed from a four-letter alphabet.  In general, there are $k^n$n-letter words that can be constructed from a _k_-letter alphabet.  Write a program called `nkwords.py` that takes in two integers, _k_ and _n_, and prints all _n_-letter words that can be constructed with the first _k_ letters of the alphabet.  For example:

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