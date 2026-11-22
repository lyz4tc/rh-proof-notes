# Compact integration by parts gives a holomorphic formula for the polar coefficient

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Keep the hypotheses and notation for $A,\Psi,F,m,\Lambda,T$ from the [leading-minor construction](leading-minors-give-the-decay-of-the-lowest-type-coefficient.md). Write $\tau=dT_{\mathbb C}$ for the complexified compact action. For every $g_0\in U(p,q)$, there are a neighborhood of $g_0$ in the complex invertible matrices and a fixed $k_0\in K$ such that for the group elements $g$ in that neighborhood,
$$
 \Psi(g)=T(k_0)A(g^{-1}k_0).
 \tag{1}
$$
In particular, the polar extension is the restriction of a holomorphic function locally on the group. Formula (1) permits complexified right derivatives on $\Psi$ to be computed by complex left derivatives on $A$.

## Differentiating the compact average

Fix a positive definite matrix $x$ and a Hermitian block-diagonal matrix $H$, with blocks given by the signs. Write
$$
 z=k^{-1}xk,\qquad B=k^{-1}Hk,\qquad R(B)=B_--B_+ ,
$$
where the two subscripts denote the strictly lower and strictly upper triangular parts. Let $P=P_u$, put $P(k)=T(k)PT(k)^{-1}$, and write $f(k)=F(z)P(k)$ for the integrand. Since $B$ is Hermitian, $R(B)$ is skew Hermitian and block-diagonal. Use the vector field $W$ on $K$ whose value at $k$ is the tangent to $k\exp(tR(B))$ at $t=0$. Acting on the integrand gives
$$
 W f(k)=dF_z(zR-Rz)P(k)+F(z)T(k)[\tau(R),P]T(k)^{-1}.
$$

The congruence derivative of the scalar uses the tangent $Bz+zB$. Its difference from $zR-Rz$ is $(B+R)z+z(B-R)$. Here $B+R$ is lower triangular and $B-R$ is upper triangular. Left multiplication by a lower triangular matrix and right multiplication by an upper triangular one act on each leading determinant through the corresponding leading diagonal product. Telescoping the exponents in the definition of $F$ shows that the extra derivative is $-2(\sum_a m_a B_{aa})F(z)$.

For the operator part, the highest vector is killed by the upper root operators in the compact blocks. Furthermore $P$ kills the range of each lower root operator because its adjoint is an upper root operator. This gives
$$
 \tau(B)P+P\tau(B)=[\tau(R),P]+2\left(\sum_a\Lambda_a B_{aa}\right)P .
$$
Combining the two calculations and using $m=\Lambda+2\rho_c$, the derivative of the original integrand in the direction $Hx+xH$ is
$$
 W f(k)-\tau(H)f(k)-f(k)\tau(H)-4\left(\sum_a(\rho_c)_a B_{aa}\right)f(k).
 \tag{2}
$$

The divergence of $W$ for compact Haar measure is $-4\sum_a(\rho_c)_a B_{aa}$. To calculate it, expand the field in the constant right multiplication derivatives for the matrix units $e_{ab}$ within one block, using complex linear combinations of real skew-Hermitian generators. These constant fields have zero divergence. Along the field for $e_{ab}$, the derivative of $B$ is $[B,e_{ab}]$, with $ab$-entry $B_{aa}-B_{bb}$. The coefficient of $e_{ab}$ in $R$ is $B_{ab}$ below the diagonal and $-B_{ab}$ above. Summing each such pair gives $-2(B_{aa}-B_{bb})$ for $a<b$ in a block. Summing over the compact positive roots gives the divergence claimed. The first and last terms of (2) therefore integrate to zero together, by applying compact integration by parts entrywise. This proves
$$
 dA_x(Hx+xH)=-\tau(H)A(x)-A(x)\tau(H).
 \tag{3}
$$
This is where the difference $m-\Lambda=2\rho_c$ enters. Its contribution cancels the divergence.

The identity $A(k^{-1}xk)=T(k)^{-1}A(x)T(k)$ follows by changing the variable in the compact integral. Its derivative for skew-Hermitian block-diagonal $Y$ describes $dA_x(xY-Yx)$. Apply (3) to $iY$ and use complex linearity to describe $dA_x(xY+Yx)$. Together they give
$$
 dA_x(xY)=-\tau(Y)A(x),\qquad
 dA_x(Yx)=-A(x)\tau(Y).
 \tag{4}
$$
The skew-Hermitian block matrices span the complexified block Lie algebra, so (4) holds for every complex block-diagonal $Y$. Both sides are holomorphic in $x$ on the domain of $A$; the positive definite Hermitian matrices are open in a real form of the full complex matrix space. The identity thus extends to a complex neighborhood of each positive definite matrix. For instance, expand in complex Taylor series in a real Hermitian basis and differentiate the identity on the real slice.

## Integrating the infinitesimal identity

For $r=\exp(Y)$ in $K$ near $1$ and $x$ near a fixed positive definite matrix, take the path $x\exp(tY)$ in the domain of (4). The first differential identity gives a linear differential equation, with solution
$$
 A(xr)=T(r)^{-1}A(x).
$$
Take $k_0$ from the polar decomposition of $g_0$. For $g=k e^X$ close to $g_0$, the element $r=k^{-1}k_0$ is close to $1$ by continuity of polar decomposition, and $g^{-1}k_0=e^{-X}r$. The diagonal sign matrix $J$ is central in $K$ and conjugates $X$ to $-X$, so compact equivariance and centrality of $T(J)$ give $A(e^{-X})=A(e^X)$. Hence $T(k_0)A(g^{-1}k_0)=T(k)A(e^X)$, as in (1). Since inversion and multiplication by $k_0$ are holomorphic on the invertible matrices, this is the required local formula.

## Lean correspondence

- [Ssum_eq](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/LowMinusUpExpand.lean#L172) computes the vector-field contribution, and [psM_inf_herm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/LowMinusUpExpand.lean#L269) integrates the congruence derivative.
- [psM_inf_right](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/InfRight.lean#L69) and [psM_inf_nhd](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/PsMInfNhd.lean#L21) prove and extend (4). [psM_exp_neg](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/ContinuousConjProjection.lean#L223) gives the sign-matrix symmetry.
- [psiM_local](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/CasimirCoefficients/PsiMLocal.lean#L22) is the local inversion formula used for differentiating the coefficient.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
