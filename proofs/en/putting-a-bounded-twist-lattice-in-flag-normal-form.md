# Putting a bounded twist lattice in flag normal form

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $P$ be a finite place of a number field $E$ with rational prime norm $q$. Assume $q$ has valuation one at $P$, and set $A=\mathcal O_{E,P}$. Fix $N,c,j\ge0$, an ordinary subspace $W=E^N$ in $E^{N+c}$, and the standard lattice $L=A^{N+c}$. The group $\mathcal R$ called `R1` consists of invertible maps preserving the flag obtained by appending one extra coordinate at a time. Its action is the identity on the successive one-dimensional quotients above $W$, and it fixes the first extra basis vector when $c>0$.

Suppose $h\in\mathrm{GL}_{N+c}(E)$ is bounded in the sense of `TwBdd`,
$$
h^{-1} L\subseteq L,\qquad q^j h L\subseteq L.
$$
Then some $r\in\mathcal R$ makes $h'=rh$ have normal form `TwNF`. More explicitly, write $(x,y)\in W\oplus E^c$ and choose $y_0$ to be the first extra coordinate, or $0$ if $c=0$. There are integers $-j\le n_i\le0$ for $0\le i<c$ and a vector $z\in A^N$ such that
$$
(x,y)\in h'L\quad\Longleftrightarrow\quad
x-y_0 z\in A^N\quad\text{and}\quad y_i\in q^{n_i}A\ \ (0\le i<c).
$$
The new matrix still obeys `TwBdd`. Moreover, if $J$ is the twist level `JQ` preserving $L$ and the indicated parahoric sublattice, the restriction to $W$ of every element of $\mathcal R\cap h'J(h')^{-1}$ is an integral automorphism of $A^N$. In particular $h'$ is in the same left $\mathcal R$ and right $J$ double coset as $h$, with integral projected level.

### A flag basis for the bounded lattice

Let $M=hL$, so $L\subseteq M\subseteq q^{-j}L$. Number all coordinates $0,\ldots,N+c-1$. Intersect $M$ with the span of the basis vectors up to coordinate $l$ and project this intersection to coordinate $l$. The image is an $A$-submodule of $E$ between $A$ and $q^{-j}A$. Since $q$ is a uniformizer, it is $q^{-k_l}A$ for some $0\le k_l\le j$. One can see this by taking the minimum valuation among its nonzero elements. It is a bounded set of integer valuations containing $0$, and an element of minimal valuation generates the whole image over $A$.

Choose $b_l$ in the indicated intersection with coordinate $q^{-k_l}$ at $l$. The vectors form an upper triangular matrix of columns with nonzero diagonal. Every vector of $M$ is a linear combination of these columns with coefficients in $A$: starting at the largest coordinate, subtract its multiple of $b_l$ to cancel that coordinate, staying in $M$, and continue downwards. Conversely every such combination is in $M$. The coefficients are unique because the triangular matrix is invertible over $E$. More particularly, when a vector of $M$ is supported strictly below coordinate $l$, its coefficient tuple in this basis also vanishes from coordinate $l$ onwards. This follows by the same descent from the largest possibly nonzero coefficient.

### Changing the extra columns while fixing the first extra vector

Keep $b_l$ as the $l$th column for $l<N$. For every extra coordinate $l\ge N$ multiply that column by $q^{k_l}$ to make its diagonal entry $1$. If $c>0$, the first scaled extra column has the form
$$
q^{k_N}b_N=e_N+v
$$
with $v\in W$. Both summands in $v=q^{k_N}b_N-e_N$ belong to $M$, since $e_N\in L\subseteq M$. Expanding $v$ in the triangular basis gives coefficients $\zeta_l\in A$ for $l<N$ and zero coefficients for $l\ge N$, because $v\in W$. Let $z=(\zeta_l)_{l<N}\in A^N$. Replace the first scaled extra column by $e_N$. This replacement subtracts $v$, so adds no entries below the diagonal. If $c=0$, take $z=0$ and omit each step involving an extra column.

Let $C$ be the matrix of the resulting columns. It is invertible and preserves the flag in both directions by upper triangularity. Its extra diagonal entries are $1$, and it fixes the first extra vector. Therefore $r=C^{-1}$ belongs to $\mathcal R$. A vector $(x,y)$ is in $rM$ precisely when $C(x,y)$ belongs to $M$. Expressing $C(x,y)$ in the original triangular basis $(b_l)$, its ordinary coefficients are $x_l-y_0\zeta_l$. The extra coefficient at $l=N+i$ is $q^{k_{N+i}}y_i$ because the subtracted vector $v$ has no extra coefficients. Membership in $M$ means exactly that all these coefficients are integral. Taking $n_i=-k_{N+i}$ gives the claimed normal form.

### What the normal form preserves

If the entries of $(x,y)$ are integral then $x-y_0z$ is integral, and $y_i\in q^{n_i}A$ since $n_i\le0$. Thus $L\subseteq h'L$. Conversely in normal form $q^j y_i$ is integral for all $i$, since $n_i\ge-j$. Since $z$ is integral, $q^j x=q^j(x-y_0z)+q^jy_0z$ is integral as well. Hence $h'L\subseteq q^{-j}L$, which proves the two chart bounds for $h'$.

Finally $h'L\cap W=A^N$, as is seen by taking $y=0$ in the normal form. An element of $\mathcal R\cap h'J(h')^{-1}$ and its inverse preserve both $h'L$ and $W$. They therefore preserve $A^N$ on restriction to $W$, proving the integral projected level. The double coset statement follows from using only the left factor $r$.

### Lean correspondence

- [`TwBdd` and `TwNF`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L15) give the bound and the asserted lattice form. [`ideal_form` and `herm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedNormLattice/IdealForm.lean#L12) construct the bounded flag basis.
- [`comb_reflect` and `combinationEquiv_inv_mem_unipotentFlagGroup`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedNormLattice/CombinationEquivInvMemUnipotentFlagGroup.lean#L25) recover the triangular coefficients and check membership in the first parabolic. [`twNormLat_main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedNormLattice/TwNormLatMain.lean#L10) constructs the normal form.
- [`bdd_of_nf` and `prX_le_of_nf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/TwistedNormLattice/PrXLeOfNf.lean#L33) give the new bounds and projected integrality. [`twNormRep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwAux.lean#L15) applies the calculation at a twist place of the column chain.

Status. Source-based reconstruction draft. Transferring nonvanishing of the unfolded function to the new chart representative requires the double-coset transformation law. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
