# Leading minors give the decay of the lowest-type coefficient

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p,q\ge1$, $n=p+q$, and use the signs and roots of the [noncompact layer estimate](compact-casimir-growth-controls-the-noncompact-word-filtration.md). Let $\lambda$ be strictly decreasing with $m_i=\lambda_i+\rho_i\in\mathbb Z$, indexing coordinates by $0\le i<n$. Assume $\lambda_i-\lambda_j\ge h>0$ for $i<j$ with opposite signs. Let $T$ be the compact irreducible representation of highest weight $\Lambda=\lambda+\rho_n-\rho_c$, $u$ a unit highest vector, $P_u$ its orthogonal rank-one projection, and $D=\dim T$. For a complex matrix $Z$, let $\Delta_a(Z)$ be its leading $a$-by-$a$ determinant. Put $m_n=0$ and, on the open set where all leading determinants are nonzero, define
$$
 F(Z)=\prod_{a=1}^n\Delta_a(Z)^{-(m_{a-1}-m_a)} .
$$
The compact average and its polar extension are
$$
 A(Z)=D\int_K F(k^{-1}Zk)\,T(k)P_uT(k)^{-1}\,dk,\qquad
 \Psi(k_0 e^X)=T(k_0)A(e^X),
 \tag{1}
$$
where $dk$ has mass $1$, $Z$ lies sufficiently near the positive definite cone, and $X$ is Hermitian with entries only between opposite signs. In particular this defines $\Psi$ on $U(p,q)$ by polar decomposition. The common domain on which every conjugate has nonzero leading determinants is open by compactness of $K$. The integral there is holomorphic because the derivatives of the integrand are uniformly bounded over $K$ on small compact neighborhoods.

Write $r=\|X\|_{\mathrm F}$ for the Frobenius norm and $c=\sqrt{2\min(p,q)}$. Then
$$
 \|\Psi(k_0e^X)\|_{\rm op}\le
 \exp\!\left(-\frac h8\min(r^2,r/c)\right).
 \tag{2}
$$
Consequently $\Psi$ is integrable for $h>16n\min(p,q)$, and $\int_{U(p,q)} \|\Psi(g)\|_{\rm op}^2\|g\|_{\rm F}^s\,dg<\infty$ for $s\ge0$ and $h>8n\min(p,q)+4sc$, for any Haar normalization. The source uses $s=0$ and $s=2$ in constructing a discrete series and its finite-tensor projections.

## The estimate in an exterior power

For the coordinate wedge $\xi_a=e_0\wedge\cdots\wedge e_{a-1}$ and induced Lie algebra endomorphism $X^{[a]}$,
$$
 \Delta_a(e^X)=\langle \xi_a,e^{X^{[a]}}\xi_a\rangle.
$$
The first moment $\langle \xi_a,X^{[a]}\xi_a\rangle$ is zero because $X$ has zero diagonal. The second moment is
$$
 V_a=\|X^{[a]}\xi_a\|^2=\sum_{i<a\le j}|X_{ji}|^2 .
$$
Indeed $X^{[a]}\xi_a$ changes a single coordinate of the wedge to one outside it, giving pairwise orthogonal wedges. The eigenvalues of $X^{[a]}$ are sums of $a$ distinct eigenvalues of $X$. The sum of the absolute eigenvalues of $X$ is at most $cr$ by Cauchy–Schwarz, since $X$ has rank at most $2\min(p,q)$.

When $cr\le1$, the scalar inequality $e^t\ge 1+t+t^2/e$ for $|t|\le1$ gives $\Delta_a(e^X)\ge1+V_a/e$ by the spectral theorem. The scalar inequality follows from $e^t=1+t+t^2\int_0^1(1-s)e^{st}\,ds$. Now $0\le V_a\le1$, so $\log(1+V_a/e)\ge V_a/(e+1)\ge V_a/4$. The full determinant is $\exp(\operatorname{tr}X)=1$. For the remaining factors of $F$ we have
$$
 \begin{aligned}
 -\log F(e^X)
 &\ge \tfrac14\sum_{a=1}^{n-1}(m_{a-1}-m_a)V_a \\
 &= \tfrac14\sum_{i<j}(m_i-m_j)|X_{ji}|^2
 \ge \tfrac h8 r^2.
 \end{aligned}
$$
The last inequality uses that $X$ is supported between opposite signs and that $\rho_i-\rho_j=j-i$. Along any ray, each function $\log\Delta_a(e^{tX})$ is convex by the log-sum-exp formula for the spectral resolution of $X^{[a]}$. Its coefficient $m_{a-1}-m_a$ is positive for $a<n$. The resulting convex function $-\log F(e^{tX})$ vanishes at zero, so its secant slope from zero is nondecreasing. Scaling the small-radius estimate from $r=1/c$ therefore gives $-\log F(e^X)\ge hr/(8c)$ for $r\ge1/c$.

All the conjugates of $X$ by $K$ have the same $r$ and allowed support. Their scalars $F(e^{k^{-1}Xk})$ are real and positive. Moreover $D\int_K T(k)P_uT(k)^{-1}\,dk=I$ by Schur's lemma and the trace. Thus the uniform scalar bound gives the same operator bound for $A(e^X)$ in the order of Hermitian operators. Left multiplication by the unitary $T(k_0)$ leaves its norm unchanged, proving (2). The same averaging argument yields $A(I)=I$.

## Haar integration

In these polar coordinates the Haar density relative to compact Haar times Euclidean measure on the Hermitian off-block subspace is bounded by a constant times $e^{ncr}$. To see the bound, the noncompact block of the differential of the exponential, after right translation and removal of the compact directions, is $\sinh(\operatorname{ad}X)/\operatorname{ad}X$ restricted to that subspace. This follows from $(e^{\operatorname{ad}X}-1)/\operatorname{ad}X$ and the fact that the odd powers exchange compact and noncompact directions. Its determinant is bounded by the product over all eigenvalues $\nu_i-\nu_j$, $i<j$, of $\sinh(\nu_i-\nu_j)/(\nu_i-\nu_j)$, where the $\nu_i$ are the eigenvalues of $X$. Indeed on each nonzero squared eigenspace the compact and noncompact parts have equal dimension, exchanged by $\operatorname{ad}X$, and the real $\mathfrak u(p,q)$ multiplicities together equal the complex multiplicities on $\mathfrak{gl}_n$. The factors for zero are $1$. Bound each factor by $e^{|\nu_i-\nu_j|}$ and use $\sum_{i<j}|\nu_i-\nu_j|\le(n-1)\sum_i|\nu_i|\le ncr$. Also $\|k_0e^X\|_{\rm F}\le\sqrt n e^r$. Beyond the fixed radius $1/c$ the resulting weighted square integral is bounded by a constant times the Euclidean integral of $e^{-(h/(4c)-nc-s)r}$, which is finite under the stated hypothesis. Without squaring the condition is $h/(8c)>nc$. The bounded-radius integrals are finite by continuity.

## Lean correspondence

- [PhiM](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/IsClosedKset.lean#L21) and [psM and PsiM](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/IsClosedKset.lean#L56) define the minor function, compact average and polar extension. [psM_exp_pmat](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FBridge.lean#L104) identifies this average with the polar coefficient used in the Gaussian calculation.
- [phiM_exp_le](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/PhiDecayCore.lean#L131) and [psiM_dec](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/PhiDecayCore.lean#L186) give (2). The exterior-power argument above expresses the same variance and convexity calculation in matrix form.
- [haar_polar_le](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/HaarPolar.lean#L135) and [psiM_integrable](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/Integr.lean#L22) give the density bound and the three integrability thresholds.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
