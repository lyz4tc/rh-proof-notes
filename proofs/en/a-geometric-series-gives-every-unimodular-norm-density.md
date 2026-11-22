# A geometric series gives every unimodular norm density

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the quadratic local algebra and norm congruence of [the primitive count](primitive-gradient-bounds-stabilize-the-local-norm-density.md), now with the Gram determinant a unit. Put $\eta=1$ in the split case and $\eta=-1$ in the inert case. For any nonzero integral target $a$, with $j=v_\varpi(a)$, the normalized norm density is
$$
 \alpha(a)=B\sum_{i=0}^{j} r^i,\qquad
 B=1-\eta^m q^{-m},\qquad r=\eta^m q^{-(m-1)} .
\tag{1}
$$
In particular $\alpha(a)=B$ when $a$ is a unit. When $m\ge2$, the quotient $\rho(j)=\alpha(a)/B$ satisfies $\rho(0)=1$ and
$$
 |\rho(j+1)-\rho(j)|=q^{-(m-1)(j+1)}\le q^{-1}.
$$
This difference gives the summability for [the mass-ratio density average](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md). [Unit formula and valuation dependence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/AlphaNOfVdZeroUnit.lean#L83) · [Difference bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/AlphaNOfVdZeroUnit.lean#L109)

## Determine the primitive density

The reduction of $h$ modulo $\varpi$ is nondegenerate. Over the split algebra it is equivalent to the standard pairing of two $m$-component vectors, and over the inert quadratic residue field to the sum of $m$ field norms by diagonalization and surjectivity of the residue norm. By [the finite residue norm count](counting-nonzero-residue-norms-gives-the-local-fibre-density.md), the number of vectors of any fixed nonzero residue norm is $q^{2m-1}B$. Summing these counts for the $q-1$ nonzero residues and subtracting from $q^{2m}$ gives the zero-norm count. Its primitive part is obtained by removing the zero vector. After division by $q^{2m-1}$ this gives
$$
 \frac{q^{2m}-(q-1)q^{2m-1}B-1}{q^{2m-1}}=B(1+r).
$$
At a nonzero residue vector, the norm differential is onto the residue field, by nondegeneracy and the perfect trace pairing. Each such residue solution therefore has $q^{2m-1}$ lifts at every additional level for the prescribed target. Thus the primitive density is $B$ for a target of valuation $0$ and $B(1+r)$ for all targets of positive valuation.

## Recover all the common-divisor contributions

If $j=0$ or $j=1$ there are no vectors divisible by $\varpi$ at sufficiently high levels, since their norms are divisible by $\varpi^2$. For $j\ge2$ write any such vector as $x=\varpi y$, which changes its target to $a/\varpi^2$. At level $k$ this takes the $y$-count at level $k-2$ and multiplies it by $q^{2m}$, the number of lifts from level $k-2$ to level $k-1$ for $y$. On dividing by $q^{(2m-1)k}$, the factor is $q^{-(2m-2)}=r^2$. Hence the total density satisfies
$$
 \alpha_j=B(1+r)+r^2\alpha_{j-2}\qquad(j\ge2).
$$
The initial values and this recurrence give (1). The difference is its last summand divided by $B$, proving the stated estimate. [The closed density formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/UnitaryDensityFieldFurther.lean#L8) · [Use of differences in the global average](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/UnimodularClassRepresentatives/ALocEqRoL.lean#L61)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
