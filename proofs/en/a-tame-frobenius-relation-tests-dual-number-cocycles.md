# A tame Frobenius relation tests dual-number cocycles

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a residue prime $\ell$, an integer $M\ge1$ and a finite place $v\nmid\ell$ of norm $q$ with $q\equiv1\pmod{2\ell^M}$. Let $D_v$ and $I_v$ be its decomposition and inertia groups. Let $d:D_v\to\mathbb Z/\ell^M\mathbb Z$ be continuous and surjective on inertia. Fix a Frobenius lift $\phi$ with the convention that it conjugates tame inertia by the $q$-th power. The prime-to-$\ell$ inertia kernel $J$ is normal in $D_v$, its finite continuous quotients have order prime to $\ell$, and $I_v/J\simeq\mathbb Z_\ell$ admits a lift $\gamma_0$ of a topological generator. Modulo $J$ one has $\phi\gamma_0\phi^{-1}=\gamma_0^q$. These are the tame quotient facts used in the proof.

**Proposition.** There exists $\gamma\in I_v$ with $d(\gamma)=1$ such that for every field $K$ of characteristic $\ell$, $K$-space $W$, and continuous maps $z_0,z_1:D_v\to W$ and $\lambda:D_v\to K$ with discrete targets, the following holds. Suppose $z_0,\lambda$ are additive homomorphisms and

$$
z_1(gh)=z_1(g)+z_1(h)+\lambda(g)z_0(h).
$$

Then $z_0(\gamma)=0$ implies $z_0|_{I_v}=0$, and
$\lambda(\gamma)z_0(\phi)=\lambda(\phi)z_0(\gamma)$.

**Proof.** Every continuous additive homomorphism from $J$ to an additive group of characteristic $\ell$ vanishes, since its finite image is an $\ell$-group and also a prime-to-$\ell$ quotient. The same reasoning makes $d|_J=0$. Consequently $d(\gamma_0)$ generates the cyclic quotient, so choose an integer $k$ prime to $\ell$ with $k\,d(\gamma_0)=1$. Put $\gamma=\gamma_0^k$. If $z_0(\gamma)=kz_0(\gamma_0)=0$, the scalar $k$ is invertible in $K$, so $z_0(\gamma_0)=0$. Continuity, generation modulo $J$, and $z_0|_J=0$ give vanishing throughout inertia.

The restrictions of $z_0,\lambda$ to $J$ vanish. On $J$ the law for $z_1$ thus reduces to additivity, so $z_1|_J=0$ as well. The three functions descend across $J$, since their values at $gj$ equal those at $g$ for $j\in J$. The law for $z_1$ gives by induction

$$
z_1(\gamma_0^q)=qz_1(\gamma_0)+\binom q2\lambda(\gamma_0)z_0(\gamma_0).
$$

The congruence on $q$ gives $q=1$ and $\binom q2=0$ in $K$. The factor $2$ in the modulus ensures the latter even in characteristic two, since $q(q-1)/2$ is divisible by $\ell$. Thus $z_1(\gamma_0^q)=z_1(\gamma_0)$ and $\lambda(\gamma_0^q)=\lambda(\gamma_0)$. Evaluate $z_1$ on $\phi\gamma_0=\gamma_0^q\phi$ modulo $J$. Cancelling the two common terms gives $\lambda(\phi)z_0(\gamma_0)=\lambda(\gamma_0)z_0(\phi)$. Multiplication by $k$ yields the formula with $\gamma$.

This law applies to a cocycle with coefficients in $W\otimes K[\epsilon]/(\epsilon^2)$ if the original representation is trivial on $D_v$ and the new twist there is $1+\epsilon\lambda(g)$. The constant term of the cocycle is $z_0$; its first-order coefficient is $z_1$.

**Lean correspondence.** `hom_trivial` and `vanish_of_additive` use the prime-to-$\ell$ inertia quotients. `second_pow` expands the cocycle on powers, `cast_of_mod` proves the two scalar congruences, and `tame_relation` gives the stated Frobenius–inertia test. Source-based reconstruction. [Prime-to-residue inertia vanishing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TameLocalRelationDualNumberCocycle.lean#L15) · [Power law for a first-order cocycle](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TameLocalRelationDualNumberCocycle.lean#L65) · [Congruences in the residual field](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TameLocalRelationDualNumberCocycle.lean#L84) · [The tame local relation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TameLocalRelationDualNumberCocycle.lean#L101).
