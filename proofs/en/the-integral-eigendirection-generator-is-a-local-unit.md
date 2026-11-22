# The integral eigendirection generator is a local unit

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be the host CM number field, $E_0$ its quadratic subfield with $E/E_0$ Galois, and $M\subseteq\mathbb C$ a number field containing the images of $E$ under the chosen embeddings $\sigma_\tau$, indexed by a finite set $\mathcal T$. These embeddings come from a fixed embedding by distinct automorphisms of $E/E_0$. Let $\mathfrak b$ be the integral half-different ideal in $E$, with $\mathfrak b^{-1}$ the fractional ideal containing $1$. For a rational prime $p$, fix an embedding $\lambda:\overline{\mathbb Q}\cap\mathbb C\to\mathbb C_p$. Assume that at all the places over $p$ induced by $\lambda\circ\sigma_\tau$, the ideal $\mathfrak b$ localizes to the unit ideal and the inertia subgroups of $\operatorname{Gal}(E/E_0)$ are trivial. In the project these two conditions follow from $p$ being outside the set of prime divisors of $Q_S$ and distinct from the distinguished host prime.

Write $L$ for the $\mathcal O_M$-span in $M^{\mathcal T}$ of the tuples $(\sigma_\tau(x))_\tau$ for $x\in\mathfrak b^{-1}$. At index $\tau_0$, let $L_{\tau_0}=\{s\in M:s e_{\tau_0}\in L\}$, where $e_{\tau_0}$ is the standard coordinate vector. If $L_{\tau_0}=\mathcal O_M s$, then $|\lambda(s)|_p=1$. The generators chosen for these rank-one modules give the normalizing directions $c_\tau$ in the split-prime derivative estimate.

### Proof

First every coordinate of $L$ has norm at most one. For a generating tuple and index $\tau$, choose $u\in\mathfrak b$ outside the ideal of elements of $\mathcal O_E$ of norm less than one under $\lambda\circ\sigma_\tau$. Such $u$ exists by the local unit assumption on $\mathfrak b$. The norm of its image is one, while $ux\in\mathcal O_E$ for $x\in\mathfrak b^{-1}$. Thus $|\lambda(\sigma_\tau(x))|_p\le1$. The same upper bound holds for $\mathcal O_M$-linear combinations by the ultrametric inequality and the norm bound for algebraic integers. In particular $|\lambda(s)|_p\le1$.

For two distinct indices $\tau_0,\tau$, there is an $x_\tau\in\mathcal O_E$ such that
$$
\bigl|\lambda(\sigma_{\tau_0}(x_\tau)-\sigma_\tau(x_\tau))\bigr|_p=1 .
$$
Indeed let $\gamma\in\operatorname{Gal}(E/E_0)$ satisfy $\sigma_\tau=\sigma_{\tau_0}\circ\gamma$. The distinctness of the embeddings gives $\gamma\ne1$. If the difference had norm less than one for every integral $x$, then $\gamma x-x$ would belong to the prime $P$ induced by $\lambda\circ\sigma_{\tau_0}$ for all $x\in\mathcal O_E$. This means that $\gamma$ preserves $P$ and acts trivially on its residue field, so it would lie in the inertia group at $P$. This contradicts the triviality assumption. The norm of the difference is at most one by integrality, so the desired value is exactly one.

For $x\in\mathcal O_E$, coordinatewise multiplication by $(\sigma_\tau(x))_\tau$ preserves $L$, since multiplying any generator by this tuple sends its parameter $a\in\mathfrak b^{-1}$ to $xa\in\mathfrak b^{-1}$. Start with the all-ones tuple in $L$ using $1\in\mathfrak b^{-1}$. Successively for each $\tau\ne\tau_0$ apply the operation
$$
(v_\eta)_\eta\longmapsto
\bigl((\sigma_\eta(x_\tau)-\sigma_\tau(x_\tau))v_\eta\bigr)_\eta .
$$
It preserves $L$, as it is the difference of the coordinatewise multiplication just considered and multiplication by the algebraic integer $\sigma_\tau(x_\tau)$ of $M$. It kills coordinate $\tau$, keeps earlier zero coordinates zero, and multiplies coordinate $\tau_0$ by an element of norm one. At the end the resulting vector is $v e_{\tau_0}\in L$ with $|\lambda(v)|_p=1$.

Since $v\in L_{\tau_0}=\mathcal O_M s$, we can write $v=a s$ with $a\in\mathcal O_M$. The norm of $\lambda(a)$ is at most one, so $1=|\lambda(v)|_p\le |\lambda(s)|_p$. Combining the two inequalities proves that $\lambda(s)$ has norm one.

### Lean correspondence

- [`mmM` and `ellT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ColumnData.lean#L159) define the span and coordinate modules. [`inertiaK_trivial`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CyclotomicBounds/RamifiedDiscriminants/OffSmall.lean#L68) gives the residue inertia condition at the allowed host primes.
- [`norm_padicEmbedding_le_one_of_mem_inverseHalfDifferent`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormPadicEmbeddingLeOneOfMemInverseHalfDifferent.lean#L64) bounds the generating coordinates, and [`exists_sep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormPadicEmbeddingLeOneOfMemInverseHalfDifferent.lean#L82) separates the two embeddings modulo the maximal ideal.
- [`mul_mem_mmM`, `norm_coord_le` and `exists_vanishing`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormPadicEmbeddingLeOneOfMemInverseHalfDifferent.lean#L133) carry out the operations on the span. [`norm_generator_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormPadicEmbeddingLeOneOfMemInverseHalfDifferent.lean#L202) concludes the unit norm.

Status. Source-based reconstruction draft. The proof assumes that the coordinate module is generated by $s$, and uses the specified local half-different and inertia conditions. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
