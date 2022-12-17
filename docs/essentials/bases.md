---
layout: default
parent: Linear Algebra
grand_parent: Essentials
nav_order: 2
title: Bases
---

# Bases



Similar to the previous section, we will first informally motivate the definition of a basis, and only then formalize it.

## Informal definition

The basis of a vector space provides an organized way to represent any vector in that space. As a simple example, 
let's think about possible colors produced by a pixel on the screen you are reading this on. Every pixel consists of 3 
lighting elements: red, green, and blue, and every other color can be reproduced by varying the intensities of each of 
these colors. Since the lighting elements are independent, we can represent an arbitrary color $$\mathbf{c}$$ as follows:

$$\mathbf{c} =  \begin{bmatrix}
           r_i\\
           g_i \\
           b_i
         \end{bmatrix},$$

where $$r_i$$, $$g_i$$, and $$b_i$$ denote the intensities of the red/green/blue light. By tuning these three numbers, 
we can represent any color reproducible by our monitor. Now, let's rewrite this more suggestively:

$$\mathbf{c} = \begin{bmatrix}
           r_i \\
           0 \\
           0
         \end{bmatrix} +   \begin{bmatrix}
           0\\
           g_i \\
           0
         \end{bmatrix} +  \begin{bmatrix}
           0\\
           0 \\
           b_i
         \end{bmatrix} =  r_i \cdot \begin{bmatrix}
           1\\
           0 \\
           0
         \end{bmatrix} + g_i \cdot \begin{bmatrix}
           0\\
           1 \\
           0
         \end{bmatrix} + b_i \cdot\begin{bmatrix}
           0\\
           0 \\
           1
         \end{bmatrix}.$$

We can now also give unique names to the column vectors and write the previous expression as follows:

$$\mathbf{c} = r_i \cdot \mathbf{r} + g_i \cdot \mathbf{g} + b_i \cdot \mathbf{b},$$

where: 
$$\mathbf{r} =  \begin{bmatrix}
           1\\
           0 \\
           0 \end{bmatrix}, \, \, \, \, 
\mathbf{g} =  \begin{bmatrix}
           0\\
           1 \\
           0 \end{bmatrix}, \, \, \, \, 
\mathbf{b} =  \begin{bmatrix}
           0\\
           0 \\
           1 \end{bmatrix}.$$


The color vector $$\mathbf{c}$$ has been written as a weighted sum of other vectors, and this is called a linear combination. 
Since we can uniquely represent any vector (color) using these three vectors, we say that vectors $$\mathbf{r}$$, 
$$\mathbf{g}$$ and $$\mathbf{b}$$ form a basis. A basis can be thought of as a set of independent vectors whose linear 
combination can uniquely represent any vector. The basis of this form, where the $$n$$-th basis vector has $$1$$ as the 
$$n$$-th element and $$0$$ otherwise, is called a canonical basis and is the most simple form of basis. 


It is worth investigating why we impose the condition that the basis vectors need to be independent, and what independence means. 
For simplicity, imagine that a purple color $$\mathbf{p}$$ can be expressed as a linear combination of red and blue:

$$\mathbf{p} = \frac{1}{\sqrt{2}}\, \mathbf{r} + \frac{1}{\sqrt{2}}\, \mathbf{b} = \frac{1}{\sqrt{2}}\, \begin{bmatrix}
           1 \\
           0 \\
           1
         \end{bmatrix}$$

Now, let's imagine that we add the color purple to our basis, so our basis now consists of $$\left\{\mathbf{r},\mathbf{g},\mathbf{b},\mathbf{p} \right\}$$ 
(you have 4 lights in your pixel now). Your friend told you about an imaginary color durple $$\mathbf{d}$$, and they told 
you that they use the $$\left\{\mathbf{r},\mathbf{g},\mathbf{b} \right\}$$ basis for their pixels. They represent the color durple as follows:

$$ \mathbf{d} =\frac{1}{\sqrt{2}}\, \begin{bmatrix}
           -1 \\
           0 \\
           1
         \end{bmatrix}$$

In order to reproduce this color, you start turning the 4 knobs of color intensities (one for each different color in your pixel). 
First, you do not use your purple color, and you just stick with red and blue. You find that the following combination reproduces durple:

$$\mathbf{d}=  - \frac{1}{\sqrt{2}}\, \mathbf{r} + \frac{1}{\sqrt{2}}\, \mathbf{b} =- \frac{1}{\sqrt{2}}\, \begin{bmatrix}
           1 \\
           0 \\
           0
         \end{bmatrix} + \frac{1}{\sqrt{2}} \begin{bmatrix}
           0 \\
           0 \\
           1
         \end{bmatrix} = \frac{1}{\sqrt{2}} \begin{bmatrix}
           -1 \\
           0 \\
           1
         \end{bmatrix}$$

However, you start turning the purple knob, tune red and blue a bit, and you realize that also the following combination produces durple:

$$\mathbf{d}=  -  2\cdot \mathbf{r} + \mathbf{p} = - \frac{1}{\sqrt{2}}\, \begin{bmatrix}
           2 \\
           0 \\
           0
         \end{bmatrix} + \frac{1}{\sqrt{2}}\, \begin{bmatrix}
           1 \\
           0 \\
           1
         \end{bmatrix} = \frac{1}{\sqrt{2}}\, \begin{bmatrix}
           -1 \\
           0 \\
           1
         \end{bmatrix}$$

This tells us that after adding the purple color to our basis, our representation of the durple color was no longer unique, 
i.e. there were multiple ways to produce it. This stems from the fact that we have added purple to our basis, which was not 
independent since we were able to write it as a linear combination of already existing colors (red and blue). An equally 
valid choice of basis would have been to remove the color red from our basis set, and simply have $$\left\{\mathbf{g},\mathbf{b},\mathbf{p} \right\}$$ as our basis. 


An intuitive way to think of a basis is as a set of vectors, of which none can be written as a linear combination of the rest. 
Formally it can be shown that the number of basis vectors has to equal the dimension of the vector space. For example, 
in the example above, the number of basis vectors was 3, as we had 3-dimensional vectors. 
If we were to add any more vectors to our basis, we would necessarily add vectors that are no longer independent of each 
other, and thus we wouldn't have a systematic and unique way to represent arbitrary vectors. If we were to remove any vectors 
(for example, have 2 vectors in our basis), we wouldn't be able to express an arbitrary vector as a linear combination of the 
basis vectors, as we would be missing _building blocks_.

## Formal definition

In Linear Algebra, the basis of a vector space V is formally defined as follows.
>A basis $$B$$ of a vector space $$V$$ over a field $$\mathbb{F}$$ is a linearly independent subset of $$V$$ that _spans_ $$V$$. 
>This subset, therefore, has to satisfy the following conditions:
- **Linear independence**: For every finite subset $$\{ \mathbf{v_1}, \cdots, \, \textbf{v}_m\}$$ of $$B$$, neither of the $$m$$ elements can be represented as a linear combination of the rest.
- **Spanning property**: For every vector $$\mathbf{v}$$ in $$V$$, one can choose scalars $$\lambda_1, \cdots, \lambda_n$$ from the field $$\mathbb{F}$$ and $$\mathbf{v_1}, \cdots,  \mathbf{v_n}$$ such that $$\mathbf{v} = \lambda_1  \mathbf{v_1} + \cdots + \lambda_n  \mathbf{v_n}$$.


The first condition states what we discussed above; if we wish to have a basis, we mustn't be able to represent any of the 
basis elements by a linear combination of other basis elements. This is required if we wish to uniquely represent every vector using basis vectors.

The second condition tells us that we must be able to represent **any** vector from the vector space using a linear combination of the basis vectors. 
These two conditions combined lead to the fact that for a basis of a $$n$$-dimensional vector space we must have exactly $$n$$ linearly independent basis vectors.