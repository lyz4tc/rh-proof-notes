# Removing auxiliary primes gives the toric polynomial factor

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a prime $\ell$, positive integers $M,R$, and $n=\ell^M$. Let $O$ be the valuation ring of an $\ell$-adic coefficient field with uniformizer $\varpi$, write $v$ for its additive valuation, and fix one of the toric characters $\lambda$. Suppose the auxiliary primes are arranged in $R$ pairs of positions, with $Q_1$ denoting the support consisting of the first $R$ positions and $Q$ the full support. Each position denotes a conjugate pair of primes in the quadratic field. Use $X_1,\ldots,X_R$ for the first cyclic coordinates and $Y_1,\ldots,Y_R$ for the others. The corresponding coordinates have order $n$.

The coefficient input `adm9` supplies an integer $N_0\ge0$ such that $\ell^{N_0}$ clears all the toric class-sum coefficients at both supports. The removal input `adm10` says that adjoining an auxiliary conjugate pair at which the twisting character is unramified multiplies its toric evaluation by

$$
\mathcal E(y,w;q)=(1-yw)(1-y^{-1}w)+(q-1)w^2,
\qquad w=q^{-s}.
$$

Here $q$ is the norm of the auxiliary prime, $s$ is the evaluation weight, and $y=(\lambda\psi)(\operatorname{Frob}_P)$ at the indicated prime $P$. Every $q$ is $1\bmod 2n$, so $w\in O^\times$ has residue $1$. The auxiliary-coordinate hypotheses give two facts used below. When the last $R$ coordinates of $\psi$ are trivial, its value on the Frobenius at position $R+j$ is its first-block coordinate $u_j$. At each first-block prime the value of $\lambda$ on the indicated Frobenius has residue different from $1$, by the [tame inertia comparison](tame-inertia-makes-the-first-block-euler-factors-units.md).

**Proposition.** There are integral polynomials $f(X,Y)$, $g(X)$ whose evaluations at $X_j=u_j-1$, $Y_j=u_{R+j}-1$, for $n$-th roots of unity $u_j$, give the cleared toric evaluations on the full support and the first support, respectively. There is an integral polynomial $D(X)$ such that

$$
 f-Dg\in
 \bigl(Y_1,\ldots,Y_R,(1+X_1)^n-1,\ldots,(1+X_R)^n-1\bigr).
$$

The reduction of $D$ is $X_1^{e_1}\cdots X_R^{e_R}$ times a polynomial with nonzero constant coefficient, with $e_j\in\{0,2\}$. If the untwisted evaluation at empty auxiliary support has finite $\ell$-adic valuation $c_\lambda$ under the normalization $v_\ell(\ell)=1$, then $v(g(0))=v(\ell)(N_0+c_\lambda)$.

**Proof.** For each class $\delta$ that occurs in the toric class sum, choose a Galois element mapping to it under the surjective reciprocity map to the ray-class quotient. Let $d_j(\delta)\in\{0,\ldots,n-1\}$ represent the cyclic coordinates of that Galois element. If $b_\delta$ is the corresponding class-sum coefficient multiplied by $\ell^{N_0}$, the summand in the polynomial is $b_\delta\prod_j(1+Z_j)^{d_j(\delta)}$, with $Z=(X,Y)$ for the full support. At the indicated evaluations the monomial is the value of the character on the chosen preimage, which is the value on $\delta$. Thus the sum is integral and has the required evaluations. Apply the same construction on the first block to obtain $g$.

Put $r_j=\lambda(\operatorname{Frob}_{P_{R+j}})$ and $w_j=q_j^{-s}$ at the omitted second-block prime. Define

$$
D(X)=\prod_{j=1}^R\left(
(1-r_j(1+X_j)w_j)
(1-r_j^{-1}(1+X_j)^{n-1}w_j)+(q_j-1)w_j^2
\right).
$$

At $Y=0$ the character is inflated from the first support. At $X_j=u_j-1$, the equality $u_j^{n-1}=u_j^{-1}$ identifies the $j$-th factor with $\mathcal E(r_j u_j,w_j;q_j)$. Adjoin the omitted pairs one at a time. The character is unramified at each of them throughout, so the removal input yields the product of these factors. Consequently $f(X,0)-D(X)g(X)$ vanishes at every tuple $(u_j-1)_j$.

Reduce this last polynomial successively by the monic polynomials $(1+X_j)^n-1$ in their respective variables. The remainder has degree less than $n$ in each variable and vanishes on the same grid. Work over a field containing all $n$-th roots of unity. With all other variables fixed on the grid, a univariate polynomial of degree less than $n$ with $n$ distinct roots is zero. Applying this argument to its coefficient polynomials in the remaining variables proves that the remainder is zero. This gives the ideal membership in $O[X,Y]$.

For the constant term of $g$, apply the removal identity to the first-block pairs starting from empty auxiliary support and with trivial twist. At each step the residue of the Euler factor is $(1-\bar y)(1-\bar y^{-1})\ne0$, by the first-block Frobenius condition. All factors are units, so the valuation of the cleared constant term is the asserted one.

Finally the $j$-th factor of $\bar D$ is $(1-\bar r_j(1+X_j))(1-\bar r_j^{-1}(1+X_j)^{n-1})$. If $\bar r_j\ne1$, its constant coefficient is nonzero, so take $e_j=0$. If $\bar r_j=1$, each factor has a simple zero at $X_j=0$, since the two linear coefficients are $-1$ and $-(n-1)$, both nonzero in characteristic $\ell$. Take $e_j=2$. The product has the stated form. Combined with the [monomial-factor bound](a-monomial-factor-bounds-a-low-coefficient-of-the-specialized-hecke-polynomial.md), this gives the required low coefficient for the [common twist](a-single-ray-character-satisfies-all-the-exported-twist-bounds.md).

**Lean correspondence.** The polynomial and its evaluation are `eR` and `eR_res`. The repeated removal is `thEval_remove`, the grid argument is `mem_span_of_vanish_roots`, and the factor identity and constant term are assembled in `exists_lift`, `eq'_eq`, `exists_w` and `propE`. The source uses multivariate ideal reduction. Division by the displayed monic polynomials gives the equivalent argument above. The coefficient and Euler-removal inputs remain explicit in this note. Source-based reconstruction. [Vanishing on the root grid](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PropEOfAdmissible.lean#L68) · [Evaluation polynomial](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PropEOfAdmissible.lean#L106) · [Removal of support](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PropEOfAdmissible.lean#L209) · [Lifting the factorization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PropEOfAdmissible.lean#L299) · [Constant term and toric family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PropEOfAdmissible.lean#L407).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
