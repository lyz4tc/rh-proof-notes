# A finite coefficient model retains the chosen Hodge embedding

**Status: Source-based reconstruction draft.** This completes the small field-of-definition and embedding step in `LimitTop.closedAtL`. The [compact-group coefficient-field proof](https://github.com/lyz4tc/rh-proof-notes/blob/main/proofs/en/a-compact-group-representation-uses-one-finite-coefficient-field.md) already proves the Baire argument. The [fixed-embedding Hodge-jump reconstruction](how-linked-frames-recover-the-hodge-jumps-at-one-embedding.md) handles the period comparison on a chosen model. Neither argument is repeated here.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## The two field requirements

Let $E$ be a number field with algebraic closure $\Omega$, let $w$ be a place above $\ell$, and fix a valuation ring $A$ of $\Omega$ above $w$. Put $G_E=\operatorname{Gal}(\Omega/E)$ and let $D$ be the decomposition group. Use the inducing bridge $\mathcal B$ from the closure statement, with isomorphism $e:D\simeq G_K$ for its local field $K$, distinguished finite coefficient field $L_0\subseteq\overline{\mathbb Q}_\ell$, and map $j_E:E\hookrightarrow K$ induced by the bridge's embedding of $\Omega$. Write $\jmath:G_K\to G_E$ for the inverse of $e$ followed by the inclusion of $D$.

Suppose $r:G_E\to\mathrm{GL}_a(\overline{\mathbb Q}_\ell)$ is the continuous semisimple target, and $J(\tau)$ is the prescribed jump multiset for each ring embedding $\tau:E\to\overline{\mathbb Q}_\ell$. The particular output we need is the jump condition at a given $\tau$ in `ClosedAtL`. Its hypotheses provide a finite coefficient field $L_*$ and an embedding $\eta_*:K\to L_*$ over $\mathbb Q_\ell$ that induces $\tau$, meaning
$$
 \tau=\operatorname{incl}_{L_*}\circ\eta_*\circ j_E.
$$
We must find a de Rham finite model of $r|_D$ and a local embedding into its coefficient field inducing that same $\tau$, with jump multiplicities equal to $J(\tau)$. Obtaining a finite model over an arbitrary field of definition of $r$ would not give the needed embedding into that field. Conversely, $L_*$ is given to carry $\eta_*$, not to carry the matrices of $r$.

## From coefficient containment to an honest representation

Apply the compact-group theorem to the **global** group $G_E$, the continuous matrix entries of $r$, and the prescribed finite field $L_*L_0$. It gives a finite $L\subseteq\overline{\mathbb Q}_\ell$ containing $L_*$ and $L_0$ and all matrix entries of every $r(g)$. More explicitly, the Baire result first supplies a finite field of entries; `exists_finExt_entries_mem` forms its compositum with the prescribed $L_*L_0$. Thus the coefficient inclusions are actual inclusions inside the chosen algebraic closure. No period or semisimplicity argument is involved in this choice.

For every $g$ let $M(g)\in M_a(L)$ be the entrywise lift of $r(g)$, using the containment. These lifts give a continuous representation over $L$, rather than just a family of matrices. Indeed, the entrywise map $M_a(L)\to M_a(\overline{\mathbb Q}_\ell)$ is injective. The images of $M(g)M(g^{-1})$ and $M(g^{-1})M(g)$ are both $I$, so both products already equal $I$ over $L$. This gives an element $r_L(g)\in\mathrm{GL}_a(L)$ with inverse $M(g^{-1})$. By the same injectivity, $M(1)=I$ and $M(gh)=M(g)M(h)$. The matrix entries of $r_L$ are continuous in the induced topology of $L$, by continuity of the original entries and the fact that their values land in $L$. Extending coefficients recovers $r$ as an equality of homomorphisms in the chosen basis, not merely up to conjugacy.

Restrict $r_L$ to $D$, and transport it along $e$ to get the local $L$-representation $R_L$ of $G_K$. Its matrices are $r_L(\jmath(g))$ for $g\in G_K$. On coefficients in $\overline{\mathbb Q}_\ell$ these are exactly the matrices of $(r\circ\jmath)(g)$. Meanwhile $L_0\subseteq L$ is the other condition in the definition of an `IsModel` for the bridge, in addition to the requirement that base change gives $r|_D$. This is why the same model can serve in the local period construction and in its final existential conclusion.

## Evaluating the closed jump condition

At this point `closed_of_cover` applies to the pulled-back plain-trace cover and the exact matrix model just constructed. Its inputs are the continuous semisimple target and its plain linear trace approximations by the specified semistable family with jumps $J$, transported to $G_K$. For every finite model under consideration, the period result provides de Rhamness and the count identity
$$
 \operatorname{mult}(R_L,\eta,n)=
 J\bigl(\operatorname{incl}_L\circ\eta\circ j_E\bigr).\operatorname{count}(n)
 \qquad(\eta:K\to L,\ n\in\mathbb Z).
$$
It also gives crystallinity of the model if all the seeds are crystalline. These are inputs to the packaging step here, not consequences of compactness or of the entrywise descent.

To read the identity at the originally prescribed $\tau$, let $\eta$ be the composite $K\xrightarrow{\eta_*}L_*\hookrightarrow L$. The identity $\operatorname{incl}_L\circ(L_*\hookrightarrow L)=\operatorname{incl}_{L_*}$ gives
$$
 \operatorname{incl}_L\circ\eta\circ j_E
 =\operatorname{incl}_{L_*}\circ\eta_*\circ j_E=\tau
$$
as maps on $E$. Therefore the count identity is exactly the requested equality at $\tau$ and at every $n$, with no permutation or reselection of the embedding. Together with the de Rham model and the displayed equality of embeddings, this supplies the witnesses required by `IsJumpsAt`.

In the two other outputs of `ClosedAtL` no $\eta_*$ is prescribed. For the existence of a de Rham model one simply makes the coefficient choice with $L_*=L_0$ and uses de Rhamness of that model. For the separate implication about crystalline seeds one can again take $L_*=L_0$ and use the crystalline conclusion of the period comparison. The proof does not start with a crystalline target, and the coefficient step is not a claim that an independently chosen target field realizes every local embedding.

## Lean anchors and boundary

- [`ClosedAtL`, exact hypotheses and three outputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Statements/EllipticCurveLevels/ClosedAtLConclusionOfMem.lean#L105-L118); [definitions of `IsModel`, `IsInduced` and `IsJumpsAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/FiniteDimensionalWdSpace.lean#L182-L203).
- [Compact coefficient field with prescribed finite extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CompactGroupRepDefinedOverFiniteExtension.lean#L121-L128), used with $L_*L_0$ in [`ClosedAtL` lines 73–82](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ClosedAtL.lean#L73-L82). [`exists_model_of_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/DeRhamGaloisSideIffDeRhamAtLocalEmbedding.lean#L14-L36) constructs the matrix lifts and verifies their unit, homomorphism and topology properties; no Baire step is hidden in that theorem.
- [Bridge map and jump function](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ClosedAtL.lean#L30-L36), [application of the period theorem to the resulting model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ClosedAtL.lean#L84-L101), and [extension of the prescribed embedding and existential conclusions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ClosedAtL.lean#L102-L117).
- [Plain cover construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CoverExists.lean#L21-L116) uses the same lattice/transition strategy as the joint cover, but its initial approximation is of the plain global trace alone. [Cover pullback](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CoverPull.lean#L14-L60) keeps the coefficient fields, bases and transition matrices, just precomposing the actions with $\jmath$. The deeper period argument and the separate joint Weil trace branch are outside this note.
