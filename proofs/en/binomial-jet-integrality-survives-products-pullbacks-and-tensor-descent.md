# Binomial jet integrality survives products, pullbacks, and tensor descent

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $q$ be prime, $\iota:\mathbb C\simeq\mathbb C_q$ a field isomorphism, $\omega\in\mathbb C_q$, $V$ a complex normed vector space, and $\Lambda\subseteq V$ an additive subgroup. For an infinitely complex-differentiable function $G:V\to\mathbb C$, the assertion `LatInt` means the following. For every finite list $v_1,\ldots,v_k\in\Lambda$, there is a $\mathbb C_q$-linear functional $\mu$ of norm at most one on $C(\mathbb Z_q^k,\mathbb C_q)$. For every index list $j_1,\ldots,j_l\in\{1,\ldots,k\}$ of any length $l\ge0$, it satisfies
$$
 \mu(a\mapsto a_{j_1}\cdots a_{j_l})
  =\iota\!\left(D^lG(0)
      [\iota^{-1}(\omega)v_{j_1},\ldots,\iota^{-1}(\omega)v_{j_l}]\right).
\tag{1}
$$
This includes the constant test for $l=0$. Under this definition, the following operations preserve the bound.

- Finite products on $V$ and finite sums $\sum_j c_j G_j$ with $|\iota(c_j)|_q\le1$.
- Pullback by a continuous complex-linear $A:V'\to V$ if for every $v'$ in the source subgroup $\Lambda'$ there exists $s\in\mathbb Z_{>0}$ prime to $q$ with $sAv'\in\Lambda$.
- Descent from the fourth tensor on four separate copies of $V$ to $G$ on $V$: if $(z_1,z_2,z_3,z_4)\mapsto\prod_{b=1}^4G(z_b)$ satisfies `LatInt` on $\Lambda^4$, then $G$ satisfies it on $\Lambda$. In this application the Lean source takes $V=\mathbb C^{\,g}$.

The same $\iota,\omega$ are used throughout. These are the integral moment operations for the split-prime theta proof. [Moment and lattice definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/LatIntZero.lean#L12) · [Products and sums](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeJetsAreBoundedMomentsProdAndSumStatement.lean#L7) · [Pullback](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeJetsAreBoundedMomentsPullbackStatement.lean#L7) · [Fourth tensor descent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeJetsAreBoundedMomentsOfTensorFourthPowerStatement.lean#L7)

## Proof

### A criterion for a finite list of directions

For each list $v=(v_1,\ldots,v_k)$, take the formal Taylor series at zero of $G(\sum_i z_i v_i)$ in the variables $z_i$, embed its coefficients by $\iota$, and substitute $z_i=\omega\log(1+X_i)$. Denote the resulting series in $X_1,\ldots,X_k$ by $P_{G,v}$. The coefficient of each Taylor monomial uses the repeated derivative along its directions divided by the product of factorials. The transformed series are defined formally, since all logarithm series have zero constant term.

The binomial moment identity follows from
$$
 \sum_{j\ge0}\binom{a}{j}X^j=(1+X)^a=\exp(a\log(1+X))
 \quad(a\in\mathbb Z_q).
$$
Indeed the coefficient of any fixed monomial is a polynomial in $a$ with finitely many terms, and the identity holds for nonnegative integers $a$, hence for all $a\in\mathbb Z_q$. If (1) holds, applying $\mu$ coefficient by coefficient to the product $\prod_i(1+X_i)^{a_i}$ gives $P_{G,v}$, by first expanding the exponentials and using (1). Its coefficients are therefore the binomial moments $\mu(\prod_i\binom{a_i}{n_i})$. Each function tested has supremum norm at most one. Conversely if all coefficients of $P_{G,v}$ have norm at most one, [the binomial moment theorem](bounded-binomial-moments-determine-a-p-adic-measure.md) gives a functional $\mu$ of norm at most one with those coefficients as the binomial moments. In the formal identity just used, make the inverse substitution $X_i=\exp(Y_i)-1$. This shows the functional on each monomial in $a$ has exactly the required derivative in (1). Thus `LatInt` is equivalent to integrality of every $P_{G,v}$. The lists and multi-indices can include the empty ones, with the resulting constant test as above. [Mahler polynomial in the derivative data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/LatIntZero.lean#L22)

### Closure operations

The Taylor product works by the Leibniz rule and the subsequent transport is a ring homomorphism. Thus $P_{\prod_j G_j,v}=\prod_jP_{G_j,v}$. If each series is integral, so is the product, since each coefficient is a finite sum of products of integral elements. The same argument applies to a finite sum with integral multipliers $\iota(c_j)$.

For the pullback choose any $v'_1,\ldots,v'_k\in\Lambda'$, and choose positive integers $s_i$ prime to $q$ so $v_i=s_iAv'_i\in\Lambda$. Set $a_i=s_i^{-1}\in\mathbb Z_q^\times$. The Taylor maps for $G\circ A$ in the $v_i'$ directions and $G$ in the $v_i$ directions differ by scaling the $i$-th variable by $a_i$ after coefficient transport. This is realized on $P_{G,v}$ by $X_i\mapsto(1+X_i)^{a_i}-1$, since the resulting logarithm is $a_i\log(1+X_i)$. Each substituted series has integral coefficients and zero constant term, so the new series $P_{G\circ A,v'}$ is integral. This proves the pullback criterion for every list.

For descent from the fourth tensor, choose $v=(v_1,\ldots,v_k)$ in $\Lambda$. Take the list of length $4k$ in $\Lambda^4$ obtained by putting that list in each block, all other coordinates zero. The transformed Taylor series of the tensor in these directions is the product of four copies of $P_{G,v}$ in disjoint sets of variables. The coefficient of the same multi-index $\nu$ in each of the four sets of variables is $([X^\nu]P_{G,v})^4$. By the assumed bound its norm is at most one, so $|[X^\nu]P_{G,v}|_q\le1$. This holds for every $v,\nu$. The criterion proves the desired descent even when $G(0)=0$. [Four independent blocks](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeJetsAreBoundedMomentsOfTensorFourthPowerStatement.lean#L7)

## Source and verification

The three operations and the quantity bounded were checked against their source statements. The proof uses the equivalent coefficient criterion, with the functional recovered by the linked Mahler theorem. It involves a new list for each pullback or tensor test, exactly as permitted by the quantified moment definition. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
