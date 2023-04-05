---
layout: default
parent: Multivariate Calculus
grand_parent: Essentials
nav_order: 4
title: Jacobians
---


# Jacobians

{: .motivation }
As we have seen, computing multivariate derivatives can be quite convoluted. Luckily for us, we can often save **a lot** 
of work in machine learning. In this section, we will cover some basic patterns of computing higher-dimensional derivatives.

## A new friend: Kronecker Delta

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

Let us know zoom in on one of the terms of the summation, i.e. we only consider $$\frac{d}{dx_j} w_{ik}x_k$$. If we have 
that $$x_k \neq x_j$$, we will always have that $$\frac{d}{dx_j} w_{ik}x_k = 0$$, because the entire term does not depend on 
$$x_j$$. When $$x_j = x_k$$, however, we see that the derivative is given by $$w_{ik}$$. We can express this `if-else' statement 
quite easily mathematically using something called the **Kronecker delta**. The Kronecker delta over two variables 
$$i$$ and $$j$$ is equal to $$1$$ if $$i$$ is equal to $$j$$, and equal to $$0$$ other, or:

$$\delta_{ij} = \begin{cases}1& \text{ if } i = j \\ 0& \text{ otherwise }\end{cases}$$

Sometimes this is written with so-called **Iverson brackets** as $$[i=j]$$. These brackets do the same thing, i.e. 
$$[\mathsf{S}] = 1$$ if $$\mathsf{S}$$ is true, else $$[\mathsf{S}] = 0$$ for any statement $$\mathsf{S}$$. 
The most important property (for us) of this Kronecker Delta is that

$$\sum_j \delta_{ij} x_j = x_i,$$

i.e. when summing over elements $$x_j$$, we can filter out $$x_i$$ by introducing $$\delta_{ij}$$. 
Please verify this carefully, for this will be our main workhorse throughout this section.


## Jacobians



If we go back to our example, we see that hence our derivative is given by $$\frac{d}{dx_j} w_{ik}x_k = \delta_{jk} w_{ik}$$ 
for any combination of $$x_j$$ and $$x_k$$. That is, the derivative is equal to $$0$$ if $$x_j$$ and $$x_k$$ are different, and equal 
to $$w_{ik}$$ when $$x_j$$ and $$x_k$$ are the same. Plugging this back in, we find

$$\sum_{k=1}^m \frac{d}{dx_j} w_{ik}x_k = \sum_{k=1}^m\delta_{jk} w_{ik}.$$

This we know how to evaluate using our workhorse, and hence we see that
$$\frac{df_i}{dx_j} = \sum_{k=1}^m\delta_{jk} w_{ik} = w_{ij}.$$

Neat! We just found a general approach to taking the derivative of the linear layer and concluded that the effect of the 
$$j$$th variable on the $$i$$th output is given by the weight $$w_{ij}$$. We can write out the entire Jacobian (where the element 
in $$i$$th row, $$j$$th column is the derivative of $$y_i$$ with respect to $$x_j$$) again:

$$\frac{d\textbf{y}}{d\textbf{x}}  = \begin{bmatrix}w_{11} & w_{12} & \cdots & w_{1m} \\ w_{21} & w_{22} & \cdots & w_{2m} \\
\vdots & \vdots & \ddots & \vdots & \\
w_{n1} & w_{n2} & \cdots & w_{nm} \end{bmatrix} \in \mathbb{R}^{n \times m}.$$

But wait! This matrix we recognize from earlier, namely as our matrix $$\textbf{W}$$. This allows us to write

$$\frac{d\textbf{y}}{d\textbf{x}} = \textbf{W}.$$ 

We call this approach if finding a single entry of the derivative and 
then generalizing the 'index method'.

Please note that not only did we just derive the derivative of the linear layer, but we found that 
$$\frac{d}{d\textbf{x}} \mathbf{W}\textbf{x} = \mathbf{W}$$ for arbitrary matrices and vectors, e.g. we also know now that

$$\frac{d}{d\textbf{v}}\mathbf{(AB + C)v} = \mathbf{AB + C}, $$

by simply remembering that $$\mathbf{AB + C = W'}$$ for some matrix $$\mathbf{W'}$$.

Another very common derivative you will encounter is $$\frac{d}{d\textbf{x}} \mathbf{a^Tx}$$. In this case, we have that
$$\mathbf{a^Tw}$$ is simply a scalar, and hence our Jacobian will be of the shape $$(1 \times m)$$ if $$\textbf{x}$$ is $$m$$-dimensional. 
Let us again use the index method, and aim to find

$$\frac{d}{dx_j} \mathbf{a^Tx} = \frac{d}{dx_j} \sum_{k=1}^m a_k x_{k} = \sum_{k=1}^m \frac{d}{dx_j} a_k x_k.$$

As before, we see that the derivative is equal to $$a_k$$ when $$k = j$$, and equal to zero otherwise, and thus

$$\sum_{k=1}^m \frac{d}{dx_j} a_k x_k = \delta_{jk} a_k = a_j,$$

where we find $$a_j$$ by applying our workhorse again. This means that the $$j$$th element of our derivative is given by $$a_j$$, 
or the entire derivative is given by $$\textbf{a}$$. 

But... $$\textbf{a}$$ is a column vector, where our Jacobian should be a row vector as we argued earlier. Sadly, this 
problem cannot quite be overcome, and we just need to always check of our answer should be transposed or not. In this case, 
we see that our Jacobian matches $$\mathbf{a^T}$$. This is slightly annoying, but luckily our answer is always either correct 
or needs to be only transposed, and checking it will become second nature soon enough! Let this inconvenience not distract
us from the fact that we did just find our new identity though, that is:

$$\frac{d}{d\textbf{x}} \mathbf{a^Tx} = \mathbf{a^T}.$$


{: .exercise }
Your turn! Try and verify that $$\frac{d}{d\textbf{x}} \mathbf{y^T  A x} = \mathbf{y^T A},$$ where 
$$\textbf{x} \in \mathbb{R}^m$$, $$\mathbf{A} \in \mathbb{R}^{n \times m}$$, and $$\textbf{y} \in \mathbb{R}^m$$. Please do 
this 1) using index notation, and 2) using our identity friends we have already found. 


We know that $$\mathbf{y^T Ax}$$ is a scalar (why?), and hence the Jacobian will be again of the form $$(1 \times m)$$ if 
$$\textbf{x}$$ is a $$m$$-dimensional vector. Using index notation, we aim to find $$\frac{d}{dx_i} \mathbf{y^T Ax}$$. We observe that

$$\frac{d}{dx_i} \mathbf{y^T A x} = \frac{d}{dx_i} \sum_{k=1}^n \sum_{j=1}^m y_{k}A_{kj}x_j = \sum_{k=1}^n \sum_{j=1}^m \frac{d}{dx_i} y_{k}A_{kj}x_j.$$

Again, since $$y_kA_{kj}$$ are just scalars, we know that the derivative is simply found by 

$$\frac{d}{dx_i} y_k A_{kj}x_j = \delta_{ij} y_k A_{kj}.$$

This gives us the following derivative:

$$ \sum_{k=1}^n \sum_{j=1}^m \frac{d}{dx_i} y_{k}A_{kj}x_j = \sum_{k=1}^n \sum_{j=1}^m \delta_{ij} y_k A_{kj} = \sum_{k=1}^n  y_k A_{ki}.$$

But this term we recognize as $$[\mathbf{y^T A}]_i$$. This means that our full derivative is simply given by $$\mathbf{y^T A}$$, 
which aligns with our desired shape so we are done. 

So... That's quite a lot of work. And actually, we could have done way less work using our previous identities. 
Observe that $$\mathbf{y^T A}$$ is just a row vector, i.e. it can be written as $$\mathbf{v^T = y^T A}$$ for some vector 
$$\textbf{v}$$. Thus, we can write $$\mathbf{y^T Ax = v^T x}$$. But we know how to differentiate with our tricks, that is 
$$\frac{d}{d\textbf{x}} \mathbf{v^T x} = \mathbf{v^T}$$, and hence we know that $$\frac{d}{d\textbf{x}} \mathbf{y^T Ax} = \mathbf{y^T A}$$.

This should cover the basics of vector calculus! During the first week of the course, we will spend some more time on time 
on this and you will receive an excellent document written by two other TAs. If you understand these basics, you are well 
on your way to doing machine learning soon enough! 

{: .summary }
In this section, you have seen the Kronecker delta and a general strategy for finding multivariate derivatives.
