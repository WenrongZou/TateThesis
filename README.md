# Tate's Thesis in Lean 4

[![Lean Action CI](https://github.com/WenrongZou/TateThesis/actions/workflows/lean_action_ci.yml/badge.svg)](https://github.com/WenrongZou/TateThesis/actions/workflows/lean_action_ci.yml)

This repository contains a formalization, in [Lean 4](https://lean-lang.org/) and
[Mathlib](https://github.com/leanprover-community/mathlib4), of **Tate's thesis**
(J. Tate, *Fourier analysis in number fields and Hecke's zeta-functions*, 1950).
The main goal is to prove the **meromorphic continuation and functional equation of the
L-function attached to a Hecke character** of a number field, following Tate's adelic method.

This is part of the Ph.D. project of Wenrong Zou, supervised by
**Filippo A. E. Nuccio** and **Riccardo Brasca**, within the ANR project
[**FALSE**](https://anr-false.github.io) (*Formalising Arithmetic in the Lean Software Environment*).

## The ANR project FALSE

[FALSE](https://anr-false.github.io) (ANR-25-CE40-7639) is a research project funded by the
French *Agence Nationale de la Recherche*. Its aim is to formalise central results of algebraic
number theory and arithmetic geometry in Lean. The formalisation of Tate's thesis is one of
the Ph.D. subjects of the project.

## Main goal

Let $K$ be a number field, $`\mathbb{A}_K`$ its ring of adeles and $`\mathbb{A}_K^\times`$ its
group of ideles. A *Hecke character* is a continuous unitary character
$`\chi : \mathbb{A}_K^\times / K^\times \to \mathbb{C}^\times`$.

For a Schwartz–Bruhat function $f$ on $`\mathbb{A}_K`$, Tate's global zeta integral is

```math
Z(f, \chi, s) = \int_{\mathbb{A}_K^\times} f(x)\, \chi(x)\, \lvert x \rvert^s \, \mathrm{d}^\times x ,
```

which converges absolutely for $`\mathrm{Re}(s) > 1`$. Following Tate, we aim to prove that
$`Z(f, \chi, s)`$ extends to a meromorphic function on $`\mathbb{C}`$ satisfying the functional
equation

```math
Z(f, \chi, s) = Z(\mathcal{F}f, \chi^{-1}, 1 - s),
```

where $`\mathcal{F}f`$ is the Fourier transform of $f$ with respect to the self-dual Haar
measure. Moreover, $`Z(f, \chi, s)`$ is entire unless $`\chi = \lvert \cdot \rvert^{i\tau}`$
for some $`\tau \in \mathbb{R}`$, in which case it has at most simple poles at $`s = -i\tau`$
and $`s = 1 - i\tau`$.

Combined with the local theory, this yields the functional equation of the completed Hecke
L-function $`\Lambda(s, \chi) = \prod_v L_v(s, \chi_v)`$:

```math
\Lambda(s, \chi) = \varepsilon(s, \chi)\, \Lambda(1 - s, \chi^{-1}),
```

where $`\varepsilon(s, \chi) = \prod_v \varepsilon_v(s, \chi_v, \psi_v)`$ is the global epsilon
factor. It has the form

```math
\varepsilon(s, \chi) = W(\chi) \left( \lvert d_K \rvert \, N(\mathfrak{f}_\chi) \right)^{1/2 - s},
```

where $`d_K`$ is the discriminant of $K$, $`\mathfrak{f}_\chi`$ is the conductor of $`\chi`$,
and $`\lvert W(\chi) \rvert = 1`$.

## Building the project

You need a working Lean 4 installation via [`elan`](https://github.com/leanprover/elan);
see the [Lean installation guide](https://lean-lang.org/install/). Then run:

```bash
git clone https://github.com/WenrongZou/TateThesis.git
cd TateThesis
lake exe cache get   # download precompiled Mathlib
lake build
```

The Lean and Mathlib versions are pinned in [`lean-toolchain`](lean-toolchain) and
[`lakefile.toml`](lakefile.toml).

## References

- J. Tate, *Fourier analysis in number fields and Hecke's zeta-functions*, Ph.D. thesis,
  Princeton University, 1950. Reprinted in J. W. S. Cassels and A. Fröhlich (eds.),
  *Algebraic Number Theory*, Academic Press, 1967.
- D. Ramakrishnan and R. J. Valenza, *Fourier Analysis on Number Fields*,
  Graduate Texts in Mathematics 186, Springer, 1999.
- S. S. Kudla, *Tate's thesis*, in J. Bernstein and S. Gelbart (eds.),
  *An Introduction to the Langlands Program*, Birkhäuser, 2003.
- J. Neukirch, *Algebraic Number Theory*, Grundlehren der mathematischen Wissenschaften 322,
  Springer, 1999, Chapter VII.
