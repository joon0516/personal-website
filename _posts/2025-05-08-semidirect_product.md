---
layout: distill
title: Notes on Semidirect Products
description: # an example of a distill-style blog post and main elements
tags: math abstract-algebra
# giscus_comments: true
date: 2025-05-08
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


## Direct Product

Let $$ N $$ and $$ H $$ be groups. Recall that the direct product is defined as:  
$$
N \times H = \{(n, h) \mid n \in N, h \in H\}
$$
with component-wise operation:
$$
(n_1, h_1)(n_2, h_2) = (n_1n_2, h_1h_2)
$$
where the identity is $$ (e_N, e_H) $$ and the inverse is $$ (n, h)^{-1} = (n^{-1}, h^{-1}) $$. This is also known as the **external direct product** of groups.  

Notice how we are constructing a *larger* group (in terms of set cardinality) from two smaller groups using the external direct product. Informally, the **internal direct product** refers to the opposite process—splitting a larger group into two subgroups such that their direct product is isomorphic to the original group. Before we dive into the concept of the **internal direct product**, let us first define what it means for one subgroup to be a complement of another.

### Complement
**Definition**  
Let $$ G $$ be a group and $$ N \leq G $$. A subgroup $$ H \leq G $$ is called a **complement** of $$ N $$ in $$ G $$ if:
- $$ G = NH $$ (i.e., every element $$ g \in G $$ can be written as $$ g = nh $$ for some $$ n \in N, h \in H $$)  
- $$ N \cap H = \{e\} $$.

**Remark**  
If $$ H $$ is a complement of $$ N $$ in $$ G $$, then $$ N $$ is a complement of $$ H $$ in $$ G $$ (i.e., $$ NH = HN $$ iff $$ NH \leq G $$)

**Lemma**  
If $$ N, H $$ are complements in $$ G $$, then $$ \phi: N \times H \to G $$ with $$ \phi(n, h) = nh $$ is a bijection.

**Proof**  
$$ \phi $$ is injective because  
$$
\begin{aligned}
h_1 n_1 &= h_2 n_2 \\
\Rightarrow h_2^{-1} h_1 &= n_2 n_1^{-1} \\
\Rightarrow h_2^{-1} h_1 &= n_2 n_1^{-1} = e \in N \cap H = \{ e \} \\
\Rightarrow h_1 &= h_2, \quad n_1 = n_2
\end{aligned}
$$  
$$ \phi $$ is surjective because $$ \text{Im}(\phi) = \{ nh \mid n \in N, h \in H \} = NH = G $$.  
Thus, $$ \phi $$ is a bijection. ∎

### Internal Direct Product
Now, let's discuss the internal direct product.

**Definition**  
A group $$ G $$ is the **internal direct product** of two subgroups $$ N $$ and $$ H $$ if:

- $N \trianglelefteq G$, $H \trianglelefteq G$
- $N \cap H = $ $$\{e\}$$
- $NH = G$

We claim that $$ G \cong N \times H $$.

**Proof**  
We know that $$ \phi $$ is a bijection. So, we only need to now show that $$ \phi $$ is a homomorphism.

First, notice that  
$$
h_1 n_2 = h_1 n_2 h_1^{-1} h_1 = (h_1 n_2 h_1^{-1}) h_1 = \mathbf{n} h_1 \quad (\text{since } h_1 n_2 h_1^{-1} \in N)
$$  
Then, notice  
$$
h_1 n_2 = n_2 n_2^{-1} h_1 n_2 = n_2 (n_2^{-1} h_1 n_2) = n_2 \mathbf{h} \quad (\text{since } n_2^{-1} h_1 n_2 \in H)
$$  
So, $$ \mathbf{n} = n_2 $$, $$ \mathbf{h} = h_1 $$ and $$ h_1 n_2 =  \textbf{nh} = n_2 h_1 $$.

Finally,  
$$
\begin{aligned}
\phi((n_1, h_1)\cdot(n_2, h_2)) 
&= \phi((n_1n_2, h_1h_2)) \\
&= n_1n_2h_1h_2 \\
&= n_1 h_1 n_2 h_2 \quad \text{since } h_1n_2 = n_2h_1 \\ 
&= \phi(n_1, h_1) \cdot \phi(n_2, h_2)
\end{aligned}
$$

Therefore, $$ G \cong N \times H $$. ∎

## Semidirect Product

**Question.** Can we still have an isomorphism $ G \cong N \ \text{(some operator)} \ H $ when $$ H \leq G $$ but not normal?

The answer is **yes**. We can define the group operation as  
$$
(n_1, h_1)\cdot(n_2, h_2) = (n_1h_1n_2h_1^{-1}, h_1h_2),
$$  
which gives a structure known as the **semi-direct product**. Note that $$ n_1(h_1n_2h_1^{-1}) \in N $$ since $$ N \trianglelefteq G $$. Commonly, this is expressed as  
$$
(n_1, h_1)\cdot(n_2, h_2) = (n_1 \varphi_{h_1}(n_2), h_1h_2)
$$  
where $$ \varphi: H \to \text{Aut}(N) $$ is defined by $$ \varphi_h(n) = hnh^{-1} $$. And this structure is denoted by the operator $$ N \rtimes H $$.  

**Definition**  
A group $$ G $$ is the **internal semi-direct product** of two subgroups $$ N $$ and $$ H $$ if:

- $N \trianglelefteq G$, $H \leq G$ (Notice that the $H \trianglelefteq G$ requirement is relaxed)
- $N \cap H = $ $$\{e\}$$
- $NH = G$

We claim that $$ G \cong N \rtimes  H $$.

**Proof**  
We know that $$ \phi $$ is a bijection. So, we only need to now show that $$ \phi $$ is a homomorphism. Notice that,

$$
\begin{aligned}
\phi((n_1, h_1)\cdot(n_2, h_2)) 
&= \phi((n_1h_1n_2h_1^{-1}, h_1h_2)) \\
&= n_1h_1n_2h_1^{-1}h_1h_2 \\
&= n_1 h_1 n_2 h_2 \\ 
&= \phi(n_1, h_1) \cdot \phi(n_2, h_2)
\end{aligned}
$$

Therefore, $$ G \cong N \times H $$. ∎

**Remark**  
Notice how direct product is a special case of semi-direct product. To see this, let $$ \varphi $$ be trivial (i.e., $$ \varphi_h(n) = hnh^{-1} = n $$), then the semi-direct product becomes a direct product since  
$$
(n_1, h_1)\cdot(n_2, h_2) = (n_1 \varphi_{h_1}(n_2), h_1h_2) = (n_1n_2, h_1h_2).
$$

## Zappa–Szép Product

Can we relax the requirements even further? The answer is yes.  
If we only assume:
- $ N, H \leq G $
- $ N \cap H = $ $$\{e\}$$
- $ NH = G $

then $$ G $$ can be expressed as an **internal Zappa–Szép product**, written as $$ G \cong N \bowtie H $$.  
We won’t go into the details here, but feel free to explore this generalization further.
