# A half-dimensional good space gives dense generic Hecke systems

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be a CM field, $\ell$ prime, $a\ge1$, and $\iota\colon\overline{\mathbb Q}_\ell\simeq\mathbb C$. Use the transported norm $|z|_\ell=|\iota^{-1}(z)|_\ell$ on complex scalars. Let $G$ be the standard totally definite unitary group of rank $a$, $w_0\mid\ell$ a split place of $E/E^+$, and $K$ a compact open finite level away from the pair of $w_0$. Fix an algebraic weight $W$, and a finite set $S$ of split places outside that pair where $K$ is hyperspecial. For every $w\in S$ fix a nonzero polynomial $\Phi_w$ in the $a$ Satake coordinates. A summand will be called good when $\Phi_w$ is nonzero at every ordering of its Satake multiset for every $w\in S$.

For every $K$-fixed algebraic automorphic form $f$ of weight $W$ and every $\varepsilon>0$, there is a finite sum $G_f$ of $K$-fixed forms of the same weight in good automorphic summands and a function $e$ on the adeles with
$$
 f(v)(g)-G_f(v)(g)=e(g) f(v)(g),\qquad |e(g)|_\ell\le\varepsilon.
$$
This is the density assertion `DenseGen` used to build simultaneous [Hecke and Satake approximations](one-approximation-preserves-hecke-coordinates-and-adds-generic-satake-data.md). [Density proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/DenseGen.lean#L14) · [Test-place hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GenDataEmpty.lean#L65)

## A finite $\ell$-group acting on forms

By smoothness, choose a small torsion-free principal congruence subgroup $J_0\subseteq\mathrm{GL}_a(E_{w_0})$ fixing $f$ at $w_0$. Take a nested tower $J_n$ of deeper principal congruence subgroups, normal in $J_0$, with $x^{\ell^n}\in J_n$ for every $x\in J_0$. For instance choose $J_n=1+\ell^{m+n} M_a(\mathcal O_{E_{w_0}})$ with $m\ge2$ sufficiently large. The binomial expansion of the $\ell$-th power sends $1+\ell^{m+n}X$ into $J_{n+1}$. Thus $H=J_0/J_n$ is a finite $\ell$-group, since it is finite and every element has $\ell$-power order. Let $C=KJ_0$ and $C'=KJ_n$. The projection $C\to H$ is surjective with kernel $C'$ and kills every finite-order element because $J_0$ is torsion-free. [Level tower](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/TowerPf.lean#L8) · [Passage to the finite quotient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepPf.lean#L8)

As in the [double-coset construction for local types](finite-fourier-sums-insert-a-supercuspidal-local-type.md), choose one representative per left rational and right $C G_\infty$ double coset. From the $C$-coordinate of a factorization, take its image in $H$ and call it $r(g)$. This is well-defined because a difference between two coordinates is the finite part of an element in a compact group conjugate to a rational stabilizer, hence is of finite order and has trivial image. The map is invariant under left rational and right archimedean translation, is locally constant, and satisfies $r(gc)=r(g)\lambda(c)$ for $c\in C$, with $\lambda\colon C\to H$ the quotient. For any $\varphi\colon H\to\mathbb C$ we get a form in the $C'$-fixed space by setting
$$
 \Psi(\varphi)(v)(g)=\varphi(r(g))f(v)(g).
$$
This is a linear map from $\mathbb C^H$ to the forms of weight $W$. It intertwines right translation on $H$ with right translation on forms by a lift in $C$, since $f$ is $C$-fixed. The lift does not matter on the $C'$-fixed space. [Finite-coordinate map](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepCore.lean#L9)

## Pulling back the good space

Use the [bad-space dimension estimate](separated-hecke-translates-bound-the-dimension-of-bad-forms.md) to choose $n$ with $2\dim V^{\rm bad}\le |H|$, where $V^{\rm bad}$ is the span of bad summands at weight $W$ and level $C'$. Let $V^{\rm good}$ be the corresponding good span. The full $C'$-fixed space is the sum of the two spans by irreducible decomposition. It follows that the quotient by $V^{\rm good}$ has dimension at most $\dim V^{\rm bad}$. Denote by $P=\Psi^{-1}(V^{\rm good})$ the kernel of the composite of $\Psi$ with this quotient. Then
$$
 \dim_\mathbb C P\ge |H|-\dim V^{\rm bad}\ge |H|/2 .
$$
The subspace $P$ is right-translation stable. Indeed, $C$ normalizes $C'$, so right translation by $C$ preserves the $C'$-fixed part of every global automorphic summand, and hence preserves the good span. This argument does not require $\Psi$ to be injective. [Rank-nullity and stability](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepCore.lean#L36)

By the [group determinant estimate for translation spaces](the-group-determinant-approximates-one-in-a-large-translation-space.md), transported to $\mathbb C$, some $\varphi\in P$ satisfies $|1-\varphi(h)|_\ell\le\ell^{-1/2}$ for all $h\in H$. Let $G_1=\Psi(\varphi)$. Then $G_1$ belongs to the good span and is $K$-fixed because $K\subseteq C'$. Its pointwise error from $f$ is $e_1(g)f(v)(g)$, with $e_1(g)=1-\varphi(r(g))$. This gives the uniform improvement $\ell^{-1/2}$ for any $K$-fixed form. [One improvement step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepCore.lean#L9) · [Removing the deep level from the output requirement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepPf.lean#L8)

Apply the same construction to the residual $f-G_1$, which is again $K$-fixed of weight $W$, and continue. At every step add the new good form to the previous approximant. The multiplicative error acquires one factor $e_i(g)$ of norm at most $\ell^{-1/2}$, so after $m$ steps its norm is at most $\ell^{-m/2}$. Choose $m$ with $\ell^{-m/2}\le\varepsilon$. This is the claimed approximation. [Iterating the improvement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/DenseGen.lean#L14)

## Lean correspondence

- `UpperTheory.Gal.Gen.stepCore_pf` pulls back the good space, estimates its codimension and applies the group determinant bound. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepCore.lean#L9)
- `UpperTheory.Gal.Gen.step_pf` supplies the shrinking level, finite quotient and requisite dimension bound on the bad space. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StepPf.lean#L8)
- `UpperTheory.Gal.Gen.denseGen_pf` iterates the multiplicative reduction. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/DenseGen.lean#L14)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof. The finite class set, definite-unitary decomposition and fixed-level smoothness enter through the companion proofs.
