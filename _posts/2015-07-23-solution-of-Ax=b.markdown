---
layout: post
title:  "Solution of $Ax=b$"
date:   2015-07-23 20:38:50
categories: math matrix
---



## **Problem** ##
Given $Ax=b$, where$A\in R^{m\times n}$, $x\in R^{n}$,  $b \in R^{m}$, what is the solution?


----------

## **Solution** ##

It has a little difference from $Ax=0$. There may be no solution or unique solution and more. What we should first think about here is augmented matrix $\tilde{A} = [ A \| b ]$ and to compare $rank(\tilde{A})$ and $rank(A)$.

 - if $rank(\tilde{A}) > rank(A)$, there\'ll be no solution here.
 - if  $rank(\tilde{A}) = rank(A)$, there exists at least one solution.

So let\'s look about the case of existing solutions, which is much similar to the form $Ax = 0$.

> 1. if $m = n$ and $rank(A) = n$,  then $A^{-1}$ exists, so $x = A^{-1}b$.
> 2. if $m = n$ and $rank(A) < n$,  there exists at least one free variable, the number of which is $n - rank(A)$
> 3. if $m \neq n$ and $rank(A)$ must not be more than $min(m, n)$.
>  - if $m < n$, then $rank(A) <= m < n$, so the equations will be undetermined, which means there exists non-trivial solutions.
>  - if $m > n$, then $rank(A) <= n < m$. For $rank(A) = n$, the system has an unique solution. What\'s interesting here is that A is not really overdetermined. We could remove $m-n$ rows from $\tilde{A}$ and change  the linear system to **case 1**. While $rank(A) < n$, it degenerates to be undetermined with non-trivial solutions.

----------

## **Least Squares** ##

What if there\'s no solution for $Ax = b$ in theory, namely $rank(\tilde{A}) > rank(A)$? That\'s what least squares does.

If $A$ is overdetermined, we could use least squares to get an approximate solution by converting $Ax = b$ to an optimization problem, which means $E(x) = \|Ax - b\|^{2}$. The following shows least squares figure:

![Least Squares Approximation](https://upload.wikimedia.org/wikipedia/commons/3/3a/Linear_regression.svg)

What we should realize is that if the blue dots all lie in the same red line, that implies $rank(\tilde{A}) = rank(A)$, which is **case 3.2**.

----------

## **References** ##

 

 1. [http://ocw.mit.edu/courses/mathematics/18-06sc-linear-algebra-fall-2011/ax-b-and-the-four-subspaces/solving-ax-b-row-reduced-form-r/MIT18_06SCF11_Ses1.8sum.pdf](http://ocw.mit.edu/courses/mathematics/18-06sc-linear-algebra-fall-2011/ax-b-and-the-four-subspaces/solving-ax-b-row-reduced-form-r/MIT18_06SCF11_Ses1.8sum.pdf)
 2. [https://en.wikipedia.org/wiki/System_of_linear_equations](https://en.wikipedia.org/wiki/System_of_linear_equations)
 3. [https://en.wikipedia.org/wiki/Least_squares](https://en.wikipedia.org/wiki/Least_squares)

