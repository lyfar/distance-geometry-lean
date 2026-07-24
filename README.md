# Distance Geometry in Lean

This repository is part of an AI-assisted research workflow that formalizes mathematics in Lean so results are independently checkable. For this project, the possible biomedical path is indirect. Distance geometry
is used in [protein-structure determination](https://pmc.ncbi.nlm.nih.gov/articles/PMC4384350/),
and structural analysis informs
[gene-therapy vector design](https://www.nature.com/articles/gt2009101).
This repository does not claim a gene-therapy result. It tests whether our
AI-assisted workflow can turn mathematics into correct, reviewable, reusable
proofs.

This repository contains a Lean 4 formalization of several results in finite
Euclidean distance geometry. It connects squared-distance matrices with Gram
matrices anchored at a basepoint, proves a two-candidate trilateration bound, and
treats the segment and triangle cases of the Cayley--Menger determinant.

## Main declarations

- `DistanceGeometry.schoenberg`: for `n ≥ 1`, a symmetric hollow `n × n` matrix
  embeds as squared distances in `k`-dimensional Euclidean space if and only if its
  basepoint-centered Gram matrix is positive semidefinite and has rank at most `k`.
- `DistanceGeometry.encard_setOf_forall_dist_eq_le_two`: if a family of centers
  spans a hyperplane, the points with prescribed distances to those centers form
  a set of cardinality at most two.
- `DistanceGeometry.trilateration_le_two`: three affinely independent centers in
  three-dimensional Euclidean space determine at most two points with any
  prescribed triple of distances.
- `DistanceGeometry.cayleyMenger_det_heron`: for three points in the Euclidean
  plane, the Cayley--Menger determinant equals `-16` times the squared area of
  the triangle.

The last declaration states the triangle-area identity underlying Heron's formula.
After expansion and factorization in the three side lengths, the identity is equivalent
to Heron's formula. The repository does not state the factorized formula as a separate
theorem.

The supporting API includes a rank-controlled factorization of
positive-semidefinite matrices and algebraic Cayley--Menger formulas for segments
and triangles.

## Scope

The development concerns finite configurations over the real numbers. The
Cayley--Menger part covers dimensions one and two. The DMDGP connection consists
of the two-candidate sphere-intersection theorem; algorithmic reconstruction and
the general dimension formula are outside the current scope.

`IsPreDistMatrix` is the project's symmetric-and-hollow structural predicate. It
omits entrywise nonnegativity; some distance-geometry references include that
condition in the term "pre-distance matrix".

The mathematics is classical. This repository contributes a Lean formalization
and reusable definitions and lemmas around it.

## Build

Install Lean through `elan`, then run:

```sh
lake exe cache get
lake build
```

The repository pins its Lean and Mathlib versions.

## Source

I. J. Schoenberg, “Remarks to Maurice Fréchet's Article *Sur la définition
axiomatique d'une classe d'espace distanciés vectoriellement applicable sur
l'espace de Hilbert*” (1935). [DOI 10.2307/1968654](https://doi.org/10.2307/1968654).

## Provenance

Project direction: Egor Lyfar. AI systems produced most of the Lean code. Lean
checks the proofs with the pinned toolchain.

## License

Apache-2.0
