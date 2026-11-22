# Spherical Fourier inversion makes bad Satake support small

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be a nonarchimedean local field, $a\ge1$, $G=\mathrm{GL}_a(F)$, and $K=\mathrm{GL}_a(\mathcal O_F)$. Let $\Phi\in\mathbb C[X_1,\ldots,X_a]$ be nonzero. For every $\delta>0$, there is a finitely supported sum of right translations on $G$, with coefficients $b_g\in\mathbb C$ at distinct cosets $gK$, such that
$$
 \sum_g |b_g|^2\le \delta .
$$
It acts as the identity on the $K$-fixed vectors of every irreducible smooth spherical representation whose Satake multiset has an ordering $z\in(\mathbb C^\times)^a$ with $\Phi(z)=0$. The squares here use the ordinary complex absolute value. At a split unitary place away from $w_0$ one can support the corresponding global operator there and use it to bound the dimension of bad systems as the level at $w_0$ shrinks. [Local operator estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StGlob.lean#L27) · [Negligibility theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/NeglAt.lean#L8)

## A polynomial equal to one on the bad set

Write $P(z)=\prod_{\sigma\in S_a}\Phi(z_{\sigma(1)},\ldots,z_{\sigma(a)})$, a nonzero symmetric polynomial. Define $P^*(z)$ by conjugating its coefficients and replacing $z_i$ by $z_i^{-1}$, so $P^*=\overline P$ on the unit torus $\mathbb T^a$. Choose $c>0$ with $c\max_{\mathbb T^a}|P|^2<1$, and set
$$
 p_m(z)=(1-cP(z)P^*(z))^m.
$$
These are symmetric Laurent polynomials. If any ordering gives $\Phi(z)=0$, then $P(z)=0$ and $p_m(z)=1$, even for parameters off the unit torus. On the torus $0\le 1-c|P|^2\le1$ and the right endpoint is attained only on the zero set of $P$. That zero set has Haar measure zero. In one variable the nonzero polynomial has finitely many roots. Inductively, regard the polynomial as a polynomial in its last coordinate, choose a nonzero coefficient polynomial in the other coordinates, exclude its measure-zero zero set and apply the one-variable assertion and Fubini. Thus $p_m\to0$ almost everywhere, and dominated convergence yields $\int_{\mathbb T^a}|p_m|^2\to0$. [Null zero set](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/NullZero.lean#L42) · [Symmetric Laurent construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/SmallPf.lean#L5)

## Averaging a spherical function gives the unit coset

Let $q$ be the size of the residue field, $t=q^{-1}$, and let $d z$ denote normalized product Haar measure on $\mathbb T^a$. For $z\in\mathbb T^a$, set
$$
 A_t(z)=\prod_{i<j}\frac{1-z_i/z_j}{1-tz_i/z_j},
 \qquad D_t(z)=A_t(z)A_t(z^{-1}),\qquad
 V_a(t)=\prod_{j=1}^a\frac{1-t^j}{1-t}.
$$
These functions have no poles on the unit torus and $D_t$ is symmetric and bounded. Write $\gamma_z$ for the normalized spherical function with Satake parameter $z$, so $\gamma_z(1)=1$. The required spherical identity is
$$
 V_a(t)\int_{\mathbb T^a}\gamma_z(g)D_t(z)\,d z
 =a!\,1_K(g).
$$
Here is the calculation in the project. Cartan decomposition writes $g\in K\operatorname{diag}(\varpi^{\alpha_i})K$ with $\alpha_1\ge\cdots\ge\alpha_a$ and $\varpi$ a uniformizer. Macdonald's formula on this double coset gives
$$
 V_a(t)\gamma_z(g)
   =b_\alpha\sum_{\sigma\in S_a}
       \prod_i z_{\sigma(i)}^{\alpha_i}
       \prod_{i<j}\frac{z_{\sigma(i)}-t z_{\sigma(j)}}{z_{\sigma(i)}-z_{\sigma(j)}} ,
$$
for distinct $z_i$, with $b_\alpha=q^{-\frac12\sum_{i<j}(\alpha_i-\alpha_j)}$, the square root of the modulus of the upper Borel on the indicated diagonal. The formula extends continuously as a symmetric Laurent polynomial. Since the fraction product is $A_t((z\circ\sigma)^{-1})^{-1}$, multiplying by $D_t$ and integrating reduces to $a!b_\alpha$ times $\int z^\alpha A_t(z)\,d z$. [Macdonald's formula, original Chapter IV, §4.1](https://link.springer.com/chapter/10.1007/978-3-032-15671-6_4) · [Lean formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/AutomorphicForms/MacdonaldFormula.lean#L111) · [Multiplication by the density](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/RIntPf.lean#L5)

To evaluate the last integral, replace $z_i$ by $\xi^{c-i}z_i$ for $\xi\in\mathbb T$ and an integer $c$. Averaging in $\xi$ leaves the integral unchanged. Every ratio $z_i/z_j$ with $i<j$ picks up $\xi^{j-i}$. The product defining $A_t$ then has an absolutely convergent power series in $\xi$ on the circle, with no negative exponents and constant term $1$. The monomial $z^\alpha$ acquires exponent $m=\sum_i(c-i)\alpha_i$. If $\alpha=0$ we have $m=0$ and the average is $1$. If $\sum_i\alpha_i\ne0$, choose $c$ of the appropriate sign and magnitude so $m>0$. If the sum is zero and $\alpha\ne0$, monotonicity gives
$$
 \sum_i(-i)\alpha_i
  =\frac1a\sum_{i<j}(j-i)(\alpha_i-\alpha_j)>0 .
$$
Thus $m>0$ for any $c$ in that case. All Fourier terms then have positive frequency and their average is zero. The coincident-coordinate set has Haar measure zero by the same one-variable argument used for $P$. This proves the spherical identity, since $\alpha=0$ exactly for $g\in K$ and $b_0=1$. [Constant term argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/HalfInt.lean#L68) · [Averaged spherical identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GammaInt.lean#L14)

## Controlling the coefficients of the operator

Use the Satake isomorphism with Haar measure on $G$ normalized by $\operatorname{vol}(K)=1$. Let $h$ be the bi-$K$-invariant compactly supported function corresponding to a symmetric Laurent polynomial $p$. Choose one representative $g$ of each right $K$-coset in its support and set $b_g=h(g)$. For every $y\in G$ and each parameter $z$,
$$
 \sum_g b_g\gamma_z(yg)=p(z)\gamma_z(y).
$$
This is the spherical eigenrelation after splitting the convolution integral over right cosets. Use $y=g_0^{-1}$, multiply by $D_t(z)$ and integrate. The preceding identity leaves only the term $g=g_0$, giving
$$
 b_{g_0}=\frac{V_a(t)}{a!}\int_{\mathbb T^a} p(z)\gamma_z(g_0^{-1})D_t(z)\,d z.
$$
For unitary $z$, one has $\gamma_z(g^{-1})=\overline{\gamma_z(g)}$. This follows from the same formula by replacing $\alpha$ with the decreasing rearrangement of $-\alpha$, since $t$ is real and $z_i^{-1}=\overline{z_i}$. Multiply the coefficient identity by $\overline{b_{g_0}}$ and sum, using the conjugate of the eigenrelation at $y=1$. The result is
$$
 \sum_g |b_g|^2
   =\frac{V_a(t)}{a!}\int_{\mathbb T^a}|p(z)|^2D_t(z)\,d z
   \le \frac{V_a(t)}{a!}\|D_t\|_\infty\int_{\mathbb T^a}|p(z)|^2\,d z .
$$
Lean allows any Haar normalization, absorbing its volume factor in the constant. Take $p=p_m$ for sufficiently large $m$. The operator has scalar $p_m(z)=1$ on every bad parameter, proving the claim. [Coset sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/RepsEx.lean#L5) · [Spherical eigenrelation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GammaEig.lean#L6) · [Coefficient mass bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/Planch.lean#L110)

For the global unitary group, assume the level is hyperspecial at a split place $w$ outside the $w_0$-pair. Identify the adelic factor at $w$ with $\mathrm{GL}_a(E_w)$ and place each translation representative only in that factor. The coset-separation condition carries over since an element supported at $w$ lies in the global level precisely when its local component lies in the hyperspecial subgroup. The same coefficients act on the globally fixed vectors by the local eigenrelation. This is the small operator input in the global bad-space dimension bound. [Globalization of the local operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GlobOp.lean#L18) · [Exact form of the input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StGlob.lean#L41)

## Lean correspondence

- `UpperTheory.Gal.Gen.small_pf` makes a symmetric Laurent polynomial equal to one on the bad locus with arbitrarily small torus square mean. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/SmallPf.lean#L5)
- `UpperTheory.Gal.Gen.gammaInt_pf` and `planch_pf` prove the averaged spherical identity and the coefficient bound. [Identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GammaInt.lean#L14) · [Bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/Planch.lean#L110)
- `UpperTheory.Gal.Gen.globOp_pf` and `neglAt_pf` give the corresponding finitely supported global operator for the bad summands. [Global operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/GlobOp.lean#L18) · [Negligibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/NeglAt.lean#L8)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof. This reconstruction uses Macdonald's spherical function formula and the Satake isomorphism as stated in the proof, with their Lean uses linked above.
