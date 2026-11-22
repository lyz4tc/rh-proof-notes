# From a local representation cover to uniformly linked crystalline frames

**Status:** Source-based reconstruction draft, not a human-reviewed proof. This note expands `UpperTheory.Gal.ClosedPhiFromClosedTrace.frEx_holds` and the relevant calculations in its immediate dependencies. It does not prove the existence of the cover, construct the global Galois representations, or derive trace closure from the frames.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## 1. The exact input and output

Fix a prime $\ell$, finite extensions $K,L_0$ of $\mathbf Q_\ell$ inside the source's ambient field $\Omega_\ell=\mathrm{Om}\,\ell$, a Breuil–Kisin datum $bk$ for $K$, and a period $\tau_p\in A_{\inf}$ satisfying $bk.\mathrm{IsPer}(\tau_p)$. Fix the tied local-period data $(P,AI,T)$, of types `LocPrime`, `LocAinf`, and `LocTied`. Every $\mathbf Q_\ell$-embedding of $K$ into $\Omega_\ell$ is required to have image in $L_0$.

Let $r:G_K\to\mathrm{GL}_a(\Omega_\ell)$ be a group homomorphism, $\mathcal C$ a set of homomorphisms of the same type, and $\mathrm{Cv}:\mathrm{Cover}(L_0,r,\mathcal C)$ given. In particular the cover contains:

- an integral target $\rho:G_K\to\mathrm{GL}_d(\mathbf Z_\ell)$;
- integral layer representations $\rho_m$ of ranks $d_m$, with continuity, and layer data $\mathrm{Ly}_m:\mathrm{Layer}(L_0,\mathcal C,\rho_m)$;
- a tower with maps $\Pi_m:\mathbf Z_\ell^{d_m}\to\mathbf Z_\ell^d$ that intertwine the actions and have a right inverse modulo $\ell^m$. The layer-to-layer arrows are exactly equivariant and commute with the $\Pi_m$ modulo $\ell^m$.

The theorem does not assume that $r$ belongs to $\mathcal C$. Nor does it independently postulate continuity of $r$; it takes an already constructed cover.

Specify a multiset $J(\sigma)$ of integers for each $\mathbf Q_\ell$-embedding $\sigma:K\hookrightarrow\Omega_\ell$. The two hypotheses on $\mathcal C$ apply to **every** $\rho_1\in\mathcal C$ and **every** finite coefficient model $(L,r',R)$: $L\supseteq L_0$, the action of $R$ on $L^a$ is multiplication by $r'(g)$, and all entries of $r'(g)$ agree with $\rho_1(g)$ after embedding $L$ into $\Omega_\ell$. For every such model:

1. $R$ is semistable in the period data $P$; for each $\tau:K\hookrightarrow L$ and $n\in\mathbf Z$, its filtration multiplicity is exactly $\mathrm{multV}_{\tau}(R,n)=\#_{J(\iota_L\circ\tau)}(n)$.
2. $R$ is crystalline in $P.\mathrm{PD}(K)$.

The conclusion is a common integer $N\ge0$, crystalline frames $F_m$ for all $\rho_m$ and $F_\infty$ for $\rho$, all at the **same** frame parameter $N$, and one $s\ge0$ such that for each precision $n$ there is an $m\ge n$ with $\mathrm{Link}(bk,F_\infty.T,F_m.T,\Pi_m,n,s)$. Lean calls the target frame `F₀`; the subscript $\infty$ here distinguishes it from a stage-zero frame. Write $T_\infty$ and $T_m$ for the respective Witt-coordinate matrices. A link means that there exist $d$-by-$d_m$ and $d_m$-by-$d$ matrices $R_m,G_m$ over the Breuil–Kisin ring $S=bk.S$ satisfying, entry by entry,
$$
 z_W(\Pi_m)T_m\equiv T_\infty\operatorname{ev}_W(R_m)\pmod{\ell^n},\qquad
 R_mG_m\equiv\ell^s I_d\pmod{\ell^n}.
$$
The first congruence is in $W C^\flat$ (the source's `WCb`); the second is in $S$. The level and the witnesses can depend on $n$. The denominator exponent $s$ cannot. This does not assert exact stagewise commutation, one level good at all precisions, or a frame directly for the original $a$-dimensional $r$.

[Statement and quantifiers][fr] · [Layer, tower and cover][data] · [Frame and link definitions][frame]

## 2. Why the layer hypotheses transfer

Put $N=\max_{\sigma}\max_{u\in J(\sigma)}|u|$, taking the supremum of an empty set of nonnegative integers to be zero. The set of embeddings of $K$ is finite, and each multiset is finite. For each occurrence $u\in J(\sigma)$, first bound $|u|$ by the supremum of the absolute values in its own multiset, then bound that supremum by $N$. This proves the required bound without bounding any layer ranks or coefficient fields.

Fix one layer $\mathrm{Ly}$ of rank $d'$ and write $V=\mathbf Q_\ell^{d'}$. Its finite list has members $\rho_k\in\mathcal C$ with coefficients in $L_k\supseteq L_0$. The matrices $\rho_k(g)$ give a representation over $L_k$: the unit and multiplicativity identities descend entrywise, and $\rho_k(g^{-1})$ is the inverse. Denote the action on $L_k^a$ by $W_k$. The layer gives matrices $b_{j,k}$ over $L_k$ whose tuples are independent over $\mathbf Q_\ell$ and span the product of full matrix spaces. Thus the coordinate map
$$
 v=(v_j)_j\longmapsto \left(\sum_j v_j b_{j,k}\right)_k
$$
is a $\mathbf Q_\ell$-linear isomorphism. Decompose each output matrix by columns, giving an isomorphism with $\prod_{k,c}\operatorname{Res}_{L_k/\mathbf Q_\ell} W_k$, with $a$ columns for each $k$.

To check the action, the layer's `Reads.equi` is the equality
$$
 \rho_k(g)b_{j,k}=\sum_i(\rho_m(g))_{ij} b_{i,k}
$$
when the layer is $\mathrm{Ly}_m$. Multiply by $v_j$ and sum over $j$: the coordinate map intertwines $q\mathrm{Rep}(\rho_m)$ on $V$ with left multiplication on every matrix, hence with the action of $W_k$ on each column. Here $q\mathrm{Rep}$ is the rational extension of the integral matrix action, not the passage from a global to a local Galois group.

By the two hypotheses, the models $W_k$ are semistable and crystalline. For semistability, restriction of scalars leaves the period invariants the same underlying set; the corresponding ranks over $\mathbf Q_\ell$ multiply by $[L_k:\mathbf Q_\ell]$. Period invariants of a finite block sum are the product of the invariants, so the rank equality defining semistability adds across factors. The crystalline branch uses the source's crystalline restriction-of-scalars equivalence and its block-sum lemma with the same equivariant isomorphism. Hence every rational layer is both semistable and crystalline. These are **two** preservation statements; the theorem's separate hypotheses have not been collapsed.

[Common bound and layer calls][holds] · [Layer coordinate isomorphism and equivariance][layer] · [Preservation proof][layer-end]

### Filtration endpoints: why the same interval works for each layer

The bound needed by the frame constructor is not merely a slogan about weights. It is the pair
$$
 D_{\rm dR}(V)\subseteq\mathrm{Fil}^{-N},\qquad
 D_{\rm dR}(V)\cap\mathrm{Fil}^{N+1}=0,
$$
where $\mathrm{Fil}$ is the ambient tensor-period filtration `FilV` in the statement. Work first on $W_k$ with coefficients in $L_k$. Composing a $K\to L_k$ embedding with $L_k\hookrightarrow\Omega_\ell$ is injective and surjective on the sets of embeddings: any ambient embedding factors through $L_0\subseteq L_k$, by hypothesis. Consequently the number of embeddings is $[K:\mathbf Q_\ell]$ and the source's embedding decomposition of $D_{\rm dR}\cap\mathrm{Fil}^u$ applies.

On each embedding component the filtration is decreasing and finite-dimensional. Its consecutive rank drop equals the multiplicity of the corresponding integer in $J$. For $|u|>N$ this multiplicity is zero; a subspace contained in another of equal finite dimension is equal to it. Iterating downwards gives stabilization at $-N$ on the lower side, and iterating upwards gives stabilization at $N+1$ on the upper side. By separatedness, the latter stabilized space is zero. By exhaustiveness, any de Rham vector belongs to some ambient $\mathrm{Fil}^u$: if $u\ge-N$ it is already in $\mathrm{Fil}^{-N}$, while if $u<-N$ its embedding components stabilize at level $-N$. Summing the components gives the two endpoint assertions on $W_k$.

For transfer to $V$, denote the column maps by $f_{k,c}:V\to W_k$ over $\mathbf Q_\ell$. They are jointly injective by independence of the tuple of basis matrices. A linear left inverse of their joint map supplies maps $g_{k,c}:W_k\to V$ for which $\sum g_{k,c}f_{k,c}=1_V$. Tensor this identity in the period ring. The $f_{k,c}$ are equivariant, so they take de Rham invariants to de Rham invariants. Both types of linear maps preserve the ambient filtration after tensoring; it is not necessary to assert equivariance of the chosen $g_{k,c}$. If $x$ is a de Rham invariant, all its images lie in $\mathrm{Fil}^{-N}$; recovering $x$ by the sum then places it in $\mathrm{Fil}^{-N}$. If $x$ belongs also to $\mathrm{Fil}^{N+1}$, each image is zero by the factor result, so the same sum says $x=0$.

[Stabilization][stabilize] · [Factor endpoint proof][factor] · [Tensor maps and splitting][tensor] · [Embedding count and transfer to layer][bounds]

## 3. Uniform frames, then the linked limit

For each continuous $\rho_m$, the semistable-frame theorem applies to its rational action and the two endpoint bounds. It returns a frame $F_m$ at the prescribed $N$, with $F_m.\mathrm{IsDR}$ and the implication that crystallinity of the rational representation makes **that frame** crystalline. Its proof first obtains a Hodge basis from de Rham admissibility; the endpoint condition supplies the bound on the exponents of that basis. It chooses a period seed by cases: crystalline seed with trivial auxiliary cocycle, or semistable seed constructed from $A_{\rm cris}$ periods. The period construction gives a frame at some preliminary $N'$. The height-adjustment theorem changes to the specified $N$ while preserving its period matrix and its $A_{\inf}$-valued cocycle. The latter equality transfers the de Rham and crystalline frame conditions, since both are conditions on that cocycle. Apply the previously proved crystallinity to discharge the implication for every layer.

To obtain $F_\infty$, first forget the layer cocycles, retaining their preframes. The preframe limit theorem supplies a target preframe and a fixed $s$ with links of all precisions. It builds an étale-basis candidate, uses Mittag–Leffler stabilization and bounded poles to construct a Breuil–Kisin preframe, and obtains $s$ from a right-inverse descent lemma **before** choosing the precision. A linked-preframe theorem completes this exact preframe to a frame, so its Witt-coordinate matrix and the old links are unchanged. The de Rham condition passes by the separate `isDR_of_links'` theorem. The next calculation expands the crystalline part of the limit step.

[Frame construction and height adjustment][frame-sst] · [Height-adjustment statement][height] · [Preframe limit and uniform right inverse][prelim] · [Linked frame completion][completion] · [Assembly of the limit theorem][limit]

### One explicit limit calculation: crystallinity is preserved

Fix $g\in G_K$ and write $\sigma$ for its action on $A_{\inf}$ and $x=\operatorname{ev}(X)$. Choose a precision $n$ and a linked $m\ge n$. Set $A=\operatorname{ev}(R_m)$ and $B=\operatorname{ev}(G_m)$, and let $\varepsilon_\infty,\varepsilon_m$ be the target and layer frame cocycles evaluated at $g$. Reduction of the representation intertwiner from modulus $\ell^m$ to modulus $\ell^n$, together with the first link congruence, gives the cocycle congruence
$$
 \varepsilon_\infty\,\sigma(A)\equiv A\varepsilon_m\pmod{\ell^n}.
$$
This is a matrix identity modulo $\ell^n$ in $A_{\inf}$; it is not deduced merely by replacing Witt-coordinate entries by their reductions. The second link gives $AB\equiv\ell^s I\pmod{\ell^n}$. Also $\varepsilon_m\equiv I\pmod{x}$ by crystallinity of $F_m$. For $G_m$ over $S$, one has $\sigma(B)-B\equiv0\pmod{x}$: each power series in $S$ is its constant plus $X$ times another series, the evaluated constant is fixed, and $\sigma(x)$ is a multiple of $x$ by the disc-map property.

Right-multiply the cocycle congruence by $\sigma(B)$. The left side is congruent to $\ell^s\varepsilon_\infty$ modulo $\ell^n$. On the right, replacing $\varepsilon_m$ by $I$ and $\sigma(B)$ by $B$ costs only multiples of $x$, so the right side is congruent to $\ell^s I$ modulo $(\ell^n,x)$. Thus, entrywise,
$$
 \ell^s(\varepsilon_\infty-I)\in \ell^n A_{\inf}+xA_{\inf}.
$$
The exponent $s$ is fixed while $n$ is arbitrary. Under the injection $A_{\inf}\hookrightarrow W C^\flat$, the image of $x$ is a unit (its first Witt coefficient is nonzero). The principal-ideal saturation and closedness theorem now removes the fixed $\ell^s$: an element $w$ of $W C^\flat$ for which every $\ell^n$-neighborhood of $\ell^s w$ meets the image of $xA_{\inf}$ itself lies in that image. Injectivity gives $x\mid(\varepsilon_\infty-I)_{ij}$ in $A_{\inf}$, for every $g,i,j$. That is exactly $F_\infty.\mathrm{IsCr}$. This is also why one must retain the approximate right inverse with a denominator bounded independently of precision.

[Cocycle transport][cocycle] · [Disc divisibility and crystalline inheritance][crlimit] · [Saturated closed principal ideal statement][sat]

## 4. Where this branch stops

`closedTr_of` constructs the pulled-back cover on $G_{K_w}$ and supplies the finite-model conditions using its global input: the bridge's splitting property puts embeddings inside $L_0$; comparison transports the semistability, jump multiplicities, and crystallinity. Separately, it obtains crystallinity of the target **coefficient model** before invoking this frame theorem. The output here is the package $(N,F,F_\infty,s)$ with crystalline frame conditions and links, handed to the operator-existence step. Trace comparison and the final limiting argument are downstream.

The present reconstruction leaves the internal proofs of the semistable/crystalline seed comparison theorems, the integral height-adjustment theorem, the étale/preframe limit construction, completion of a linked preframe, and de Rham inheritance from links as named source inputs. It expands the layer and filtration arguments and the crystalline limit calculation; it neither replays the Lean archive nor certifies the other branches of ClosedPhi.

[Caller and transfer of hypotheses][caller] · [Assembly into ClosedTr and ClosedPhi][assembly]

[fr]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L107-L118
[holds]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/FrExHolds.lean#L11-L37
[data]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L89-L157
[frame]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L55-L87
[layer]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsSemistableLatticeInMatrixAlgebraLayer.lean#L69-L174
[layer-end]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsSemistableLatticeInMatrixAlgebraLayer.lean#L178-L192
[stabilize]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LayerDdRBounds.lean#L20-L39
[factor]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LayerDdRBounds.lean#L124-L162
[tensor]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LayerDdRBounds.lean#L50-L105
[bounds]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LayerDdRBounds.lean#L279-L341
[frame-sst]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinFrameSemistableBoundedJumps.lean#L102-L134
[height]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinFrameHeightOfJumpsLeStatement.lean#L11-L12
[prelim]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinBasisLimitLattice.lean#L35-L63
[completion]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsBreuilKisinLatticeFrameOfLinkedPreframe.lean#L13
[limit]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsDeRhamFrameLimitLatticeBreuilKisinTower.lean#L16-L24
[cocycle]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinLatticeFrameCocyclesLinkedStatement.lean#L11-L12
[crlimit]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinFrameIsCrOfLinkedTower.lean#L25-L106
[sat]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AinfPrincipalIdealSaturatedClosedStatement.lean#L11-L12
[caller]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ClosedPhiOfClosedTr.lean#L13-L70
[assembly]: https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ClosedPhiHolds.lean#L34-L44
