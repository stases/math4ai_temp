---
layout: default
parent: Linear Algebra
grand_parent: Essentials
nav_order: 1
title: Vector Spaces
---

# Vector spaces

In order to introduce vector spaces, which is a space where vectors _live_, we will first try to motivate its formal definition which will follow later. 

## Informal definition

First, let's denote a vector by a bold letter $$\mathbf{v}$$. The easiest way to visualize a vector is to associate it 
with something familiar. For example, imagine you live on a flat Earth and you're on a hike and you wish to send your 
friends your location. You could, for example, represent your location as a 3D vector:

$$ \mathbf{v} = \begin{bmatrix}
           x_1 \\
           y_1 \\
           z_1
         \end{bmatrix}$$


In this notation, $$x_1$$ and $$y_1$$ are your initial longitude/latitude offset from the bottom of the mountain 
(the amount you moved west/east and south/north), while $$z_1$$ might represent your altitude. You continue your hike, 
change your longitude/latitude by $$x_2$$ and $$y_2$$, and climb up by $$z_2$$ to reach the peak. Then, your new coordinates $$\mathbf{v}$$ are:

$$\mathbf{v}' = \begin{bmatrix}
           x_1+x_2 \\
           y_1+y_2 \\
           z_1+z_2
         \end{bmatrix}$$

In other words, your new coordinates are simply a sum of the two offsets. Notice that the sum of two independent 
offsets produced a new location $$\mathbf{v}'$$ which also represents a valid location. 


Now, imagine you're going on the same hike, but this time the mountain grew in size by a factor of $$\lambda$$, and you 
wish to come to the same peak as last time. Intuitively, we can deduce that the you will have to move further by a factor 
of $$\lambda$$ in each direction, so the total offset $$\mathbf{w}$$ will be given by:

$$\mathbf{w} = \begin{bmatrix}
           \lambda x_1+\lambda x_2 \\
           \lambda y_1+\lambda y_2 \\
           \lambda z_1+\lambda z_2
         \end{bmatrix} = \lambda \begin{bmatrix}
           x_1+x_2 \\
           y_1+y_2 \\
           z_1+z_2
         \end{bmatrix} = \lambda \mathbf{v}'$$

This tells us that even if we multiply our offsets by a number $$\lambda$$, we can still represent a valid location.


This was a very specific example to aid the visualization of certain properties that define a vector space, which we 
will soon define. If we think of a vector as an abstract object which doesn't correspond to anything visualizable, 
then the above-mentioned properties can be thought as the following. First, we want the sum of two vectors to also 
be vector from the same space. Second, if we scale a given vector, we wish that the scaled version is also a part of 
the same vector space. 

## Formal definition

We shall now introduce a formal definition of a vector space.

> A vector space over a field $$\mathbb{F}$$ is a set $$V$$ with two binary operations:
- Vector addition assigns to any two vectors $$\mathbf{v}$$ and $$\mathbf{w}$$ in $$V$$ a third vector in $$V$$ which is denoted by $$\mathbf{v} +\mathbf{w}$$. 
- Scalar multiplication assigns to any scalar $$\lambda$$ in $$\mathbb{F}$$ and any vector $$\mathbf{v}$$ in $$V$$ a new vector in $$V$$, which is denoted by $$\lambda \mathbf{v}$$. 


Vector spaces also have to satisfy 8 axioms, most of them are trivial and intuitive (these can be found on e.g. wikipedia).

In the definition above, a field $$\mathbb{F}$$ is simply an algebraic structure from which we take scalars that we multiply our vectors by. 
In almost all cases, the field will simply be real numbers $$\mathbb{R}$$. Another example is $$\mathbb{C}$$, or the complex numbers.

If we come back to the hiking example, we were dealing with the vectors from $$\mathbb{R}^3$$, as we had 3 entries of the vector, 
and each entry was a real number (coordinates are real numbers).

## Summary 

Vectors are objects that live in a vector space. It is important to note that a vector space is a space defined by only 
two operations with objects: how to add objects and how to scale them. If we know how to do that, we call that space a vector space.
In further sections, we will explore other ways to utilize and transform vectors besides the addition of vectors and multiplication by a scalar. 