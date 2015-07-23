---
layout: post
title:  "Solution of $Ax=0$"
date:   2015-07-22 22:42:50
categories: math matrix
---

###**Problem** ###
Given $Ax=0$, where$A\in R^{m\times n}$，$x\in R^{n}$, What is the solution?


----------

###**Solution** ###

Obviously the homogenous system always has the solution $x = 0$. But what about other solutions?


> 1. if $m = n$ and $rank(A) = n$, $x = 0$
> 2. if $m = n$ and $rank(A) < n$,  there exists at least one free variable, the number of which is $n - rank(A)$
> 3. if $m \neq n$ and $rank(A)$ must not be more than $min(m, n)$.
>  - if $m < n$, then $rank(A) <= m < n$, so the equations will be indeterminate, which means there exists non-trivial solutions.
>  - if $m > n$, then $rank(A) <= n < m$. For $rank(A) = n$, the system has an unique solution, which is $x = 0$. While $rank(A) < n$, it degenerates to be indeterminate with non-trivial solutions.

----------

###**Some Thoughts** ###


> ***Q***: Can $Ax = 0 \Rightarrow x = 0$ be true?

***A***: From the solution part, we could see clearly that it\'s false.

> ***Q***:  For $M(Ax-b) = 0$, how to solve $x$?

***A***:  From above question, we couldn\'t get $Ax=b$ directly, except $M^{-1}$ exists(**case 1**) or **case 3.2**. So we need to expand the equation into $MAx = Mb$ and solve the form as $ \tilde{A} x= \tilde{b}$.

> ***Q***:  For the form $Ax=0$, if it\'s overdetermined, how about least squares?

***A***: No matter whether it is overdetermined, the least squares is meaningless since the result will always be $x = 0$.


----------

###**References** ###

 1. [http://www.math.ku.edu/~lerner/LAnotes/Chapter5.pdf](http://www.math.ku.edu/~lerner/LAnotes/Chapter5.pdf)
 2. [http://www.math.northwestern.edu/~clark/285/handouts/soln-set.pdf](http://www.math.northwestern.edu/~clark/285/handouts/soln-set.pdf)