# A dilation fixes the scalar in the one-vector Siegel mean

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic CM extension, $f=[F:\mathbb Q]$, $W$ a nondegenerate Hermitian space of rank $n\ge3$, and $\beta\in F^\times$. Use coordinate Haar measures from an $F$-basis of $E$. On the base field $F_v$ at a finite place normalize Haar measure by $\mathcal O_{F_v}$ of mass one. At infinity give a fundamental domain for $\mathcal O_F$ measure one. On each tuple space use the product coordinate measures, and on the $1$-by-$1$ Gram target use the base coordinate measure under $t\mapsto[t]$. Let $\omega_{\infty,\beta},\omega_{v,\beta}$ be the continuous fibre measures of the norm map in these normalizations. Let $I_\beta$ be the measure on $W(\mathbb A_F)$ defined by averaging the point measures at $g^{-1}x$ for all rational $x$ of norm $\beta$, over the Haar probability space $U(W)(F)\backslash U(W)(\mathbb A_F)$.

**Claim.** With these normalizations $I_\beta$ is the restricted product of the local fibre measures, with scalar $1$. Precisely, fix the coordinate lattice $L_v$ at each finite place. For a nonnegative Borel test $\Phi_\infty$ and finite nonnegative Borel tests $\Phi_v$ equal to $\mathbf 1_{L_v}$ away from a finite set, the mean integral is the product of their local fibre integrals. The factors off the finite set have finite mass and the sum of the absolute deviations of those masses from $1$ is finite. In the full `SWMeas` statement this is read on restricted-product cylinders. It suffices to take a finite set containing all exceptional places and enlarge it freely.

Three ingredients of the Lean proof enter the normalization argument.

1. The mean is locally finite, invariant under $U(W)(\mathbb A_F)$, and carried by the norm-$\beta$ fibre. For rank $n\ge3$, the orbital measure theorem says that any locally finite invariant measure supported on that fibre is the product of the continuous coordinate fibre measures up to one scalar $c\ge0$, with the tail convergence stated above. If any local fibre measure is zero, the measure is zero and the product equality holds with scalar $1$. The [finite-projection proof](finite-projections-determine-the-adelic-norm-orbit-measure.md) uses local transitivity, the integral tails, and summable estimates for their lattice masses.
2. Put $B_v(a)=a^{-1}L_v$ for a positive integer $a$, and $P(a)=\prod_{v<\infty}\omega_{v,\beta}(B_v(a))$. There is a strictly positive continuous function $\varphi$ on $W_\infty$ and a constant $C\ge0$ independent of $a$ such that $w=\int\varphi\,d\omega_{\infty,\beta}<\infty$, the mean
   $$
     I(a)=\int \varphi(y_\infty)\prod_{v<\infty}\mathbf1_{B_v(a)}(y_v)\,dI_\beta(y)
   $$
   is finite, and $\lvert I(a)-w P(a)\rvert\le C a^{fn}$.
3. If all finite local fibre measures are nonzero, some $\kappa>0$ satisfies $P(a)\ge\kappa a^{f(2n-2)}$ for arbitrarily large positive integers $a$.

To see the initial invariance, for $k\in U(W)(\mathbb A_F)$ replace $g$ by $gk^{-1}$ in the point-measure mean. The unitary adelic group is unimodular, so the normalized quotient measure is invariant under the right action. The expression is well defined on the quotient because $U(W)(F)$ permutes the rational vectors of the prescribed norm. The fibre support follows from invariance of the Hermitian form. Apply the first ingredient to obtain the scalar $c$. If any local measure is zero, the first ingredient gives the claimed equality directly. Otherwise $\varphi>0$ everywhere implies $w>0$, since $\omega_{\infty,\beta}\ne0$.

For a fixed $a$, $B_v(a)=L_v$ at every place where $a$ is a unit. At each other place $B_v(a)$ is compact and its fibre mass is finite. Thus the test defining $I(a)$ is an admissible pure tensor in the orbital measure theorem. Its product is finite and $I(a)=cwP(a)$. Substituting into the error bound gives
$$
|c-1|\, wP(a)\le C a^{fn}.
$$
Use the lower bound for the arbitrarily large integers furnished by the third ingredient. Since
$$
 f(2n-2)-fn=f(n-2)\ge1,
$$
it follows that $|c-1|w\kappa a\le C$ for those integers, which forces $c=1$. This is why the growth comparison works starting in rank $3$. Equality with this scalar then holds for all the tests of the orbital measure theorem.

### Source and scope

The mean measure and the restricted product identity are [`thetaMeas`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/IsEulerProd.lean#L84) and [`SWMeas`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/IsEulerProd.lean#L111). Invariance and local finiteness come from [`theta_measure_locally_finite`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/ThetaFin.lean#L12) and the invariance lemma used in [`sw_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SwOne.lean#L23).

The first ingredient is [`exists_isEulerProd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SiegelWeilFormulaRange.lean#L95). The second follows by [extracting a Fourier coefficient](a-fourier-coefficient-converts-the-theta-bound-into-a-count-error.md) in [`bound_hermitian`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HaarFundamentalDomainRankOneDensity.lean#L29). The third follows from the [denominator sequence](a-denominator-sequence-gives-the-full-growth-of-the-local-density-product.md) proved in [`growth`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RankOneLocalDensitiesProductConverges.lean#L386). The proof that uses the three inputs is `sw_one` above. The convergent formula for multiple Gram rows adds a separate block induction. In the one-row formula, the resulting measure identity is rescaled to self-dual Haar measures and gives the [measurable norm mean](one-by-one-gram-fibres-give-the-measurable-norm-mean.md).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
