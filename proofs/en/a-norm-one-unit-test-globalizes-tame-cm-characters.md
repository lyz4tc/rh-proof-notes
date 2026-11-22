# A norm-one unit test globalizes tame CM characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM quadratic extension, with conjugation $c$, and let $(\varphi_i)_{i\in I}$ be one complex embedding of $E$ above each real embedding of $F$. Fix integers $e_i$. Let $S$ be a finite set of finite primes of $E$ such that $S\cap cS=\varnothing$, and for $v\in S$ prescribe a unitary character $\theta_v$ of the multiplicative group of its residue field. Suppose for every root of unity $\zeta\in E$ that
$$
 \prod_i\varphi_i(\zeta)^{-e_i}\prod_{v\in S}\theta_v(\bar\zeta_v)=1 .
 \tag{1}
$$
Here $\bar\zeta_v$ is the reduction at $v$. Then there is a unitary Hecke character $\chi$ of $E$, trivial on the ideles of $F$, whose archimedean components are $(z/|z|)^{-2e_i}$. It is tame at each finite prime and unramified off $S\cup cS$. On local units at $v\in S$ it induces $\theta_v$; at $c(v)$ it induces the inverse transported by conjugation. In particular the inertia orders on both sides of a prescribed pair are exactly the order of $\theta_v$.

Let $G=\mathbb A_E^\times$, and let $U=E_\infty^\times\prod_{v<\infty}\mathcal O_v^\times$. The restricted product topology makes $U$ an open subgroup. Give it the continuous unitary character
$$
 \psi\big((z_i)_i,(u_v)_v\big)
 =\prod_i(z_i/|z_i|)^{-e_i}\prod_{v\in S}\theta_v(\bar u_v).
$$
Let $A$ be the image in $G$ of the diagonal group of $k\in E^\times$ with $k\,c(k)=1$. Any element of $A\cap U$ comes from a global unit with all complex absolute values $1$, and hence a root of unity. For the latter fact, every power of this algebraic integer has all conjugates of modulus $1$ and degree at most $[E:\mathbb Q]$. The integer coefficients of those minimal polynomials are bounded by elementary symmetric sums, so only finitely many powers are possible. By (1), $\psi$ is trivial on $A\cap U$. It therefore defines a character on $UA$ by $\psi(ua)=\psi(u)$.

A circle-valued character on a subgroup of an abelian group extends to the group. One proof uses a maximal extension by Zorn's lemma. To add a new generator $g$, if its class in the quotient by the existing subgroup has finite order $m$, choose an $m$-th root of the known value at $g^m$; if the class has infinite order choose any value. This gives a consistent extension on the generated subgroup. Apply this with $UA\subseteq G$. Since the extension $\nu$ agrees with $\psi$ on the open subgroup $U$, it is continuous at the identity and hence everywhere.

Define $\chi(z)=\nu(z/c(z))$. For $z\in E^\times$, $z/c(z)\in A$, so $\chi$ descends to the idele class group. Every idele from $F$ is fixed by $c$, which proves the restriction. At a complex place, $z/c(z)=z/\overline z$, whose phase is $(z/|z|)^2$. This yields the claimed infinity type. At a finite place, a local unit goes to the quotient of that unit at its place and its conjugate at the conjugate place. The quotient belongs to $U$, so the local values follow from the formula for $\psi$. Principal units reduce to $1$, and the reduction map on units is onto. This gives unramifiedness, tameness and the exact orders.

## Lean correspondence

- [normOne_unit_isRoot](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsUnitOfRoot.lean#L37) gives the intersection calculation. [exists_anti](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsHeckeCharTrivOnRealSubfieldInfinityType.lean#L140) extends the character and applies conjugate division.
- [exists_unitary_char_of_open_subgroup_and_hom](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsUnitaryCharOfOpenSubgroupAndHom.lean#L32) gives the extension with a prescribed value on a second subgroup. [Circle character extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/AdelicLatticeProofs/ExistsContinuousCircleCharExtension.lean#L1) is the underlying algebraic and topological argument.
- [exists_hecke_trivOn](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsHeckeCharTrivOnRealSubfieldInfinityType.lean#L180) computes the local properties and exact residue orders.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
