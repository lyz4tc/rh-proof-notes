# Two equal-dimensional subspaces admit an alternating pairing of corank at most one

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be any field, $V$ a finite-dimensional $K$-space, and $S_1,S_2\subseteq V$ subspaces of the same dimension. There is an alternating bilinear form $\omega$ on $V$ such that the kernel of $S_1\to S_2^\vee$, $x\mapsto\omega(x,-)$, has dimension at most one.

**Proof.** Write $W=S_1\cap S_2$, and choose complements $A$ and $B$ to $W$ in $S_1$ and $S_2$, respectively. Then $S_1+S_2=W\oplus A\oplus B$, and $\dim A=\dim B$. Choose bases $a_i$ and $b_i$ of $A$ and $B$. Set $\omega(a_i,b_j)=\delta_{ij}$ and $\omega(b_j,a_i)=-\delta_{ij}$, with no pairing within $A$ or within $B$.

On a basis $w_1,\ldots,w_m$ of $W$, pair successive vectors in two-dimensional blocks. Set $\omega(w_{2i-1},w_{2i})=1$ and $\omega(w_{2i},w_{2i-1})=-1$, and every other pairing among basis vectors in $W$ zero. Leave one unpaired vector if $m$ is odd. All pairings between $W$ and $A\oplus B$ are zero. Extend the form by zero on an additional complement of $S_1+S_2$ in $V$. Since each ordered pair cancels with its reversal, the form is alternating even in characteristic two.

If $x=w+a\in S_1$ pairs to zero with $S_2$, its values against the $b_i$ force $a=0$. Its values against $W$ then force $w$ into the common-block radical, which has dimension zero or one. This proves the claim.

In the Selmer application the second subspace is the conjugate-dual Selmer space transported to the ordinary cohomology space by the intertwiner. It need not coincide with the first subspace. The conclusion therefore supplies corank at most one for their pairing even when their intersection is proper.

**Lean correspondence.** `exists_alt_corank_le_one` is the result. The source proves it by an induction in `good_of_finrank_eq`, adding rank-two alternating blocks with `good_step`. The adapted bases above give the same conclusion directly. Source-based reconstruction. [Adding an alternating block](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsAlternatingFormLeftCorankLeOne.lean#L14) · [Equal-dimensional subspaces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsAlternatingFormLeftCorankLeOne.lean#L61) · [Corank at most one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsAlternatingFormLeftCorankLeOne.lean#L108) · [Application to the two Selmer spaces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsElementsSelmerFormsSmallCorank.lean#L266).
