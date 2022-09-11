# Dynamical Amoroso Dvornicich via Genetic Algorithms

Aaron Berry \ Preston Kelly \ Version 0.1 \ Last Updated: 9/11/2022 

---

## Introduction

This project aims to explore the dynamical analogue to a theorem by Amoroso and Dvornicich via the use of genetic algorithms. The dynamical theorem can be stated as follows:

> **Conjecture:** (Dynamical Amoroso-Dvornicich) Let $L_n$ be the splitting field for $\phi^n(x) - x$. Then there exists a bound $c = c(\phi) > 0$ depending only on $\phi$ such that <br> <br> $$h_\phi(\alpha) \geq c$$ <br> whenever $\alpha$ is not a preperiodic point of $\phi$ over $L_n$.

In particular, we want some $c$ which does not depend on $n$.

We will not attempt to prove this conjecture. Rather, we use a genetic algorithm to generate numbers $\alpha$ in $L_n$ of small height, with the goal of developing a better understanding of how dynamical height behaves over splitting fields.

---

## Outline

- Generate the splitting field for $\phi(x)$

    - Define x over a polynomial ring, choose $\phi(x)$ and fix $n$
    - Pick the largest linear factor of $\phi(x) - x$ and generate the number field $L_n$ defined by this factor
    
    
- Generate an initial generation of points

    - Define a projective space $P$ over $L_n$, and a dynamical system over $P$
    - Pick an upper bound for the canonical height and generate $m$ points $\alpha$ in $L_n$ (not preperiodic) with height lower than the chosen bound
    - Store each $\alpha$ (a polynomial $c_na^n + \dots + c_1a + c_0$ where $a$ is the generator of $L_n$) in a list, graded by height
    
    
- Keep the $n$ points of smallest height, and flush the rest


- Given a generation size $s$, "breed" $s-n$ new points from the remaining $n$ points
    - Choose $s-n$ unique pairings from $n$ remaining points
