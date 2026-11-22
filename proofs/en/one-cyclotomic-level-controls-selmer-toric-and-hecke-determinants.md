# One cyclotomic level controls Selmer, toric and Hecke determinants

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $O_0\to O$ be an injective local map of discrete valuation rings of characteristic zero with residue characteristic $\ell$, a prime. Fix integers $R,M_0,D,n_{\max}\ge0$, two finite sets $I,J$, and nonnegative integers $\mu_x$ for $x\in I$, $v_y$ for $y\in J$. Use $R$ variables $X_i$ and $R$ variables $Y_i$. For all $M\ge M_0$ suppose the following polynomial data are given.

- For each $x\in I$, a polynomial $F_{M,x}$ over $O_0$ has a coefficient of total degree at most $D$ whose integral valuation is at most $\mu_x$.
- For each $y\in J$ there are $f_{M,y},D_{M,y},g_{M,y}$ over $O$ satisfying the [monomial-factor hypotheses](a-monomial-factor-bounds-a-low-coefficient-of-the-specialized-hecke-polynomial.md) with level $M$, coefficient bound $v_y$, and monomial exponents bounded by $n_{\max}$. In particular the difference $f-Dg$ lies in the ideal of the $Y_i$ and the relations $(1+X_i)^{\ell^M}-1$.

Given $\varepsilon>0$, there exist $M\ge M_0$, $1\le k\le M$, and an exponent $e_q<k$ at each of the $2R$ variables such that $\ell^{e_q}/\varphi(\ell^k)\le\varepsilon$. For every injective local extension $O\to O'$ and every primitive $\ell^k$-th root $\zeta\in O'$, put $z_q=\zeta^{\ell^{e_q}}-1$. All the $F_{M,x}(z)$ and $f_{M,y}(z)$ are nonzero and obey
$$
 \begin{aligned}
 v_\ell(F_{M,x}(z))&\le \mu_x/v_{O_0}(\ell)+\varepsilon,\\
 v_\ell(f_{M,y}(z))&\le v_y/v_O(\ell)+\varepsilon .
 \end{aligned}
 \tag{1}
$$
Here $v_{O_0},v_O$ are the respective integral valuations, and $v_\ell$ on $O'$ has $v_\ell(\ell)=1$. In the twist construction the first family comes from Selmer presentation matrices, and the second combines the toric and Hecke linear maps. The bounds are uniform for all primitive roots and thus for both signs and all primitive powers of the selected character.

## Choose the variable exponents first

Apply [the coefficient-pattern argument](a-limit-of-coefficient-valuation-patterns-selects-a-low-monomial.md) to the first polynomial family. It gives a spacing $a$ that works in the variable order with the $X_i$ first and $Y_i$ last. Take $e_i=ai$ for $0\le i<R$ on the $X_i$, and set $s=aR$. Use the maximum $V=\max_y v_y$, or zero for an empty family, in the monomial-factor bound. This fixes $E,W_2$ based on $s$ so that any substituted second-family polynomial has a low coefficient in degree at most $W_2$ with the required bound whenever $M\ge E$ and all the $Y_i$ have exponents at least $E$. Choose their exponents $e'_i=a(R+i)+E$. This maintains spacing $a$ across all variables.

These choices determine a bound $W_1$ in the coefficient-pattern argument. There are arbitrarily large $M$ for which every polynomial in the first family after substitution has a coefficient of degree at most $W_1$ and valuation at most $\mu_x$ in $O_0$. At each such $M\ge E$ the second family has the corresponding witnesses in $O$ with degree at most $W_2$.

## Bound the bad levels before fixing the polynomials

Put
$$
 N=\sum_{x\in I}(W_1+\mu_x)+\sum_{y\in J}(W_2+v_y).
$$
At any $M$ as above the [Newton-polygon estimate](a-newton-polygon-excludes-finitely-many-cyclotomic-levels.md) shows that the union of the bad levels for the specialized one-variable polynomials has cardinality at most $N$. The coefficients of those polynomials may still depend on $M$. The bound on the cardinality depends only on the two sets of coefficient witnesses.

Choose $k_1\ge1$ so large that for every $k\ge k_1$ the exponents $e_q$ are less than $k$, and $\max\{\ell^{e_q},W_1,W_2\}/\varphi(\ell^k)\le\varepsilon$ for every $q$, with the degree bounds imposed also if there are no variables. Choose one of the arbitrarily large admissible $M$ with $M\ge\max\{M_0,E,k_1+N\}$. With the polynomials now fixed at $M$, select $k\in\{k_1,\ldots,k_1+N\}$ outside the at most $N$ bad levels. Evaluating the one-variable substitution at $T=\zeta-1$ is exactly the multivariable evaluation $z_q=\zeta^{\ell^{e_q}}-1$. The Newton-polygon estimate therefore gives (1) simultaneously. Each comparison survives the injective local embeddings since normalized valuations on the coefficients are preserved.

## Lean correspondence

- [order_eval](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsLevelOrderExponentsSmallValuationDetermina.lean#L278) separates the $X_i,Y_i$ exponents, uses the two coefficient witnesses and chooses $M$ before removing the finite exceptional levels.
- [exists_level](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsAuxiliaryPlaceFamilyAtLevelMono.lean#L321) applies this to the two coefficient rings and the level-dependent determinant inputs. [admissibleIndexBoundAllPowers_of_conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AdmissibleIndexBoundAllPowersOfConditions.lean#L92) uses the resulting common $M,k,e_q$ in the twist character construction.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
