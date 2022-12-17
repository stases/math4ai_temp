---
layout: default
parent: Linear Algebra
grand_parent: Essentials
nav_order: 6
title: Determinants
---

# Determinants


In mathematics, a determinant is a scalar value that is a function of a matrix, denoted as det$$(\mathbf{A})$$ or $$\left| \mathbf{A}\right|$$. 
Intuitively, we can think of a determinant as a measure of how much the unit area enclosed by original vectors changes under a transformation. 
To visualize this, let's assume that we have a transformation $$\mathbf{A}$$ of the following form:

$$\mathbf{A} = \begin{bmatrix}
           a & b\\
           c & d
         \end{bmatrix}.$$

If our original vectors were $$\mathbf{v_1}$$ and $$\mathbf{v_2}$$ as shown in the figure below (they are unit vectors), 
then the transformed vectors $$\mathbf{w_1}$$ and $$\mathbf{w_2}$$ are given by:

$$\mathbf{w_1} = \mathbf{A}\mathbf{v_1} = \begin{bmatrix}
           a \\
           c
\end{bmatrix} ,\, \, \, \mathbf{w_2} = \mathbf{A}\mathbf{v_2} = \begin{bmatrix}
           b \\
           d
\end{bmatrix}.$$


Now, let's denote the area of surfaces enclosed by original/transformed vectors as $$A_1$$ and $$A_2$$ respectively. 
Firstly, we can see that the area $$A_1$$ is simply a square and is equal to $$1$$, since both vectors are unit vectors. 
The second area $$A_2$$ is equal to $$A_2 = ad-bc$$, as can be easily proven using the formula for the surface of a 
parallelogram. Since the determinant is geometrically interpreted as the ratio of the original/transformed surface area 
enclosed by vectors, the determinant of the matrix $$\mathbf{A}$$ is then given by:

$$\text{det}(\mathbf{A}) = \frac{A_2}{A_1} = ad-bc.$$

In this simple example, we were dealing with a $$2\times 2$$ matrix, so we were calculating the surface areas. For example, 
in the case of a $$3 \times 3$$ matrix, we would be calculating the ratio of volumes enclosed by $$3$$ vectors, and generally, 
for a $$n\times n$$ matrix, we would calculate the $$n$$-dimensional volume. Now, let's come up with some constraints which 
naturally follow from the intuition provided above. 


Firstly, we can see that determinants can be only defined for square matrices. In order to justify this claim, let's think 
of how non-square act on vectors. Let's imagine we have a $$\mathbf{B} \in \mathbb{R}^{m\time n}$$ (i.e. we have a $$m \times n$$ matrix). 
This means that the input vector is $$n$$-dimensional, while the output vector is $$m$$-dimensional. If we wish to calculate 
the ratio of volumes, we can very quickly see that we come to a problem. In the original space, we had a $$n$$-dimensional volume, 
while in the output space, we have a $$m$$-dimensional volume, and we cannot calculate the ratio of the two because we are 
dealing with different objects. For example, if $$n=2$$ and $$m=3$$, then the determinant would be the ratio of a volume 
and a surface area, which does not make sense. So, the first constraint is that only square matrices have a determinant. 

Secondly, not only that the matrix has to be a square matrix, but it also has to be invertible. To see why this is the case, 
let's assume that the matrix isn't invertible. As we know, a property of a matrix $$\mathbf{A}$$ to be invertible implies 
that there is a transformation $$\mathbf{A}^{-1}$$ such that $$\mathbf{A}\mathbf{A}^{-1}=\mathbf{A}^{-1}\mathbf{A} = \mathbf{I}$$, 
i.e. there exists a matrix $$\mathbf{A}^{-1}$$ which uniquely undoes the transformation $$\mathbf{A}$$. Visually, if a matrix 
is not invertible, then this implies that some vectors are mapped to the same axis in the output space, i.e. we cannot 
disentangle them. For example, imagine a case where we have a $$3 \times 3$$ matrix that maps two basis vectors to the 
same axis (i.e. they are colinear). This mapping then isn't invertible, because we cannot distinguish input vectors 
that were mapped to the same axis in the output space, so we cannot write a unique way to map output vectors back to the 
input space. We can visualize this as having a box, and then we fold so it "crumbles" into a 2D-shaped object. 
Although this is mapping from 3D space to 3D space, two dimensions are the same, so we effectively have a 3D to 2D mapping, 
and we know that in this case, we cannot calculate the determinant. Although this condition can be shown more formally, 
this is the main intuition behind it. To summarize, the second constraint is that the matrix whose determinant we wish to 
calculate has to be invertible. 

We have shown a formula for calculating determinants of square invertible $$2\times 2$$ matrices, but how would we 
generalize this for $$n \times n$$ matrices? There is a general formula is quite elaborate, however, in practice, you 
will never calculate determinants of matrices by hand. 
