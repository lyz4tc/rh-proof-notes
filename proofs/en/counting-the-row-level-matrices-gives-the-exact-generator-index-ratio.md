# Counting the row-level matrices gives the exact generator index ratio

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $g\ge3$ be a prime, $k\ge1$ and $m\ge2$ even. Put $s=m/2-1$ and $r=k+m-1=2s+k+1$. The column subgroup of $\mathrm{GL}_k(\mathbb F_g)$ is the upper unitriangular group. The row subgroup of $\mathrm{GL}_r(\mathbb F_g)$ uses ordered block sizes
$$
 \underbrace{1,\ldots,1}_{s},\ k+1,\ \underbrace{1,\ldots,1}_{s}.
$$
Take diagonal entries $1$, zero entries below the block diagonal, and arbitrary entries in the blocks above it. In the central block, take an upper unitriangular $k$-by-$k$ block in its first $k$ coordinates and fix its final coordinate, with zero off-diagonal entries in the final row and column of that central block. These are the predicates `IsUnitri` and `IsRowLev`. Denote their indices in the two general linear groups by $I_{\pi}(g),I_\sigma(g)$. For $P_n(g)=\prod_{j=1}^n(1-g^{-j})$,
$$
 I_\pi(g)=g^{k(k+1)/2}P_k(g),\qquad
 I_\sigma(g)=g^{(r^2+3k+1+2s)/2}P_r(g).
\tag{1}
$$
[Level subgroups](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/GapAtLeast.lean#L56) · [Local index formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/DimensionMassJointBound.lean#L57)

## Count the free positions

An upper unitriangular column matrix has $k(k-1)/2$ arbitrary entries. For the row matrix, any pair of coordinate indices in different blocks contributes one upper-block entry, counted by
$$
 \frac{r^2-(k+1)^2-2s}{2}.
$$
Indeed the numerator is the number of ordered pairs across distinct blocks and each unordered pair contributes one. The additional central free positions come from the strictly upper part of the first $k$ coordinates, giving $k(k-1)/2$. All other entries are forced. Each assignment determines an invertible matrix because its diagonal is $1$ and it is upper triangular. The cardinalities are $g$ to the respective free-position counts. [Free support condition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ThickPlacesCorollaryOfAnyTranslate.lean#L212) · [Row-level cardinality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ThickPlacesCorollaryOfAnyTranslate.lean#L277)

To count $\mathrm{GL}_n(\mathbb F_g)$, choose its columns in order. After $j$ independent columns the next is any vector outside their span, giving $g^n-g^j$ choices. Thus the cardinality is $g^{n^2}P_n(g)$. Dividing by the two subgroup orders yields (1). For the row exponent the subtraction is
$$
 r^2-\frac{r^2-(k+1)^2-2s+k(k-1)}{2}
 =\frac{r^2+3k+1+2s}{2}.
$$
Consequently the exponent in $I_\sigma(g)/I_\pi(g)$ is $m(2k+m-1)/2$, using $r=k+m-1$ and $2s=m-2$.

## Bound the finite products uniformly

For numbers $0\le a_i\le1$, induction gives $\prod_i(1-a_i)\ge1-\sum_i a_i$. Apply it to $a_i=g^{-i}$, so $1/2\le P_n(g)\le1$ because $\sum_{i\ge1}g^{-i}=1/(g-1)\le1/2$. Also
$$
 1-2g^{-(k+1)}
 \le \frac{P_r(g)}{P_k(g)}=\prod_{j=k+1}^r(1-g^{-j})\le1.
$$
The lower bound follows by summing the geometric tail and using $(1-g^{-1})^{-1}\le2$. Lean's uniform bound uses an induction on the product as well. For two generator primes $g_1,g_2$ and $f\ge1$, multiply (1) for both primes and take the $f$-th power. The exact residual factor is the product of the two displayed tail ratios to power $f$. Using $P_r\ge1/2$ and $P_k\le1$ yields the convenient lower bound $2^{-2f}(g_1g_2)^{fm(2k+m-1)/2}$ for the full row-to-column index ratio. [Bounds for the finite product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/BlockDimensionIdentities.lean#L124) · [Exact tail ratio](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GlobalRankLatticeProofs/LemmaFiveOneOfTheoremTwo.lean#L287) · [Ratio at the two primes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L124)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
