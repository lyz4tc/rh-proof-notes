# A deep weight shift forces the required gap and generic tests

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $a\ge1$, let $\lambda_0\ge\cdots\ge\lambda_{a-1}$ be an integral dominant weight, and set $J_i=i-\lambda_i$. Suppose for nonnegative integers $D,N$ that
$$
\bigl|\lambda_i+N(a+1)^i\bigr|\le D\quad(0\le i<a),
\qquad (a+1)(2D+a)<N .
$$
Then $J_0<\cdots<J_{a-1}$ and $a(J_i-J_0)<J_{i+1}-J_0$ for all $i<a-1$. This gives a sufficient condition for the lacunary weight used by the geometric seed. The same congruence argument also uses a nonzero polynomial `DGen` to impose genericity on finite Satake multisets. [Weight estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/CongruenceOddLevel/LacunaryBaseWeightAntitone.lean#L48) · [Definition of `DGen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/LimWPhi.lean#L14)

## Dominant weights near a rapidly decreasing weight

Write $e_i=\lambda_i+N(a+1)^i$, so that $|e_i|\le D$. Dominance gives $J_{i+1}-J_i\ge1$. For adjacent indices,
$$
\begin{aligned}
(J_{i+1}-J_0)-a(J_i-J_0)
 &=N\bigl((a+1)^i+a-1\bigr)+1-(a-1)i\\
 &\qquad+a(e_i-e_0)-(e_{i+1}-e_0).
\end{aligned}
$$
The quantity multiplying $N$ is at least $1$. The linear term in $i$ is bounded below by $-a(a+1)$, and the error from the $e_i$ is bounded below by $-2D(a+1)$. Hence the expression is positive by the bound on $N$. This calculation uses the project's $a$ jumps obtained from the infinitesimal-character multiset by $z\mapsto(a-1)/2-z$, which gives exactly $J_i=i-\lambda_i$. The [average comparison](a-gap-condition-separates-the-averages-of-disjoint-weight-sets.md) then proves lacunarity.

## A polynomial testing several genericity conditions at once

For indeterminates $X_0,\ldots,X_{a-1}$, the genericity polynomial is the product of the following binomials, with the indicated finite ranges:
$$
\begin{array}{ll}
X_i^c-X_j^c & i\ne j,\ 1\le c\le a,\\
X_iX_k-X_j^2 & j\ne i,\ j\ne k,\\
\prod_i X_i^{m_i}-\prod_i X_i
  & m_i\ge0,\ \sum_i m_i=a,\ (m_i)_i\ne(1)_i .
\end{array}
$$
The middle family allows $i=k$. In each binomial the exponent vectors of the two monomials differ. For the first family they differ at $i$. For the second they differ at $j$. For the third this is the condition excluding the all-ones vector. The two monomials are therefore linearly independent over $\mathbb Z$, so every factor is nonzero. The polynomial ring is an integral domain, proving that the full product is nonzero. Empty products are interpreted as $1$. [Nonvanishing proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/CongruenceOddLevel/LacunaryBaseWeightAntitone.lean#L90)

The nonvanishing condition at a Satake multiset is imposed for every ordering of its eigenvalues. In particular it yields pairwise distinct eigenvalues and product-genericity. To check the latter, label the distinct entries by their indices. A multiset of size $a$ selected from them with repetition is specified by its multiplicities $m_i$, and a different multiset from the original is one with $(m_i)_i\ne(1)_i$. The last family of factors excludes equality of its product with the original product. This is the genericity used in identifying the exact local roots of the extracted representation. [From the test to product-genericity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/ZetaCharacterDivisibility/PDGenMul.lean#L16)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
