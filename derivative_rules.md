---
title: Derivative Rules
layout: default
nav_order: 4
---


## Derivative Rules

Here we provide the basic derivative rules. We separated them into (1) the most basic identities you should memorize, and (2) 
properties of the derivatives of complex functions.

### 1) Identities

- $$f(x) = c \implies f'(x) = 0$$,
- $$f(x) = x^n \implies f'(x) = nx^{n-1}$$,
- $$f(x) = a^x \implies f'(x) = a^x \log a$$, and hence $$f(x) = e^x \implies f'(x) = e^x$$,
- $$f(x) = \log_b x \implies f'(x) = \frac{1}{\log (b) \cdot x}$$, and hence $$f(x) = \log x \implies f'(x) = \frac{1}{x}$$,
- $$f(x) = \sin x \implies f'(x) = \cos x$$,
- $$f(x) = \cos x \implies f'(x) = - \sin x$$,
- $$f(x) = \tan x \implies f'(x) = \frac{1}{\cos^2 x}$$.

Moreover, it is useful to remember special cases of the second rule:
- $$f(x) = x \implies f'(x) = 1$$,  
- $$f(x) = ax \implies f'(x) = a$$, 
- $$f(x) = \sqrt{x} \implies f'(x) = \frac{1}{2\sqrt{x}}$$. 

### 2) Complex derivative rules

- $$(c \cdot f)'(x) = c \cdot f'(x)$$,
- $$(f + g)'(x) = f'(x) + g'(x)$$,
- $$(f \cdot g)'(x) = f'(x) \cdot g(x) + f(x) \cdot g'(x)$$,
- $$(\frac{f}{g})'(x) = \frac{f'(x) g(x) - f(x)g'(x)}{g(x)^2}$$,
- $$(f \circ g)'(x) = (f' \circ g)(x) \cdot g'(x)$$.

