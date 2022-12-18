---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 3
title: Graphical Models
---

# Graphical Models

## Motivation

Although this might sound surprising to many, there is actually a lot of statistics we can do without specifying specific 
distributions over our variables. Our main way to go about that is through using **graphical models** in which we explicitly 
define our variables and how they relate to each other. This allows us to formulate the (conditional) independence relationships 
between the variables.

First of all, you might wonder why we would exactly care about these conditional independence relations. Suppose, 
for the time being, we measure $$4$$ different binary variables, denoted as $$X_1, X_2, X_3$$, and $$Y$$. 
For example, $$X_1, X_2, X_3$$ could denote 3 different aspects of a house (e.g. $$X_1$$ is many/few rooms, 
$$X_2$$ is old/new house, and $$X_3$$ one/multiple floors) and $$Y$$ denotes whether it was sold for a high or low price.[^1]
We can imagine that these $4$ variables define one large join distribution (of an unknown kind), i.e. for all values 
$$x_1, x_2, x_3$$, and $$y$$, we can assess $$\mathbb{P}(X_1 = x_1, X_2 = x_2, X_3 = x_3, Y=y)$$. It is important to 
realize that when we have a joint distribution, we can find any marginal or conditional probability of the variable. 
For example, to find the probability of there being many rooms, given that the house was sold for a high price and the 
house was old, we can find this:

$$\mathbb{P}(X_1 = 1 \mid Y=1, X_2 = 0) = \frac{\mathbb{P}(Y=1, X_1 = 1, X_2 = 0)}{\mathbb{P}(Y=1, X_2 = 0)},$$

which we can evaluate through marginalisation by

$$\mathbb{P}(X_1 = 1 \mid Y=1, X_2 = 0) = \frac{\sum_{x_3} 
 \mathbb{P}(Y=1, X_1 = 1, X_2 = 0, X_3 = x_3)}{\sum_{x_1, x_3} 
 \mathbb{P}(Y=1, X_1 = x_1, X_2 = 0, X_3 = x_3)}.$$



Having the full joint distribution is our ideal case, exactly it allows us to ask these types of questions. In this case, 
we need to specify $$2^4 = 16$$ different values for each of the combinations of $$X_1, X_2, X_3$$, and $$Y$$.[^2] 
However, now imagine our variables taking on $$10$$ different values (which still, compared to variables that take on an 
infinite number of values) and having $$20$$ different variables. We would have to specify $$10^{20}$$ different values. 
To put this into perspective, that are more values than there are grains of sand on the planet. 

We will see that using graphical models and the independence relations they describe will allow us to reduce the number of parameters a lot.


## Bayesian networks

A directed graph $$\mathcal{G} = (\mathcal{V}, \mathcal{E})$$ is pair of nodes $$\mathcal{V}$$ and edges $$\mathcal{E}$$. 
For example, the graph with nodes $$\mathcal{V} = \{v_1, v_2, v_3 \}$$ and edges $$\mathcal{E} = \{(v_1, v_2), (v_3, v_2)\}$$ 
is given by:

**add**

If the edges have no direction, contrary to the graph above, we call the graph undirected. If we graph is directed, 
there might be some path over the edges that cycles back to its starting point, in which case we call the graph cyclic. 
If there is no such cycle, we call the graph acyclic.

A (probabilistic) graphical model is a way to express the conditional independence structures between random variables 
using a graph. Before diving into the formalities, let us start with an example. We will mostly focus on one type of 
graphical model, based on directed acyclic graphs. These models are called Bayesian networks. Do not worry if it does 
not all make sense in one go, it takes some time.

Suppose we revisit our espresso/strawberry story from earlier, i.e. we have variables $$E$$ for espresso, $$S$$ for strawberry, 
and $$F$$ for the person lighting fireworks. We now imagine a graph with $$3$$ nodes, corresponding to these variables. 
The only thing missing is the edges, and we want to add an edge from $$X$$ to $$Y$$ if we expect there might be a direct influence of 
$$X$$ on $$Y$$. Since there is no reason to assume that the espresso I drink influences how sweet my strawberry is, we 
draw no arrow from $$E$$ to $$S$$ and visa versa. Moreover, there is a direct effect from $$E$$ to $$F$$, since if I 
drink my espresso, the fireworks will be lit. Similarly, there will be an arrow from $$S$$ to $$F$$. This results in the following graph:

**add**

Now, suppose we make formal what we have written above. Since $$S$$ is not influenced directly by either $$E$$ or $$F$$, we conclude that 

$$\mathbb{P}(S \mid E, F) = \mathbb{P}(S),$$

and since $$E$$ is not influenced by $$S$$ or $$F$$ directly we know that

$$\mathbb{P}(E \mid C, F) = \mathbb{P}(E).$$

Moreover, since $$C$$ is influenced by both $$S$$ and $$E$$, we cannot remove any of the variables there. 

Let us know zoom in on the joint distribution $$\mathbb{P}(S, C, F$)$$. Again, if we can assess this distribution for 
all values $$s, c, f$$, we can ask all questions we want about it. If we write it out now, we observe by the chain rule that:

$$\mathbb{P}(S, C, F) = \mathbb{P}(S) \cdot \mathbb{P}(C \mid S) \cdot \mathbb{P}(F \mid C, S).$$

So far so good. Now, using our new independence relations, we know we can also write


$$\mathbb{P}(S, C, F) = \mathbb{P}(S) \cdot \mathbb{P}(C) \cdot \mathbb{P}(F \mid C, S),$$

since $$C$$ is independent of $$S$$. 

Let us try one more example. Suppose we have $$5$$ variables, $$X_1$$ up to $$X_5$$. In the naive setting, we would have that 
$$\mathbb{P}(X_1, \cdots, X_5)$$ needs $$2^5 - 1 = 31$$ values. Suppose now, that the effects are pretty simple, e.g. 
$$X_1$$ affects only $$X_2$$, $$X_2$$ affects only $$X_3$$, and so on. That is, our graph looks like this:

**add**

Then, we could write our joint as:

$$\mathbb{P}(X_1, \cdots, X_5) = \mathbb{P}(X_1) \cdot \mathbb{P}(X_2 \mid X_1) \cdot \mathbb{P}(X_3 \mid X_2) \cdot \mathbb{P}(X_4 \mid  X_3) \cdot \mathbb{P}(X_5 \mid X_4).$$

In this factorization, we observe that we need $$1$$ parameter for the $$\mathbb{P}(X_1)$$ distribution, and need $$3$$ 
parameters for each of the $$\mathbb{P}(X_i \mid X_{i-1})$$ distributions, i.e. a total of $$13$$ parameters rather than the 
$$31$$ we started off with. 




[^1]: Of course, the assumption of binary variables is a little awkward here, but the intuition will be slightly easier as such.
[^2]: Technically, since we know that all the probabilities will sum up to 1, we need only 15 parameters.