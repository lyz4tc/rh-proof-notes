# One prime-to-$p$ integer clears both lattice inclusions

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be a number field, $p$ a rational prime, and $M,M'$ submodules of an $\mathcal O_E$-module $W$. Assume $M$ is finitely generated and that at every prime $P$ of $\mathcal O_E$ above $p$, each element of $M$ belongs to the localization of $M'$ at $P$. In other words, for every $x\in M$ and $P\mid p$ some $a\in\mathcal O_E\setminus P$ satisfies $ax\in M'$. Then there is an integer $s\ge1$ with $p\nmid s$ and $sM\subseteq M'$.

In particular, if a full lattice $N\subseteq E^n$ is standard at all $P\mid p$, meaning $N_{(P)}=\mathcal O_{E,P}^{\,n}$ at each such $P$, then there is a single integer $s\ge1$ prime to $p$ such that
$$
sN\subseteq\mathcal O_E^n,\qquad s\mathcal O_E^n\subseteq N .
$$
These two inclusions express the comparison with the standard lattice used in the split-prime jet argument.

### Proof

Fix $x\in M$ and let $I_x=\{a\in\mathcal O_E:ax\in M'\}$. This is an ideal, and the localization hypothesis says that $I_x$ is contained in no prime of $\mathcal O_E$ over $p$. Consequently $I_x+p\mathcal O_E=\mathcal O_E$. Indeed, any proper sum would be contained in a maximal ideal $P$ above $p$ and would imply $I_x\subseteq P$. Choose $a\in I_x$ with $a\equiv1\pmod{p\mathcal O_E}$.

The matrix of multiplication by $a$ on the free abelian group $\mathcal O_E$ reduces to the identity modulo $p$. Its determinant is $\mathrm N_{E/\mathbb Q}(a)\equiv1\pmod p$. Furthermore that determinant belongs to $a\mathcal O_E$. To see this, apply the adjugate of the multiplication matrix to the element $1\in\mathcal O_E$. Multiplying the resulting element by $a$ gives $\mathrm N_{E/\mathbb Q}(a)\cdot1$. Since $I_x$ is an ideal and $a\in I_x$, the positive integer $s_x=|\mathrm N_{E/\mathbb Q}(a)|$ belongs to $I_x$ and is prime to $p$.

Choose finitely many generators of $M$ and multiply their integers $s_x$. The resulting $s$ is prime to $p$ and sends every generator into $M'$, so $sM\subseteq M'$. For the lattice assertion, apply the result first to $(M,M')=(N,\mathcal O_E^n)$, then to $(\mathcal O_E^n,N)$. Both source modules are finitely generated. Multiplying the two prime-to-$p$ integers gives a single integer that works for both inclusions.

### Lean correspondence

- [`StdOver`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/CharacterValuation.lean#L29) asserts standardness at all places above $p$. [`exists_denom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/DatumJetsTranslate.lean#L18) gives the prime-to-$p$ integer for a single inclusion. In the formal proof, if $I_x\cap\mathbb Z$ were contained in $(p)$, lying over for the integral extension $\mathbb Z\subseteq\mathcal O_E$ would give a prime $P\mid p$ containing $I_x$. The norm argument above proves the same implication directly.
- [`stdAt_of_stdOver`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/DatumJetsTranslate.lean#L59) obtains both inclusions and transports them to the ambient analytic lattice. [`mem_stdL` and `eqAt_std`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CoeffInLetters.lean#L22) identify the standard integral coordinates on the analytic side.
- [`jetLossAll_of_jetSplitAmb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L261) uses the comparison for both source and target lattices before applying the split-prime estimate.

Status. Source-based reconstruction draft. The lattice lemma takes finite generation and standardness at every $P\mid p$ as input. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
