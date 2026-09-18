+++
title = 'Cascade Operators and the Euler–Arnold Form: Papers I–III'
date = 2026-09-18
summary = "A three-paper sequence asking whether Tao's averaged Navier–Stokes blowup operator can be an Euler–Arnold operator — the form Arnold's theorem gives the Euler equations. Paper I excludes twelve of the sixteen couplings of his cascade from the frequency support alone; Paper II settles the four survivors in the isotropic category and shows no basic cascade operator is an isotropic Euler–Arnold operator at all; Paper III takes the remaining sum question across triads and answers it negatively, by measurement rather than by proof, for two-species cascades and every scalar inertia multiplier. Produced with substantial AI assistance under my direction; not yet independently reviewed."
tags = ['research', 'topic']
draft = false
# Unlisted: `private` makes the theme emit <meta name="robots" content="noindex,
# nofollow">; the build options keep the page out of the /projects/ index, the
# sitemap and RSS while it keeps its URL. See also static/robots.txt.
private = true
[build]
  list = 'never'
  render = 'always'
+++

*Three preprints, all dated 18 September 2026. All three were produced with substantial AI assistance under my direction — the full statement is at the [bottom of this page](#status-and-attribution).*

## The question

By Arnold's theorem the Euler equations are not just a bilinear operator obeying an energy identity: they are the Euler–Arnold equation of a Lie algebra with an inertia operator. Tao's averaged Navier–Stokes equation replaces the Euler nonlinearity with an averaged operator that blows up in finite time, and it satisfies the same energy identity. The sequence asks whether that operator can be an Euler–Arnold operator — whether the blowup mechanism is compatible with the geometric structure the Euler equations actually have, or only with the energy identity they happen to satisfy. The answer, across the three papers, is that it is not.

## The three papers

**I. Rigidity of the Euler–Arnold Form under Energy-Preserving Deformation** — 16 pp. Two classes of deformation of the Euler vertex are treated: triad reweightings, and vertices twisted by scalar Fourier multipliers on the three legs. On SDiff(T³) the energy-preserving triad reweightings that remain Euler–Arnold are exactly the global rescalings, and the family does not reopen for anisotropic, matrix-valued inertia operators; on Zeitlin's su(N) truncation of SDiff(T²) the corresponding family is two-dimensional instead, which is what gives the three-dimensional statement its content. Tao's operator lies in neither class and is reached separately: because his profiles all live in one thin annulus, a cascade triple is compatible with the Euler bracket only if it carries three distinct species, and twelve of the sixteen non-zero structure constants of his Table 1 carry fewer. Corollary 6.5 sharpens this — the twelve include every coupling that moves energy between scales, so what survives is single-scale and provably bounded. [Preprint](/preprints/euler-arnold-rigidity.pdf)

**II. The Isotropic Directional Obstruction for Cascade Operators** — 14 pp. The four couplings that pass Paper I's frequency-support test are settled in the isotropic category, by an argument using the directional structure of the Euler vertex and nothing about frequency geometry: on any non-degenerate triad, no rank-one tensor is an isotropic Euler–Arnold vertex. Since a basic cascade operator contributes exactly one rank-one tensor per block, no basic cascade operator is an isotropic Euler–Arnold operator — irrespective of species count, of the thin annulus, and of whether its frequencies close up. For general anisotropic inertia operators the complementary statement is proved: no block of an Euler–Arnold vertex vanishes faster than κ⁻¹ in the joint spread κ of the three inertia operators, and that rate is sharp, while Tao's surviving coupling needs a block to vanish identically. The paper also fixes the shape any treatment of finite sums must take — the only linear functionals vanishing on the Euler–Arnold class are the componentwise energy identity, which every cascade operator satisfies by construction, so the sum case cannot be decided linearly, nor on one triad at all. [Preprint](/preprints/isotropic-directional-obstruction.pdf)

**III. Cross-Triad Rigidity for Cascade Operators** — 7 pp. What Paper II leaves is whether one fixed coefficient set can reproduce an Euler–Arnold vertex on *all* triads at once. For a two-species cascade this is a gauge-trivialisation problem, answered negatively for every scalar inertia multiplier — by measurement rather than by proof, with residuals reported rather than ranks. A first invariant — the ratios of the blocks' Cayley hyperdeterminants — excludes all exponents but s = 0 and s = −2, Euler and its vorticity dual; that degeneracy is shown to be structural rather than accidental, since on the relevant stratum the hyperdeterminant reduces to the product of the block's four entries. It is also shown to be only a weakness of that invariant: the correct condition, that all the vertices lie in a single GL(2)³ orbit, fails at s = 0 and s = −2 as well. [Preprint](/preprints/cross-triad-rigidity.pdf)

## Status and attribution

Papers I and II prove what they assert, with a small number of finite hypotheses checked by an accompanying script rather than established in general. Paper III's negative answer is reached by measurement rather than by proof, as its own abstract states. The question and the direction are mine. The derivations, the numerical work, the reconstruction of Tao's cascade, and a first draft were produced with substantial AI assistance under my direction, and I am responsible for the contents, including any errors. Not yet independently reviewed; corrections welcome.
