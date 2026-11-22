# Cuspidal cancellation bounds the weighted theta difference

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be totally real of degree $f$, let $n\ge3$, and let $B$ be an invertible symmetric matrix over $F$ of size $2n$. At every real place $w$ use a positive definite matrix $P_w$ with $P_w B_w^{-1}P_w=B_w$, where $B_w$ is the image of $B$. Write $q(x)=x^TBx/2$. Let $g_\omega$ be a measurable family of adelic isometries of $B$ on a probability space $\Omega$. Assume the average count condition: for every positive integer $N$ there is $C_N$ such that the expected number of nonzero $x\in F^{2n}$ with $Ng_{\omega,f}x$ integral and $\max_w\|g_{\omega,w}x_w\|\le R$ is at most $C_N(R^{fn}+R^{2fn})$ for all $R>0$. Use the standard additive character on the finite adeles whose value on $b\in F$ is $e^{-2\pi i\operatorname{Tr}_{F/\mathbb Q}b}$.

For $\phi$ a Schwartz–Bruhat function on the finite adele vector space and $\tau=(x_w+iy_w)_w$ with $y_w>0$, put
$$
 G_\tau(X)=\prod_w \exp\!\big(2\pi i x_w q_w(X_w)-\pi y_w X_w^T P_w X_w\big)
$$
and
$$
 \Theta_\phi(\tau)=
 \int_\Omega\sum_{x\in F^{2n}} \phi(g_{\omega,f}x)G_\tau(g_{\omega,\infty}x)\,d\mathbb P(\omega).
$$
The comparison function $E_\phi$ is the absolutely convergent series
$$
 E_\phi(\tau)=\phi(0)+\sum_{b\in F}
             F_\phi(b)\,C_G(\tau+b),
\quad
 F_\phi(b)=\int \phi(u)\psi_f(bq(u))\,d\mu_f(u),
\quad
 C_G(\tau)=|\mathrm N_{F/\mathbb Q}\det B|^{1/2}\int G_\tau(X)\,dX .
$$
Here $dX$ is archimedean Lebesgue measure and $\mu_f$ is the self-dual coordinate Haar measure for the finite trace pairing determined by $B$ and $\psi_f$. In $\tau+b$ the real part at $w$ is shifted by the real embedding of $b$. Let $\mathrm{wt}(\tau)=\prod_w y_w^{n/2}$. Then for each fixed $\phi$ there is $C_\phi$ such that
$$
 \mathrm{wt}(\tau)\,|\Theta_\phi(\tau)-E_\phi(\tau)|\le C_\phi
 \quad\text{for every }\tau.
$$
The proof uses the common transformation laws of the two functions, the finite compact-orbit property for test functions, and reduction to Siegel sets, in the versions described below.

### The difference on the reduced region

Fix $t,\kappa>0$, and suppose $y_w\ge t$ and $\kappa y_w\le y_v$ for all real $v,w$. Put $y_*=\min_w y_w$. The term $x=0$ in $\Theta_\phi$ is $\phi(0)$, since the probability measure has mass one. Because $\phi$ has compact support in the finite adeles, all terms counted in its support lie in one finite denominator box for some $N$. Its sup norm is finite. If $r_x=\max_w\|g_{\omega,w}x_w\|$, positivity of the finitely many $P_w$ gives $|G_\tau(g_{\omega,\infty}x)|\le e^{-c y_* r_x^2}$ for some $c>0$. Use
$$
 e^{-c y_* r^2}=\int_r^\infty 2c y_* R e^{-c y_* R^2}\,dR .
$$
Tonelli and the average count condition bound $|\Theta_\phi-\phi(0)|$ by a constant times
$$
 \int_0^\infty 2c y_* R e^{-c y_*R^2}(R^{fn}+R^{2fn})\,dR
 \ \ll\ y_*^{-fn/2}+y_*^{-fn}.
$$
This follows by changing variables $R\mapsto y_*^{1/2}R$. Comparability of the heights gives $\mathrm{wt}(\tau)\le\kappa^{-fn/2}y_*^{fn/2}$, and $y_*\ge t$, so the weighted theta remainder is uniformly bounded.

The Eisenstein remainder $E_\phi-\phi(0)$ satisfies a companion bound on the larger region $y_w\ge t$, given by the weighted absolute sum of its terms. To see the summability mechanism, one has $|F_\phi(b)|\ll_\phi \mathrm N(\mathfrak d_b)^{-n}$, where $\mathfrak d_b=\{a\in\mathcal O_F:ab\in\mathcal O_F\}$. The project proves this finite oscillatory-integral bound by expressing the Fourier transform of $\psi_f(bq)\phi$ using Iwasawa decomposition of a finite adelic $2$-by-$2$ matrix. The diagonal part contributes $\mathrm N(\mathfrak d_b)^{-n}$; the integral-matrix part acts in a bounded finite-dimensional space of test functions. The archimedean Gaussian gives
$$
 |C_G(\tau+b)|=\prod_w \big((x_w+b_w)^2+y_w^2\big)^{-n/2}.
$$
Indeed $P_w^{-1/2}B_wP_w^{-1/2}$ has eigenvalues $\pm1$ by the majorant identity. Diagonalize it after changing to $P_w$-coordinates and integrate each one-variable complex Gaussian. The scalar determinant factors cancel against the one in $C_G$.

For a fixed denominator ideal $\mathfrak d$, the elements $b$ lie in $\mathfrak d^{-1}$, with at most $\mathrm N\mathfrak d$ classes modulo $\mathcal O_F$. In each class sum the archimedean bound over a translate of the lattice of $\mathcal O_F$. Uniformly in the translate and $x_w$, the sum times $\mathrm{wt}(\tau)$ is bounded for $y_w\ge t$: divide the real product into cubes of side one. Each has uniformly boundedly many lattice points, and the sup of $\prod_w y_w^{n/2}(X_w^2+y_w^2)^{-n/2}$ over one cube is at most a constant depending on $t,n,f$ times the inf there. The latter comparison follows in each coordinate from $|X-X'|\le1$ and $y_w\ge t$. The integral over all cubes is a fixed constant times $\prod_w y_w^{1-n/2}$, bounded since $n\ge3$. Summing over denominator ideals now uses $\sum_{\mathfrak d}(\mathrm N\mathfrak d)^{1-n}<\infty$, from the Euler product for $\zeta_F(n-1)$ in its absolute convergence region. This proves the weighted absolute bound for the Eisenstein remainder. Both functions have the same term $\phi(0)$. Their difference on the reduced region consequently has a uniform weighted bound.

### Moving a general point to that region

The two transformation laws have the same multipliers. More precisely for each $\gamma\in\mathrm{SL}_2(F)$ there is an implementing linear operator $T_\gamma$ on finite Schwartz–Bruhat functions such that the weighted absolute difference at $(\phi,\tau)$ equals that at $(T_\gamma\phi,\gamma\tau)$. This follows for upper unipotents, diagonal matrices and the Weyl inversion from their common explicit theta and Eisenstein transformations. Those elements generate $\mathrm{SL}_2(F)$, so compose the operators. Finite multipliers of modulus one do not affect this equality.

The reduction theorem used here gives a finite set of rational matrices $r$ and numbers $t,\kappa>0$ such that for every $\tau$ some $rk$, $k\in\mathrm{SL}_2(\mathcal O_F)$, puts it in the region just treated. It is essential that the bound cover the new test $T_{rk}\phi$. For fixed $\phi$, all $T_k\phi$ are linear combinations with uniformly bounded coefficients of one finite set of coset indicators. In the source this follows by choosing a compact open finite lattice on which the support and local constancy are measured, and then a small enough common lattice in the two Heisenberg coordinates. Since $k$ is integral adelically, it preserves the pair of small lattices. Covariance with translations and their dual modulations then forces the transformed functions to retain common compact support and a common translation lattice. There are only finitely many cosets to record. Preservation of the $L^2$ norm bounds every coefficient, by the positive common coset measure. After the finitely many $T_r$, the new functions are still bounded linear combinations of finitely many fixed tests. Apply the reduced-region estimate to each such test and sum using linearity of both $\Theta$ and $E$. The resulting constant is independent of $\tau$. This proves the bound.

### Source and scope

The functions, weight and count assumption are [`QSetup`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/CountData.lean#L93), [`thTerm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/CountData.lean#L114) and [`CountData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/CountData.lean#L149). The Eisenstein absolute estimate is [`summable_norm_eiTerm_and_wt_mul_tsum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionGrowthBoundStatement.lean#L7); its finite oscillatory bound is [`fstar_decay`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/OrbitAdelic.lean#L76). The finite transformed tests come from [`orbit_adelic`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/OrbitAdelic.lean#L54) and the weighted transformation from [`good_ex`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/ProdRho.lean#L57). The combination with the reduction theorem and the count estimate is [`bounded`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/Bounded.lean#L20). The modularity and reduction statements and the average vector count for the unitary quotient are separate dependency inputs.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
