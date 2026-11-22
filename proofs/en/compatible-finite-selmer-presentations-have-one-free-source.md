# Compatible finite Selmer presentations have one free source

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $(\Lambda,\mathfrak m,k)$ be a Noetherian local ring with finite residue field. Let $F$ be a $\Lambda$-linear left-exact functor on $\mathfrak m$-power torsion modules with $F(k)$ finite. Here each element is killed by some power of $\mathfrak m$, with the power allowed to depend on the element. For each $n\ge1$ choose a [finite representing pair](a-maximal-minimal-pair-represents-the-finite-selmer-stage.md) $(M_n,\xi_n)$ for finite modules killed by $\mathfrak m^n$. The module $M_n$ is itself killed by $\mathfrak m^n$. Any distinguished element at that level comes from $\xi_n$, and two maps from $M_n$ into any torsion target coincide if their evaluations on $\xi_n$ coincide under $F$.

**Proposition.** The transition maps $t_n:M_{n+1}\to M_n$ carrying $\xi_{n+1}$ to $\xi_n$ under $F$ are surjective with kernel $\mathfrak m^nM_{n+1}$. There are compatible surjections $p_n:\Lambda^a\to M_n$, with $a=\dim_k M_1$, $t_np_{n+1}=p_n$ and $\ker p_1=\mathfrak m\Lambda^a$.

**Proof.** Representability at level $n+1$ produces $t_n$, since $M_n$ is a finite target at that level. The projection $M_n\to\operatorname{coker}t_n$ evaluates to zero on $\xi_n=F(t_n)\xi_{n+1}$. Uniqueness at level $n$ forces the projection to be zero, so $t_n$ is surjective.

The inclusion $\mathfrak m^nM_{n+1}\subseteq\ker t_n$ follows from annihilation of $M_n$. For the reverse inclusion take the projection $q:M_{n+1}\to M_{n+1}/\mathfrak m^nM_{n+1}$. Its target is finite and killed by $\mathfrak m^n$, so representability at level $n$ supplies $v$ from $M_n$ into that quotient with $F(v)\xi_n=F(q)\xi_{n+1}$. Then $vt_n$ and $q$ evaluate equally on $\xi_{n+1}$ and hence coincide. This puts $\ker t_n$ inside $\ker q=\mathfrak m^nM_{n+1}$.

Send the free basis of $\Lambda^a$ to a $k$-basis of $M_1$ to obtain $p_1$ and its stated kernel. Given $p_n$, lift its basis images to $M_{n+1}$ to obtain $p_{n+1}$. Every $y\in M_{n+1}$ agrees modulo $\ker t_n$ with such an image: lift $t_n(y)$ to $x\in\Lambda^a$ and use $p_{n+1}(x)$. Since the transition kernel is contained in $\mathfrak mM_{n+1}$, Nakayama's lemma shows that $p_{n+1}$ is surjective. This gives the whole tower by induction.

In particular, writing $P=\Lambda^a$ and $N_n=\ker p_n$, one has

$$
N_n=N_{n+1}+\mathfrak m^nP.
$$

Indeed $N_n$ is the preimage of $\mathfrak m^nM_{n+1}$ under $p_{n+1}$, and surjectivity allows each element of that submodule to be lifted from $\mathfrak m^nP$.

**Lean correspondence.** `kernelRep` constructs the transitions, proves surjectivity and bounds their kernels. The other inclusion is automatic from the annihilation of $M_n$. `exists_surjective_lift_of_ker_le_maximalIdeal_smul` gives the Nakayama step, and `exists_compatible_generators_tower` gives one free source. Its residue-basis argument applies to any finite first module. Here $M_1$ already is a $k$-space. Source-based reconstruction. [Construction of the transitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TorsionLeftExactFunctorKernelSquareMatrix.lean#L340) · [Lifting generators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCompatibleGeneratorsTowerLocalRing.lean#L36) · [The compatible free source](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCompatibleGeneratorsTowerLocalRing.lean#L55).
