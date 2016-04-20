---
layout: post
title:  "Camera Model"
date:   2016-04-19 18:38:50
categories: math matrix camera
---

Camera Model is used in both computer vision and computer graphics. The basic theory is the same, but the usage is different since the unknown parameters are different. 

The usual model includes orthogonal model and perspective model. Here we focus on the latter one. All is about how to transform 3d points in world coordinates to 2d points in pixel coordinates. We will introduce the process step by step, which includes the basic concepts of camera: **extrinsic and intrinsic parameters.**

## World Coordinates to Camera Coordinates ##
Given 3d point $P=(X,Y,Z)$ in world coordinates, the position $P_c=(X_c, Y_c, Z_c)$ is:

\begin{equation}
\begin{bmatrix}
X_c  \cr Y_c  \cr Z_c  \cr 1
\end{bmatrix}=
\begin{bmatrix}
R & T \cr
0 & 1
\end{bmatrix} 
\begin{bmatrix}
X  \cr Y  \cr Z  \cr 1
\end{bmatrix}
\end{equation}

where R is a 3*3 rotation matrix represents camera orientation and
T is a three vector that represents camera translation. These are the extrinsic parameters, which is based on the origin choice of world coordinates.

## Camera Coordinates to Image Plane ##
After getting position in camera view, the perspective projection from 3d to 2d image need to be considered, by which homogeneous coordinates is used to work. If $P_i=(x,y,1)$, then due to similar triangulation, $x=f\frac{X_c}{Z_c}$, $y=f\frac{Y_c}{Z_c}$, where $f$ is the focus length of camera. We could use homogeneous coordinates to represent the computing way:

\begin{equation}
\begin{bmatrix}
x  \cr y \cr 1
\end{bmatrix}=
\begin{bmatrix}
f & 0 & 0 & 0 \cr
0 & f & 0 & 0 \cr
0 & 0 & 1 & 0 
\end{bmatrix} 
\begin{bmatrix}
X_c  \cr Y_c  \cr Z_c  \cr 1
\end{bmatrix}
\end{equation}

**Note that the equality "=" here holds in homogeneous coordinates, not Cartesian one. If you want the exact values, the right side of equation need to be divided by $Z_c$.**

## Image Plane to Pixel Coordinates ##
The final component is the 2D to 2D transformation that relates points $P_i$ on the camera image plane to pixel coordinates $p=(u,v,1)$. This is written as follows:

\begin{equation}
p=KP_i
\end{equation}

where $K$ is an upper triangular camera calibration matrix of the form:

\begin{equation}
K=
\begin{bmatrix}
\alpha_u & s & u_0  \cr
0 & \alpha_v & v_0  \cr
0 & 0 & 1
\end{bmatrix} 
\end{equation}

$\alpha_u$ and $\alpha_v$ are scale factors, $s$ is skew, and $(u_0,v_0)$ is the principal point, which is the position of optical center in pixel coordinates. These are intrinsic parameters. More details could be found in reference.

We could combine the steps to get the whole transform $T$ to represent that:

\begin{equation}
p=TP
\end{equation}

## Vision and Graphics Usage ##
In vision field, $p$ is usually known but not $T$ and $P$. So we need camera calibration and have other application like structure-from-motion. In graphics field, $T$ and $P$ are indicated by users and they care about what is $p$ called rendering. They are totally inverse.

## References ##

 - [http://ksimek.github.io/2013/08/13/intrinsic/](http://ksimek.github.io/2013/08/13/intrinsic/)
 
 - [http://mi.eng.cam.ac.uk/~cipolla/publications/contributionToEditedBook/2008-SFM-chapters.pdf](http://mi.eng.cam.ac.uk/~cipolla/publications/contributionToEditedBook/2008-SFM-chapters.pdf)

