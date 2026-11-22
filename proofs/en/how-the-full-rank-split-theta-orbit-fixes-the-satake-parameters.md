# How the full-rank split theta orbit fixes the Satake parameters

**Status: Source-based reconstruction draft.** Revised after source review; no new Lean build.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot. This prose was subsequently checked against the cited source by Codex.

**Scope.** This note proves the split spherical Satake comparison **conditional on the existence of a nonzero local equivariant pairing with the specified Weil action**. It does not construct the global lift, prove its integrability or nonvanishing, or compare two global lifts.

## 1. Setup and result

Let $k$ be the nonarchimedean field of the split chart, with ring of integers $\mathcal O$, uniformizer $\varpi$ and residue cardinality $q$. Let $r$ be the source rank and $d=r+t$ the target rank, with $r<t$ (equivalently $2r<d$). The actual charted representations are smooth and irreducible over $\mathbb C$; the source is unitarisable and spherical with normalized Satake multiset $B$. Let $\chi_X,\chi_W:k^\times\to\mathbb C^\times$ be the smooth unramified unitary splitting characters, and put $b=\chi_X$, $\nu=\chi_W^{-1}$, $x=b(\varpi)$ and $y=\chi_W(\varpi)$.

In the application, assume the local pairing `LocPair` of the actual source and target supplied by the global theorem. This is not an arbitrary nonzero bilinear form: it is linear in the Schwartz function and target vector, conjugate-linear in the source vector, and invariant for the simultaneous split Weil and representation actions. Section 4 describes how this input gives the following **bilinear** model, which is the precise pairing hypothesis for Sections 2–3. Write $\sigma_0$ and $\pi_0$ for its source and target actions on $V$ and $W$, and $\mu=b^{-1}$. Assume a nonzero complex-bilinear map $D:\mathcal S(M_{d,r}(k))\times W\to V$ such that for every $g\in GL_r(k)$, $h\in GL_d(k)$, $\Phi\in\mathcal S(M_{d,r}(k))$ and $w\in W$,
$$
D(\omega_\mu(g,h)\Phi,\pi_0(h)w)=\sigma_0(g)D(\Phi,w),
$$
where $\mathcal S$ here consists of compactly supported locally constant functions and
$$
(\omega_\mu(g,h)\Phi)(X)
=\frac{\mu(\det g)}{\mu(\det h)}|\det g|^{d/2}|\det h|^{-r/2}\Phi(h^{-1}Xg).
$$
In this model $\sigma_0$ is unitarisable and $\pi_0$ is smooth and irreducible. To deduce the isomorphism in Section 3 the normalized induction of $\sigma_0\boxtimes(\mu\circ\det)$ must also be irreducible. The actual caller supplies it via `Mix.top`; it is not an implication of the norm estimate.

Then the actual target is spherical with normalized Satake multiset
$$
(xy^{-1})B\;\sqcup\;\{\,xq^{(t-1)/2-j}:0\le j<t\,\}.
$$
The braces are interpreted as a multiset. This is not a statement about arithmetic Frobenius normalization or nonspherical local parameters.

## 2. The strict inequality is a contraction on smaller-rank orbits

In the bilinear `ThetaPair` model, use the transposed matrix space $M_{d,r}(k)$. Write $\sigma_0$ for its source representation, $\pi_0$ for its target, $\mu$ for its character, and $D(\Phi)w$ for the evaluation of the pairing on a Schwartz function and a target vector. This paragraph uses these transformed representations, not the actual spherical source and target. For the source-only action, equivariance says
$$
 D(\omega_\mu(g,1)\Phi)w=\sigma_0(g)D(\Phi)w,\qquad
 (\omega_\mu(g,1)\Phi)(X)=\mu(\det g)|\det g|^{d/2}\Phi(Xg).
$$
Assume $D$ kills test functions vanishing on ranks at most $j$, and let $0\le j<r$. Let $E_j$ be the rectangular matrix with $I_j$ in the upper left and zero elsewhere; take $\Phi=1_{E_j+cM_{d,r}(\mathcal O)}$ for $0<|c|<1$. For each $R\in M_{j,r-j}(\mathcal O/\varpi\mathcal O)$ choose an integral lift $\widetilde R$ and put
$$
 g_R=\begin{pmatrix}I_j&\varpi^{-1}c\widetilde R\\
                    0&\varpi^{-1}I_{r-j}\end{pmatrix}.
$$
On matrices $X$ of rank at most $j$, the exact identity is $\Phi(X)=\sum_R\Phi(Xg_R)$. To see this, split $X=(A,C)$ into its first $j$ and remaining $r-j$ columns. All the terms require the same condition $A\equiv\binom{I_j}{0}\pmod{c\mathcal O}$. If it holds, $A$ has rank $j$ with its top block in $GL_j(\mathcal O)$, so $C=AT$ for a unique $T$. The condition that the last columns lie in $cM(\mathcal O)$ becomes $T\in cM(\mathcal O)$. In the term indexed by $R$, those columns are instead $A\varpi^{-1}(T+c\widetilde R)$; the condition becomes $T+c\widetilde R\in c\varpi M(\mathcal O)$. There is exactly one residue class $R=-T/c\bmod\varpi$ when $T/c$ is integral and none otherwise. The empty top block at $j=0$ is harmless: the only tested matrix has rank zero and the unique empty $R$ gives the same indicator.

All the $g_R$ have determinant $\varpi^{-(r-j)}$. Thus the scalar $s=\mu(\det g_R)|\det g_R|^{d/2}$ is independent of $R$ with $|s|=q^{d(r-j)/2}$. Apply $D$ to the indicator identity modulo the subspace of functions vanishing on ranks at most $j$. Writing $v=D(\Phi)w$ gives
$$
 v=\sum_R s^{-1}\sigma_0(g_R)v,\qquad
 \|v\|\le q^{(r-j)(j-d/2)}\|v\|.
$$
The norm comes from the invariant positive definite Hermitian form; no Hilbert completion or continuity assumption on the linear pairing is needed. Since $2j<d$, $v=0$. The count alone would not imply vanishing if the ratio were merely at most one.

Here is how this local calculation rules out a pairing supported only on singular ranks. Functions vanishing on ranks below $j$ are cut into small clopen pieces. A piece around a rank-$j$ point is transported by invertible row and column operations to a neighborhood of $E_j$; within that neighborhood, rank-$j$ centers of the small balls are carried to $E_j$ by integral invertibles, which preserve the ball lattices. Pieces supported on higher ranks already vanish by hypothesis. This is the role of the ball, local partition, and rank-normal-form lemmas in `MemBallMSelf.step`, not a claim that a general test function on the singular matrices can be extended independently of its neighborhood. Hence `VanRk D (j+1)` implies `VanRk D j`. If $D$ vanished on every full-rank-supported test function, descending from $j=r-1$ would give `VanRk D 0`, i.e. $D=0$, a contradiction. The actual theorem imposes $r<t$; the contraction by itself is not a proof of classification at any endpoint outside that theorem.

## 3. The full-rank germ gives normalized induction

Take $e=\binom{I_r}{0}$ and give the additive matrix space Haar measure, normalized to give the integral matrix lattice volume one. The proof of [`germ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/PointAveraging/MinkowskiBalls/MeasurableSetBallM.lean#L347-L405) works as follows. Fix $w$. The stabilizer of $w$ in $GL_d(k)$ is open by smoothness, and the kernel of $\mu\circ\det$ is open because $\mu$ is smooth. Choose $c\in k^\times$ with $|c|<1$ such that the principal congruence subgroup with matrix entries congruent to the identity modulo $c\mathcal O$ lies in their intersection. If $X\in e+cM_{d,r}(\mathcal O)$, adjoining the last $t$ columns of the identity to $X$ gives an element $h$ of that subgroup with $he=X$. It has determinant of absolute value one and preserves every radius lattice $c'M_{d,r}(\mathcal O)$. The equivariance at $(1,h)$ therefore gives
$$
D(1_{X+c'M_{d,r}(\mathcal O)},w)
 =
D(1_{e+c'M_{d,r}(\mathcal O)},w).
$$

For any test $\Phi$ supported in $U=e+cM_{d,r}(\mathcal O)$, refine both $\Phi$ and $1_U$ into finite sums of indicators of balls of a common sufficiently small radius $c'$. A ball's contribution under $D(-,w)$ is a scalar multiple of the common vector above; its integral is the same scalar times the common positive volume. Comparing the two sums gives
$$
D(\Phi,w)=\left(\int\Phi\right)\operatorname{ev}(w),\qquad
\operatorname{ev}(w)=D(1_U,w)/\operatorname{vol}(U).
$$
The radius may depend on $w$. Testing on a smaller ball of nonzero volume proves uniqueness and, by shrinking to a common radius for finitely many vectors, linearity. If $\operatorname{ev}=0$, transitivity on full-rank matrices and equivariance transport zero germs to all full-rank points. A finite clopen partition then kills every test supported on the full-rank locus, contradicting Section 2.

For $p\in P_{r,t}$ with Levi blocks $a$ and $u$, the map $X\mapsto p^{-1}Xa$ fixes $e$. Write $A=|\det a|$, $U=|\det u|$. The integral of $\omega_\mu(a,p)\Phi$, divided by the integral of $\Phi$ when nonzero, is
$$
 \mu(\det a)\mu(\det p)^{-1}\, A^{-d/2}|\det p|^{r/2}
   =\mu(\det u)^{-1} A^{-t/2}U^{r/2}.
$$
Indeed the substitution contributes $A^{-d}|\det p|^r$, which combines with the Weil-model scalar $A^{d/2}|\det p|^{-r/2}$. Shrink the test ball so both germ identities apply. Comparing them by equivariance gives
$$
 \operatorname{ev}(\pi_0(p)w)
   =\delta_{P_{r,t}}^{1/2}(p)\,\mu(\det u)\,
      \sigma_0(a)\operatorname{ev}(w),\quad
 \delta_{P_{r,t}}^{1/2}(p)=A^{t/2}U^{-r/2}.
$$
Thus $w\mapsto [g\mapsto\operatorname{ev}(\pi_0(g)w)\otimes1]$ gives a nonzero intertwiner into normalized induction of $\sigma_0\boxtimes(\mu\circ\det)$; evaluate at $g=1$ for nonvanishing. It is an isomorphism once both representations are irreducible. The actual caller proves irreducibility of this specific induction via `Mix.top` (using the geometric lemma and the Zelevinsky polynomial-ring result); the norm argument above does not prove it.

## 4. Keep the three source conventions separate

1. **Actual split local component.** `pairSat` pulls both local representations back through the split chart. The pairing in `LocPair` is conjugate-linear in the actual source variable. The invariant form yields a conjugate-linear intertwiner to the smooth source dual, so `IsLift` starts from the smooth contragredient of the charted source. If the actual source multiset is $B$, the source multiset at this intermediate stage is $U=B^{-1}$, with entrywise inverse.
2. **Bilinear matrix model.** Given `IsLift` with source $\sigma$ and target $\pi$, `PairOfLift` transposes the matrix, applies inverse-transpose on the source with determinant twist $\nu b$, and passes to smooth duals. This yields $\operatorname{ThetaPair}_{b^{-1}}\big((\operatorname{src}(\nu b)\sigma)^\vee,\pi^\vee\big)$. For example, the split-model identity is $\omega_A(\nu,b;g^{-T},h)(\Phi\circ{}^T)=(\nu b)(\det g)\,[\omega_{b^{-1}}(g,h)\Phi]\circ{}^T$. Existence of a nonzero dual pairing uses that the smooth dual separates points, not that algebraic and smooth duals coincide.
3. **Returning from induction.** Let $z=(\nu b)(\varpi)=xy^{-1}$. The twist and inverse-transpose give $zU^{-1}$, and the source smooth dual gives $z^{-1}U$. The determinant representation on $GL_t$ gives the multiset $\{x^{-1} q^{(t-1)/2-j}:0\le j<t\}$. Normalized induction takes the multiset union. Passing back from $\pi^\vee$ to $\pi$ takes entrywise inverses, leaving $zU^{-1}$ and the segment with coefficient $x$ (the permutation $j\mapsto t-1-j$ fixes the exponent multiset). Now insert $U=B^{-1}$ from step 1, yielding $zB$. This last inverse is essential: applying `liftSat_of` straight to the actual source multiset would incorrectly put $B^{-1}$ in the final answer.

## 5. Source map and limits

The independent roadmap is *The Riemann hypothesis and GRH for Dirichlet L-functions: A readable account of the Lean proof in Levent Alpöge’s archive*, credited to `rh-lean-roadmap`, November 2026, sixth version, pinned at `32b37eda73ced0174240bd183e5a0d54edd26eed`. [Part IX, printed p. 447 / PDF p. 448](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/src/book/main.tex#L20694-L20732) states Proposition 40.57 (B9.39; global stable range), Lemma 40.58 (B9.40; integral criteria), and Lemma 40.59 (B9.40a; split spherical parameters). The [appendix proofs](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/src/book/main.tex#L41124-L41205) start on printed pp. 1025, 1026 and 1027 respectively (PDF pp. 1026–1028); the [declaration index](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/src/book/main.tex#L45177-L45191) connects these names with the code (printed p. 1123 / PDF p. 1124 at `tLiftK`). The main split-spherical entry is a proof outline; its appendix already describes the rank argument. This note independently reconstructs the exact indicator count, the Jacobian and the sign of each dual/twist from Lean rather than reprinting that outline.

- [`ValLeOneOfLc.ind_eq` and `core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/PointAveraging/MinkowskiBalls/ValLeOneOfLc.lean#L285-L460), [`MemBallMSelf.step`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/PointAveraging/MinkowskiBalls/MemBallMSelf.lean#L134-L194), [`MingZel.lift_of_irr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/FockModels/MingZel.lean#L17-L44): indicator count, rank descent, nonzero full-rank germ and irreducible intertwiner.
- [`germ` (proof of the local integral formula)](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/PointAveraging/MinkowskiBalls/MeasurableSetBallM.lean#L347-L405); [`IsGerm` and `ParLaw` (definitions)](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/CoreStatements/TemperedRepresentationTheory/GermIntegrals/IsGerm.lean#L15-L40), [`RealPowerProductEqOne.law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/CoreStatements/TemperedRepresentationTheory/GermIntegrals/RealPowerProductEqOne.lean#L34-L133), [`LFrob.frob`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/CoreStatements/TemperedRepresentationTheory/GermIntegrals/LFrob.lean#L14-L78): integral normalization and induction; see also [the caller of `Mix.top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/LocalTypeDictionary/ThetaLiftGlOfZelevinskyClassification.lean#L8-L14).
- [`PairOfLift` interface and matrix dictionary](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SatakeLifts/PairOfLiftAlt.lean#L21-L47), [`liftIso_of` / `liftSat_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SatakeLifts/IsUnitaryCharInv.lean#L22-L56), [`pairSat` via split chart](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SatakeLifts/PairSatPf.lean#L45-L110): exact local representation chain. The `LiftSat` statement differs from the final `PairSat` statement as Section 4 explains.
- The global lift package [`TLiftK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/HalfIndexLattices/TLiftK.lean#L12-L24) and [its conclusion `LocPair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SchurStep.lean#L93-L101) supply the local input used here. These are not supplied by doing the orbit calculation. The roadmap's [adelic see-saw](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/src/book/main.tex#L4188-L4196) compares orders of integration, and its [Part VIII see-saw](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/src/book/main.tex#L36832-L36835) concerns row separation. Neither is the mechanism of this split local rank argument. PC-4's checks involving `TriStep.tri`, `valX` and `MIstar2` likewise have a different immediate task: this note makes no claim about their full transitive dependency graph or about having discharged their arithmetic obligations.
