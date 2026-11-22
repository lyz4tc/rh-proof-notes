# A telescoping log sum replaces the negative block by the target weights

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Assume the hypotheses of [the one-place Vandermonde bound](interlacing-bounds-the-vandermonde-ratio-at-one-place.md). Let $C_0\ge0$ satisfy $k\le x^{C_0}$. With $V(R),V(u)$ and $L=x^\varepsilon$ as there, put $K=(2+2C_0)/\varepsilon$. Then all $w_j$ are positive, and
$$
 k\sum_{j=0}^{m-1}\log w_j
 \le \log V(R)-\log V(u)+kL(20+K)+2mL .
\tag{1}
$$
[One-place estimate in target weights](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/LogRatioLowerBoundOfLogVandermondeGap.lean#L53)

The first weight $b_0$ is at least $4k\Delta x\ge8$, so every $b_j,w_j$ is greater than one. Since $b_j<w_j<b_{j+1}$, the intervals $[\log b_j,\log w_j]$ are disjoint and ordered. Their total length is at most $\log w_{m-1}-\log b_0\le\log 2+L\le1+L$. Also each $\log b_j\le1+L$, since $b_j<w_j\le w_{m-1}\le2e^L$. Therefore
$$
 k\sum_j\log w_j
 \le (k-1)\sum_j\log b_j + (m+k)(1+L).
$$
This compares the full list jointly. In particular the cost of passing from $\log b_j$ to $\log w_j$, before multiplying by $k$, is bounded by a single endpoint difference.

Since $x\ge1$ and $\varepsilon>0$, $L=e^{\varepsilon\log x}\ge1$, and $e^t\ge1+t$ gives $\log x\le L/\varepsilon$. Thus $\log k\le C_0 L/\varepsilon$ and $\log(8xe^L)\le7+L/\varepsilon+L$, using $\log8\le7$. Inserting (1) of the one-place bound gives
$$
\begin{aligned}
 k\sum_j\log w_j-(\log V(R)-\log V(u))
 &\le (m+k)(1+L)+2k\log(8xe^L)+2k(1+\log k)\\
 &\le 2mL+kL(20+(2+2C_0)/\varepsilon).
\end{aligned}
$$
The second line majorizes $1+L$ by $2L$ and every constant term involving $k$ by the same constant times $kL$. This proves (1). [Telescope and absorb the endpoint losses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/LogRatioLowerBoundOfLogVandermondeGap.lean#L53)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
