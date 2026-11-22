# Denominator classes and lattice translates bound the Eisenstein series

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be totally real, $d=2M$ with $M\ge3$, and take the symmetric form $B$, positive majorants and finite Fourier data of [the Gaussian calculation](a-hermitian-involution-diagonalizes-the-archimedean-gaussian.md). For a Schwartz–Bruhat test $\phi$, write
$$
 J_\phi(b)=\int_{\mathbb A_f^d}\phi(u)\psi_f(b\,u^{\mathsf T}Bu/2)\,d_f u,\qquad
 E_\phi(\tau)=\phi(0)+\sum_{b\in F}J_\phi(b)c(\tau+b),
 \qquad W(\tau)=\prod_\sigma y_\sigma^{M/2}.
$$
Here $\tau_\sigma=x_\sigma+iy_\sigma$ ranges over the product of upper half-planes and $b$ in $\tau+b$ means its real embeddings. For each $\phi$ and $t>0$ there is $C$ such that
$$
 W(\tau)\sum_{b\in F}|J_\phi(b)c(\tau+b)|\le C
 \quad\text{if }y_\sigma\ge t\text{ at every }\sigma.
$$
In particular the series converges absolutely at every $\tau$. The bound is for the terms following $\phi(0)$. [Weighted absolute estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionGrowthBound.lean#L74)

## Separate the finite denominator

Put $I(b)=\{r\in\mathcal O_F:rb\in\mathcal O_F\}$. This nonzero integral ideal is constant under adding an integer of $F$. If $I(b)=I$, the class of $b$ lies in $I^{-1}/\mathcal O_F$. This quotient has size $\mathrm NI$, as is seen locally by writing $I\mathcal O_v=\varpi_v^{e_v}\mathcal O_v$: the local quotient has size $q_v^{e_v}$, and the finite places with $e_v=0$ contribute one. The product gives $\mathrm NI$. Thus
$$
 \sum_{[b]\in F/\mathcal O_F}(\mathrm N I(b))^{-M}\le
 \sum_{0\ne I\subseteq\mathcal O_F}(\mathrm NI)^{1-M}<\infty .
$$
For the last inequality, unique factorization of ideals gives the Euler product at $s=M-1>1$. Above each rational prime $p$ there are at most $[F:\mathbb Q]$ prime ideals and each has norm at least $p$. The product is bounded by $\zeta(M-1)^{[F:\mathbb Q]}$. [Bound per denominator norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/DenominatorPowerSummable.lean#L35) · [Denominator summability](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/DenominatorPowerSummable.lean#L135)

[The finite oscillatory integral](finite-integral-operators-give-the-denominator-decay-of-the-quadratic-integral.md) gives $|J_\phi(b)|\le C_\phi(\mathrm NI(b))^{-M}$. The Gaussian norm formula gives $|c(\tau+b)|=\prod_\sigma |\tau_\sigma+\sigma(b)|^{-M}$. Choose one $b_0$ in each additive class. Within that class the first bound is constant, so it remains to estimate the second one along $b=b_0+a$ for $a\in\mathcal O_F$. [Majorize and decompose the sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionGrowthBound.lean#L74)

## Sum over the archimedean lattice

For each $a$, take the coordinatewise floors $k_\sigma$ of $x_\sigma+\sigma(b_0+a)$. A fixed floor tuple has at most one preimage. If two distinct integers of $F$ occurred in the same unit cube, their nonzero difference would have every conjugate of absolute value strictly less than one. Its absolute norm would then be a positive integer strictly less than one.

For any real $X$ with $k\le X<k+1$ and any $y\ge t$, one has
$$
 |k|+y\le |X|+1+y\le(\sqrt2+t^{-1})\sqrt{X^2+y^2}.
$$
Consequently the lattice sum is bounded by a constant depending on $t,M,F$ times $\prod_\sigma\sum_{k\in\mathbb Z}(|k|+y_\sigma)^{-M}$. In one coordinate, the term at zero is $y^{-M}\le t^{-1}y^{1-M}$. The positive half of the sum is bounded by $\int_0^\infty (u+y)^{-M}\,du=y^{1-M}/(M-1)$, because the summand decreases. The negative half is the same. Multiplying the resulting estimate by $W(\tau)$ yields a constant times $\prod_\sigma y_\sigma^{1-M/2}$, bounded when $y_\sigma\ge t$. This estimate is independent of $b_0$ and of the real parts. Combine it with the convergent denominator sum to prove the claim. Lean uses a uniform bound for the sizes of the floor fibres and a telescoping estimate for the same one-dimensional series. [One-dimensional summation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/EisensteinLatticeSumBound.lean#L54) · [Floor fibres](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/EisensteinLatticeSumBound.lean#L179) · [Archimedean lattice estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/EisensteinLatticeSumBound.lean#L204)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
