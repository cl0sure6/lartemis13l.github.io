+++
title = 'Leray-Hopf Weak Solutions of the 2D Navier-Stokes Equations on the Torus: An Expository Construction'
date = 2026-09-03
summary = 'A self-contained construction of Leray-Hopf weak solutions to the two-dimensional incompressible Navier-Stokes equations on the flat torus — Galerkin approximation, energy estimates, Aubin-Lions compactness — followed by proofs of uniqueness in two dimensions and of global strong solutions for initial data in V. A closing section carries the identical estimates to the three-dimensional torus and halts at the precise line where they fail to close, stating the 3D result as a hypothesis and deliberately leaving the argument unclosed. Expository: no originality is claimed for any result.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

This is an expository article, not a research contribution, and it says so in its own abstract. Its purpose is to carry a single classical construction all the way through at full detail: given divergence-free initial data of finite energy on the torus, build a global-in-time weak solution of the incompressible Navier-Stokes equations, prove it is unique in two dimensions, and identify exactly what breaks in three.

The work sits at the end of the transition recorded elsewhere on this site — from control theory into functional analysis and partial differential equations. Its function as a document is to demonstrate that the analysis in the reading list has actually been absorbed to the point where a graduate-level argument can be reconstructed, checked and written down without gaps, rather than merely read.

Everything is set on the flat torus T² = R²/2πZ², and that choice is load-bearing in two specific places rather than cosmetic. It removes the boundary, so no trace theory is needed; it preserves the compact Sobolev embedding H¹ ↪ L² that the Aubin-Lions argument requires and that fails on R², where mass can escape to infinity; and it makes the Galerkin basis explicit, since the Stokes eigenfunctions are then just the divergence-free Fourier modes. The article states plainly that the corresponding results on R² and on bounded domains are true but are *not* corollaries of what it proves.

## My role

Single-author work; the write-up, the reconstruction of every argument, and the selection and sequencing of the material are mine.

## Approach

The account follows *The Three-Dimensional Navier-Stokes Equations: Classical Theory* by Robinson, Rodrigo and Sadowski most closely, with functional-analytic background drawn from Brezis and Evans and the Navier-Stokes framework from Temam and Constantin-Foias. No originality is claimed for any result; the contribution, such as it is, is one of assembly and completeness — the standing propositions are collected up front and each is referenced at its point of use, so the construction can be read without recourse to the sources.

The chain runs: Helmholtz-Leray decomposition and the Stokes operator, continuity estimates for the trilinear form, an explicit Galerkin basis, local and then global existence for the finite-dimensional Galerkin system, uniform energy bounds, compactness, and passage to the limit.

## What the article establishes

- **Existence (Leray, Hopf).** For every u₀ in H(T²) there exists at least one global-in-time weak solution attaining that initial datum. The limit is extracted from the Galerkin sequence by Aubin-Lions compactness together with Banach-Alaoglu, and the constructed solution is shown to satisfy the strong energy inequality.
- **Uniqueness in 2D.** The weak solutions constructed above are unique — the two-dimensional case of the question left open in three, closed here by a Grönwall argument on the difference of two solutions.
- **Global strong solutions in 2D (Ladyzhenskaya).** Initial data in V give rise to strong solutions that are global in time, with the enstrophy estimate closing because the 2D Ladyzhenskaya inequality distributes its weight as (1/2, 1/2) between the function and its gradient.
- **Where 3D fails, exactly.** Sections 3 through 5 never used the dimension, so Leray-Hopf weak solutions exist globally on T³ as well; what does not transfer is the passage from weak to strong. Taking the curl exposes the vortex-stretching term (ω·∇)u, absent in two dimensions, where vorticity is merely transported and diffused. The 3D Ladyzhenskaya exponents shift from (1/2, 1/2) to (1/4, 3/4), loading the gradient, and the Grönwall bracket becomes ‖u‖²‖∇u‖⁶ in place of the two-dimensional ‖u‖²‖∇u‖². The energy inequality still gives ‖u‖² bounded uniformly and ‖∇u‖² ∈ L¹(0,T), but it says nothing about ‖∇u‖⁶ — integrability there would require ∇u ∈ L⁶(0,T; L²), strictly more than the energy estimate provides — so the bracket need not be integrable and Grönwall does not apply.
- **An argument deliberately left open.** The 3D statement is given as *Hypothesis 7.3* rather than as a theorem, and the attempted proof is presented precisely in order to exhibit its own point of failure. Fujita-Kato supplies local-in-time strong solutions, but nothing bounds the enstrophy growth, so the local solution cannot be extended and global existence remains unproven. The conclusion names the obstruction — the energy estimate controls u in H¹ while the scaling-critical space is Ḣ^{1/2}, the "half-derivative gap" — and states explicitly that nothing in the article closes it, and that no claim is made about the Millennium problem.

## Links

- [Report / preprint](/preprints/ex_article.pdf)

## Remark

Expository work, written at the level of a first graduate course; 34 pages. It is offered as evidence of preparation in analysis and PDE rather than as a claim to a new result, and it is careful throughout to mark the boundary between what it proves and what remains open.
