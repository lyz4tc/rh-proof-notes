# The compact and noncompact roots bound the row formal degree

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p,q\ge1$, $N=p+q$, and give the indices $0,\ldots,N-1$ a sign with $p$ pluses and $q$ minuses. Let $\lambda_0>\cdots>\lambda_{N-1}$ be an integral Harish–Chandra parameter, meaning its entries are integers translated by $(N-1)/2$. Let $V(\lambda)=\prod_{i<j}(\lambda_i-\lambda_j)$, $F(n)=\prod_{i=0}^{n-1}i!$, and $U=\max_{i,j}|\lambda_i-\lambda_j|$. Write $\rho_c,\rho_n$ for the half-sums of the positive roots $e_i-e_j$, $i<j$, of the same and opposite sign, respectively. Define
$$
 d_K(\lambda)=
 \frac{\displaystyle\prod_{i<j,\ \mathrm{sign}(i)=\mathrm{sign}(j)}
                (\lambda_i-\lambda_j+(\rho_n)_i-(\rho_n)_j)}
      {F(p)F(q)} .
$$
It is the dimension of the compact $K=U(p)\times U(q)$ highest weight $\lambda+\rho_n-\rho_c$. With the source's compact-dual Haar normalization, the large-gap formal-degree identity is $d_\sigma=V(\lambda)/F(N)$. Conditional on this identity, one has the sharper comparison
$$
 d_\sigma\le d_K(\lambda)U^{pq}.
\tag{1}
$$
In particular $ (1-\eta)V(\lambda)/F(N)\le d_\sigma\le 4d_K(\lambda)(3pqU)^{pq}$ for $0<\eta<1/2$. [Root shifts and compact dimension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/GapAtLeast.lean#L32) · [Formal-degree product comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL5/TheoremThreeAllUnitary.lean#L114) · [Two-sided comparison with the normalized degree](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfGappedMultiplicity.lean#L67)

For $i<j$ of the same sign, $(\rho_n)_i-(\rho_n)_j$ is the number of opposite-sign indices strictly between them. This follows by subtracting the half of the difference of the counts to the right and to the left in the definition of $\rho_n$. Thus each same-sign gap in $V(\lambda)$ is at most the corresponding positive shifted gap in $d_K$. The $pq$ opposite-sign gaps are at most $U$, as one comes from each pair formed by choosing one index of each sign. Finally $F(N)\ge F(p)F(q)$, since $(p+j)!\ge j!$ for $0\le j<q$. Dividing the product inequality by $F(N)$ gives (1). The Weyl formula for the compact groups gives the numerator as the differences of $(\lambda+\rho_n-\rho_c)+\rho_c$, with denominator $F(p)F(q)$. The same product arises for the full compact group $U(N)$ with parameter $\lambda$ and denominator $F(N)$. [Lowest compact type and its Weyl dimension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfGappedMultiplicity.lean#L22) · [Full Weyl denominator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L320)

## Why the formal-degree identity can be used at the row

For $e^{-N}\le\eta<1/2$, the family assumes the lower bound
$$
 h=\frac{8192\min(p,q)(pq)^3\log N}{\eta^2}
$$
on all opposite-sign gaps. It implies $h>32Npq+2$: use $\eta^{-2}>4$, $\log N\ge\log2>1/2$, $\min(p,q)\ge1$ and $N\le2pq$. This in turn implies the thresholds $h>\max(2N,8N\min(p,q))$ for discrete-series existence and $h>Npq+1$ for lowest compact type multiplicity one. The large-gap formal-degree theorem applies with these data and the Haar normalization specified in [the normalization argument](a-weight-shift-and-a-gaussian-limit-fix-the-formal-degree-constant.md). The project's row scalar $d_\sigma$ agrees with the degree via the equalities of Haar scales and of the row degree with the normalized Schur coefficient. In detail, square-integrability and Schur orthogonality yield the coefficient integral $\|v\|^4/d_\sigma$ for every $v\ne0$, with the given measure. Scaling that measure by a factor $c>0$ divides the degree by $c$. This is the equality used to identify the project scalar. The numerical inequalities therefore hold at each real place and each family member that meets the gap condition. [Threshold arithmetic](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/FormalDegreeGap/DimensionBoundOfGapUniform.lean#L10) · [Match the normalized coefficient to the row scalar](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/FormalDegreeGap/DimensionFamilyOfWeylMultiplicity.lean#L15) · [Large-gap discrete-series existence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/ExceptionalGroupG2/HarishChandraMultiplicityBound.lean#L16) · [Apply at one real place](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfGappedMultiplicity.lean#L131)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
