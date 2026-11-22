# The Casimir bound and a small-time ODE give the coefficient Gaussian

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $p,q\ge1$ and the signs and parameter $\lambda$ of [the formal-degree calculation](a-weight-shift-and-a-gaussian-limit-fix-the-formal-degree-constant.md). Put $D_i=N-1-i$, $\lambda_t=\lambda+tD$ and $\Lambda_t=\lambda_t+\rho_n-\rho_c$. Suppose $\sigma_t$ is a unitary representation of the real unitary group with a smooth unit vector $w_t$ of compact highest weight $\Lambda_t$. This means that for the complexified derived action $E_{ij}=d\sigma_t(e_{ij})$, $E_{ii}w_t=\Lambda_{t,i}w_t$ and $E_{ij}w_t=0$ for $i<j$ of the same sign. Assume also that the quadratic Casimir $\Omega=\sum_{i,j}E_{ij}E_{ji}$ acts on $w_t$ by $\|\lambda_t\|^2-\|\rho\|^2$, with $\rho=\rho_c+\rho_n$. These are the source's highest-weight vector hypotheses. For each fixed $y$ in the $pq$ noncompact coordinates of [the polar calculation](the-rescaled-polar-potential-has-a-gaussian-integral-limit.md), one has
$$
 \big\langle w_t,\sigma_t(e^{X(y)/\sqrt t})w_t\big\rangle
 =e^{-Q(y)/2}+O_y(t^{-1/2}),\qquad
 Q(y)=\sum_{i<j,\ \mathrm{sign}(i)\ne\mathrm{sign}(j)}(j-i)|y_{ij}|^2 .
\tag{1}
$$
The constants depend on the fixed signs, $\lambda$ and $y$. This is the specialization of the source's tangent estimate to the polar coordinates. [Smooth highest-weight hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/IsHWSmooth.lean#L55) · [General tangent estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/RaisingLoweringNormIdentities.lean#L68) · [Polar specialization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdPointwise.lean#L120)

## Uniform bounds for the lowering directions

Let $s_i$ be the diagonal signs. On the smooth vectors infinitesimal unitarity gives $E_{ij}^*=s_i s_j E_{ji}$. The bracket $[E_{ij},E_{ji}]=E_{ii}-E_{jj}$ implies, for $i<j$,
$$
 s_i s_j\bigl(\|E_{ji}w_t\|^2-\|E_{ij}w_t\|^2\bigr)=\Lambda_{t,i}-\Lambda_{t,j}.
$$
For equal signs $E_{ij}w_t=0$. For opposite signs the norm difference instead gives $\|E_{ij}w_t\|^2=\|E_{ji}w_t\|^2+\Lambda_{t,i}-\Lambda_{t,j}$. Expand $\langle w_t,\Omega w_t\rangle$ using the adjoint law and pair the off-diagonal terms by $i<j$. This gives
$$
 \|\Lambda_t\|^2+2\langle\Lambda_t,\rho_c-\rho_n\rangle
 -2\sum_{i<j,\ s_i\ne s_j}\|E_{ji}w_t\|^2
 =\|\lambda_t\|^2-\|\rho\|^2 .
$$
The first two terms equal $\|\lambda_t\|^2-\|\rho_n-\rho_c\|^2$. Thus the sum of the noncompact lower-triangular norms squared is a constant independent of $t$. Each such norm is $O(1)$, and the other off-diagonal norms are $O(\sqrt t)$ by the bracket identity. The diagonal differs from $tD_iw_t$ by $O(1)$. In particular, for a complex matrix $A$ and $\ell(A)=\operatorname{tr}(\operatorname{diag}(D)A)$,
$$
 \|d\sigma_t(A)w_t-t\ell(A)w_t\|\le C\sqrt t\|A\|.
\tag{2}
$$
Any fixed matrix norm can be used because the matrix space is finite dimensional. These are the uniform bounds used in the tangent calculation. [Casimir and root norms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/DoubleSumDiagSplit.lean#L39) · [Uniform linear-action bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/NoncompactLoweringNormSmall.lean#L51)

## Conjugate the growing term before taking the derivative

Write $X=X(y)=L+U$, with strictly lower and upper triangular parts $L,U$. Their entries join opposite signs only. Write $A^\dagger=J A^*J$ for the signed conjugate transpose on the matrix space, with $J$ the diagonal sign matrix. Then $U^\dagger=-L$, so both $d\sigma_t(L)w_t$ and $d\sigma_t(U^\dagger)w_t$ are $O_y(1)$.

Let $g_s=e^{sX/\sqrt t}$, $a_t(s)=\langle w_t,\sigma_t(g_s)w_t\rangle$ for $0\le s\le1$, with the inner product linear in its second variable. Smoothness gives
$$
 a_t'(s)=t^{-1/2}\langle w_t,\sigma_t(g_s)d\sigma_t(L+U)w_t\rangle.
$$
The $L$-term is $O_y(t^{-1/2})$ by unitarity. Move the $U$-term by covariance of the derived action, then take its adjoint. Its inner product becomes $\langle d\sigma_t((g_s U g_s^{-1})^\dagger)w_t,\sigma_t(g_s)w_t\rangle$. With $\tau=s/\sqrt t$,
$$
 g_s U g_s^{-1}=U+\tau[X,U]+O_y(\tau^2).
$$
The $U^\dagger$ part is again $O_y(1)$ before division by $\sqrt t$. Apply (2) to the remainder after $U$, which has matrix norm $O_y(\tau)$. After division by $\sqrt t$ the error is $O_y(t^{-1/2})$, uniformly for $s\in[0,1]$. The leading diagonal term is $s\ell([X,U])a_t(s)$: the adjoint conjugates the trace scalar and the inner product conjugates it back. Each pair $i<j$ in the noncompact coordinates contributes $-D_i|y_{ij}|^2+D_j|y_{ij}|^2$ to $\ell([X,U])$, since $[X,U]=[L,U]$. Thus $\ell([X,U])=-Q(y)$. [Move the derivative to the other vector](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/InvMulSelfOfMemIndefiniteUnitary.lean#L178) · [Differentiate the coefficient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/B3b.lean#L12) · [Conjugation expansion and uniform error](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/MatrixCoeffBoundsImplyBound.lean#L69)

We obtain $a_t'(s)+sQ(y)a_t(s)=O_y(t^{-1/2})$ with $a_t(0)=1$. Multiply by $e^{s^2Q(y)/2}$, integrate over $[0,1]$ and divide by $e^{Q(y)/2}$ to get (1). This gives the coefficient limit used with Fatou's lemma. [Integrating factor argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/LaplaceOperators/LaplaceFoundations/OneParameterSubgroups/OneParam.lean#L10)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
