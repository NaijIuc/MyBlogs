---
title: Tim's homework 3 performed with R
author: Jian.C
date: '2020-09-08'
slug: tim-s-homework-3-performed-with-r
categories:
  - R
  - Teaching
tags: []
image:
  caption: ""
  focal_point: ""
  preview_only: true
---
How many times do you expect you will have to toss an unbiased coin before it comes up "heads" twice in a row? How many times do you expect you will need to flip it before it comes up "heads" immediately followed by "tails"? Write a program that simulates a string of fair coin tosses. The program should:

* Perform 10000 trials in which a coin is tossed until "heads-heads" occurs, and 10000 trials in which a coin is tossed until "heads-tails" occurs.

```r
coin <- c("head", "tail")

sample(coin, 2, replace = T)
```
* Print the expected number of coin tosses before "heads-heads" and the expected number of tosses before "heads-tails".

__This is a demo of one option:__
```r
x = -1
  repeat{
    t = sample(coin, 2, replace = T)
    x = x + 1
    if(all(t == c("head", "tail")) | all(t == c("tail", "head"))){ 
    # or for another toss: if(all(t == c("head", "head"))){
      break
    }
  }
```
* Create a histogram of the number of tosses before each condition is met.

__This is a demo of one option:__

```r
ht <- NULL
for (i in 1:10000) {
  x = -1
  repeat{
    t = sample(coin, 2, replace = T)
    x = x + 1
    if(all(t == c("head", "tail")) | all(t == c("tail", "head"))){ 
    # or for another toss: if(all(t == c("head", "head"))){
      break
    }
  }
  ht <- c(ht, x)
}

# Plot the result (ht, "head tail"; hh, "head head"): 

hist(ht, main = "Head tail", xlab = "Times")
hist(hh, main = "Head head", xlab = "Times")
```
The "head tail" result ![](hwk3/hw3.fig1.png)

The "head head" result ![](hwk3/hw3.fig2.png)

__I want to compare thses two results and put both histgram in one figure:__

```r
# As the two histograms would overlap, here the color definition helps create two transparent colors
c1 <- rgb(173,216,230,max = 255, alpha = 90)
c2 <- rgb(255,192,203, max = 255, alpha = 90)

# To determine proper breaks of both histograms
bks <- pretty(min(c(ht,hh)):max(c(ht,hh)), 
             n = 31)

# To get the histgram frequencies
hg.ht <- hist(ht, breaks = bks, plot = F)
hg.hh <- hist(hh, breaks = bks, plot = F)

# Plotting
plot(hg.ht, col = c1, main = "Comparsion", xlab = "Times")
plot(hg.hh, col = c2, add = T)
legend("topright", legend=c("head tail", "head head"),
       fill=c(c1, c2),cex=0.8,
       box.lty=0)
```
The "comperasion" result ![](hwk3/hw3.fig3.png)