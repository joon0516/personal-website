---
layout: distill
title: Is every function integrable?
description: # an example of a distill-style blog post and main elements
tags: math real-analysis
# giscus_comments: true
date: 2024-05-23
featured: true
thumbnail: #assets/img/9.jpg

bibliography: 2018-12-22-distill.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
# toc:
#   - name: Equations
#     # if a section has subsections, you can add them as follows:
#     # subsections:
#     #   - name: Example Child Subsection 1
#     #   - name: Example Child Subsection 2
#   - name: Citations
#   - name: Footnotes
#   - name: Code Blocks
#   - name: Interactive Plots
#   - name: Layouts
#   - name: Other Typography?

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }
---


## Differentiability

In a standard calculus course, we often learn functions that are differentiable, namely functions that are continuous, have no "sharp turns", and have no vertical tanglent line. So, a function like $$ f(x) = x $$ is differentiable but $$ g(x) = \vert x \vert $$ and $$ h(x) = \sqrt[3]{x} $$ are not since $$ g $$ has a "sharp turn" at 0 and $$ h $$ has a vertical tangent line at 0.

To be more precise, a function $$ f \colon A \to \mathbb{R} $$ is said to be differentiable at $$ c \in A$$ if $$ f'(x) = \lim_{x \to c} \frac{f(x)-f(c)}{x-c} $$ exists. One beautiful result of this definition is that differentiability implies continuity.

<b>Theorem 1.1.1.</b> <i>If $$ f \colon A \to \mathbb{R} $$ is differentiable at $$ c \in A$$, then $$ f $$ is continuous at $$ c $$. </i> <d-cite key="abbott2015understanding"></d-cite> \\
<i>Proof. </i>
Suppose $$ f $$ is differentiable at $$ c $$, so $$ f'(x) = \lim_{x \to c} \frac{f(x)-f(c)}{x-c} $$ exists. Notice that $$ \lim_{x \to c} (f(x)-f(c)) = \lim_{x \to c} (\frac{f(x)-f(c)}{x-c})(x-c) = f'(c) \cdot 0 = 0$$. Therefore,  $$ \lim_{x \to c} f(x) = f(c) $$, thus $$ f $$ is continuous at $$ c $$. ∎

Now you may wonder, what are the functions that are integrable? Is there even a function that is not integrable? What is the relationship between continuity and integrability? To answer these questions, we need to rigorously define what it means to be integrable just like how we did for differentiability.


## Integrability

In a standard calculus course, it is not often discussed whether a function is integrable. We learn about Riemann sums and how the upper sum is an overestimation and how the lower sum is an underestimation of the area under the curve. And to find the exact area under the curve, we make the width of each rectangle infinitesimally small, so that when you add all those rectangles up, you get the exact area under the curve. So, you have probably seen this: $$ \int_a^b f(x) \, dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^*) \Delta x_i $$ where $$ x_i^* $$ is any number that is in the $$ i^{th} $$ subinterval.

Now consider $$ f \colon \mathbb{R} \to \{0, 1\} $$ where $$ f(x) =
\begin{cases} 
1 & \text{if } x \in \mathbb{Q}, \\
0 & \text{if } x \notin \mathbb{Q}.
\end{cases} $$.
This function is also known as the Dirichlet function, named after the German mathematician <i>Peter Gustav Lejeune Dirichlet<i>.

Say we want to compute $$ \int_0^1 f(x) dx$$. No matter how we partition $$[0,1]$$, you can find a rational number and an irrational number in each subinterval since $$ \mathbb{Q} $$ and $$ \mathbb{I} $$ are both dense in $$ \mathbb{R} $$. This means that our smallest value in each subinterval is 0 and the largest value in each subinterval is 1. This implies that letting $$ f(x_i^*) $$ be the smallest value in that subinterval results in $$ \int_0^1 f(x) dx = 0$$, but letting $$ f(x_i^*) $$ be the largest value in that subinterval results in $$ \int_0^1 f(x) dx = 1$$. We all know that $$0 \not= 1$$, so... what went wrong?

We need to know for sure that $$ f $$ is integrable before we can compute $$ \int_0^1 f(x) dx$$. Before we do that, let's introduce some notation. Let $$P$$ of $$ [a,b] $$ be a finite set of points in $$[a,b]$$ (we call this a partition of $$[a,b]$$). The convention is to list these points in increasing order, so an example of $$P$$ in $$[0,1]$$ might be $$P=\{0, 0.2, 0.4, 0.5, 0.7, 0.9 ,1\}$$. Now, let arbitary  $$P=\{a=x_0, x_1, x_2, ... ,x_n=b\}$$. We define $$ m_k = \inf\{f(x) \vert x \in [x_{k-1}, x_k] \} $$ (the smallest value of $$f(x)$$ in $$k^{th}$$ subinterval) and $$ M_k = \sup\{f(x) \vert x \in [x_{k-1}, x_k] \} $$ (the largest value of $$f(x)$$ in $$k^{th}$$ subinterval). Then, the lower and upper sum of $$f$$ with the partition $$P$$ is given by $$L(f,P) = \sum_{k=1}^n m_k(x_k - x_{k-1})$$ and  $$U(f,P) = \sum_{k=1}^n M_k(x_k - x_{k-1})$$ respectively. Now, let $$ \mathcal{P} $$ be the set of all possible partitions of $$[a,b]$$. So, any $$P$$ of $$[a,b]$$ is an element of $$ \mathcal{P} $$. We define lower integral of $$f$$ as $$ L(f) = \sup\{L(f,P) \vert P \in \mathcal{P} \} $$ (greatest $$L(f,P)$$ out of every partition $$P$$). Similarily, we define upper integral of $$f$$ as $$ U(f) = \inf\{U(f,P) \vert P \in \mathcal{P} \} $$ (smallest $$U(f,P)$$ out of every partition $$P$$). It is not hard to see that $$U(f) \geq L(f)$$ if $$f$$ is bounded. <d-cite key="abbott2015understanding"></d-cite>

Finally, let us define what it means for a function to be integrable (more specifically, Riemann-integrable). \\
<b>Definition 1.1.2.</b> <i>A bounded function $$f$$ defined on $$[a,b]$$ is Riemann-integrable if $$U(f) = L(f)$$.</i> <d-cite key="abbott2015understanding"></d-cite> \\
If $$f$$ is Riemann-integrable, then $$\int_a^b f(x) dx = U(f) = L(f)$$.




