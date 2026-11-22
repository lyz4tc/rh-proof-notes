# An invariant section gives one rational crystalline basis per layer

**Status: Source-based reconstruction draft.** This joins the invariant-section proof to the known integral Weil-operator comparison. Revised against the pinned Lean statements and call sites. No Lean build.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statements and inputs

Fix a prime $\ell$, a finite extension $K/\mathbb Q_\ell$, and Breuil–Kisin data $\mathrm{bk}$ with power-series ring $\mathfrak S$, variable $X$, and Eisenstein element $E$. Here $A_{\inf}=W(\mathcal O_{\mathbb C_\ell}^{\flat})$, $W_{\rm tilt}=W(\mathbb C_\ell^\flat)$, $R=A_{\rm cris}$, and $B=B_{\rm cris}$. Let $\iota:A_{\inf}\hookrightarrow W_{\rm tilt}$ be the Witt inclusion, $f_I:A_{\inf}\to R$ Witt Frobenius followed by the integral period map, $\jmath:R\hookrightarrow B$ the crystalline inclusion, and $f=\jmath\circ f_I$. The Galois actions are the corresponding entrywise actions, and $f$ sends the integral scalar coefficients $\mathbb Z_\ell$ to their prescribed copy in $B$.

**Invariant basis (`InvU`).** For every compatible period $\tau\in A_{\inf}$ satisfying $\mathrm{bk.IsPer}(\tau)$, $w=f(\tau)$ is a unit in $B$. For any $N,k,d\ge0$ and $\rho:G_K\to GL_d(\mathbb Z_\ell)$, assume the following additional inputs:

1. A Breuil–Kisin frame $F$ of height $N$ for $\rho$: it gives a Witt matrix $T\in GL_d(W_{\rm tilt})$, matrices $A,A'\in M_d(\mathfrak S)$ satisfying $AA'=E^{2N}I$, and an integral Galois cocycle $C_g\in M_d(A_{\inf})$. The defining relations are those in [the pole-clearing note](a-breuil-kisin-frame-has-integral-matrices-after-clearing-its-poles.md#setting-and-result).
2. Matrices $Y,Y'\in M_d(A_{\inf})$ with $\iota(Y)=\iota(\tau)^N T$ and $YY'=\tau^{2N}I$. These are inputs to `InvU`; their existence from the underlying preframe is the separate theorem [`breuilKisinPreframe_bounded_poles`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinPreframeBoundedPolesStatement.lean#L11-L12). After the matrices are given, [`frame_ainf_matrix_frobenius_galois_eqs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrameAinfMatrixFrobeniusGaloisEqsStatement.lean#L12) gives the cleared Galois law
   $$
   \tau^N\rho(g)g(Y)=g(\tau)^N Y C_g
   $$
   in $A_{\inf}$, for every $g\in G_K$. This law is derived from the frame, not postulated as a fourth input of `InvU`.
3. Matrices $Q,Q'\in M_d(R)$ with $QQ'=\ell^{2k}I$ and $f_I(C_g)g(Q)=Q$ for every $g\in G_K$. The Galois identity belongs to the inputs of `InvU`. To **obtain** these matrices in the operator proof, [`SecU`](a-uniform-frobenius-section-over-acris.md) first fixes $k$ for $\ell,K,\mathrm{bk},N$, before any dimension or choice of $A,A'$, and constructs the section pair with its cleared inverse, Frobenius relation, and congruences. This alone does not give Galois invariance. For a crystalline frame (meaning $C_g-I$ is entrywise divisible by $\operatorname{ev}(X)$ for every $g$), [`InvQ`](frobenius-divisibility-kills-the-integral-galois-defect.md) gives precisely the identity $f_I(C_g)g(Q)=Q$ for that section.

Then there is an invertible matrix $U$ in $M_d(B)$ whose columns are invariant for the semilinear action, and which obeys the cleared identity
$$
\rho(g)g(U)=U\quad(g\in G_K), \qquad w^N U=\jmath(f_I(Y)Q).
$$
The theorem does not assert that $U$ is an integral matrix over $R$, and does not require crystallinity of the frame if the Galois identity for $Q$ is otherwise supplied.

**Constant-evaluation fixedness (`FixW`).** For every such $\ell,K,\mathrm{bk}$, take a local period-ring package $P$, an integral Witt-period realization $AI$, and a tie between that package and the displayed period rings that intertwines Frobenius and Galois. Suppose $n\ge0$ and the $n$th power of the unramified Frobenius fixes every element of the maximal unramified algebraic extension that lies in $K$ (the hypothesis `FixUr K n`). For every $s\in\mathfrak S$, applying the indicated Frobenius power to $f_0(s)\in R$ fixes it. The source defines $f_0=i_A\circ\operatorname{ev}\circ\phi_{\mathfrak S}\circ C\circ\operatorname{ct}$, where $i_A:A_{\inf}\to R$. By the evaluation–Frobenius law this equals $f_I\circ\operatorname{ev}\circ C\circ\operatorname{ct}$, with $\operatorname{ct}$ the constant coefficient and $C$ the constant-series inclusion. This is an equality over $R$, not only after passage to $B$.

## From integral data to the invariant basis

The rational crystalline ring inverts $\ell$. For $w$, the period factorization gives $w=a_B(\eta)a_B([\epsilon]-1)$, where $a_B:A_{\inf}\to B$ is the natural map. The first factor is the image of an integral unit and the second is a unit by [the cyclotomic denominator proof, Sections 2–3](the-cyclotomic-denominator-in-an-invariant-crystalline-basis.md#2-divisibility-before-localization) proving [`CrisLoc.unit_of_root_aB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/CrystallinePeriods/CrisLoc.lean#L40-L42). Thus $w\in B^\times$ before any of the matrices are chosen. Set
$$
Z=f_I(Y)Q,\qquad Z'=Q'f_I(Y'),\qquad U=w^{-N}\jmath(Z).
$$

In $R$, $ZZ'=f_I(\tau)^{2N}\ell^{2k}I$ by the two cleared inverse identities. The image of this scalar is invertible in $B$, so $U$ has a right inverse, explicitly $w^{-N}\ell^{-2k}\jmath(Z')$. For square matrices over the commutative ring $B$ this is also the left inverse by the determinant and adjugate. The cleared identity $w^N U=\jmath(f_I(Y)Q)$ holds by construction.

Push the cleared Galois law for $Y$ through $f$. Compatibility with the Galois action and cancellation of the unit $w^N$ give
$$
 \rho(g)g(f(Y))=\frac{g(w)^N}{w^N}\, f(Y)f(C_g).
$$
Pushing the section invariance through $\jmath$ gives $f(C_g)g(\jmath Q)=\jmath Q$. Multiply these relations in their displayed order. The factors of $g(w)^N$ then cancel against the action on $w^{-N}$ in $U$, proving $\rho(g)g(U)=U$. Thus the cocycle in the preframe is removed by precisely the same integral section that clears the Frobenius relation.

## Fixing constant evaluations before comparing operators

For every $s\in\mathfrak S$, let $x=f_0(s)$, where $f_0$ evaluates constant terms and then applies Frobenius. Let $n\ge0$ satisfy the actual FixUr hypothesis: the $n$th unramified Frobenius fixes every element of $K$ in the maximal unramified coefficient field. Then $\phi^n(x)=x$ in $R$ (the conclusion of FixW).

Indeed $x$ is Galois-fixed: the constant Witt coefficients are fixed over $K$ and the two actions commute under the embeddings. Transfer $\jmath(x)$ back to the comparison period ring along the tie. Its $G_K$-invariance places it in the image of an element $c$ of the unramified coefficient field lying in $K$, by the invariant-ring statement of these period data. Frobenius on this image is unramified Frobenius on $c$, so the stated hypothesis fixes the image after $n$ iterations. Transfer forward through the tie and use Frobenius compatibility with $\jmath$; injectivity brings the equality back to $R$. Galois invariance of $x$ alone is not the assertion that all Frobenius powers fix it. The chosen exponent matters.

## Joining the earlier comparison

In OpEx2 choose the section exponent $k$ using the common height $N$ before the target and layer dimensions. For each frame, the construction above gives $Z$ and $U$ with the same scalars $f_I(\tau)^N$ and $\ell^{2k}$, and for every precision $M$ the LinkZ step gives
$$
\Pi_m Z_m-Z\,f_0(R_m)\equiv0\pmod{\ell^M}
$$
for a suitable $m\ge M$ and link matrix $R_m$ over $\mathfrak S$. To obtain the congruence, meet the LinkZ input threshold and the desired output precision in the same choice of layer. Apply FixW to $f_0(R_m)$ for both nonnegative Frobenius exponents $n_1,n_2$, which have the requisite FixUr hypotheses. Now use the [existing integral operator identity](https://github.com/lyz4tc/rh-proof-notes/blob/main/proofs/en/compatible-period-bases-give-compatible-integral-frobenius-operators.md) to turn this congruence into $V\Pi_m-\Pi_mV_m\equiv0$ with a common denominator. For trace closure the two exponents have $n_2-n_1=\alpha(g)$, not $\alpha(g)=n_1+n_2$. This is where the exponent chosen independently of dimension is used again.

## Lean and comparative sources

- [InvU interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L35-L42) and [the FixW interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L81-L83). [invU_holds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvUHolds.lean#L16-L92) constructs $U$; [fixW_holds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/FixWHolds.lean#L11-L57) proves the constant-field assertion.
- [OpEx2 assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72-L102) uses the common $k$, LinkZ, both fixed powers and the integral operator identity. [closedTr_of](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ClosedPhiOfClosedTr.lean#L54-L70) chooses $n_1,n_2$ from the signed Weil exponent.
- The still-open inputs for this note are the tied invariant-field comparison and crystalline-inclusion injectivity used by `FixW`. The cyclotomic unit, bounded-pole lift and frame law are split out and linked above, not hypotheses of the top-level closedness result.
- Comparative source: rh-lean-roadmap, sixth book version, 22 November 2026, commit 32b37eda73ced0174240bd183e5a0d54edd26eed, [appendix proof of Lemma 40.44, printed pp. 1011–1012](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/book.pdf). It also gives the product $Z=\phi(Y)Q$ and the common denominator. The present note follows the pinned quantifiers and gives the fixedness of the constant evaluation as a separate input rather than treating it as a formal consequence of the section recurrence.
