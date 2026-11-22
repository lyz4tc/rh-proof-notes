# A nonzero unfolding descends the twist level character

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a twist place $P$ of prime norm $q$ with $\operatorname{ord}_P(q)=1$. Let $A=\mathcal O_{E,P}$ and let $K$ be the coefficient number field. Fix an ordinary true-chain step $0\le i<m-2$ and bounded enlarged source and target charts $g,h$ at layers $i,i+1$. Assume the local additive phase $\psi$ is multiplicative on $q^{-D}A$ and trivial on $A$, with $D\ge i+1$. Write $C_h=\mathcal R\cap hJh^{-1}$ for the target first-parabolic group with conjugated twist level $J$. Let $H_h$ be its image under restriction to the target ordinary subspace. Assume $H_h\subseteq\mathrm{GL}_{N_{i+1}}(A)$, as for a chart in [flag normal form](putting-a-bounded-twist-lattice-in-flag-normal-form.md).

For $r\in C_h$ set
$$
\chi_h(r)=\psi(n(r))^{-1}\lambda_Q(h^{-1}rh),
$$
where $n(r)$ is the sum of adjacent superdiagonal entries between extra target coordinates and $\lambda_Q$ is the [inverse quotient determinant character](the-twist-local-test-transforms-by-the-quotient-determinant.md). If the first unfolding for $g,h$ is a nonzero function for all sufficiently large depths, then $\chi_h(r)\in K^\times$ depends only on $u=r|_{E^{N_{i+1}}}$, and the resulting map $H_h\to K^\times$ is a character. These are the assertions encoded in `TwChrOk`.

For the identity target chart, the same projection character is defined for each layer with the standard twist level, without a nonvanishing input. It is trivial at the initial layer and is the inverse quotient determinant character on the zero-extra-coordinate chart at layer $m-1$.

### Transformation of the nonzero unfolding

Let $F(X)$ be the stabilized first unfolding, a function on the original rectangular matrices. It is nonzero by the given nonvanishing and [stabilization](why-the-twist-unfolding-stabilizes-as-the-box-grows.md). The normalization in the enlarged test depends only on the chosen charts. If $r\in C_h$, the transformed test at $rY$ evaluates the original twist function at
$$
h^{-1}rYg=(h^{-1}rh)(h^{-1}Yg).
$$
The target twist matrix law applies with $k=h^{-1}rh\in J$. Since $r$ has identity on the successive extra-coordinate quotients, $\det r=\det u=\det k$. Therefore multiplication of the test at $rY$ by $\xi(\overline{\det u})^{-1}$ gives the test at $Y$ times $\lambda_Q(k)$.

The [reindexing of the large columns](reindexing-the-ordinary-local-unfolding-sum.md) now changes the original matrix to $uX$ and adds $n(r)$ to the additive argument. One may use the same finite congruence quotient on both sides, since $r$ preserves the moved target lattice. Equivalently, on the free columns the linear part of the affine substitution is a direct sum of the restrictions of $r$ to the permitted flag subspaces. On each such subspace its determinant is $\det u$, because it is the identity on each successive quotient above the ordinary coordinates. Hence the determinant in the [affine sum formula](an-affine-change-of-unfolding-variables-contributes-a-determinant-factor.md) is a unit at $P$ and its factor is $1$. The support bound puts both additive arguments in $q^{-D}A$ whenever the matrix test is nonzero. Their difference is then in the domain of $\psi$, and the phase ratio is $\psi(n(r))^{-1}$. If the matrix test vanishes, it vanishes on both sides of this substitution. The resulting target equation is
$$
\xi(\overline{\det(u^{-1})}) F(uX)=\chi_h(r)F(X).
$$
The determinant factor on the left is exactly `rhoT` evaluated at the inverse determinant in the twist case.

### Nonzero value and descent

Choose $X_0$ with $F(X_0)\ne0$. For any $r$ as above use $X=u^{-1}X_0$ in the target equation. Its left-hand side is a nonzero character factor times $F(X_0)$, so $\chi_h(r)\ne0$. If two lifts have the same restriction $u$, the left-hand side for $X_0$ is identical for both and cancellation of $F(X_0)$ gives the same value $\chi_h$. Denote this common value by $\chi(u)$.

For two restrictions $u,v$, put $a(u)=\xi(\overline{\det(u^{-1})})$. This factor is multiplicative because determinant and reduction are multiplicative on integral units. Applying the target equation twice gives
$$
a(uv)F(uv X_0)
=a(v)\chi(u)F(v X_0)
=\chi(u)\chi(v)F(X_0).
$$
The equation for a lift of $uv$ gives the same left-hand side and $\chi(uv)F(X_0)$ on the right. Cancelling $F(X_0)$ proves multiplicativity. The lift $1$ has value $1$, completing the proof of the character.

### Identity charts

If $h=1$, each lift belongs to the integral twist level. Thus $n(r)$ is integral and the phase equals $1$. In the original coordinates the last determinant block defining $\lambda_Q$ uses only the ordinary coordinates with indices from $k+j$ to $N_j-1$ in layer $j$. That block depends only on the restriction to the ordinary space. Its determinant is the determinant on the quotient of the ordinary residue space by its first $k+j$ coordinates. This subspace is preserved because the full twist level preserves the cut with the auxiliary coordinates inserted. The quotient determinant is multiplicative and nonzero on the residue of every such lift. For $j=0$, the cut is $k=N_0$, so the quotient has dimension zero and the character is $1$. At layer $m-1$ the extra coordinates are gone and the restriction is the entire integral transformation.

### Lean correspondence

- [`chiInv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L977) defines the lifted value. [`TwChrOk` and `twChiVal_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L104) state the nonzero and multiplicativity conditions and use them to make the projected character.
- [`TargetEquivarianceAtPrime` and `TargetEquivarianceLargeDepths`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainLawXiQ.lean#L20) specify the target equation. [`clXQ_chrOk`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainLawXiQ.lean#L158) chooses depths common to the equation and nonvanishing, then cancels a nonzero value. [`clXQ_chrOk_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainLawXiQF.lean#L22) provides the equation for the bounded twist charts.
- [`twChrOk_one` and `twChrQ_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAux.lean#L41) treat identity charts and assemble the twist character condition.

Status. Source-based reconstruction draft. The ordinary argument uses eventual nonvanishing for the particular chart and a projected level inside the integral group. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
