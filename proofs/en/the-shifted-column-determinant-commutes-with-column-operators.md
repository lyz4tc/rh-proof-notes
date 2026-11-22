# The shifted column determinant commutes with column operators

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $D_{ab}$ for $1\le a,b\le n$ be endomorphisms of a vector space over $\mathbb Q$ satisfying
$$
[D_{kl},D_{ab}]=\delta_{la}D_{kb}-\delta_{kb}D_{al}.
$$
For an integer $u$, define the Capelli determinant with column order indicated by the product
$$
C(u)=\sum_{\alpha\in\mathfrak S_n}\operatorname{sgn}(\alpha)
\prod_{j=1}^{n}\bigl((u+j-1)\delta_{\alpha(j),j}-D_{\alpha(j),j}\bigr).
\tag{1}
$$
Endomorphisms are multiplied by composition, so the rightmost factor acts first. Then $C(u)$ commutes with every $D_{kl}$. Also if $D_{ab}v=0$ for $a<b$ and $D_{aa}v=\mu_av$, then
$$
C(u)v=\prod_{j=1}^n (u+j-1-\mu_j)\,v.
\tag{2}
$$
The operator in the branching proof uses $D_{ab}=\sum_{i=1}^{n}X_{ia}\partial_{X_{ib}}$ on polynomials in an $n\times n$ matrix $X$ and an extra row $z$. It has integral coefficients, commutes with every row substitution on $X$, and preserves polynomials of prescribed total column multidegree in $(X,z)$ that are invariant under adding any earlier column to a later column. It preserves each last-row exponent separately.

### Proof of commutation

Put $F_j(a,b)=(u+j-1)\delta_{ab}-D_{ab}$. For a list of column labels $\beta(1),\ldots,\beta(n)$, let $P(\beta)$ be the alternating sum in (1) with $j$ in the second argument replaced by $\beta(j)$, keeping the factor shifts $u+j-1$. We first show that swapping adjacent column labels reverses the sign. Pair the terms for permutations $\alpha$ obtained from each other by swapping their values in the two adjacent positions $j,j+1$. If those row labels are $a,c$ and the column labels are $b,d$, the adjoining pair of factors occurs in the difference
$$
F_j(a,b)F_{j+1}(c,d)-F_j(c,b)F_{j+1}(a,d).
$$
Its value plus the corresponding expression with $b,d$ exchanged is zero. Indeed, put $F=F_j$ and use $F_{j+1}(a,d)=F(a,d)+\delta_{ad}$. The resulting sum is
$$
[F(a,b),F(c,d)]+[F(a,d),F(c,b)]
+F(a,b)\delta_{cd}-F(c,b)\delta_{ad}
+F(a,d)\delta_{cb}-F(c,d)\delta_{ab}.
$$
The two commutators expand to $\delta_{bc}D_{ad}-\delta_{ad}D_{cb}+\delta_{dc}D_{ab}-\delta_{ab}D_{cd}$. The terms from the four copies of $-D$ cancel these, and the constant terms from the four copies of $(u+j-1)\delta$ cancel in pairs. This proves the adjacent swap identity. Composing such swaps makes $P$ alternating in the column labels. A repeated column label therefore gives zero.

The commutator with $D_{kl}$ satisfies
$$
[D_{kl},F_j(a,b)]
=\delta_{la}F_j(k,b)-\delta_{kb}F_j(a,l),
$$
as the scalar terms on the right cancel. Applying the product rule for commutators to every term of (1) gives two alternating sums. In the first, the row label $l$ has been replaced by $k$ in each product. In the second, the column label $k$ has been replaced by $l$. For $k=l$ the two sums are the same. For $k\ne l$, the first is zero by pairing row permutations that interchange the two original labels $k,l$, since their resulting products coincide and their signs are opposite. The second is zero by the repeated column label rule. This proves $[D_{kl},C(u)]=0$.

### Eigenvalues and the polynomial action

The term with $\alpha=1$ acts on $v$ by the product in (2). For any other permutation choose the last position $j$ with $\alpha(j)\ne j$. All positions to its right are fixed, so their factors act by scalars. Since $\alpha(j)<j$, the factor at position $j$ is $-D_{\alpha(j),j}$ and kills $v$. Only the identity term survives.

On the matrix polynomial ring the displayed differential operators satisfy the commutator identity by the product rule. Their coefficients and all shifts in (1) are integral. Substitution on the matrix rows commutes with the derivation that replaces a column infinitesimally by another column. Thus each $D_{ab}$ commutes with row substitutions on $X$. It acts only on $X$, preserving each exponent of $z$ and commuting with $z_a\partial_{z_b}$. It follows from the preceding commutator proof that $C(u)$ commutes with the total column derivations $D_{ab}+z_a\partial_{z_b}$. The diagonal ones measure the total column degrees. For $a<b$, adding $t$ times column $a$ to column $b$ acts by the finite exponential of $t(D_{ab}+z_a\partial_{z_b})$ on each polynomial. Hence $C(u)$ preserves the column multidegree and all the required invariances. The same statements hold on the integral polynomials because the operators have integral coefficients and the polynomial identities can be checked over $\mathbb Q$.

### Lean correspondence

- [`bmF`, `bmM`, `bmPi` and `capDet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L12) define (1). [`bmE` and `bmCap`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L30) give its differential realization.
- [`bmA_four` and `bmA_Pi_adj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L619) prove antisymmetry in adjacent column labels. [`bmA_comm_entry` and `capDet_central`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L780) compute and cancel the two commutator sums.
- [`capDet_eigen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L887) proves (2). [`bm_rowAct_comm_bmEL`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L389) and [`bmK_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L2415) check compatibility with the row action and the polynomial Weyl space.

Status. Source-based reconstruction draft. The calculation proves centrality and the scalar formula used for integral branching. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
