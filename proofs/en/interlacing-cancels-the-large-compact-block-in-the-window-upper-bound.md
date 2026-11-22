# Interlacing cancels the large compact block in the window upper bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Take the setup of [the one-place interlacing bound](interlacing-bounds-the-vandermonde-ratio-at-one-place.md) with $2\le m\le k$ and $m$ even, and assume every gap $u_i-u_j$, $i<j$, is at least one. Let $\lambda=(v,-b)$, $r=k-1+m$, $p=k-1+m/2$, $q=m/2$, with the [row signs](spacing-the-negative-weights-provides-the-discrete-series-gap.md). Write $d_K(\lambda)$ for the compact Weyl dimension in [the degree comparison](the-compact-and-noncompact-roots-bound-the-row-formal-degree.md). For $C\ge1$ put $Q=Cpqr(v_0+b_{m-1})$. Then
$$
 \log\bigl(4d_K(\lambda)Q^{pq}\bigr)-\log\operatorname{dim}(u)
 \le km\bigl(\log C+5\log(2k)+5L+10\bigr).
\tag{1}
$$
In the formal proof this bounds the logarithmic ratio of the real-place degree to the column dimension, using $C=3$ in the large-gap comparison. [Full local upper bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/UpperPlace.lean#L7) · [Pass to the actual row degree](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogFactorialProductDifference.lean#L22)

For pairs within the $v$-block all signs are positive, with no opposite sign between them. Thus their factors in the numerator of $d_K$ give exactly $V(v)$. Every other same-sign pair meets the $m$-entry appended block. There are at most $mr$ of them, and each shifted gap is positive and at most $H=v_0+b_{m-1}+2k$. This follows since the diameter of $\lambda$ is $v_0+b_{m-1}$, and the shift for the pair counts at most $r\le2k$ indices. Hence the compact numerator is at most $V(v)H^{mr}$.

For $i<j<k-1$, interlacing gives $v_i-v_j\le u_i-u_{j+1}$. The pairs $(i,j+1)$ are all distinct and the other factors of $V(u)$ are at least one. Hence $V(v)\le V(u)$. Since $p\ge k$, $F(p)F(q)\ge F(k)$, where $F(s)=\prod_{i<s}i!$. Therefore
$$
 d_K(\lambda)/\operatorname{dim}(u)\le H^{mr}.
$$
All quantities in the logs are positive, because the lists decrease strictly and the shifted gaps in the compact numerator are positive. [Use interlacing in the upper direction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/UpperPlaceHolds.lean#L40) · [Count the factors outside the common block](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/UpperPlaceHolds.lean#L116)

By the weight bounds, $v_0\le 4k\Delta\le b_0/x\le b_{m-1}<2e^L$. Thus $H\le4e^L(2k)$ and $Q\le C(2k)^3 4e^L$, since $p,q,r\le2k$. Also $mr\le2mk$ and $pq\le mk$, since $p\le2k$ and $q=m/2$. Taking logs in the preceding product comparison bounds the left side of (1) by
$$
 \log4+2km(\log4+L+\log(2k))
 +km(\log C+3\log(2k)+\log4+L).
$$
Use $\log4\le3$, $km\ge4$ and $L\ge0$ to bound this by (1). [Assemble the bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/UpperPlaceHolds.lean#L290)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
