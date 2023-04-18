[]
# Introduction to multivariate calculus

## Intuition

Before deep diving into derivatives, it is reasonable to ask ourselves what we mean when we talk about the derivative of 
some function with respect to some variable. You may know that the derivative describes the **rate of change** of the function.
With 'rate of change' we refer to how quickly the function value increases at some point $$x$$ when we increase the value of $$x$$. 
A running metaphor we will use is the following. We can imagine a variable $$y$$ which is formed through applying function $$f$$ to 
$$x$$, i.e. $$y = f(x)$$. In this case, we call x an **input** and call y an **output**. We are often interested in 
studying how **sensitive** our outputs are to a change in the inputs, or how much our inputs **influence** our outputs, 
as we will get more into it soon. This sensitivity is exactly what is captured by the derivative, e.g. if the derivative of the 
output with respect to the input is large in some point, we know that output is 'sensitive' to a small change increase around 
that point. Now, you can picture this as a machine spitting out outputs $$y$$ controlled with many knobs, where each knob 
corresponds to a variable $$x$$. The derivative tells us how sensitive the value our function spits out is to any turn of 
the knobs. Note that standard functions $$f: \mathbb{R} \to \mathbb{R}$$ are machines with one knob and spit out one value, 
but general functions $$f: \mathbb{R}^m \to \mathbb{R}^n$$ are machines with $$m$$ knobs and spit out $$n$$ different values. 
As we will look at later in this section, we have $$m \times n$$ derivatives in the latter case, for we can look at the 
sensitivity of each output to any of the knobs.


More important, perhaps, is the question of why we care about derivatives at all. In the context of machine learning, 
we are often very interested in a function that describes how well our model performs given our parameters. What we mean 
with 'doing well' is not too important right now, so let us presume that we have some measure of 
`doing well' for the time being. It is common to instead of maximizing performance, minimize the error we make, which are equivalent views 
on the same thing. Let us, for the sake of simplicity, say that our model parameter is given by $x$ and our error rate 
is given by $$f(x) = x^2 + 4x -2$$:

**ADD IMAGE LATER**

If this function describes our error given our model parameters, we would be very interested in finding the point where 
this error rate is minimum, which is exactly why we want to use the derivative. We notice that in our minimum (which 
soon enough will turn out to be given by $$x=-2$$), the rate of change of our function is $$0$$. Please take your time to 
verify this, because this point is crucial. 

As you might remember from a previous calculus course, the derivative of the function $$f(x)$$ is given by $$f'(x) = 2x + 4$$:

**ADD IMAGE LATER**

Here we see that for all points less than $$-2$$, indeed the derivative is negative (i.e. the function decreases) and for 
all points greater than $$x=-2$$, the derivative is positive (i.e. the function increases). It is exactly the minimum point 
$$x=-2$$ where be function does from decreasing to increasing. If we want to find this point $$x=-2$$ algebraically, we simply 
solve $$2x + 4 = 0$$, which of course turns out to be for $$x=-2$$. 

The following sections will deep dive into how you can find these derivatives. We will first review the univariate case 
such as the function we just covered. We will then steadily work our way up to higher-dimensional derivatives with the aim 
of you being able to differentiate any ML/DL type of function. 

We do now want to spend too much time on basic differentiation techniques and rather give you a general approach to 
differentiation from which things such as the sum rule, product rule, chain rule, et cetera, will follow directly. 
If you need a refresher on the basic derivative rules, we included them in [this section](../../derivative_rules). Let us now 
dive into the actual derivatives!
