# Conjugate Hodge filtrations fix the product of local Selmer sizes

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be the CM host field of degree $2f$, and let $E$ be the coefficient field containing the images of all the embeddings used in its local de Rham comparison at $\ell$. Fix an integral Galois representation of rank $r$ in the construction. At every $v\mid\ell$ suppose its rational version $V_v$ is de Rham and has no invariants. In the split comparison there are $2f$ embeddings of $F$ into $E$, partitioned among the induced places above $\ell$. At an embedding $\tau$ write $d_\tau$ for the dimension of the de Rham component minus the dimension of its zeroth filtered part. The conjugate-signature relation in the source is

$$
 d_\tau+d_{\tau\circ c}=r
$$

for the CM involution $c$.

**Proposition.** Writing $b_v=\dim_E H^1_f(F_v,V_v)$, one has $\sum_{v\mid\ell} b_v=fr$. Consequently for any finite residual coefficient module $B$ as in the [local count](the-crystalline-cocycle-lattice-gives-the-local-selmer-count.md),

$$
 \prod_{v\mid\ell}\# L_v(B)=
 \left(\prod_{v\mid\ell}\#H^0(F_v,B^r)\right)(\#B)^{fr}.
$$

**Proof.** The rational Bloch–Kato dimension formula is
$\dim H^1_f=\dim H^0+\dim D_{\mathrm{dR}}-\dim\mathrm{Fil}^0 D_{\mathrm{dR}}$.
The invariants vanish here. The de Rham comparison splits the period module by the embeddings of $F_v$, and the filtration splits with it. Hence $b_v$ is the sum of $d_\tau$ over the embeddings inducing $v$. The formula is the dimension consequence of the exact sequences in [Bloch and Kato, Corollary 3.8.4](https://math.stanford.edu/~conrad/BSDseminar/refs/BKTamagawa.pdf).

Every embedding induces exactly one place, obtained by restricting the coefficient valuation to $F$, so $\sum_v b_v=\sum_\tau d_\tau$. Composition by $c$ permutes the $2f$ embeddings, with no fixed embedding because each is injective and $c$ is nontrivial. Summing the conjugate-signature identity therefore gives $2\sum_\tau d_\tau=2fr$. Multiply the individual local formulas and insert this sum to obtain the product formula.

**Lean correspondence.** `embOf_bijective` identifies the simultaneous local embedding indices with all host embeddings and `exists_conj` constructs their conjugation permutation. `h1fDim_eq` uses the rational dimension formula and the split filtration, and `sum_h1fDim` sums the conjugate pairs. `locCount` inserts the local residual count at each place. The conjugate-signature relation comes from the Galois hypotheses of this setup. Source-based reconstruction. [The indexing by embeddings](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LocalCountOfSetup.lean#L370) · [The conjugate embedding permutation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LocalCountOfSetup.lean#L411) · [Dimension at one place](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LocalCountOfSetup.lean#L447) · [The total finite dimension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LocalCountOfSetup.lean#L460) · [The product of local sizes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LocalCountOfSetup.lean#L491).
