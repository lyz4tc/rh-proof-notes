# A finite lattice sandwich controls isotropic line orbits

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $W,h$ be a nondegenerate Hermitian space of dimension $n$ over a CM extension $E/F$, and let $D\ge1$ be an integer. There are finitely many rational isometry classes of full integral lattices $\Lambda\subset W$ with $[\Lambda^\#:\Lambda]\le D$. There are also finitely many classes of pairs $(\Lambda,l)$ with $\Lambda$ as above and $l\subset W$ an isotropic $E$-line. Here isometry of pairs means a single rational isometry carries both components to the respective components. In particular for fixed $\Lambda$, its rational stabilizer has finitely many orbits on the isotropic lines. We prove the two finiteness assertions together by induction on $n$. [Finiteness statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L15) · [Strong induction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Assembly.lean#L254)

## Bound the dual index on the complement

If a pair $(\Lambda,l)$ exists, apply [the normalized hyperbolic pair construction](a-normalized-isotropic-pair-splits-a-lattice-with-uniform-denominators.md) to get $v,w,I,J',N$ and $\Lambda_0=\Lambda\cap (Ev+Ew)^\perp$. Let $P_0$ be orthogonal projection to $W_0=(Ev+Ew)^\perp$. The formula (1) of that proof implies $NP_0(\Lambda)\subseteq\Lambda_0$. This gives fullness of $\Lambda_0$ because the projections of $\Lambda$ span $W_0$. Integrality follows from restriction, and finite generation follows since it is a subgroup of $\Lambda$.

For $y\in\Lambda_0^\#$ and $x\in\Lambda$, the two hyperbolic line terms of $Nx$ pair to zero with $y$. Thus $h(Ny,x)=h(y,NP_0x)\in\mathcal O_E$. This shows $Ny\in\Lambda^\#$ and $D!Ny\in\Lambda\cap W_0=\Lambda_0$. The group $\Lambda_0^\#$ is a full lattice. It is finitely generated since its subgroup $D!N\Lambda_0^\#$ lies in the finitely generated group $\Lambda_0$. Since the additive rank of $\Lambda_0^\#$ is $(n-2)[E:\mathbb Q]$, this gives
$$
 [\Lambda_0^\#:\Lambda_0]\ \le\ (D!N)^{(n-2)[E:\mathbb Q]} .
$$
The source uses the weaker bound obtained by replacing $n-2$ by $n$. Both are uniform. [Integral complementary lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PComplementLattice.lean#L47) · [Adapted reduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PAdaptedReduction.lean#L104)

## Fix the line and classify the lattices above it

If $W$ has no rational isotropic line, the pair list is empty. Otherwise fix one hyperbolic pair $v_*,w_*$ in $W$. The [pair transitivity calculation](two-reflections-align-the-two-sides-of-a-hyperbolic-plane.md) carries each normalized $v,w$ to $v_*,w_*$. This transports $l$ to $Ev_*$, leaves the two coefficient ideals unchanged, and identifies the complement with $W_*=(Ev_*+Ew_*)^\perp$. The inductive hypothesis gives a finite set of lattices representing all possible complementary lattices at the displayed index bound, since the rank of $W_*$ is $n-2$. Extend each chosen isometry of $W_*$ by the identity on $Ev_*+Ew_*$. After this second change, the transformed lattice $\widetilde\Lambda$ satisfies
$$
 A=Iv_*+\Lambda_*+J'w_*\ \subseteq\ \widetilde\Lambda\ \subseteq\ N^{-1}A
$$
for one of finitely many triples $I,\Lambda_*,J'$. For each triple, the additive quotient $N^{-1}A/A$ is finite, and each possible $\widetilde\Lambda$ is the inverse image of a subgroup. This proves the pair finiteness assertion. For a fixed lattice, representatives of rational pair classes that occur can be moved back to that lattice, with any two choices differing by its stabilizer. [Finiteness via a bounded sandwich](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLinePairOrbitsFinite.lean#L92)

## Include lattices with no chosen line

Choose an archimedean majorant and set $g=1$ in its length. If $\Lambda$ has a nonzero vector of length less than $1$, then the vector is isotropic by [the short-vector argument](a-shortest-vector-has-bounded-index-in-its-saturated-line.md). Thus the lattice occurs as the first component of one of the finitely many pair classes just proved. In the other case every nonzero length is at least $1$, so [the compactness theorem](bounded-generators-and-gram-matrices-compactify-the-thick-part.md) with threshold $1$ puts $\Lambda$ in one of a finite list of rational isometry classes. The union of the two lists is finite. In dimensions $0,1$ the short-vector case requiring an isotropic line cannot occur, so the proof also supplies the initial ranks. [Combine the short and thick cases](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLatticeOrbitsFinite.lean#L23)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
