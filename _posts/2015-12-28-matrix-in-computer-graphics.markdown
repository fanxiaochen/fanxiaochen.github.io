---
layout: post
title:  "Matrix in Computer Graphics"
date:   2015-12-28 18:38:50
categories: math matrix
---

## The Geometric Meaning of Matrix ##

The matrix means **transform** in computer graphics. We could use matrix to change the position of object in a reference frame. 

In graphics we mostly consider about linear transform and affine transform. Rotation, scaling and orthogonal projection are linear transform. By adding **translation**, they'll be affine transforms.

What we need to take care is that the **transform** is not an absolute value but a **relative** one(in the world perspective) based on the **reference frame**. That is to say if we need to compute a transform of object using matrix, first thing to be considered is in which reference frame the object is. **The transform, the current position and the position after transform are all in one reference frame.**


----------


## The Literal Meaning of Matrix ##

What does the entry values mean in matrix?

Think about the following equations:

\begin{equation}
 \left[\begin{array}{}1 & 0 & 0 \end{array}\right]
\left[\begin{array}{}
m_{11} & m_{12} & m_{13}\\
m_{21} & m_{22} & m_{23}\\
m_{31} & m_{32} & m_{33}\end{array} \right] = 
\left[\begin{array}{}m_{11} & m_{12} & m_{13} \end{array}\right]
\end{equation}

\begin{equation}
 \left[\begin{array}{}0 & 1 & 0 \end{array}\right]
\left[\begin{array}{}
m_{11} & m_{12} & m_{13}\\
m_{21} & m_{22} & m_{23}\\
m_{31} & m_{32} & m_{33}\end{array} \right] = 
\left[\begin{array}{}m_{21} & m_{22} & m_{23} \end{array}\right]
\end{equation}

\begin{equation}
 \left[\begin{array}{}0 & 0 & 1 \end{array}\right]
\left[\begin{array}{}
m_{11} & m_{12} & m_{13}\\
m_{21} & m_{22} & m_{23}\\
m_{31} & m_{32} & m_{33}\end{array} \right] = 
\left[\begin{array}{}m_{31} & m_{32} & m_{33} \end{array}\right]
\end{equation}

If the matrix is a transform, we could see that the three base vectors are exactly the same as three rows of matrix after the transform. **In other words,  the matrix could be considered as three vectors which are transformed from three base vectors in the original reference frame.**

![](https://github.com/fanxiaochen/fanxiaochen.github.io/tree/master/css/pics/matrix-literal-meaning.jpg)


----------


## Transform Between Different Reference Frames##

We only talked about transforms in the same reference frame before. Now we need to think about transforms in different Frames which is an important problem in computer graphics.

Given a 2d reference frame named $F_g$,  the base vectors are $\alpha_1 = \begin{array}{}[1 & 0]\end{array}$, $\alpha_2 = \begin{array}{}[0 & 1]\end{array}$ and the original point is $O_g = \begin{array}{}[0 & 0]\end{array}$, the new reference frame named $F_n$, the new base vectors are $\beta_1 = \begin{array}{}[m_1 & m_2]\end{array}$, $\beta_2 = \begin{array}{}[n_1 & n_2]\end{array}$ and the original point is $O_n = \begin{array}{}[o_1 & o_2]\end{array}$ which are all measured in the given frame $F_g$. Now given a point $P_g$ in $F_g$, what's the value $P_n$ in $F_n$?

This problem is the basic setting of this part.

From vector rules, we could get $\overrightarrow{\rm O_nP_n} = \overrightarrow{\rm O_nO_g} + \overrightarrow{\rm O_gP_g}$, that is 
\begin{equation}
(x_n*\beta_1 + y_n*\beta_2) = (O_g - O_n) + (x_g*\alpha_1 + y_g*\alpha_2)
\end{equation}

Matrix form:
\begin{equation}
\left[\begin{array}{}x_n & y_n\end{array}\right]
\left[\begin{array}{}
m_1 & m_2  \\

n_1 & n_2
\end{array}\right] = 
\left[\begin{array}{}-o_1 & -o_2\end{array}\right] + 
\left[\begin{array}{}x_g & y_g\end{array}\right]
\left[\begin{array}{}
1 & 0\\

0 & 1
\end{array}\right]
\end{equation}

Homogeneous coordinates:
\begin{equation}
\left[\begin{array}{}x_n & y_n & 1\end{array}\right]
\left[\begin{array}{}
m_1 & m_2 & 0\\

n_1 & n_2 & 0 \\

0 & 0 & 1
\end{array}\right] = 
\left[\begin{array}{}x_g & y_g & 1\end{array}\right]
\left[\begin{array}{}
1 & 0 & 0\\

0 & 1 & 0 \\

-o_1 & -o_2 & 1
\end{array}\right]
\end{equation}

So we could solve it and get the transform matrix $T$, let $P_n = P_g T$



