# The split generator lies in the quadratic order

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $d$ be an odd positive prime, and let $a,b\in\mathbb Q$ satisfy $2a\in\mathbb Z$ and $a^2+db^2=g\in\mathbb Z$. Then
$$
a+b\sqrt{-d}=m+n\frac{1+\sqrt{-d}}2,\qquad m,n\in\mathbb Z.
$$
In the application, $d\equiv3\pmod4$ and $E$ contains $\mathbb Q(\sqrt{-d})$. Suppose the type-prime generator $\pi\in\mathcal O_E$ belongs to this quadratic subfield and $\pi\bar\pi=p$, where $p$ is its associated rational prime and conjugation restricts to quadratic conjugation. For a complex embedding sending $\sqrt{-d}$ to $i\sqrt d$, the image of $\pi$ lies in the quadratic order $\mathbb Z[(1+i\sqrt d)/2]$. Its membership is called `IsQInt` in the analytic split-prime estimate.

### Proof

Put $t=2a\in\mathbb Z$. The norm relation gives
$$
\bigl(d(2b)\bigr)^2=d(4g-t^2)\in\mathbb Z.
$$
A rational number whose square is an integer is itself an integer, by writing it in lowest terms. Write $r=d(2b)\in\mathbb Z$. Since the prime $d$ divides $r^2$, it divides $r$, so $n=2b=r/d$ is an integer. Now $t^2+dn^2=4g$ and $d$ is odd, so modulo two, $t$ and $n$ have the same parity. Therefore $m=(t-n)/2\in\mathbb Z$. Substituting $a=m+n/2$ and $b=n/2$ yields the formula.

For $\pi=a+b\sqrt{-d}\in\mathcal O_E$, the trace $\pi+\bar\pi=2a$ is both rational and an algebraic integer, so it lies in $\mathbb Z$. Its product with $\bar\pi$ is $a^2+db^2=p$. The preceding argument applies, and the stated complex embedding gives the claimed order membership. At the chosen CM embeddings of the project all the restrictions to this quadratic field agree. Hence the same complex image $\pi$ can be used in their split-prime estimates.

### Lean correspondence

- [`IsQInt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/StatementB.lean#L16) defines order membership in the basis $1,(1+i\sqrt d)/2$.
- [`half_coords`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L171) is the rational coordinate argument, and [`isQInt_piG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L195) applies trace integrality and the prescribed norm to the actual generator.
- [`JetSplitAmb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/JetSplitAmb.lean#L15) requires this order membership and the splitting conditions when applying the local scaled jet estimate.

Status. Source-based reconstruction draft. The application uses a chosen type-prime generator in the quadratic subfield and its prescribed norm. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
