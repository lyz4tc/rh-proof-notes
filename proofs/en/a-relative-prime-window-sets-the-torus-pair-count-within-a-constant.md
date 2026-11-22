# A relative prime window sets the torus-pair count within a constant

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $f,k\ge1$ be integers with $f\le2^{k-1}$, and let $D^*,d^*>0$, $\Gamma\ge1$. Put
$$
 X=(D^*/d^*)^{1/(fk)},\qquad Y=X\Gamma^{-2/(fk)},\qquad D'=D^*\Gamma^{-2}.
$$
If $T\ge2$ and $Y\le T\le Y(1+1/(fk))$, then
$$
 \frac12D'\le d^*(T^k-1)^f\le eD',
 \qquad
 \log X-\frac{2\log\Gamma}{fk}\le\log T\le\log X+1 .
\tag{1}
$$
Here $(T^k-1)^f$ is the factor for a nonzero vector at each of the $f$ split places over the word prime. These estimates give the numerical part of `TorusPairsWithVariant` once the relevant logarithmic bounds for $X$ are in place. [Power-product bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/OneAddInvPowLeExpOne.lean#L73) · [Apply to a word prime](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/PartFiveExplicitOfPropositions.lean#L157)

Raising the window bounds to the $fk$-th power gives
$$
 D'\le d^*T^{fk}\le eD'.
$$
The first identity uses $d^*Y^{fk}=D'$. The upper bound uses $(1+1/(fk))^{fk}\le e$, which follows from $\log(1+t)\le t$ for $t\ge0$. The correction from $T^{fk}$ to $(T^k-1)^f$ is the factor $(1-T^{-k})^f$. The bound $T\ge2$ and Bernoulli's inequality give
$$
 1\ge (1-T^{-k})^f\ge 1-f T^{-k}\ge 1-f2^{-k}\ge\tfrac12.
$$
The product bounds follow. Taking logarithms of the original window gives the lower log bound and the upper bound $\log X-2\log\Gamma/(fk)+\log(1+1/(fk))\le\log X+1$.

In the family application $T$ is prime and $f\le k\le2^{k-1}$, so the two elementary size conditions follow. The normalization yields $\left|\log(d^*(T^k-1)^f/D')\right|\le1$. Also any lower bound $A_-\le\log X$ gives $A_--2\log\Gamma/(fk)\le\log T$. If $mL\ge1$ and $\log X\le(15+3C_Y)mL$, then $\log T\le(16+3C_Y)mL$. This accounts for the change in the upper constant when passing to the selected prime. [Deduce the three numerical clauses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeOfExplicitAndCompact.lean#L289) · [Use the clauses to size the word prime](the-logarithmic-window-bounds-give-the-word-prime-size.md)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
