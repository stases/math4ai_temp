---
layout: default
parent: Statistics
grand_parent: Essentials
nav_order: 3
title: Independence
---

{: .content }
In this section you will learn about independence of random variables.

# Independence

## Basic independence

Going back our intitial example with a customer rating out movie on a scale of $$1$$ to $$5$$, denoted as $$R$$, and them
being happy, denoted as $$H$$. Suppose we now introduce yet another variable, $$B$$ which denotes whether the user has blue eyes, again taking on values $$1$$ 
and $$0$$ denoting whether or not the user has blue eyes respectively. In this case, there is no reason to assume that my
belief that someone is happy changes after observing whether or not someone has blue eyes, i.e.

$$\mathbb{P}(H \mid B=1) = \mathbb{P}(H).$$

Without defining these notions formally here, you can convince yourself that there is no information about $$H$$ in $$B$$. 
However, we could imagine a situation where someone giving a higher rating for a movie because they are happy, i.e. if we
know that $$H=1$$, our believe in $$R=5$$ increases, that is:

$$\mathbb{P}(R=5 \mid H=1) > \mathbb{P}(R=5).$$

When there is no information about $$X$$ in $$Y$$, or when 

$$\mathbb{P}(X \mid Y) = \mathbb{P}(X),$$ 

 we say that $$X$$ and $$Y$$ are **independent**. You may also have encountered this as

$$\mathbb{P}(X, Y)  = \mathbb{P}(X) \cdot \mathbb{P}(Y),$$

which is exactly the same thing when multiplied by $$\mathbb{P}(Y)$$ and making using of the fact that 
$$\mathbb{P}(X, Y) = \mathbb{P}(Y) \cdot \mathbb{P}(X \mid Y).$$ When $$X$$ and $$Y$$ are not independent, i.e.
when $$X$$ tell me something about $$Y$$, we call them **dependent**. 

{: .exercise }
Suppose we want to parametrize a joint over 10 binary random variables, $$X_1, \cdots, X_{10}$$. If we do not assume any independence,
we would need $$2^{10} - 1 = 1023$$ parameters to describe this joint. Suppose now that all $$X_i$$ are independent, i.e.
that $$\mathbb{P}(X_1, \cdots, X_{10}) = \prod_{i=1}^{10} \mathbb{P}(X_i)$$. Explain why now we only need $$10$$ parameters
to describe our joint.

## Conditional Independence

In a real-life situation, simple independence is almost something you never encounter. A much more common scenario is 
that of two random variables being independent given some third variable. Suppose we consider two students that both 
travel by the same train to the university, and we denote $$S_1$$ as the binary variable describing whether student $$1$$ 
is on time for the lecture, and $$S_2$$ the binary variable describing whether student $$2$$ is on time. Intuitively, these 
events are related, since when you tell me that $$S_1$$ is on time, that increased my belief that $$S_2$$ also is on time, 
for the reason that the trains were not delayed. In other words,

$$\mathbb{P}(S_2 = 1 \mid S_1 = 1) > \mathbb{P}(S_2 = 1).$$ 

Similarly, if $$S_1$$ is not on time, in increased my belief that $$S_2$$
won't be on time. Therefore, we observe that $$S_1$$ and $$S_2$$ are not independent.

However, let us now introduce yet a third binary variable $$T$$ denoting whether the train was on time. By a similar argument, we have that 
How does knowing $$T$$ change the above situation? In this case, observing that $$S_1$$ is or is not on time if I 
already know $$T$$ will not tell me any **more** information than I could already derive from $$T$$. The reason is, that
the only thing it could tell me is something about whether or not the train is delayed, and since we already knew that the train 
was not delayed we obtain no information.

In this case, we have that

$$\mathbb{P}(S_2 \mid T, S_1) = \mathbb{P}(S_2 \mid T).$$

In that case, we say that $$S_2$$ is **conditionally independent** of $$S_1$$ given $$T$$. 
In other words, we say that $$X$$ is conditionally independent of $$Y$$ given $$Z$$, if my belief in $$X$$ is not affected by the 
outcome of $$Y$$ if I already know that $$Z$$. 

In the case above, we had a situation where $$X$$ and $$Y$$ were dependent, but $$X$$ and $$Y$$ were independent given some $$Z$$. 
I.e., even if there is an 'information flow' between $$X$$ and $$Y$$, there can be no 'information flow' from $$X$$ to $$Y$$ if 
we know that $$Z$$. Actually, the other case is also possible, the situation where $$X$$ and $$Y$$ are independent variables, 
but they become dependent given some variable $$Z$$. To illustrate this, let us consider a totally new - quite inspired on our breakfast - scenario.

Suppose that $$S$$ is the random variables that describes whether or not the first strawberry I eat on a day is sweet.
Moreover, let $$E$$ denote whether or not the first coffee I prepare is an espresso. Needless 
to say, the outcomes of these events do not affect each other, and hence $$S$$ and $$E$$ are independent. The reasons we picked such a weird
example is that even such totally disjoint event **can be made** conditionally independent if we consider a crazy enough third variable...


Assume for a moment we asked someone to follow us around during breakfast, making sure to light some fireworks 
exactly when either the first strawberry we eat on a given day is sweet or the first coffee we drink is an espresso 
(or both), denoted with $$F$$. Even though this example is perhaps not the most realistic one, it does show us an interesting
behaviour that can occur with these random variables: even though $$S$$ would not tell me anything about $$E$$ in general, suppose
now that $$F=1$$, i.e. I have seen some fireworks gone of, and I also just had a very sour strawberry. Then, is must be the case
that indeed my first coffee was an espresso, i.e. now $$S=0$$ did indeed tell me that $$E=1$$ **through** our third random
variable $$F=1$$. So here, fireworks did allow for an information stream between my morning espresso and strawberry. Of course, this 
example is slightly silly, but is does illustrate something fundamental: one needs to be careful when considering how random
variables affect one another, being imprecise about which variables we assume to be (conditionally) independent can remove and create patterns in 
our observations that are unexpected.

