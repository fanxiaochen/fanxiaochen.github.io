---
layout: post
title:  "Epipolar Geometry"
date:   2016-07-08 23:18:50
categories: math camera cv
---

In computer vision, especially in multiple view geometry, **epipolar constraint** and **essential matrix** are the basic concepts, which reveal the geometry relationship of different cameras. We could estimate camera position and recover the depth of scene by this relationship.

## Essential Matrix ##

Given two cameras with different poses, what is the relationship between them?

![](https://fanxiaochen.github.io/css/pics/epipolar-geometry.png)

From the camera model, we know the projection between 3d coordinates and image plane is that $x=f\frac{X}{Z}$ and $y=f\frac{Y}{Z}$. Assume $X_1$ and $X_2$ are the same space points in the two camera views, what we want to know is the transform between that, which is:

\begin{equation}
X_2 = RX_1+T
\end{equation}

By using the 2d points in images, we have:

\begin{equation}
\lambda_2x_2=\lambda_1Rx_1+T
\end{equation}

where $\lambda_1, \lambda_2$ are the ratios between focal length and depth.

Multiply by $T_c=
\begin{bmatrix}
0 & -t_z & t_y  \cr 
t_z & 0 & -t_x \cr 
-t_y & t_x & 0 
\end{bmatrix}$($TT_c=0$), we get:

\begin{equation}
\lambda_2T_cx_2=\lambda_1T_cRx_1
\end{equation}

Then multiply by $x_2^T$, **the left side will become zero**. So we could get the final relationship:

\begin{equation}
x_2^TEx_1=0
\end{equation}

where $E=T_cR$, which is called the essential matrix. If we put the intrinsic parameters of cameras into the equation, the fundamental matrix will be got.


## Epipolar Constraint ##

Another important rule is about epipolar constraint. As we could see that the space point and two camera centers form a triangle which represents the epipolar plane. The points projected on the two images **must** lie in the intersection lines, which are called epipolar lines, from the geometry. 

Now if we consider the $x_2^TE$ as line parameters like $[a \ b \ c]$, and $x_1$ as unknown points like $[x \ y \ 1]$, the line could be represented as $ax+by+c=0$, **which is the epipolar line $l_1$.** **It is decided by $x_2$ and passes through $x_1$**. Vice versa. The relation is denoted as:

\begin{equation}
l_1 : x_2^TE
\end{equation}

**However,  the line $l_1$ passes through $x_1$, but many lines do the same thing, why does it must be epipolar line?**

![](https://fanxiaochen.github.io/css/pics/epipolar-line.png)

**We can see that, in the projection line, every points on the image are at the same position $x_2$, and decide the same line. As the space points are coplanar based on triangulation,  the decided line must be epipolar line $l_1$.**

Since epipolar point $e_1$ lies in the line $l_1$, it has $x_2Ee_1=0$. As we could see that, **it belongs to all epipolar lines**. That is to say that no matter what $x_2$ is, the equation is forever established. So there exists:

\begin{equation}
Ee_1=0
\end{equation}

The epipolar constraint could be used by fast point correspondence matching and other useful computation process.


## References ##

 - [http://frc.ri.cmu.edu/~kaess/vslam_cvpr14/media/VSLAM-Tutorial-CVPR14-A11-VisualOdometry.pdf](http://frc.ri.cmu.edu/~kaess/vslam_cvpr14/media/VSLAM-Tutorial-CVPR14-A11-VisualOdometry.pdf)

 

 - Multiple View Geometry

