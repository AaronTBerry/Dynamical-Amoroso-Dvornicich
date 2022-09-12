# Dynamical Amoroso Dvornicich via Genetic Algorithms

Aaron Berry \ Preston Kelly \ Version 0.1 \ Last Updated: 9/11/2022 

---

## Introduction

This project aims to explore the dynamical analogue to a theorem by Amoroso and Dvornicich via the use of genetic algorithms. The dynamical theorem can be stated as follows:

> **Conjecture:** (Dynamical Amoroso-Dvornicich) Let $L_n$ be the splitting field for $\phi^n(x) - x$. Then there exists a bound $c = c(\phi) > 0$ depending only on $\phi$ such that <br> <br> $$h_\phi(\alpha) \geq c$$ <br> whenever $\alpha$ is not a preperiodic point of $\phi$ over $L_n$.

In particular, we want some $c$ which does not depend on $n$.

We will not attempt to prove this conjecture. Rather, we use a genetic algorithm to generate numbers $\alpha$ in $L_n$ of small height, with the goal of developing a better understanding of how dynamical height behaves over splitting fields.

---

## Algorithm Outline

1. (Preliminaries) Fix $\phi(x)$ and a power $n$, and generate the splitting field $L_{n,\phi}$ with the largest linear factor of $\phi^n(x) - x$ as the defining polynomial (note that we additionaly generate an associated 1-dimensional projective space $P_L$ over $L_{n,\phi}$ and a dynamical system $D_P$ over $P_L$).
1. (Initialization) Choose $k$ points $\alpha$ in $L_{n,\phi}$ such that no $\alpha$ is preperiodic in $D_P$ (i.e. all $\alpha$ have canonical height $\hat{h}_\phi(\alpha) > 0$). This is the **initial population**.
    1. Note that each $\alpha$ will have the form $$\alpha = c_da^d + c_{d-1}a^{d-1} + \dots + c_1a + c_0$$ with each $c_i$ an integer and $a$ the generator for $L_{n,\phi}$.
1. (Store and Grade) Store the initial population in an array sorted in ascending order by $\hat{h}_\phi(\alpha)$. This canonical height will serve as the **fitness score** for each $\alpha$ -- a lower height corresponds to a better score. 
1. (Selection) Choose the $l$ elements with best fitness score from the initial population. These $\alpha_1, \dots, \alpha_l$ are **parents**.
1. (Breeding) Randomly select $k - l$ unique pairings from the parents. For each paring $(\alpha_i,\alpha_j)$, define $$\beta_{ij} = b_da^d + b_{d-1}a^{d-1} + \dots + b_1a + b_0$$ where each coefficient $b_m$ is with equal probability either the corresponding coefficient (in terms of degree) of $\alpha_i$ or $\alpha_j$. These $\beta$ are the **offspring**.
    1. (Mutation) For each $b_m$ include a small chance of mutation, where a random integer in [-10,10] is chosen instead (currenly via Uniform Distribution).
1. (Store and Grade) Store the parents and offspring along with each of their canonical heights in a new array, called the **offspring population**, sorted in ascending order by height. 
    1. (Generational Fitness) Optionally report a mean fitness score for the offspring population.
1. (Main Loop) Repeat steps 4-7 by choosing parents from the offspring population until termination is triggered.
1. (Termination) Terminate the main loop after fitness score is minimized or $N$ generations are bred. Report candidates with best fitness score from the final offspring generation.

---

## Changelog v0.2

---

## To Do

---

## Resources and References

- J. H. Silverman. *The Arithmetic of Dynamical Systems*, Springer, New York, 2007
- F. Amoroso and R. Dvornicich. A lower bound for the height in abelian extensions. *J. Number Theory*, 80(2):260–272, 2000
- M. Keet. "Genetic Algorithms - An overview (inline)," http://www.meteck.org/gaover.html
- El Otmani, S. and Rhin, G. and Sac-Epee, J.-M. Finding new limit points of {M}ahler's measure by genetic algorithms. *Exp. Math.*, 28(2):129-131, 2019
- C. James. Introduction to some problems in Arithmetic Dynamics. https://github.com/carsonaj/Mathematics/blob/master/Introduction%20to%20Arithmetic%20Dynamics/Arithmetic%20Dynamics%20Notes.pdf


