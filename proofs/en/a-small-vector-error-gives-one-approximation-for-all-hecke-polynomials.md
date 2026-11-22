# A small vector error gives one approximation for all Hecke polynomials

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $L=\overline{\mathbb Q}_\ell$ with its $\ell$-adic norm, and fix an isomorphism $\iota\colon L\simeq\mathbb C$. Let $V$ be a complex vector space, $T_j$ linear operators indexed by a set $J$, and $e_x\colon V\to\mathbb C$ linear functionals indexed by a set $X$. Assume that $T_j$ sends vectors whose every $|\iota^{-1}e_x|$ is at most $R$ to vectors with the same bound, for every $j$ and every real $R$. Suppose $v_0$ and a finite family $v_i$ are simultaneous eigenvectors, with eigenvalues $\theta_j,\eta_{i,j}$, and that $|\iota^{-1}e_{x_0}(v_0)|=1$ for some $x_0$. If
$$
\left|\iota^{-1}e_x\!\left(v_0+\sum_i v_i\right)\right|\le\varepsilon
\quad\text{for all }x,
$$
then there are coefficients $c_i\in L$, independent of the polynomial, for which
$$
\left|P(\iota^{-1}\theta)-\sum_i c_i P(\iota^{-1}\eta_i)\right|\le\varepsilon
\qquad(P\in\mathbb Z[X_j:j\in J]).
$$
The coefficients of repeated eigenvalue tuples may be combined. When such approximations exist for every $\varepsilon>0$ with finite sets drawn from a prescribed set of tuples, the project calls the result `PolyApprox`. [Small-vector theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/EigenvectorSmallSubFiniteEigenApproxInequality.lean#L9) · [Definition of the approximation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/PolyApproxZeroPadic.lean#L10)

## Proof

For an integer polynomial $P$ put
$$
u(P)=P(\theta)v_0+\sum_i P(\eta_i)v_i.
$$
For a constant integer $n$, the assertion $|\iota^{-1}e_x(u(n))|\le\varepsilon$ holds by the hypothesis on $v_0+\sum_i v_i$ and the bound $|n|_\ell\le1$. It is closed under polynomial addition by the ultrametric inequality. Also $u(X_jP)=T_j u(P)$, by the simultaneous eigenvector identities. The contraction hypothesis gives the assertion for $X_jP$ whenever it holds for $P$. These rules give it for all integer polynomials, each of which uses only finitely many variables and monomials.

Apply it at $x_0$ and divide by the unit $\iota^{-1}e_{x_0}(v_0)$. Then the coefficients
$$
c_i=-\frac{\iota^{-1}e_{x_0}(v_i)}{\iota^{-1}e_{x_0}(v_0)}
$$
give the required inequality. Since they were chosen before $P$, this works uniformly for all polynomials. [Induction and coefficient choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/EigenvectorSmallSubFiniteEigenApproxInequality.lean#L9)

## Cutting by an additional polynomial test

Suppose an evaluation at $\theta$ can be approximated from evaluations at tuples in $S$, and for each $\eta\in S$ the evaluation at $\eta$ can be approximated by tuples in $T$. Suppose also a fixed integer polynomial $Q$ satisfies $Q(\eta)\ne0$ on $S$. Then the evaluations approximating $\theta$ can be taken at tuples in $T$ with nonzero $Q$.

For one $\eta$, apply its approximation at error $\varepsilon |Q(\eta)|$ to $P Q$ and divide by $Q(\eta)$. The new coefficient on a tuple $\zeta$ is the old coefficient times $Q(\zeta)/Q(\eta)$. If $Q(\zeta)=0$, it contributes zero for every $P$. Thus the approximation to $\eta$ can be restricted to the desired tuples. Compose with the approximation to $\theta$, first choosing error $\varepsilon/2$ for its finite combination with coefficients $b_\eta$. Approximate each intermediate evaluation at error $\varepsilon/[2(1+\sum_\eta |b_\eta|)]$. Substitution and the triangle inequality bound the total error by $\varepsilon$. The coefficients are still independent of $P$. This explains how genericity tests are maintained while changing weights and adding local types. [Cutting and composing in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/Combine.lean#L11) · [Combined theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/Combine.lean#L94)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
