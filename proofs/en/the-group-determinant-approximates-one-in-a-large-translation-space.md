# The group determinant approximates one in a large translation space

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $k$ be a field with a nonarchimedean absolute value, $\ell$ a prime integer, and $H$ a finite group of $\ell$-power order. Let $P\subseteq k^H$ be a linear subspace stable under right translation $c(x)\mapsto c(xh)$ by every $h\in H$. If $2\dim P\ge |H|$, there exists $c\in P$ with
$$
 \max_{x\in H}|1-c(x)|\le |\ell|^{1/2}.
$$
The application uses $k=\overline{\mathbb Q}_\ell$, with the conclusion also transferred to $\mathbb C$ by an isomorphism of fields. This is the numerical improvement step in the approximation by generic automorphic forms. [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GroupDetAlt.lean#L35) · [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/AlgPf.lean#L4)

## The determinant bound

For a function $a\colon H\to k$ with $|a(h)|\le1$, put $N=|H|$ and form the matrix $A_{x,y}=a(xy^{-1})$. This is the matrix $\sum_h a(h)L_h$, where $L_h$ is the integer permutation matrix of left multiplication by $h$ on $H$. We claim that
$$
 \left|\sum_h a(h)\right|^N\le |\ell|^{N-\operatorname{rank}A}.
$$
Every finite-dimensional $\mathbb F_\ell$-representation of $H$ admits a flag with successive one-dimensional trivial quotients. In a nonzero representation space, the number of fixed vectors is a multiple of $\ell$, since all nontrivial orbits have cardinality divisible by $\ell$ and the space itself has $\ell$-power cardinality. There is a nonzero fixed vector. Applying this to successive quotients constructs the flag. Use an adapted basis for the regular representation modulo $\ell$, and lift its change-of-basis matrix and inverse to integer matrices $P_0,Q_0$. For each $h$ the matrix $Q_0 L_h P_0$ is upper triangular with diagonal $1$ modulo $\ell$. [Flag and lifted matrices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/ExistsInvariantFlagModL.lean#L62) · [Triangularization modulo $\ell$](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/TriMat.lean#L22)

In $A'=Q_0 A P_0$, the lower triangular entries off the diagonal are therefore $\ell$ times sums of integer multiples of $a(h)$, and the diagonal differs from $\sum_h a(h)$ by such quantities. Choose a matrix $B$ by negating those sums on and below the diagonal and taking zeros above it. Then $A'+\ell B$ is upper triangular with constant diagonal $\sum_h a(h)$. The entries of $A'$ and $B$ have norm at most $1$, and $\operatorname{rank}A'\le\operatorname{rank}A$. Expanding $\det(A'+\ell B)$ by multilinearity in the columns, every term that chooses more than $\operatorname{rank}A$ columns from $A'$ vanishes. The others contain at least $N-\operatorname{rank}A$ factors of $\ell$. Each determinant made out of columns of $A'$ and $B$ has norm at most $1$, by the ultrametric bound on the permutation expansion. Since $|\ell|\le1$, this proves the claim. [Column determinant estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/DetLow.lean#L56) · [Group determinant](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GroupDet.lean#L19)

## Distance to a subspace over an ultrametric field

In any finite coordinate space $k^X$, if $\big|\sum_x a(x)v(x)\big|\le r$ for all $|a(x)|\le1$ annihilating a subspace $P$, then some $c\in P$ satisfies $\max_x|v(x)-c(x)|\le r$. Here is the elimination proof. If $P=0$, test with each coordinate evaluation. Otherwise choose a nonzero vector in $P$ and divide by a coordinate of maximum norm to give $p\in P$ with $p(x_0)=1$ and $\max_x|p(x)|\le1$. Write $P_0=\{u\in P:u(x_0)=0\}$ and $v_0=v-v(x_0)p$. Given a bounded coefficient functional $a$ annihilating $P_0$, the functional $a_0=a-a(p)\operatorname{ev}_{x_0}$ annihilates $P$ and is still bounded by $1$ in each coefficient. Moreover $a(v_0)=a_0(v)$, so $v_0$ satisfies the same hypothesis for $P_0$. Induct on dimension to find $c_0\in P_0$ within $r$ of $v_0$, then take $c=v(x_0)p+c_0$. [Ultrametric elimination](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/ExistsCloseVectorUltrametric.lean#L8)

Apply this with the vector $v=1$. If $a$ annihilates $P$, then so do the columns of $A$ for the preceding pairing:
$$
 \sum_x a(xy^{-1})c(x)=\sum_u a(u)c(uy)=0\quad(c\in P).
$$
The last equality uses right translation stability. Thus $\operatorname{rank}A\le N-\dim P$. The group determinant claim gives $\left|\sum_xa(x)\right|^N\le|\ell|^{\dim P}$. Since $2\dim P\ge N$, this implies $\left|\sum_x a(x)\right|\le|\ell|^{1/2}$. The case $|\ell|=0$ also follows because $\dim P>0$. The subspace estimate now gives the desired vector $c$. [Using the rank bound in the dual inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/AlgPf.lean#L4)

## Lean correspondence

- `UpperTheory.Gal.Gen.groupDet_pf` uses modular triangularization and a rank-sensitive determinant bound. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GroupDet.lean#L19)
- `UpperTheory.Gal.Gen.hB_pf` proves the finite coordinate approximation from bounded annihilators. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/ExistsCloseVectorUltrametric.lean#L108)
- `UpperTheory.Gal.Gen.alg_pf` applies the two results to the constant function, and `algC_pf` transports the conclusion across the coefficient field isomorphism. [Approximation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/AlgPf.lean#L4) · [Transport](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/AlgCPf.lean#L9)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
