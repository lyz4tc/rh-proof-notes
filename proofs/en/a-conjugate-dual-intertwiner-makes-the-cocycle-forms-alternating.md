# A conjugate-dual intertwiner makes the cocycle forms alternating

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $G,\sigma,L$ be as in the [polarized cocycle calculation](polarized-cocycle-evaluations-span-when-the-representations-differ.md). Let $T:G\to\operatorname{GL}_r(K)$ linearly span $M_r(K)$, with $r$ odd, and suppose $T|_L=1$. Let $\epsilon:G\to K^\times$ be $\sigma$-invariant. Suppose an invertible matrix $A$ gives the relation

$$
 T(\sigma g)^{\mathsf t}A T(g)=\epsilon(g)A .
$$

Assume $z$ is central modulo $L$, $T(z)=dI$, $\epsilon(z)=1$, and $d^2\ne1$. Let $x_1,\ldots,x_n$ be cocycles of $T$ representing linearly independent classes.

**Proposition.** The matrices
$M(h)_{ij}=x_i(h)^{\mathsf t}A x_j(\sigma h)-x_i(\sigma h)^{\mathsf t}A x_j(h)$, $h\in L$, span all alternating $n\times n$ matrices over $K$. An alternating matrix here has diagonal zero and $M_{ji}=-M_{ij}$, including in characteristic two.

**Proof.** Apply the intertwining identity at $\sigma g$ and transpose it. This gives the same identity for $A^{\mathsf t}$, since $\sigma^2=1$ and $\epsilon(\sigma g)=\epsilon(g)$. Hence $A^{-1}A^{\mathsf t}$ commutes with every $T(g)$. The commutant of all matrix units consists of scalars, so $A^{\mathsf t}=bA$ for some $b\in K^\times$. Transposing twice gives $b^2=1$, and taking determinants gives $b^r=1$. Since $r$ is odd, $b=1$. The matrices $M(h)$ are therefore alternating.

Suppose $C=(c_{ij})$ annihilates every $M(h)$ under the entrywise pairing, and put $a_{ij}=c_{ij}-c_{ji}$. By symmetry of $A$, the assumed identity is $P(h,h)=0$ for the bilinear expression on cocycle values

$$
 P(h,k)=\sum_{i,j} a_{ij}\,x_i(h)^{\mathsf t}A x_j(\sigma k).
$$

The restrictions of the cocycles to $L$ are additive, so evaluating at $hk$ gives $P(h,k)+P(k,h)=0$ for $h,k\in L$. In particular the same equation holds with $k$ replaced by $zkz^{-1}$. The intertwining identity at $z$ gives $T(\sigma z)=d^{-1}I$. Conjugating $k$ in the first slot of $P$ scales it by $d$, while conjugating it in the second slot scales it by $d^{-1}$. Hence $d^{-1}P(h,k)+dP(k,h)=0$. Combining the two relations and using $d^2\ne1$ gives $P(h,k)=0$.

For fixed $k$, set $w_i=A\sum_j a_{ij}x_j(\sigma k)$. Conjugating $h$ by an arbitrary $g$ now gives $\sum_i (T(g)x_i(h))^{\mathsf t}w_i=0$. Replace $T(g)$ by any matrix using the spanning assumption, then evaluate at a matrix unit $E_{pq}$. It gives $\sum_i (w_i)_p (x_i(h))_q=0$ for each $p,q$. The [restriction argument](a-central-scalar-keeps-cocycle-classes-visible-on-a-small-subgroup.md) applied with scalar $d$ makes the restrictions of the $x_i$ independent, so each $w_i=0$. Varying $k$ through $L$, using invertibility of $A$ and $\sigma(L)=L$, the same independence gives $a_{ij}=0$. Thus every annihilator of the $M(h)$ is symmetric. Conversely any symmetric array annihilates all alternating matrices, by cancelling paired off-diagonal entries and using zero diagonal. The double annihilator gives the desired span in every characteristic.

If the second cocycle family is obtained from $x_j$ by $y_j(\sigma g)=A x_j(g)$, these are exactly the two-evaluation forms between $x_i$ and $y_j$ used in the Selmer application.

**Lean correspondence.** `symm_of_invariant` proves symmetry of the intertwiner. The polarization, scalar separation and entrywise test are `symm_of_forms`, using `comb_vanish` for the matrix units. `spanTwo_of_galHyp` supplies the residual representation hypotheses. Source-based reconstruction. [Odd rank gives a symmetric intertwiner](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SpanTwoOfGaloisHypothesis.lean#L42) · [Separating coordinates by matrix units](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SpanTwoOfGaloisHypothesis.lean#L96) · [The alternating span](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SpanTwoOfGaloisHypothesis.lean#L110) · [The residual conjugate-dual case](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SpanTwoOfGaloisHypothesis.lean#L196).
