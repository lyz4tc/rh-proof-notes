# Enlarging coefficients preserves the local Weil–Deligne parameter

**Status: Source-based reconstruction draft.** The argument follows the coefficient-coordinate decomposition and the comparison of the specialized complex spaces in the pinned source. No Lean rebuild.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement

Fix a prime $\ell$, an identification $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$, a number field $E$ with algebraic closure $\Omega$, and a valuation ring $A$ of $\Omega$ above a finite place $w$ of $E$. Fix the project's local period package $P$ and an inducing bridge $B$ at this place, identifying the decomposition group with $G_K$ for its finite local field $K/\mathbb Q_\ell$. Use the same bridge, its topological commutative $\mathbb Z_\ell$-algebra and the same $\iota$ throughout.

Let $L_1\subseteq L_2$ be finite coefficient fields inside $\overline{\mathbb Q}_\ell$, and let $r_1$ be a rank-$m$ matrix representation of the decomposition group over $L_1$. Set $V_i=L_i^m$, with actions $\rho_i$ via the bridge, where the matrices of $\rho_2$ are obtained by applying the inclusion to those of $\rho_1$. If $\rho_1$ is potentially semistable for $P$, then so is $\rho_2$. The complex Frobenius-semisimplified Weil–Deligne parameters `wdPst` of $\rho_1$ and $\rho_2$ are equal as isomorphism classes, including monodromy. There is no irreducibility assumption, and the local field $K$ is not enlarged.

Write $F_{\mathrm{ur}}$ for the maximal unramified subfield of the coefficient algebraic closure. In this proof $D_i$ denotes the potentially semistable period space in $V_i\otimes_{\mathbb Q_\ell}B_{\mathrm{st}}(P)$, whose elements are fixed by the Galois group of some finite local extension. We use the underlying $F_{\mathrm{ur}}$-space, equipped also with its $L_i$-action and the operators from the period factor. The complex Weil–Deligne space is the specialization `WDSpace` using the two embeddings induced by $\iota$, from $L_i$ and from $F_{\mathrm{ur}}$. In particular the canonical maps $\operatorname{wdMk}_i:D_i\to W_i$ are additive, balance both actions against the corresponding complex scalars, and their images span.

## Coordinates over the smaller field

Choose a basis $b_1,\ldots,b_t$ of $L_2/L_1$. Let $f:V_1\to V_2$ be entrywise inclusion and $\pi_j:V_2\to V_1$ the coordinate projections for this basis, so
$$
v=\sum_j b_j f(\pi_j v).
$$
Because the matrix entries acting on $V_2$ lie in the image of $L_1$, $f$ and every $\pi_j$ commute with Galois, with the correct source and target. For example, to compute $\pi_j(Mv)$ for such a matrix $M$, distribute $M$ over the displayed sum and compare the $b_j$ coefficients. This gives $\pi_j(Mv)=M\pi_j(v)$.

Tensor with the identity on $B_{\mathrm{st}}(P)$. An element of the large tensor product that is fixed by an open Galois subgroup has each coordinate fixed by that subgroup. Conversely a finite list of coordinates, each fixed by the group of a finite local extension, is fixed simultaneously after taking the compositum of those extensions. Thus the coordinate decomposition identifies the underlying $F_{\mathrm{ur}}$-space of $D_2$ with $D_1^t$. This agrees with the $F_{\mathrm{ur}}$ action because coordinate projections act only on $V_2$. The dimensions over $F_{\mathrm{ur}}$ and over $\mathbb Q_\ell$ on the representation side both multiply by $t$. Hence the dimension equality defining potential semistability is preserved. This is the argument of `PstExt.isPst_enlarge`.

## Same specialized parameter

The map $f\otimes 1$ restricts to an additive map $T:D_1\to D_2$ over the inclusion $L_1\subseteq L_2$. It preserves the action of $F_{\mathrm{ur}}$ and commutes with local Galois action, Frobenius and monodromy. For the period operators this can be checked on pure tensors, as $f$ acts on the representation factor and the period action on the other. For the Weil operator, use the product of the local Galois action and the appropriate signed inverse Frobenius power. Intertwining an invertible Frobenius also intertwines its inverse. This is the same signed exponent on both sides because the bridge and place are fixed.

The specialization of $T$ is a complex-linear $\Phi:W_1\to W_2$ sending $\operatorname{wdMk}_1(x)$ to $\operatorname{wdMk}_2(Tx)$. The scalar relations respect this formula since both maps $L_i\to\mathbb C$ are restrictions of the same $\iota$ and the $F_{\mathrm{ur}}$ structure is unchanged. The tensor-coordinate decomposition above also holds inside $D_2$: if $\pi_{j,D}$ is the period map induced by $\pi_j\otimes1$, then
$$
\operatorname{wdMk}_2(y)
 =\sum_j \iota(b_j)\,\Phi\bigl(\operatorname{wdMk}_1(\pi_{j,D}y)\bigr)
 \qquad(y\in D_2).
$$
The spanning property of $\operatorname{wdMk}_2$ proves surjectivity. Potential semistability on both sides gives $\dim_{\mathbb C}W_i=\dim_{L_i}V_i=m$. Thus $\Phi$ is an isomorphism. The spanning property on the source extends the period identities to all of $W_1$: $\Phi$ intertwines the unsimplified Weil operators and monodromy. Finally semisimplification respects this intertwining. Conjugating by $\Phi$ preserves commutation and the nilpotent part of each Weil endomorphism; uniqueness of its semisimple part gives the indicated isomorphism after Frobenius semisimplification, with unchanged monodromy. In the general Lean comparison lemma monodromy may match up to a nonzero scalar; this application takes that scalar to be $1$.

In particular, any two finite potentially semistable models of the same decomposition-group matrices can be compared in the finite compositum $L_1L_2$. Their enlarged matrices coincide, hence their complex parameters coincide. This is the missing justification for the compositum step in the companion split-comparison draft.

## Source correspondence and remaining inputs

- [`mem_Dpst_coord`, `dpstCoord`, and `isPst_enlarge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IsPotentiallySemistableCoefficientFieldEnlarge.lean#L37-L96) establish the coordinate decomposition and dimension equality.
- [`isFrobSS_wdRep`, `wdPst_eq_of_map`, `mem_span_dQ`, and `wdPst_enlarge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/WeilDeligneParamAboveLIndependentLocalEmbedding.lean#L241-L355) establish the specialized comparison. The raw maps act on the period spaces; the isomorphism is only asserted after complex specialization.
- The period-space inputs used here are the `mem_Dpst` membership criterion (fixed over some finite local extension), `span_wdMk` (the specialized period symbols span), and `LetterDim.finrank_wdSpace` (for potentially semistable $V/L$, the complex dimension equals $\dim_L V$). They are invoked in the linked proofs with the same $P,\iota$ and local bridge; the rank comparison of this note does not reprove the dimension of the specialized space or its period-ring foundations. Expand the latter starting with the exact `LetterDim.finrank_wdSpace` used in `wdPst_eq_of_map`.
- [`wdAt_of_model`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/PositivityTheory/AutomorphicForms/PublishedInputs/RealGaloisRepresentations/IwahoriSphericalTransfer/WdRelOfFrobSS.lean#L17-L35) applies this result in the split transport used by `holdsS_all_phi`.
