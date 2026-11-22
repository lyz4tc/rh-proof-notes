# The normalized factorial pairing dualizes the two Weyl lattices

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $r\ge n\ge0$, and let $\nu=(\nu_1,\ldots,\nu_n)$ be a nonincreasing list of nonnegative integers. In the polynomials in an $r\times n$ matrix $Y$, let $\nabla_\nu(\mathbb Z)$ be those of column multidegree $\nu$ with integer coefficients that satisfy the polynomial identities for adding an earlier column to a later one. Let $\Delta_\nu(\mathbb Z)$ be the integral span of the words of divided row operators on the product $h_\nu$ of leading minors with exponents $\nu_j-\nu_{j+1}$, where $\nu_{n+1}=0$. These are the [dual Weyl and Weyl constructions](why-the-weyl-words-span-in-characteristic-zero.md). Work inside their common rational space $\nabla_\nu(\mathbb Q)$ and use the normalized factorial pairing
$$
\langle F,G\rangle_\nu=
\frac{\sum_\alpha \alpha!\,[Y^\alpha]F\,[Y^\alpha]G}
{\sum_\alpha \alpha!\,([Y^\alpha]h_\nu)^2}.
$$
Then $\nabla_\nu(\mathbb Z)$ consists exactly of the elements pairing integrally with every element of $\Delta_\nu(\mathbb Z)$, and $\Delta_\nu(\mathbb Z)$ consists exactly of the elements pairing integrally with every element of $\nabla_\nu(\mathbb Z)$. In the square case this is the integral pairing input for the branching map.

### The highest-weight vector represents evaluation at the identity frame

Let $I_{r,n}$ be the first $n$ columns of the $r\times r$ identity. The column operations on the set where all leading minors are nonzero suffice to make a matrix lower triangular in its first $n$ columns. In column $j$ subtract a linear combination of the earlier columns to clear the first $j-1$ entries. The leading $(j-1)\times(j-1)$ matrix of those columns is invertible because the earlier operations preserve its determinant. Thus any column-invariant polynomial is determined by its restriction to $Y_{as}=0$ for $a<s$. This argument works over any infinite field. If an invariant polynomial vanishes at these lower triangular matrices, it vanishes on the set of nonzero leading minors. Multiplying it by the product of the leading minors then gives a polynomial vanishing on every matrix, so it is zero.

The row multidegree of $h_\nu$ is $(\nu_1,\ldots,\nu_n,0,\ldots,0)$. Take the component of $F\in\nabla_\nu(\mathbb Q)$ of this same row multidegree. It remains column-invariant since column additions preserve row multidegrees. On lower triangular matrices its monomials have matching row and column degrees, hence only diagonal entries. Indeed
$$
\sum_{a,s}(a-s)\alpha_{as}=0
$$
by the matching degrees, and each term on the lower triangular support is nonnegative. The surviving diagonal monomial is $\prod_j Y_{jj}^{\nu_j}$, with coefficient $F(I_{r,n})$. The leading-minor product restricts to that monomial as well. By the preceding injectivity of restriction, this row component is $F(I_{r,n})h_\nu$. Since the factorial pairing pairs $h_\nu$ only with that row component and $h_\nu(I_{r,n})=1$, we have $\langle F,h_\nu\rangle_\nu=F(I_{r,n})$.

### Integral pairings detect the lower triangular coefficients

Write $D_{ab}^{(u)}$ for the coefficient of $t^u$ when $t$ times row $a$ is added to row $b$. Its adjoint is $D_{ba}^{(u)}$ by the [factorial substitution identity](the-point-value-pairing-is-positive-and-unitary.md). The adjoint of a word reverses its order and interchanges its two row indices at each letter. Therefore the pairing of a polynomial $F\in\nabla_\nu(\mathbb Q)$ with the Weyl word $D h_\nu$ is $(D^\ast F)(I_{r,n})$. If $F$ has integral coefficients, the operators and evaluation preserve integrality, proving one inclusion.

Conversely suppose these pairings are integers. Consider a monomial on the lower triangular entries of column degree $\nu$. Set the diagonal entries to one and leave a variable $t_{as}$ in every position $a>s$ of the first $n$ columns. The coefficient of the specified off-diagonal exponents in this restriction is the original monomial coefficient. The column degrees determine the missing diagonal exponents uniquely. This restriction of $F$ is obtained by evaluating $F$ at the first $n$ columns of
$$
\prod_{s=1}^n\prod_{a>s}(1+t_{as}E_{as}),
$$
where $E_{as}$ is the matrix unit and the displayed factors are written with their source column $s$ increasing from left to right. All cross terms in the product vanish because the column of a left factor is at most the column of a right factor, whose row strictly exceeds its column. Taking the coefficients of the separate $t_{as}$ is exactly the evaluation at $I_{r,n}$ of a word of the $D_{sa}^{(u)}$. In the operator composition the order of the factors is reversed, since substituting $Y\mapsto AY$ in $F(BY)$ gives $F(BAY)$. This coefficient is consequently the pairing of $F$ with an integral Weyl word, by using the adjoint word. Thus all lower triangular coefficients of $F$ are integers.

To deduce full coefficient integrality, choose the least positive integer $d$ for which $dF$ has integral coefficients. If $p$ divides $d$, the reduction of $dF$ modulo $p$ is a nonzero polynomial by minimality of $d$. The column invariance identities have integral coefficients and still hold for this reduction over an algebraic closure of $\mathbb F_p$. Every lower triangular coefficient reduces to zero since it was an integer in $F$ and was multiplied by $d$. The lower triangular restriction of the reduction is zero. The column elimination argument over the infinite algebraic closure implies the whole reduction is zero, a contradiction. Hence $d=1$ and the integral polynomial belongs to $\nabla_\nu(\mathbb Z)$.

### Duality in the reverse direction

The lattice $\Delta_\nu(\mathbb Z)$ is a subgroup of the finite rank free abelian group on the monomials of column multidegree $\nu$, so it is free of finite rank. Its rational span is the whole space by [characteristic-zero spanning](why-the-weyl-words-span-in-characteristic-zero.md). The pairing is nondegenerate by positivity. If $v_1,\ldots,v_D$ is a basis of this lattice, the rational dual basis $v_1^\ast,\ldots,v_D^\ast$ for the pairing forms a basis of its dual lattice, since coordinates in this dual basis are the pairings with $v_j$. The double dual therefore has basis $v_1,\ldots,v_D$ again. Since the first part identified the dual with $\nabla_\nu(\mathbb Z)$, the reverse duality follows.

### Lean correspondence

- [`CoeffWord`, `FockQHW` and `FockQWordAdj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/StatementE.lean#L50) give the coefficient extraction, highest-weight evaluation and adjoint word. [`fock_space_highest_weight`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/FockQHW.lean#L24) proves the evaluation using the highest row weight, and [`coefficient_word`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PieriBlockIdeals/PieriColumnMinors/LrfcApplyWordAppendSingle.lean#L512) identifies the word in descending order of operator indices.
- [`lower_triangular_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PieriBlockIdeals/PieriColumnMinors/LowerTriangularIntegral.lean#L44) proves the integral coefficient test by subtracting integral bideterminants with matching monic leading monomials. The reduction argument above proves the same conclusion.
- [`nabla_eq_dual_weyl_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/CoefficientsModP/WeTransposeWordTransposeWord.lean#L74) proves the first duality by these tests. [`weyl_eq_dual_nabla_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/CoefficientsModP/WeTransposeWordTransposeWord.lean#L246) takes the double dual. [`FactDelDualNabla`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/DataCoeff.lean#L126) states the square case normalized by the highest-weight pairing.

Status. Source-based reconstruction draft. The coefficient-integrality step is proved here by reduction modulo a prime and column elimination. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
