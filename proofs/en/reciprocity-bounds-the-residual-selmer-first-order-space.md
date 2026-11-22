# Reciprocity bounds the residual Selmer first-order space

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Work over the residue field $k$ of the twist coefficient ring. Let $T$ be the residual Galois representation on $k^r$, $T^D$ its cyclotomic dual, and write $S_T,S_{T^D}$ for the unrelaxed Selmer spaces. Let $S_T(Q)$ be the Selmer space of $T$ in which the unramified conditions are removed at the auxiliary support $Q$. The support consists of two blocks of $R$ places and their conjugates. On first-block places the local $H^1$ for $T$ vanishes. On second-block places $P_j$ and their conjugates the residual representations and cyclotomic character are trivial on the decomposition groups. Let $\phi_j,\gamma_j$ be Frobenius and inertia there, and let a superscript $c$ denote the corresponding conjugate elements. Each $\gamma_j$ is the generator detected by the auxiliary character in the [tame Frobenius relation](a-tame-frobenius-relation-tests-dual-number-cocycles.md).

Use the usual dot pairing between the underlying spaces for $T$ and $T^D$, in their chosen dual coordinates. The two arithmetic inputs used here are:

- There are $c_j\in k^\times$ such that for all $x\in S_T(Q)$ and $y\in S_{T^D}$,
  $$
    \sum_j c_j\bigl(\langle x(\gamma_j),y(\phi_j)\rangle-
               \langle x(\gamma_j^c),y(\phi_j^c)\rangle\bigr)=0.
  $$
- There are $c_j^0\in k$ such that the subspace of $x\in S_T$ satisfying
  $$
    \sum_j c_j^0\bigl(\langle x(\phi_j),y(\phi_j)\rangle-
               \langle x(\phi_j^c),y(\phi_j^c)\rangle\bigr)=0
       \quad\text{for every }y\in S_{T^D}
  $$
  has dimension at most $e$, with $e\in\{0,1\}$.

The values in these formulas can be read on any representing cocycle. At each element used in an evaluation the corresponding residual action is the identity, so coboundaries have zero value there.

**Proposition.** Let $V$ be the kernel of the augmentation reduction of a universal Selmer matrix. Identify it with its image in $S_T(Q)$ under the natural injection furnished by the matrix presentation. Put $U=(k^r\times k^r)^R$ and $\lambda_j=c_j^0/c_j$. Define $t,u:V\to U$ by $t(x)_j=(x(\gamma_j),x(\gamma_j^c))$ and $u(x)_j=\lambda_j(x(\phi_j),x(\phi_j^c))$. Then
$\dim_k\{x_0\in V:t(x_0)=0,\ u(x_0)\in t(V)\}\le e$. In particular $\dim_k V\le 2rR+e$.

**Proof.** Specializing the group ring to $k$ by augmentation sends the inverse auxiliary twist to the identity. The universal kernel isomorphism therefore embeds $V$ into the global $H^1$ of $T$, and its image satisfies the relaxed Selmer conditions. This furnishes the injection used in the proposition.

Suppose $t(x_0)=0$. Cocycle restrictions to the second-block decomposition groups are additive because the residual action is trivial. The zero values at $\gamma_j$ and $\gamma_j^c$ imply vanishing on the inertia groups by the tame generator test. Inertia groups above a fixed place are conjugate. For an inertia element acting trivially, the cocycle value after conjugation is the old value acted on by the conjugating element, so zero is independent of this choice. The first-block local groups already vanish by hypothesis, and the remaining conditions were never relaxed. Thus $x_0\in S_T$.

If $t(x_1)=u(x_0)$, apply the first arithmetic identity to $x_1\in S_T(Q)$ and any $y\in S_{T^D}$. Replace, for every $j$, the two inertia evaluations of $x_1$ by $\lambda_j$ times the corresponding Frobenius evaluations of $x_0$. The coefficient becomes $c_j\lambda_j=c_j^0$, so the second arithmetic hypothesis puts $x_0$ in a subspace of dimension at most $e$. The injection of $V$ ensures that the dimension bound transfers to the asserted subspace of $V$. Finally the [kernel and quotient dimension calculation](laurent-specialization-controls-the-residual-first-order-kernel.md) gives $\dim V\le\dim U+e=2rR+e$.

**Lean correspondence.** The pairing `form`, the reciprocity input `Recip` and the rank input `Corank` are in the definitions of the residual dual representation. `exists_ev` justifies evaluation on cohomology. `computes_transfer` specializes the universal matrix and preserves cocycle evaluation through coefficient maps. `unrelax` removes the auxiliary relaxations, and `core` combines these inputs. The [simultaneous evaluation-rank argument](one-list-of-residual-tests-works-for-all-good-signatures.md) explains the second arithmetic input. The [mixed reciprocity identity](global-reciprocity-leaves-only-the-second-block-cup-products.md) follows by computing the surviving local cup products. Source-based reconstruction. [Reciprocity and rank assumptions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/IsDualDualRep.lean#L107) · [Evaluation on cohomology](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ResidualSelmerDeterminantOrderBound.lean#L26) · [Transfer through the residual augmentation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixComputesTwistedSelmerResidualTransfer.lean#L136) · [Removing the relaxations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/RelaxedResidualSelmerMemUnrelaxed.lean#L77) · [The residual test](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ResidualSelmerDeterminantOrderBound.lean#L118).
