# The log Vandermonde drift between words is a harmonic sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $k\ge2$ and $\Delta>0$. For two lists $u,u'$ of length $k$, assume that for $0=i<j$ the gaps in both lists are at least $4k\Delta$ and differ by at most $\Delta$. For $1\le i<j$, assume the gaps are at least $3(j-i)\Delta$ and differ by at most $2\Delta$. Then $V(u),V(u')>0$, with $V$ as in [the one-place interlacing bound](interlacing-bounds-the-vandermonde-ratio-at-one-place.md), and
$$
 |\log V(u)-\log V(u')|\le \frac14+\frac23 k(1+\log k).
\tag{1}
$$
[Separated-list estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogVandermondeVariationGeneric.lean#L71)

For $A,B\ge c>0$, integrating $1/t$ between them gives $|\log A-\log B|\le |A-B|/c$. Thus each pair involving position zero contributes at most $1/(4k)$ to the absolute sum of the log-gap changes. The total of these is at most $1/4$. Each pair with $i\ge1$ contributes at most $2/(3(j-i))$. Summing in $j$ for each such $i$ gives at most $\tfrac23(1+\log k)$, by the integral comparison for the harmonic series. There are at most $k$ rows to sum. Since the log of each positive Vandermonde product is the sum of the log gaps, the triangle inequality proves (1). [Logarithm estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogVandermondeVariationGeneric.lean#L8) · [Harmonic estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogVandermondeVariationGeneric.lean#L30)

## Why the word weights satisfy these gap conditions

At an embedding the common list $v$ has step $4\Delta$, all its entries are nonnegative, and the interior weight at index $1\le i\le k-2$ is
$$
 u_i=v_{i-1}-1/2-\delta_i,\qquad \delta_i\in\{0,\Delta\},
$$
with only the $\delta_i$ varying from one word to another. The first and last entries are shared. The first is at least $v_0+4k\Delta$, while the last is $v_{k-2}-1/2$ away from the top places and at most $-4k\Delta$ at the top places. Thus every gap starting at zero has the claimed lower bound and changes by at most $\Delta$. For interior pairs the gap is at least $4(j-i)\Delta-\Delta\ge3(j-i)\Delta$, with a change at most $2\Delta$. For an interior $i$ and the last entry $j=k-1$, the same lower bound holds away from the top places by the formula for the last entry. At a top place it is enough that $v_{k-2}-1/2\ge-4k\Delta$, which follows from $v_{k-2}\ge0$ and $\Delta\ge1$ in the application. Replacing the last entry by a lower value can only enlarge the gap. The gap changes by at most $\Delta$ across words. [Read the common grid and compare all pairs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogVandermondeVariationGeneric.lean#L155)

If $D^*>0$ and $d_u^*=C\prod_{\rho=1}^fV(u_\rho)$ with common $C>0$, then the unadjusted center has logarithm $\log(D^*/d_u^*)/(fk)$. The common factors and $D^*$ cancel in the difference of these logarithms. Apply (1) at each place and divide their sum by $fk$. The resulting bound is at most $1+\log k+2/k$, which is the stated variation bound. The factor $C$ in the construction incorporates the common column mass, level index and factorial denominators. [Family variation statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeOfExplicitAndCompact.lean#L183) · [Sum over embeddings](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogVandermondeVariationGeneric.lean#L307)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
