---
layout: default
parent: Linear Algebra
grand_parent: Essentials
nav_order: 5
title: Change of Basis
---

# Change of Basis


In the previous section, the elements of the matrix were determined by how they transform the basis vectors. Let's 
take a closer look at two different basis in $$\mathbb{R}^2$$: a canonical basis $$\{ \mathbf{b_1}, \mathbf{b_2}\}$$ 
and an arbitrary non-canonical basis $$\{\mathbf{d_1}, \mathbf{d_2}\}$$ whose elements can be expressed in the canonical 
basis as:

$$\mathbf{d_1} =  \begin{bmatrix}
           3/5\\
           1/3
         \end{bmatrix}, \, \, \, \, \mathbf{d_2}=  \begin{bmatrix}
           1/3\\
           1
         \end{bmatrix}.$$

The two bases are visualized in the figure below.

**add**


We can think of a basis as a language we use to explicitly write vectors and operators as matrices. However, the way an 
arbitrary operator $$\mathbf{A}$$ transforms a vector $$\mathbf{v}$$ shouldn't depend on the basis we use. Therefore, 
we must adjust the entries of the matrix depending on which basis we use, because as described before, rows of the 
matrix correspond to the vectors to which the basis vectors transform to. So let's try to motivate intuitively 
how we can transform a matrix $$\mathbf{A}$$ that is written in the canonical basis $$\{ \mathbf{b_1}, \mathbf{b_2}\}$$ 
into a matrix $$\mathbf{A}'$$ which describes the same operation, but in the new basis 
$$\{\mathbf{d_1}, \mathbf{d_2}\}$$. The procedure is as follows:

- We take a vector from the written using vectors from the new basis and _translate_ it into a _language_ of the old basis using a transformation $$\mathbf{S}$$.[^1]
- We act on this _translated_ vector with the operator $$\mathbf{A}$$ expressed in the canonical basis.
- We convert the transformed vector back to the _language_ of the new basis using the inverse transformation $$\mathbf{S}^{-1}$$.

So, in total, we can express the change of basis of a matrix as:

$$\boxed{\mathbf{A}' = \mathbf{S}^{-1}\mathbf{A}\mathbf{S} }$$

Next question is, what does the transformation $$\mathbf{S}$$ between _languages_ correspond to? Well, if we speak the 
_language_ of the new basis, then we would express the vectors of the new basis as $$\mathbf{d_1} = \begin{bmatrix}1,0\end{bmatrix}^{\text{T}}$$ 
and $$\mathbf{d_2} = \begin{bmatrix}0,1\end{bmatrix}^{\text{T}}$$. However, if we want to express these new vectors in the old canonical basis, 
then we would write them in the form of earlier equation. Therefore, the transformation $$\mathbf{S}$$ for this example is equal to:

$$\mathbf{S} = \begin{bmatrix}
           3/5 & 1/3\\
           1/3 & 1
         \end{bmatrix}.$$ 


The inverse transformation can be found and is equal to:

$$\mathbf{S}^{-1} = \begin{bmatrix}
           45/22 & -15/22\\
           -15/22 & 27/22
         \end{bmatrix},$$

which is not the nicest expression, but we can transform **any** operator $$\mathbf{A}$$ written in the canonical basis 
$$\{ \mathbf{b_1}, \mathbf{b_2}\}$$ into a matrix $$\mathbf{A}'$$ written in the $$\{\mathbf{d_1}, \mathbf{d_2}\}$$ basis. 


We can check whether the transformation $$\mathbf{S}^{-1}$$ makes sense by for example applying it on the vector $$\mathbf{d_1}$$ 
written in the canonical basis:

$$\mathbf{S}^{-1}\, \mathbf{d_1} = \begin{bmatrix}
           45/22 & -15/22\\
           -15/22 & 27/22
         \end{bmatrix} \begin{bmatrix}
           1/3\\
           1 
         \end{bmatrix} =  \begin{bmatrix}
           1\\
           0 
         \end{bmatrix},$$


which is exactly the expected result, because if we speak the _language_ of the $$\{\mathbf{d_1}, \mathbf{d_2}\}$$ basis, 
we would write the vector $$\mathbf{d_1}$$ as $$\mathbf{d_1} = \begin{bmatrix}1,0\end{bmatrix}^{\text{T}}$$. 

[^1]: In this context, translation is meant in the context of the language, not as a spatial translation.