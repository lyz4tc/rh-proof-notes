# Finite adelic unitaries give lattices of one bounded dual index

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be CM and $W,h$ a nondegenerate finite-dimensional Hermitian space. Write $G_f=U(h)(\mathbb A_{F,f})$. There is a compact open subgroup $K_f\subseteq G_f$, an integer $D$, and an assignment $g\mapsto\Lambda(g)\subset W$ on $G_f$ such that each $\Lambda(g)$ is a full integral $\mathcal O_E$-lattice with $[\Lambda(g)^\#:\Lambda(g)]\le D$,
$$
 \Lambda(\gamma_f g)=\gamma\Lambda(g)
 \quad(\gamma\in U(h)(F)), \qquad
 \Lambda(g)=\Lambda(g')\ \Longleftrightarrow\ g^{-1}g'\in K_f .
$$
Here $\gamma_f$ denotes the finite components of a rational isometry. The proof below uses an integral reference $\mathcal O_E$-lattice. The Lean dictionary chooses a coordinate lattice using an $F$-basis of $E$, multiplies it by a fixed integer, and proves a uniform bound from a multiple of its local dual. [Lattice dictionary statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StatementsAdelicLattices.lean#L15) · [Lattice dictionary proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PAdelicLatticeDictionary.lean#L194)

## A reference lattice and its stabilizer

Fix an $E$-basis of $W$. Choose an integer $d>0$ such that $d^2$ times the matrix of $h$ in that basis has entries in $\mathcal O_E$. Use $\Lambda_*=d\mathcal O_E^{\dim_E W}$ in those coordinates. It is integral. Its dual $\Lambda_*^\#$ contains it with finite index by nondegeneracy. For each finite place $v$ of $F$, write $E_v=E\otimes_F F_v$, $\mathcal O_{E,v}=\mathcal O_E\otimes_{\mathcal O_F}\mathcal O_{F_v}$, and $\Lambda_{*,v}=\Lambda_*\otimes_{\mathcal O_F}\mathcal O_{F_v}$. These definitions include the product of two local fields at a split place. Let $K_f$ be the product of the local unitary stabilizers of $\Lambda_{*,v}$. Each local stabilizer is compact open, being the intersection of the closed unitary group with the compact open stabilizer of a free local lattice in the general linear group. At all but finitely many places it is the defining integral subgroup of the restricted product. Hence $K_f$ is compact open.

## Recover each local lattice from the rational intersection

For $g=(g_v)$, define $\Lambda(g)=\{x\in W:x_v\in g_v\Lambda_{*,v}\ \forall v\}$. Only finitely many local lattices differ from $\Lambda_{*,v}$. Choose an integer $m>0$ with
$$
 m\Lambda_{*,v}\subseteq g_v\Lambda_{*,v}\subseteq m^{-1}\Lambda_{*,v}
$$
at every place, possible by local commensurability. The rational intersection is then an $\mathcal O_E$-submodule between $m\Lambda_*$ and $m^{-1}\Lambda_*$. Moreover it recovers the specified local lattices after completion. Indeed, by the Chinese remainder theorem the finite quotient $m^{-1}\Lambda_*/m\Lambda_*$ is a direct sum of its local quotients. For example multiplication by $m$ identifies it with $\Lambda_*/m^2\Lambda_*$, which decomposes by the prime-ideal factorization of $m^2\mathcal O_F$. The component conditions selecting $g_v\Lambda_{*,v}/m\Lambda_{*,v}$ therefore select exactly a rational submodule with the specified local completions. This proves the claim and fullness. It also proves that two assignments agree exactly when the local lattices all agree, which is exactly the condition $g^{-1}g'\in K_f$. Rational equivariance follows by applying $\gamma$ to each local condition.

## Bound the index uniformly

The pairing on $g_v\Lambda_{*,v}$ is integral because $g_v$ is an isometry, so $h(\Lambda(g),\Lambda(g))$ is integral at every finite place and therefore in $\mathcal O_E$. Taking the Hermitian dual commutes with completion. This follows locally by representing the nondegenerate pairing against a basis of a free local lattice and solving the resulting linear equations for integral values. Equivalently, $\Lambda(g)^\#$ is the rational intersection of the lattices $g_v\Lambda_{*,v}^\#$. Consequently every local quotient has the same cardinality as $\Lambda_{*,v}^\#/\Lambda_{*,v}$. The global finite index is the product of these cardinalities by the primary decomposition of a finite module over $\mathcal O_F$. Thus $D=[\Lambda_*^\#:\Lambda_*]$ works for all $g$. This is the uniformity needed to apply the finiteness of rational lattice classes to the adelic group. [Uniform integrality and dual-bound calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PAdelicLatticeDictionary.lean#L68)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
