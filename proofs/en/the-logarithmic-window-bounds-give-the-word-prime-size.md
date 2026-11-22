# The logarithmic window bounds give the word-prime size

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a real scale $x>1$ with $0<\varepsilon<1/2$, and write $L=x^\varepsilon$, $b=e^L$. Let $f,k,m$ be positive integers. The rank parameter is $k$, there are $f$ embedding coordinates $\rho$, and $m$ is the number of added weight entries. Assume $m^2L\le k$. At one selected family member let $v\ge\pi$ be the positive host factor, and let $g_0,g_1\ge(kb)^8$ be the two generator primes. Let $\Delta\ge1$, and for each embedding take weights $a_{j,\rho},w_{j,\rho}$ for $0\le j<m$ satisfying
$$
a_{0,\rho}\ge 4k\Delta x,\qquad
a_{j,\rho}<w_{j,\rho},\qquad
w_{j,\rho}<a_{j+1,\rho}\quad(j+1<m).
\tag{1}
$$
The source uses $a_{j,\rho}=\texttt{bN}(D,\rho,j)$. These are the clauses of the full weight hypothesis `DataB` needed for the lower bound. For $C\in\mathbb R$ define
$$
A_C=\sum_{j<m}\frac1f\sum_\rho\log(w_{j,\rho}v/\pi)
       +m(\log g_0+\log g_1)
       -C\left(L+\frac{m^2L}{k}\right).
\tag{2}
$$

For a word $u$, let $D^*,d_u^*>0$ be the common target dimension factor and the corresponding column factor. The center before loss is $X_u=(D^*/d_u^*)^{1/(fk)}$. Write $\Gamma_u\ge1$ for the positive adjustment parameter and $T_u$ for the already selected prime, with
$$
\log\Gamma_u\le fk,\qquad
X_u\Gamma_u^{-2/(fk)}\le T_u\le
 X_u\Gamma_u^{-2/(fk)}\left(1+\frac1{fk}\right).
\tag{3}
$$
Use the two size clauses of `TorusPairsWithVariant`, in the given prime window,
$$
\log T_u\le C m L,\qquad
A_C-\frac{2\log\Gamma_u}{fk}\le\log T_u .
\tag{4}
$$
Then if $(4\max(C,0)+4)/31\le m$ and $C\le C_T$, one has
$$
b^{m/2}\le T_u,\qquad \log T_u\le C_TmL.
\tag{5}
$$
When these data and (4) hold uniformly for all sufficiently large $x$ in the family, (5) holds uniformly for all sufficiently large $x$. This is the word-prime size predicate `TuSize` used in the simultaneous design. Equation (4) is an input to the present deduction. The [relative-window count](a-relative-prime-window-sets-the-torus-pair-count-within-a-constant.md) gives the conversion from the center to the prime, and [the lower estimate for the adjusted center](the-row-dimension-keeps-the-prime-window-center-above-the-target-scale.md) also has a direct construction-side proof. The estimate applies to each word separately, with the same family threshold.

### The two large terms in the lower bound

By (1) the $a_{j,\rho}$ are increasing in $j$, and $w_{j,\rho}>a_{j,\rho}\ge4$. Since $v\ge\pi$, all the weight logarithms in (2) are nonnegative. The generator inequalities give $\log g_i\ge8\log(kb)\ge8L$, since $k\ge1$. Finally $m^2 L/k\le1$, and the product of $C$ with the nonnegative error factor in (2) is at most $C_+(L+1)$, where $C_+=\max(C,0)$. Therefore
$$
A_C\ge 16mL-C_+(L+1).
$$
Since $L\ge1$ and $\log\Gamma_u/(fk)\le1$, (4) yields
$$
\log T_u\ge16mL-C_+(L+1)-2\ge16mL-(2C_++2)L .
$$
The assumption on $m$ gives $2C_++2\le31m/2$, so the right side is at least $mL/2$. Exponentiation proves the lower bound in (5). The upper bound follows from the first inequality of (4) and nonnegativity of $mL$.

### The family threshold

The size record in the actual theorem gives $m\ge\sqrt{x^{1-\varepsilon/8}}\ge x^{1/4}$ and $L=x^\varepsilon\ge1$. It also gives a common $\Gamma$ for the words with $\log\Gamma\le k$, hence $\log\Gamma\le fk$. The factor identities `FactDuStar` and `FactDstar` identify the numerical center used in (4) with the value in (3), since
$$
\log X_u=\frac{\log(D^*/d_u^*)}{fk}.
$$
Thus the hypothesis that the primes are in that window is exactly the window already recorded for the selected family. Take the maximum of the threshold for the numerical bounds, the threshold for a weight profile (1), $1$ plus the family's starting point, and a threshold at which $x^{1/4}\ge(4C_++4)/31$. Every inequality used above then holds simultaneously at each family member and word.

The family selection uses $C_*=\max(5,C_{YL}+1)$ for the common row parameter $C_0=C_Y=C_*$. The `VandermondeCountBound` and the `RowsA` bounds, taken at a common threshold, supply `Conclusion5₂`, whose middle clause is `TorusPairsWithVariant`. They use $C=\max(11,16+3C_*)$. The assumed inequality $C\le C_{Tu}$ is precisely the size-constant condition `cTmin`. These inequalities give the size bound on the selected prime.

### Lean correspondence

- [`DataB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L500) gives the initial weight and generator bounds. [`lowB` and `TorusPairsWithVariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L524) give the expression (2) and the window comparisons (4).
- [`jnt_logXu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L14) identifies the two descriptions of the center. [`logGam_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L165) gives the gamma bound, and [`m_large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L241) increases the family threshold. [`lowB_ge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L259) derives the estimate for (2). [`tuGe_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L322) proves the lower bound, and [`tuSize_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/JointsL.lean#L349) proves the two-sided statement uniformly.
- [`part_five_all_of_explicit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeOfExplicitAndCompact.lean#L328) supplies the size clauses within the three numerical conclusions. [`cTmin` and `tuSize_min`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TheoremThreeFamilyOfFormalDegreeInput.lean#L93) use the common upper constant and threshold. [`row_hTu_cTmin_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/RowHTuCTmin.lean#L12) is the entry on the actual selection route. It uses the mass and volume comparison and gapped discrete-series degree bound to obtain the Vandermonde input.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
