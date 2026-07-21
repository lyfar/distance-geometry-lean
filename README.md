# Distance Geometry in Lean

This repository contains a Lean 4 formalization of several results in finite
Euclidean distance geometry. It connects squared-distance matrices with centered
Gram matrices, proves a two-candidate trilateration bound, and treats the segment
and triangle cases of the Cayley--Menger determinant.

## Main declarations

- `DistanceGeometry.schoenberg`: a symmetric hollow matrix embeds as squared
  distances in `k`-dimensional Euclidean space if and only if its centered Gram
  matrix is positive semidefinite and has rank at most `k`.
- `DistanceGeometry.encard_setOf_forall_dist_eq_le_two`: if a family of centers
  spans a hyperplane, the points with prescribed distances to those centers form
  a set of cardinality at most two.
- `DistanceGeometry.trilateration_le_two`: three affinely independent centers in
  three-dimensional Euclidean space determine at most two points with any
  prescribed triple of distances.
- `DistanceGeometry.cayleyMenger_det_heron`: for three points in the Euclidean
  plane, the Cayley--Menger determinant equals `-16` times the squared area of
  the triangle.

The supporting API includes a rank-controlled factorization of
positive-semidefinite matrices and algebraic Cayley--Menger formulas for segments
and triangles.

## Scope

The development concerns finite configurations over the real numbers. The
Cayley--Menger part covers dimensions one and two. The DMDGP connection consists
of the two-candidate sphere-intersection theorem; algorithmic reconstruction and
the general dimension formula are outside the current scope.

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
