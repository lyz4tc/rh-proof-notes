# Finite-place bumps make the stable-range theta lift nonzero

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the CM base and definite unitary Weil pair $U(X)\times U(W)$ of the [stable-range lift](a-definite-theta-lift-in-the-stable-range.md), with $1\le n$, $2n\le d$, its certified global model and splitting characters, and the identifications with the standard groups. Take the doubled embedding $e$, Siegel stabilizer and height $a$, and suppose $A(g)=a(e(g,1))$ has integrable powers $A^t$ for all $t\ge t_0$ with $t_0<d/2$. Let $U$ be an irreducible automorphic representation of the source and $f_\infty,\phi$ be a nonzero Schwartz polynomial vector and nonzero form which are images of one vector in a common finite-dimensional irreducible representation of the source group at infinity. The maps taking that vector to $f_\infty$ and $\phi$ must intertwine the two actions, as in the [archimedean construction](leading-minors-give-the-two-archimedean-types-in-theta.md). Then one can choose local Schwartz functions $\Phi_v$, equal to the model's vacuum at all but finitely many places, such that the theta lift of $\phi$ with $\Phi=f_\infty\otimes\bigotimes_v\Phi_v$ is nonzero. [Statement of `NonVan_k`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/GalTPDefs.lean#L114) · [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGNonVan.lean#L26)

## Matrix coefficients and a choice of test functions

Put $G=U(X)(\mathbb A_F)$ and write $[G]=U(X)(F)\backslash G$ with its quotient measure. The identifications let us regard $\phi$ as a function on $[G]$. Write
$$
m(g)=\int_{[G]}\phi(yg)\overline{\phi(y)}\,dy,\qquad
C_\Phi(g)=\int \bigl(\omega(g,1)\Phi\bigr)(Z)\overline{\Phi(Z)}\,dZ .
$$
The second integral is on the additive space $M_{n,d}(\mathbb A_F)$, with any additive Haar measure. Compactness and continuity give $r=m(1)=\|\phi\|_2^2>0$. The right translations are unitary for the quotient measure, so Cauchy–Schwarz gives $|m(g)|\le r$. The [doubling argument](a-doubled-eisenstein-pairing-detects-the-theta-lift.md) says that if the lift vanishes then the absolutely convergent integral of $C_\Phi(g)\overline{m(g)}$ over $G$ is zero. It suffices to choose $\Phi$ to make this integral nonzero. [The automorphic matrix coefficient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SchurStep.lean#L25) · [The matrix-coefficient bound and the reduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGNonVan.lean#L36)

For a finite place set $S$, write $G=G_\infty\times G_S\times G^S$, separating the real factors, the factors at $S$, and those outside $S$. Let $K_S\subset G_S$ and $K^S\subset G^S$ denote the subgroups integral at every place of their respective finite factors. Integrality means preserving the model's lattices. These are compact open subgroups. The source function has an open stabilizer in the finite adelic group, so $S$ may be chosen so that $\phi$ is fixed by $K^S$. Enlarge $S$ to contain every ramified place of $\chi_W$. It may be enlarged further so that, for Haar measure $\mu^S$,
$$
\int_{G^S\setminus K^S} A(c)^{d/2}\,d\mu^S(c)<\mu^S(K^S).
$$
Indeed let $K=G_\infty\times K_S\times K^S$, the full subgroup integral at all finite places, and $B_S=G_\infty\times K_S\times(G^S\setminus K^S)$. The measurable sets $B_S$ decrease to the empty set along an exhaustion of the finite places. Since $A^{d/2}\,dg$ is a finite measure, its mass on $B_S$ tends to zero and eventually is less than the positive Haar measure of $K$. The height is right invariant under integral elements, as their doubled images lie in the Siegel stabilizer, so $A(xbc)=A(c)$ for $x\in G_\infty$, $b\in K_S$. The common factor in the two product measures cancels, giving the displayed strict inequality for the outside factors. This gives a relative tail estimate although the group $G^S$ varies with $S$. [Adelic decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/GalTPDefs.lean#L69) · [Proof of the tail estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGTail.lean#L99)

At each $v\in S$ choose a nonzero Schwartz function $\Phi_v$ and a compact open integral subgroup $H_v$ small enough that it fixes $\phi$ by right translation. The finite bump lemma gives $\omega(g,1)\Phi_v=\Phi_v$ for $g\in H_v$. Its other conclusion is that if $g\notin H_v$, then there is a Heisenberg operator and its conjugate by $g$ for which $\Phi_v$ has distinct eigenvalues. Unitarity forces the local coefficient of $g$ to vanish. This lemma is where the condition $2n\le d$ is used. For $v\notin S$, choose the vacuum. Let $H=\prod_{v\in S}H_v$. The matrix-coefficient factorization in the lattice model states that $C_\Phi(1)\ne0$, and that for $x\in G_\infty,b\in G_S,c\in G^S$
$$
C_\Phi(xbc)=
\begin{cases}
s(c)C_\Phi(x),& b\in H,\\
0,&b\notin H ,
\end{cases}
\qquad |s(c)|=A(c)^{d/2},\qquad s|_{K^S}=1 .
$$
This applies to any such finite bumps with the fixed $f_\infty$. The scalar is measurable because $s(c)=C_\Phi(c)/C_\Phi(1)$. In particular the absolute value on the outside factor is the height power in the strict tail estimate. [Bump and factorization statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/GalTPDefs.lean#L77) · [Choice of bumps in the proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGNonVan.lean#L76) · [Factorization in the lattice model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGDatum.lean#L222)

## Taking the archimedean average

For $b\in H$, $\phi$ is fixed by $b$ and $b$ commutes with $c$, so $m(xbc)=m(xc)$. For the compact group $G_\infty$ one has
$$
\int_{G_\infty} C_\Phi(x)\overline{m(xc)}\,dx
=\kappa\, C_\Phi(1)\overline{m(c)},\qquad
\kappa=\frac{\operatorname{vol}(G_\infty)}{\dim V}>0,
$$
where $V$ is the common irreducible type. To obtain this, pull both coefficients back along the equivariant maps on $V$, writing $f_\infty=i(z)$ and $\phi=j(z)$. The Weil pairing on $i(V)\otimes\Phi_f$ is invariant, and the functional giving $m(xc)$ on $\rho(x)z$ includes the commuting right action of $c$. Average the conjugates of the rank-one operator $w\mapsto\langle w,z\rangle z$ under $\rho(x)$ using an invariant inner product on $V$. The average commutes with $\rho$, hence is scalar by irreducibility. Its trace gives $\operatorname{vol}(G_\infty)\|z\|^2/\dim V$, yielding the formula. [Schur coefficient identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGSchurStep.lean#L109)

Fubini now expresses $\int_G C_\Phi\overline m$, up to the positive scalar relating Haar measures, as
$$
\operatorname{vol}(H)\,\kappa C_\Phi(1)
\int_{G^S} s(c)\overline{m(c)}\,d\mu^S(c).
$$
The first factor is nonzero. On $K^S$ the integrand is exactly $r$, since both the vacuum scalar and the translation of $\phi$ are fixed there. Outside $K^S$ the absolute value of the integral is bounded by $r\int_{G^S\setminus K^S}A(c)^{d/2}\,d\mu^S(c)$, strictly less than $r\mu^S(K^S)$. The integral cannot vanish, so neither can the lift. [Product integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGNonVan.lean#L136) · [The final strict dominance argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/BlockDeterminants/AbsNe.lean#L5)

The finite bump construction and the detailed lattice-model factorization are internal inputs here. The proof gives the quantitative reason their support and height statements imply nonvanishing.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
