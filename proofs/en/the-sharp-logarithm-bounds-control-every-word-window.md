# The sharp logarithm bounds control every word window

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use $D^*,d^*,\xi$ and (1) of [the exact center identity](mass-and-finite-index-products-give-the-exact-logarithm-of-the-window-center.md). At each place take the data $(u_\rho,v_\rho,b_\rho,w_\rho)$ of [the one-place bound](interlacing-bounds-the-vandermonde-ratio-at-one-place.md), with $L=x^\varepsilon$ for $x>1$, $\varepsilon>0$. Assume all gaps in $u_\rho$ are at least one. Suppose $44\le m\le k$, $m\le x$, $L\ge9$,
$$
 2(\log8+1+\log x)\le L,\quad \log(2k)\le L,\quad
 \log(2v_E)\le L,\quad
 \log g_i\le C_Y L,\quad |\log\ell_N|\le f
$$
for $i=1,2$ and $k<N\le r$. Take the row signs and dimensions of [the upper comparison](interlacing-cancels-the-large-compact-block-in-the-window-upper-bound.md), and suppose $d_\rho$ satisfies
$$
 \frac23\operatorname{dim}((v_\rho,-b_\rho))\le d_\rho
          \le 4d_K((v_\rho,-b_\rho))(3pqU_\rho)^{pq},
\qquad U_\rho=v_{\rho,0}+b_{\rho,m-1}.
$$
Then
$$
 \frac1f\sum_\rho\sum_{j<m}\log(w_{\rho,j}v_E/\pi)
       + m G -11L
 \ \le\ \xi\ \le\ (15+3C_Y)mL.
\tag{1}
$$
These are the numerical conclusions of `Conclusion5Sharp`, used for all words with the same constants. [Statement of the sharp bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeOfExplicitAndCompact.lean#L146) · [Derive the lower bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean#L149) · [Derive the upper bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean#L318)

## Lower bound

The lower row degree and the one-place Vandermonde estimate imply
$$
 \log(d_\rho F(r)/V(u_\rho))
 \ge \log(2/3)+(k-1)\sum_j\log b_{\rho,j}-5kL .
$$
Indeed the error in that estimate is $2k(\log8+\log x+L)+2k(1+\log k)$, at most $5kL$ by the two logarithmic size bounds. The weight difference $w_{\rho,j}-b_{\rho,j}\le b_{\rho,j}/x$ gives $\log(w_{\rho,j}/b_{\rho,j})\le1/x$. Also $\log b_{\rho,j}\le\log 2+L\le2L$. Thus
$$
 k\sum_j\log w_{\rho,j} -(k-1)\sum_j\log b_{\rho,j}
 \le m(k/x+2L)\le k+2kL
$$
by $m\le x$ and $m\le k$. In the family these conditions follow from the rank bounds. Using $\log(2/3)\ge-1$, the final sum in the exact identity is at least $k\sum_{\rho,j}\log w_{\rho,j}-f(1+7kL+k)$. [Replace each negative weight by the target weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogWeightMinusLogBBound.lean#L54) · [Use the row degree and Vandermonde bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogWeightMinusLogBBound.lean#L98)

For the remaining terms of the identity, $0\le v_*\le L$, and the mass exponents yield at least $fkmv_*-fkL-f(m-1)L/2$. The $L$-value sum is at least $-f(m-1)$. The prime-power term is at least $fkmG$, because $G\ge0$. The Euler tails are each at least $1/2$, so the sum of their logarithms is at least $-2$. Subtracting the desired main terms from this combined lower bound gives a total error at most
$$
 f\bigl(8kL+\tfrac12(m-1)L+k+m+2\bigr)\le 11fkL .
$$
Here $m\le k$, $k\ge44$ and $L\ge1$. Divide by $fk$ to get the lower bound. [Combine the lower errors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogWeightMinusLogBBound.lean#L147)

## Upper bound

By the upper degree and (1) of the local upper comparison with $C=3$, the difference $\log d_\rho-\log\operatorname{dim}(u_\rho)$ is at most $km(12+10L)$. This uses $\log3\le2$, $\log(2k)\le L$, and $r\ge1$ to fit its factor $Q$. In the final sum of the exact identity there is also a difference $\log F(r)-\log F(k)$. Each of its $m-1$ terms is at most $r\log r\le2kL$, since $r\le2k$. Thus the final sum is at most $fkm(12+12L)$.

The discriminant denominator and Euler tails contribute nonpositive terms. The first mass term is at most $\tfrac32 fkmL$ since $m\le k$, and the $L$-value sum is at most $fm$. The prime-power term is at most $3fkm C_Y L$ since $G\le2C_Y L$ and $2k+m-1\le3k$. After division by $fk$ the total upper bound is
$$
 (13.5+3C_Y)mL+(12+1/k)m\le(15+3C_Y)mL ,
$$
where $L\ge9$ and $k\ge44$. This gives the other inequality. [Bound the remaining factorials](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogFactorialProductDifference.lean#L65) · [Combine the upper errors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LogFactorialProductDifference.lean#L88)

The family makes the logarithmic inequalities eventual at a common threshold, using $L=x^\varepsilon$ and the host and rank size conditions. The [gap calculation](spacing-the-negative-weights-provides-the-discrete-series-gap.md) supplies the lower bound on the opposite-sign gaps for the degree comparison, with parameter $1/3$. Combining (1) with [variation across words](the-log-vandermonde-drift-between-words-is-a-harmonic-sum.md) and [the relative-window count](a-relative-prime-window-sets-the-torus-pair-count-within-a-constant.md) gives the ingredients of the family Vandermonde bound. [Use one family threshold for all the ingredients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean#L425)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
