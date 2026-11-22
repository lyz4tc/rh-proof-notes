# Mass and finite index products give the exact logarithm of the window center

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $f\ge1$, $k\ge2$, $m\ge2$ even, and $r=k-1+m$. Let $v_E\ge\pi$, $g_1,g_2\ge3$ prime, and suppose the masses $M_k,M_r>0$ satisfy (1) of [the mass comparison](mass-factorials-cancel-the-weyl-denominators-in-the-window-lower-bound.md) with positive factors $\ell_N$. Use the two indices $I_\pi,I_\sigma$ of [the generator calculation](counting-the-row-level-matrices-gives-the-exact-generator-index-ratio.md), with the $f$-fold power at each prime. At each real place $\rho$, take a decreasing length-$k$ column weight $u_\rho$ and a positive row degree $d_\rho$. Write
$$
 D^*=M_r I_\sigma\prod_\rho d_\rho,\qquad
 d^*=M_k I_\pi\prod_\rho\operatorname{dim}(u_\rho),\qquad
 \xi=\frac{\log(D^*/d^*)}{fk}.
$$
The row identity uses the equality of the normalized base volume and $M_r$. Its quantity $\log X_u$ is $\xi$. Put $v_*=\log(v_E/\pi)$, $v_2=\log(2v_E)$, and $G=\log g_1+\log g_2$. Then
$$
\begin{aligned}
 fk\xi={}& f\bigl((m-1)k+\tfrac12m(m-1)\bigr)v_*
           -\tfrac12 f(m-1)v_2
           +\sum_{N=k+1}^r \log\ell_N\\
         &+ f\,\tfrac12 m(2k+m-1)G
           + f\sum_{i=1}^{2}\sum_{j=k+1}^r\log(1-g_i^{-j})
           +\sum_\rho\log\left(\frac{d_\rho F(r)}{V(u_\rho)}\right),
\end{aligned}
\tag{1}
$$
where $F(s)=\prod_{i=0}^{s-1}i!$. [Exact center identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeOfExplicitAndCompact.lean#L126) · [Derive it from the global mass and volume theorems](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean#L48)

Indeed, take the logarithm of the exact factored ratio $D^*/d^*$. The mass ratio contributes the sum of $fNv_*-(f/2)v_2+\log\ell_N$ and the log of the factorial product $\bigl(F(r)/F(k)\bigr)^f$. The number of terms is $r-k=m-1$, and
$$
 \sum_{N=k+1}^r N=(m-1)k+\tfrac12m(m-1).
$$
The finite index ratio contributes its exponent $fm(2k+m-1)/2$ times $G$, along with the logs of the two finite Euler tails. The column denominator is $V(u_\rho)/F(k)$ at each place, so multiplying by the factorial product from the mass puts $d_\rho F(r)/V(u_\rho)$ in the final sum. This proves (1) and records where the volume, mass, and finite index inputs enter. [Finite Euler tails](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LemmaFiveOneOfTheoremTwo.lean#L287) · [Normalized base volume](the-rank-two-genus-mass-fixes-the-normalized-volume.md)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
