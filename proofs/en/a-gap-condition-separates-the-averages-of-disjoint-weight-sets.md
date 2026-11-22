# A gap condition separates the averages of disjoint weight sets

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $J=\{j_0<j_1<\cdots<j_{a-1}\}$ be a finite set of $a$ integers. Suppose that for $0\le i<a-1$,
$$
a(j_i-j_0)<j_{i+1}-j_0.
$$
Then for any two disjoint nonempty subsets $A,B\subseteq J$ their averages are different:
$$
|B|\sum_{x\in A}x\ne |A|\sum_{x\in B}x.
$$
This is the meaning of a lacunary set of weights in the rank-extraction argument. At $a=0$ or $a=1$ there are no such two subsets, and the conclusion holds. [Gap condition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/LimWPhi.lean#L20) · [Definition of lacunarity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/DivisionOfDeterminantCharacter.lean#L15) · [Lean theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/ZetaCharacterDivisibility/PGapLac.lean#L52)

## Proof

Let $m$ be the largest element of $A\cup B$. Suppose $m\in A$, interchanging the sets if necessary. All gaps here are measured from the same minimum $j_0$. If $b<m$ is in $J$ and $m=j_k$, then $k\ge1$ and $b\le j_{k-1}$, so
$$
a(b-j_0)\le a(j_{k-1}-j_0)<m-j_0.
$$
Every $b\in B$ meets this inequality because $A$ and $B$ are disjoint. Since $|A|\le a$ and $b-j_0\ge0$, summing gives
$$
|A|\sum_{b\in B}(b-j_0)<|B|(m-j_0)
 \le |B|\sum_{x\in A}(x-j_0).
$$
The last bound holds because $m\in A$ and the other terms of the sum are nonnegative. Adding $|A||B|j_0$ to both ends gives strictly smaller average for $B$. Thus the larger maximum also determines the larger average. [The comparison inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/ZetaCharacterDivisibility/PGapLac.lean#L23)

In the geometric construction, the coefficient-prime place $v'$ carries a comparison at a weight satisfying this gap condition. It supplies a subcollection of distinct Hodge–Tate jumps of the same size as the required rank. The algebraic rank selector uses the separation of averages of disjoint subcollections of those jumps.


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
