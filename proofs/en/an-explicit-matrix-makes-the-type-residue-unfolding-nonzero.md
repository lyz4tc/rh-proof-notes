# An explicit matrix makes the type residue unfolding nonzero

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Setup and statement

Let $\kappa$ be a finite field, $\psi_0:\kappa\to\mathbb C^\times$ an additive character, and $\chi_\ell:\kappa^\times\to\mathbb C^\times$ multiplicative characters for $\ell\ge0$. Extend each $\chi_\ell$ by $0$ at zero, and interpret the reciprocal factor at an argument of zero as zero. Take integers $k\ge1$, even $m\ge4$, $1\le j\le m-2$, $t\ge0$, and put
$$
c=m-1-j,\qquad r=k+m-1,\qquad a=r+(j-1)t,\qquad N=r+jt.
$$
The source and target ordinary dimensions $n',n$ satisfy $a=n'+c+1$ and $N=n+c$. In the source $\kappa^a$ and target $\kappa^N$, write the standard basis as the ordinary vectors $e_i'$ and $e_i$ followed by the extra vectors $f'_0,\ldots,f'_c$ and $f_0,\ldots,f_{c-1}$. In the *adapted order* on each space, insert the extra vectors immediately after the first $k$ ordinary basis vectors. Matrix entries $Y_{pv}$ appearing in the test below use that adapted order, indexed from zero.

For a total bound $L\in\{a,N\}$ and indices $0\le p<N$, $0\le v<L$, the allowed off-diagonal positions are given by the following rules. For $v<k$, allow $p<v$ or $k\le p<k+m/2-1$. For $k\le v<r$, allow $k\le p<v$, and also $p<k$ if $m/2<v+1-k$. For $r\le v<L$, allow $p<r$, and also $r\le p<L$ if $p$ is in the same or an earlier block of size $t$ than $v$, counting blocks from $r$. For $t=0$ the last case has no columns.

The type test $\Phi(Y)$ is zero unless $Y_{vv}=1$ for $v<r$ and each nonzero off-diagonal entry in a column $v<a$ is allowed with $L=a$. When these conditions hold, let $B_\ell$ be the square block on the indices from $r+\ell t$ to $r+(\ell+1)t-1$ and $B$ the full initial $a\times a$ part of $Y$. The test is
$$
\Phi(Y)=\psi_0\left(\sum_{v=0}^{r-2}Y_{v,v+1}\right)
\left(\prod_{\ell=0}^{j-2}\chi_\ell(\det B_\ell)\right)
\chi_{j-1}(\det B)^{-1}.
$$
For an ordinary map $X:\kappa^{n'}\to\kappa^n$, form enlarged matrices $Y=Y(X,\tau)$ as follows. An ordinary source column is the corresponding column of $X$ extended by zero extra coordinates. The first extra column is $f_0$. For $1\le i<c$, the column at $f'_i$ is $f_i$ plus arbitrary components in the ordinary target space and $f_0,\ldots,f_{i-1}$. The last extra column, at $f'_c$, is completely free. Let $\tau$ range over all these free entries and let $\omega(Y)=\sum_{i=0}^{c-1}(Yf'_{i+1})_{f_i}$, with subscripts here denoting coefficients of the specified basis vectors. Then there is an $X$ for which the residue-field first unfolding at the identity target matrix satisfies
$$
F_1(X)=\sum_\tau\Phi(Y(X,\tau))\psi_0(-\omega(Y(X,\tau)))\ne0.
$$
This assertion holds for every additive character, including the trivial one.

### Proof

Choose $X e'_s=e_s$ for $s<k$ and $X e'_s=e_{s+1}$ for $s\ge k$. These target indices exist since $n=n'+1+t$. In the adapted order, the column at every ordinary basis vector is then the standard target column with the same index. This includes the columns after the last inserted extra coordinate, since the source has one more such coordinate than the target. The column at $f'_0$ is also the standard column. Thus only the adapted columns with indices from $k+1$ through $k+c$ can vary with $\tau$.

Suppose the support conditions of $\Phi$ hold. The variable columns have index $v<r$ because $c=m-1-j$ and $j\ge1$. The allowed positions for such a column with $v\ge k$ have $p<v$. All other columns are standard. Therefore the first $a$ rows form an upper triangular $a\times a$ matrix whose diagonal is one. The entries at indices below $r$ come from the support condition, and those at indices at least $r$ come from standard columns. The determinant of this matrix is one, and each $B_\ell$ is the identity since its columns have indices at least $r$. Thus all the multiplicative character factors equal one.

Only the varying columns can contribute to the sum $\sum_{v=0}^{r-2}Y_{v,v+1}$. For each $i=0,\ldots,c-1$, its term at the extra source column $k+i+1$ and target row $k+i$ is precisely $(Yf'_{i+1})_{f_i}$. It follows that the additive factor in the matrix test is $\psi_0(\omega(Y))$. It cancels the factor $\psi_0(-\omega(Y))$ in the unfolding. A filling satisfying the support thus contributes $1$, and every other filling contributes $0$.

Choose all free entries zero except for the ordinary coordinate $e_k$ in the last extra column, which is set to one. The last extra source column has adapted index $k+c$, and $e_k$ has that same adapted index in the target. The resulting enlarged matrix is the inclusion of the first $a$ adapted coordinate vectors into $\kappa^N$. All support conditions hold. The unfolding at the chosen $X$ is consequently a positive integer counting the admissible fillings. In particular no cancellation can make it zero.

### Lean correspondence

- [`IsFree`, `xx1`, `chArg` and `E1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OneCosetSharp.lean#L120) specify the free columns and the average, with weight parameter $1$ here. [`fIdx`, `Allow` and `PhiS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OneCosetSharp.lean#L147) give the indexing, support and matrix phase.
- [`xj0` and `τ0`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/EntryEmbedMatrix.lean#L24) choose the ordinary map and the filling. [`sum_eq_chArg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/EntryEmbedMatrix.lean#L96) identifies the sum of adjacent entries, and [`term_eq` and `claim2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/projection2/EntryEmbedMatrix.lean#L191) reduce the value to a count and prove positivity.
- [`residueFieldUnfolding_claims_hold`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ResidueFieldUnfoldingClaimsHold.lean#L6) packages this result with the support implication. [`twNonVanG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwOk.lean#L27) uses the residue nonvanishing to obtain eventual nonvanishing for the identity chart at a type place.

Status. Source-based reconstruction draft. This note proves the finite residue-field nonvanishing used as input to the large-depth comparison. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
