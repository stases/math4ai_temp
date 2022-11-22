---
layout: default
parent: Multivariate Calculus
grand_parent: Essentials
nav_order: 4
title: Jacobians
---

# Jacobians

## Jacobians

One of the most iconic functions in deep learning is the 'linear layer', which takes some input $$\textbf{x} \in \mathbb{R}^m$$ 
and takes $$n$$ linear combinations (with different factors) of the inputs. This linear layer can be considered a function 
$$\textbf{f}: \mathbb{R}^m \to \mathbb{R}^n$$ such that $$y_i = w_{i1}x_1 + \cdots w_{im}x_m = \sum_{j=1}^m, w_{ij} x_j$$, 
where we still write $$\textbf{y} = \textbf{f}(\textbf{x})$$. We call the $$\{w_{ik}\}_{k=1}^m$$ the **weights** of the function. 
Notice that for the entire function $$\textbf{f}$$ we have $$n$$ of such sets of weights, i.e. in total $$n \times m$$ weights. 
We can write this functions more compactly as $$\textbf{y} = \mathbf{Wx},$$ where 

$$\mathbf{W} = \begin{bmatrix}w_{11} & w_{12} & \cdots & w_{1m} \\ w_{21} & w_{22} & \cdots & w_{2m} \\
\vdots & \vdots & \ddots & \vdots \\
w_{n1} & w_{n2} & \cdots & w_{nm} \end{bmatrix} \in \mathbb{R}^{n \times m}.$$

When we now imagine all the streams of influence found between the $$\textbf{y}$$ and $$\textbf{x}$$, we realize that each
element $$y_i$$ is dependent on each variable $$x_j$$. If you do not see this immediately, please draw out the respective diagram.



A consequence of this is that we have a lot of derivatives, namely for each of the $$n$$ outputs $$y_i$$ we have $$m$$ different 
derivatives (for the $$m$$ inputs). To make our lives a whole lot easier, we simply determine the derivative of the $$i$$th 
element for the $$j$$th variable and see if what we end up with generalizes. 
We hence wanna find $$\frac{\partial y_i}{\partial x_j} = \frac{d}{dx_j} (\sum_{k=1}^m w_{ik}x_k)$$. We know that 

$$\frac{d}{dx_j} (\sum_{k=1}^m w_{ik}x_k) = \sum_{k=1}^m \frac{d}{dx_j} w_{ik}x_k.$$ 

Let us know zoom in into one of the terms of the summation, i.e. we only consider $$\frac{d}{dx_j} w_{ik}x_k$$. If we have 
that $$x_k \neq x_j$$, we will always have that $$\frac{d}{dx_j} w_{ik}x_k = 0$$, because the entire term does not depend on 
$$x_j$$. When $$x_j = x_k$$, however, we see that the derivative is given by $$w_{ik}$$. We can express this `if-else' statement 
quite easily mathematically using something called the **Kronecker delta**. The Kronecker delta over two variables 
$$i$$ and $$j$$ is equal to $$1$$ if $$i$$ is equal to $$j$$, and equal to $$0$$ other, or:

$$\delta_{ij} = \begin{cases}1& \text{ if } i = j \\ 0& \text{ otherwise }\end{cases}$$

Sometimes this is written with so-called **Iverson brackets** as $$[i=j]$$. These brackets do the same thing, i.e. 
$$[\mathsf{S}] = 1$$ if $$\mathsf{S}$$ is true, else $$[\mathsf{S}] = 0$$ for any statement $$\mathsf{S}$$. 
The most important property (for us) of this Kronecker delta is that

$$\sum_j \delta_{ij} x_j = x_i,$$

i.e. when summing over elements $$x_j$$, we can filter out $$x_i$$ by introducing $$\delta_{ij}$$. 
Please verify this carefully, for this will be our main workhorse throughout this section.


