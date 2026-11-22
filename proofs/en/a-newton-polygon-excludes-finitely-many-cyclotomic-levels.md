# A Newton polygon excludes finitely many cyclotomic levels

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $O$ be a discrete valuation ring with fraction field of characteristic zero and residue characteristic a prime $\ell$. Let $v$ be its additive valuation with $v(\varpi)=1$, where $\varpi$ is a uniformizer, and let $v_\ell=v/v(\ell)$. Take a polynomial $f\in O[X]$ with a nonzero coefficient $a_w$ at degree $w$. There is a set of at most $w+v(a_w)$ positive integers $k$ such that, outside the set, the following holds for every injective local map of discrete valuation rings $O\to O'$ and every primitive $\ell^k$-th root $\zeta$ in $O'$:
$$
 f(\zeta-1)\ne0,\qquad v_\ell(f(\zeta-1))
 \le v_\ell(a_w)+\frac{w}{\varphi(\ell^k)}.
 \tag{1}
$$
The valuation in the target is again normalized by the value $1$ on $\ell$.

First, $\zeta$ reduces to $1$ in residue characteristic $\ell$. For $b$ prime to $\ell$, the quotient $(1-\zeta^b)/(1-\zeta)=1+\cdots+\zeta^{b-1}$, with $1\le b<\ell^k$, reduces to $b$ and is a unit. Use
$$
 \ell=\Phi_{\ell^k}(1)=\prod_{1\le b<\ell^k,\ (b,\ell)=1}(1-\zeta^b)
$$
to obtain $v_\ell(\zeta-1)=1/\varphi(\ell^k)$. Moreover the normalized valuation on the coefficients is unchanged by the local inclusion. Indeed the image of $\varpi$ has some positive valuation $e$, every unit maps to a unit, and both the numerator and denominator in $v/v(\ell)$ scale by $e$.

For any real $t>0$ consider the minimum over nonzero coefficients of $v_\ell(a_i)+it$. Its exceptional slopes are those at which at least two indices attain the minimum. We bound the number of these slopes independently of $\deg f$. If $t<t'$, any minimizing index at $t$ is at least any minimizing index at $t'$, by comparing the two inequalities for the minimum. The intercept $v_\ell(a_i)$ is strictly increasing as one passes through distinct minimizing indices in order of increasing $t$: if indices decrease from $i$ to $j$, then $v_\ell(a_j)-v_\ell(a_i)\ge(i-j)t>0$. Two distinct indices minimizing at a common slope also have distinct intercepts, with the larger index having the smaller intercept. Thus among the minimizing indices with $i>w$, all intercepts are distinct and lie strictly below $v_\ell(a_w)$, since $v_\ell(a_i)+it\le v_\ell(a_w)+wt$. Measured in the integral valuation there are at most $v(a_w)$ such intercepts. The remaining minimizing indices belong to $\{0,\ldots,w\}$. The number of different slopes with multiple minima is therefore at most $w+v(a_w)$. For example, at each such slope the largest minimizing index becomes smaller as one passes through the slope, and the last slope still has a smaller minimizing index available.

The numbers $t=1/\varphi(\ell^k)$, $k\ge1$, are pairwise distinct. At a nonexceptional one the polynomial evaluation has a unique term of least valuation, so that term determines the valuation of the sum by the ultrametric inequality. Its valuation is at most the value of the degree-$w$ term, proving (1). The set of bad levels depends only on the original coefficient valuations. This is why the same good level works after replacing $\zeta$ by any primitive power.

For a finite family of polynomials with witnesses $w\le W$, $v(a_w)\le V_j$, take the union of these exceptional sets. Its cardinality is at most $\sum_j(W+V_j)$. Every good level satisfies (1) simultaneously for the family, with the error at most $W/\varphi(\ell^k)$.

## Lean correspondence

- [normalizedValuation_primitiveRoot_prime_pow_sub_one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormalizedValuationPrimitiveRootPrimePowSubOneStatement.lean#L5) computes the slope. [card_double_min](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ValuationPolynomialAtRootOfUnitySubOne.lean#L10) counts repeated minima and [sum_unique_min](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ValuationPolynomialAtRootOfUnitySubOne.lean#L119) evaluates a sum with one minimum.
- [value_at_root_sub_one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ValuationPolynomialAtRootOfUnitySubOne.lean#L138) proves (1). [exists_levels](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsLevelOrderExponentsSmallValuationDetermina.lean#L249) treats a finite family.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
