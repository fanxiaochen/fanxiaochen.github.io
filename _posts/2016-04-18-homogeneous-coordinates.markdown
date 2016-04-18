---
layout: post
title:  "Homogeneous Coordinates"
date:   2015-12-28 18:38:50
categories: math matrix
---



**Cartesian coordinates** is what we use every day. But in computer graphics and vision fields, when using camera model, there encounters **projective coordinates**, namely **homogeneous coordinates**.

Homogeneous coordinates has one more dimension than Cartesian coordinates when represents the same position. For example $x = 2$,
one dimension data for a point in Cartesian coordinates, is equivalent to a line in homogeneous coordinates as $\lambda(2, 1)$ or $x/w = 2$. So we realize that the original point $x=2$ in Cartesian coordinates is the projective point at $w=1$ of the line in homogeneous coordinates.

## Geometric Meaning ##

A simple drawing shows here, to visualize the meaning of homogeneous coordinates in geometry.

![Geometric Meaning of Homogeneous Coordinates](https://fanxiaochen.github.io/css/pics/homo-coords-meaning.jpg)

Note that $x_c$ represents Cartesian coordinates and $x_h$ represents homogeneous coordinates. As we could see, the point $x_c=\lambda$ are represented by intersection between line $w=1$ and $x_h/w=x_c$. If $w=0$, $x_c\to\infty$. So homogeneous coordinates can represent point at infinity.

For data more than one dimension, it's the same as above. We could see a picture from wiki to show the curve in two coordinates. 

![Rational Bézier Curve – polynomial curve defined in homogeneous coordinates (blue) and its projection on plane – rational curve (red)](https://upload.wikimedia.org/wikipedia/commons/1/12/RationalBezier2D.svg)

In camera model, the position in camera ordinates has four dimension in homogeneous coordinates, which means the data is projected from 4D space to 3D space, or from volume to plane. So it can be summarized that:

 - For **line** $(x,w)$ in homogeneous coordinates, the equivalent projection in Cartesian coordinates is a **point** $x$ at $w=1$.
 - For **plane** $(x,y,w)$ in homogeneous coordinates, the equivalent projection in Cartesian coordinates is a **line** $(x,y)$ at $w=1$.
 - For **volume** $(x,y,z,w)$ in homogeneous coordinates, the equivalent projection in Cartesian coordinates is a **plane** $(x,y,z,w)$ at $w=1$.
 
 > Note that the "**equivalence**" means  "**same numeric values**" of all dimensions in mathematics. In camera projection, the z-axis of camera coordinates which are often focus length direction should be the w-dimension. **One is not required for focus length**, since there doesn't need to be same numeric values after projection.
 
## References ##

 - [Homogeneous coordinates](https://en.wikipedia.org/wiki/Homogeneous_coordinates)
 
 