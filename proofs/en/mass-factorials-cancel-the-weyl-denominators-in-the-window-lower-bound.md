# Mass factorials cancel the Weyl denominators in the window lower bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $0<\varepsilon<1/52$, $x\ge1$, $C_0\ge0$, and let $f,m\ge1$, $2\le k\le x^{C_0}$ be integers. Write $r=k-1+m$, $L=x^\varepsilon$, and $K=(2+2C_0)/\varepsilon$. At each of the $f$ real places indexed by $\rho$, use the lists $u_\rho,R_\rho=(v_\rho,-b_\rho),w_\rho$ and hypotheses of [the interlacing bound](interlacing-bounds-the-vandermonde-ratio-at-one-place.md). For a list $s$ of length $n$ set $\operatorname{dim}(s)=V(s)/\prod_{i=0}^{n-1}i!$.

Suppose $\pi\le v_E$, $\log v_E\le L$, $g_1,g_2\ge1$, and $M_k,M_r,I_\sigma,I_\pi>0$. Here $M_j$ denotes the genus mass of rank $j$ in the application, and the two $I$'s are finite level indices. Assume
$$
\begin{aligned}
 M_r&= M_k\prod_{N=k+1}^{r}
 \frac{\big((N-1)!(v_E/\pi)^N\big)^f}{(2v_E)^{f/2}}\,\ell_N,
 &0<\ell_N,\quad |\log\ell_N|\le f\log\zeta(N),\\
 I_\sigma/I_\pi &\ge 2^{-2f}(g_1g_2)^{fm(2k+m-1)/2}. &&
\end{aligned}
\tag{1}
$$
If $D^*\ge(2/3)^f M_r I_\sigma\prod_\rho\operatorname{dim}(R_\rho)$ and $d^*=M_k I_\pi\prod_\rho\operatorname{dim}(u_\rho)$, then $D^*,d^*>0$ and
$$
 \frac{\log(D^*/d^*)}{fk}\ge
 \frac1f\sum_\rho\sum_{j<m}\log(w_{\rho,j}v_E/\pi)
 + m(\log g_1+\log g_2)
 -(30+K)\left(L+\frac{m^2 L}{k}\right).
\tag{2}
$$
[Complete numerical hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogRatioLowerBound.lean#L26) · [Lower comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/LogRatioLowerBoundOfLogVandermondeGap.lean#L162)

Positivity follows from the assumptions and the Vandermonde factors. Put $v_*=\log(v_E/\pi)$, so $0\le v_*\le L$. Take logarithms of the two dimensions and use (1). The ratio of the Weyl denominators contributes $-f\sum_{i=k}^{r-1}\log i!$, while the mass ratio contributes $f\sum_{N=k+1}^{r}\log(N-1)!$. These cancel exactly, including the empty sums for $m=1$. The remaining inequality is
$$
\begin{aligned}
 \log(D^*/d^*)\ge&
 \sum_\rho\bigl(\log V(R_\rho)-\log V(u_\rho)\bigr)
 +f\log(2/3)+\log(I_\sigma/I_\pi)\\
 &+\sum_{N=k+1}^{r}\bigl(fNv_*-\tfrac{f}{2}\log(2v_E)+\log\ell_N\bigr).
\end{aligned}
\tag{3}
$$
This is where the mass formula is used. In Lean it is supplied by [the consecutive mass ratio](two-limits-of-one-lattice-count-give-the-siegel-mass-ratio.md) and induction over rank. [Multiply the mass ratios](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L73) · [Factorial cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/LogRatioLowerBoundOfLogVandermondeGap.lean#L34)

Apply [the telescoping log bound](a-telescoping-log-sum-replaces-the-negative-block-by-the-target-weights.md) to the first sum. Its total lower bound is $k\sum_{\rho,j}\log w_{\rho,j}-fkL(20+K)-2fmL$. Since $\log g_i\ge0$, the index term is at least $fkm(\log g_1+\log g_2)-2f\log2$. For $N\ge2$, $\zeta(N)\le1+\int_1^\infty u^{-N}\,du\le2$, so $\log\ell_N\ge-f$. Also $\log(2v_E)\le1+L$. With $m-1$ mass terms and $N\ge k$, their sum is at least
$$
 fk m v_* - fk L - f(m-1)\bigl((1+L)/2+1\bigr).
$$
Here $fkL$ pays for replacing $m-1$ by $m$ in the positive term. Finally $\log(2/3)\ge-1/2$ and $\log2\le1$. Thus all losses after dividing by $fk$ are bounded by
$$
 (21+K)L+\frac{2mL}{k}
 +\frac{(m-1)((1+L)/2+1)}{k}+\frac{5}{2k}
 \le (30+K)\left(L+\frac{m^2L}{k}\right).
$$
The final comparison uses $L\ge1,m\ge1,k\ge2$. The positive main terms in (3) now give (2), because the prefactor $1/f$ in front of the sum over places produces $m v_*$ from the $fm$ logarithms. [Assemble and bound all losses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/LogRatioLowerBoundOfLogVandermondeGap.lean#L162)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
