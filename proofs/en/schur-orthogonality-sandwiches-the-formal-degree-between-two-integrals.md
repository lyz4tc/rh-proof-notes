# Schur orthogonality sandwiches the formal degree between two integrals

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

For $p,q\ge1$, $N=p+q$, use the noncompact coordinates $z$, Hermitian matrix $X(z)$, potential $\Phi_\lambda$ and Jacobian $J(z)$ of [the polar integral calculation](the-rescaled-polar-potential-has-a-gaussian-integral-limit.md). Write $G=U(p,q)$, $K=U(p)\times U(q)$, $F(s)=\prod_{i<s}i!$, and put
$$
 c_{pq}=\frac{F(N)}{\pi^{pq}F(p)F(q)}.
$$
The measure used for the degree is the Haar measure on $G$ written $c_{pq}\,dk\,J(z)\,dz$ in the polar coordinates $g=k e^{X(z)}$, with $dk$ a probability Haar measure. Take an irreducible square-integrable unitary representation $\sigma$ of degree $d>0$ in this measure, with an isometrically embedded lowest compact type $V$ of dimension $D$. Write $w\in V$ for its unit highest weight vector and $R(k)$ for the compact action on $V$. Assume the compressed operator $\mathcal A(z)=P_V\sigma(e^{X(z)})|_V$ satisfies the following integral formula:
$$
 \mathcal A(z)=D\int_K
   e^{-\Phi_\lambda(k^{-1}X(z)k)}
       |R(k)w\rangle\langle R(k)w|\,dk .
\tag{1}
$$
This is the matrix coefficient input called `FData`, and the project identifies it using the lowest compact type model. Then
$$
 c_{pq}\int |\langle w,\mathcal A(z)w\rangle|^2J(z)\,dz
 \ \le\ \frac{D}{d}\ \le\
 c_{pq}\int e^{-2\Phi_\lambda(X(z))}J(z)\,dz.
\tag{2}
$$
[Polar measure and model coefficient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/PmatIsHermitian.lean#L74) · [Coefficient model for an arbitrary representation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/DiscreteSeriesExistence/RangeDatumEmbedding.lean#L95) · [Use both inequalities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/ThmFD.lean#L21)

## Sum the coefficient identities

For an orthonormal basis $e_1,\ldots,e_D$ of $V$, Schur orthogonality gives $\int_G|\langle e_i,\sigma(g)e_j\rangle|^2\,dg=1/d$ for each $i,j$. Summing yields $D^2/d$. At $g=k e^{X(z)}$ the projection commutes with $\sigma(k)$, and the compressed operator is $R(k)\mathcal A(z)$. Its Hilbert–Schmidt norm, the square root of the sum of the squared matrix entries, is independent of $k$. Integrate out $k$ to get
$$
 c_{pq}\int \|\mathcal A(z)\|_{\mathrm{HS}}^2J(z)\,dz=D^2/d .
$$
More precisely, sum only over the target basis $e_i$ with source $w$ fixed. Then
$$
 c_{pq}\int \|\mathcal A(z)w\|^2J(z)\,dz=D/d .
$$
Cauchy–Schwarz with $\|w\|=1$ gives the left inequality of (2). [Sum all compact matrix entries](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/SumInnerBasisSqEqAdjoint.lean#L77) · [Use the single highest-weight coefficient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/SumNormAdjointSqEqHsOp.lean#L160)

## Bound the Hilbert–Schmidt norm of the model

By irreducibility of the compact type and Schur's lemma,
$$
 D\int_K |R(k)w\rangle\langle R(k)w|\,dk=1_V
$$
because the operator commutes with $K$ and has trace $D$. Thus $A:V\to L^2(K,dk)$, $Av(k)=\sqrt D\langle R(k)w,v\rangle$ with the inner product linear in $v$, is an isometry. Formula (1) writes $\mathcal A(z)=A^*M_{f_z}A$ with $f_z(k)=e^{-\Phi_\lambda(k^{-1}X(z)k)}$. The adjoint $A^*$ has norm one, so
$$
 \|\mathcal A(z)\|_{\mathrm{HS}}^2\le
       \sum_j \|M_{f_z}Ae_j\|^2
       =D\int_K |f_z(k)|^2\,dk.
$$
The equality follows by summing the squared basis coefficients of the unit vector $R(k)w$. Conjugating $X(z)$ by $k$ preserves its eigenvalues, so it preserves $J(z)$. It also preserves the Hilbert–Schmidt norm of the noncompact Hermitian space and therefore its coordinate Lebesgue measure. Thus the change of variables given by this conjugation makes the $z$-integral of $|f_z(k)|^2J(z)$ independent of $k$. Integrating the displayed upper estimate and using the $D^2/d$ identity gives the right side of (2). [Compact coefficient inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/IntegrableOfContinuousCompact.lean#L239) · [Haar integration of the upper bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/IntegrableOfContinuousCompact.lean#L299)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
