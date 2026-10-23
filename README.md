# Ancilliary Files: Universal Planar Abelian Duals for 3d N = 2 Symplectic CS-SQCD

Mathematica notebooks accompanying [**Universal Planar Abelian Duals for 3d N=2 Symplectic CS-SQCD**](https://arxiv.org/abs/2605.06776). They contain the S³ partition function asymptotics and superconformal index checks supporting the proposed dualities between USp(2N) SQCD with Chern–Simons level and their *planar* Abelian mirror quivers.

| Notebook | What it does |
|---|---|
| `USpPlanarLimit.nb` | Asymptotic (t → ∞) analysis of S³ partition functions: real-mass flows, divergent phases, finite remainders, and mass-deformation trees |
| `3d_USp_paper.nb` | Superconformal index expansions comparing a chiral theory with the planar limit of the D-type quiver |

## Requirements

- Mathematica 14.2 or later. The notebooks were written in versions 14.2 (first) and 15 (second).
- No external packages.

## `USpPlanarLimit.nb`

**Idea.** Large real masses are tracked at the level of the S³₍ᵦ₎ integrand by replacing every massive sᵦ with its asymptotics. `SbLimMod[R, x]` returns ±iπ/2 · (iQ/2 · (1 − R) + x)², with the sign set by the coefficient of `t` in `x`. If that coefficient is zero, the field is massless and the call stays unevaluated (`Hold`), to be read as log sᵦ. Constants proportional to b² + b⁻² are dropped. `GiveLev` reads off the induced Chern–Simons levels.

**Workflow** (per example):

1. Set the rank and flavour number: `NN = 1; F = 5;`.
2. Evaluate the electric exponent `El1` and the mirror exponent `Mr1`.
3. Apply the shifts Xᵣ → Xᵣ − t/2 (both sides) and zⱼ,ₐ → zⱼ,ₐ + sⱼ,ₐt (mirror), then `ReleaseHold`.
4. Split the result into the divergent phase `divphase...` (terms proportional to t and t²) and the finite remainders `Zel`, `Zmr`. The divergent phases of the two sides must coincide.
5. Obtain mass deformations by substituting, for example, X₅ → −t/2 into the remainder and repeating the analysis.

**Conventions**

- Deformations are parametrised by `t`, with X₅ = −t/2. The physical mass is m = t/2, so t = 2m when converting phases to the physical mass.
- Labels USp(2N)ₖ correspond to a factor exp(−iπku²) in the integrand.
- Where Higgsing is needed (level 1 and below on the mirror side), the notebook substitutes the pole locations directly; residue constants are not tracked.

**Contents**

1. USp(2)₋₁ with 5 flavours, its D₅ planar mirror, and the full tree of mass deformations (levels 1–5, including TQFT and free-chiral endpoints).
2. USp(4)₋₂ with 8 flavours: duality at level 0 and the full tree of deformations down to TQFT dualities.
3. Planar limits mapped to symplectic groups: USp(2), USp(4), and USp(6).
4. Planar limits mapped to orthogonal groups: SO(3), SO(4), SO(5), and SO(2).

**Checks.** The outputs have been reproduced independently in a computer algebra system, and the asymptotics compared numerically against the exact double sine function for USp(2) with F = 5, with agreement to approximately 10⁻¹⁰. The duality itself is not tested here; it is established in the paper via the superconformal index (second notebook).

## `3d_USp_paper.nb`

Defines the building blocks of the superconformal index and expands it in the fugacity `x` to compare a chiral gauge theory with the planar limit of the D-type quiver.

**Building blocks (section "Initialization")**

- `genCoef[expr, list]`: projects onto gauge-invariant terms by taking the zeroth coefficient in the Cartan fugacities (a quick Haar-measure integration).
- `Chir[ζ, ν, R]`, `ChirG[...]`: contributions of a chiral multiplet with flux ν and R-charge R (a q-Pochhammer in x²), and its extension to products and powers of gauge fugacities.
- `Vec[ζ, ν, Nc]`: vector multiplet contribution with fluxes.

**Cases**

Each section sets the number of flavours (`h = 5`), colours (`Nc = 2`), the R-charge (`r = 3/5`), the CS level (`k1`), and the level `L = −3/2`. It builds the electric index and the planar index, then compares them term by term in `x`:

- Chiral U(2)₍₀, ₋₃/₂₎ with (Q, Ã) versus the planar limit of the D-type quiver.
- The same theory with `k1 = -1/2` and `k1 = -1`.
- Variants of the planar limit "with squares".


## Usage notes

- Evaluate each notebook from top to bottom. The first section initialises the utilities; later sections reuse them.
- The first notebook sets `NN` and `F` at the start of each example, so sections can be evaluated independently after the utilities have been initialised.

## Citation
```
@article{Benvenuti:2026xcv,
    author = "Benvenuti, Sergio and Cagioni, Vittorio and Rota, Simone and Shri, Anant",
    title = "{Universal Planar Abelian Duals for 3d $\mathcal{N}=2$ Symplectic CS-SQCD}",
    eprint = "2605.06776",
    archivePrefix = "arXiv",
    primaryClass = "hep-th",
    month = "5",
    year = "2026"
}
```

## Licence
Copyright (c) the respective contributors, as shown by the AUTHORS file.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
