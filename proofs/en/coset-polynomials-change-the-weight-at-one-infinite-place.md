# Coset polynomials change the weight at one infinite place

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

The proof starts with an algebraic automorphic form on a totally definite unitary group. It multiplies suitable translates of the form by polynomials that approximate indicators of small finite-level cosets. A highest-weight matrix coefficient controls the archimedean weight. Its norm estimate is independent of how large the new weight is.

## Family approximation

Let $E$ be a CM field, $a\ge 1$, $G$ the project's standard totally definite unitary group in $a$ variables, and $G_\infty$ its subgroup of archimedean points inside $G(\mathbb A)$. Write $c_v$ for the finite local coordinate, and $c_\tau\colon G(\mathbb A)\to\mathrm{GL}_a(\mathbb C)$ for the archimedean coordinate at an embedding $\tau\colon E\hookrightarrow\mathbb C$. Fix a prime $\ell$ and an isomorphism $\iota\colon\overline{\mathbb Q}_\ell\simeq\mathbb C$. All norms on complex scalars or matrix entries below are transferred by $\iota^{-1}$.

Let $w_0\mid\ell$ and $v'$ be split places of $E$ above distinct places of its maximal totally real subfield. Assume that $\iota^{-1}\tau$ induces $v'$. Let $K$ be a compact open level in the finite adelic group away from the pair of places $w_0,\bar w_0$, with trivial coordinate there. Assume it contains the supported hyperspecial subgroup $\mathrm{GL}_a(\mathcal O_{E_{v'}})$ at the split pair $v',\bar v'$. Take any open subgroup $K_v\subset \mathrm{GL}_a(E_{v'})$. Let $f\colon V_W\to\{\text{functions on }G(\mathbb A)\}$ be an algebraic automorphic form of weight $W$, fixed by $K\cap c_{v'}^{-1}(K_v)$. Fix evaluation vectors $b(g,i)\in V_W$, for $g\in G(\mathbb A)$ and $i$ in a set $I$, such that $\{|F(b(g,i))(g)|_\ell:g,i\}$ is bounded for every algebraic form $F$ of weight $W$. Fix $\varepsilon>0$.

There is an integer $d\ge 0$ and a map $M\colon G(\mathbb A)\to\mathrm{GL}_a(\mathbb C)$ invariant under right multiplication by finite adeles with trivial $v'$-coordinate. For every dominant weight $\nu=(\nu_0\ge\cdots\ge\nu_{a-1})$ there is a family $B(y_1,y_2)v$ of $K$-fixed automorphic forms, linear in $v\in V_W$, parametrized by $y_1,y_2\in\mathrm{GL}_a(\mathbb C)$. Its values lie in a finite-dimensional space. For $x\in G_\infty$ and invertible upper triangular $b$ it satisfies
$$
R(x)B(y_1,y_2)v=B(c_\tau(x)y_1,c_\tau(x)y_2)W(x)v,\qquad
B(y_1b,y_2)v=\Big(\prod_i b_{ii}^{\nu_i}\Big) B(y_1,y_2)v.
$$
Here $R$ is right translation. Set $s_\nu(k)=\sum_{i<k}\nu_i$ for $0\le k\le a$ and $t_k(z)=\operatorname{diag}(z,\ldots,z,1,\ldots,1)$ with $k$ copies of $z$ on the complex unit circle. Let $x_k(z)\in G_\infty$ be the element supported at the chosen archimedean place with value $t_k(z)$. At each $g$, the Laurent polynomial
$$
z\longmapsto B(t_k(z)y_1,t_k(z)y_2)W(x_k(z))v(g)
$$
has exponents at most $s_\nu(k)+d$. The polynomial with first argument held equal to $1$, namely $B(1,t_k(z)y_2)W(x_k(z))v(g)$, has exponents at least $-d$. On the selected evaluations the approximation is
$$
\big|f(b(g,i))(g)-B(M(g),M(g))b(g,i)(g)\big|_\ell\le\varepsilon .
$$
[Family approximation and properties](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/DeltaNear.lean#L175) · [Automorphic and torus covariances](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfApply.lean#L55)

## Constructing the family

Enlarge $K$ to a compact open level $C=KJ_0$ by a sufficiently small torsion-free subgroup $J_0$ at $w_0$. Smoothness allows us to keep $f$ fixed by $C\cap c_{v'}^{-1}(K_v)$. The torsion-free condition makes the action of $C$ on rational and archimedean double cosets free. More precisely, $\gamma g=gcx$ with $\gamma\in G(E^+)$, $c\in C$ and $x\in G_\infty$ forces $c=1$. Choosing one representative per double coset then defines $r(g)\in C$ by writing $g=\gamma g_*r(g)x$. The choice of $r(g)$ is unique for a fixed representative. It is left rational invariant, right archimedean invariant and $r(gc)=r(g)c$. The image $c_{v'}(C)$ lies in the hyperspecial subgroup, since it is compact and contains that maximal compact subgroup. [Level construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/NeatLev.lean#L11) · [Coset coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/EllCOf.lean#L10)

The embedding $\iota^{-1}\tau$ extends continuously over $E_{v'}$. Apply that extension to entries of $c_{v'}(g)$ and then apply $\iota$; call the resulting homomorphism $\kappa(g)$. Thus $\kappa(\gamma)=c_\tau(\gamma)$ on rational points, $\kappa(x)=1$ on $G_\infty$, and $\kappa(h)=1$ for a trivial $v'$-coordinate. Set $\varphi=\kappa|_C$,
$$
M(g)=c_\tau(g)^{-1}\kappa(g),\qquad A(g)=\varphi(r(g))M(g)^{-1}.
$$
Then $M$ has the claimed right invariance. Direct substitution shows that $A$ is left rational invariant, right $C$-invariant and $A(gx)=A(g)c_\tau(x)$ for $x\in G_\infty$. All entries of $\varphi(c)$ and $\varphi(c)^{-1}$ have norm at most $1$. [Local-coordinate properties](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/DeltaNear.lean#L143) · [Construction of the two maps](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamExOf.lean#L21)

For $c\in C$ define $F_c(v)(g)=f(v)(g r(g)^{-1}c)$. The rules for $r$ give the same archimedean transformation law as for $f$, left rational invariance and right $C$-invariance. These translates have a common bound $R>0$ on the given evaluations. Indeed, $f$ is fixed by some compact open level $C_0$ by smoothness. The forms $F_c$ depend only on $c(C\cap C_0)$, and there are finitely many such cosets because $C$ is compact and $C\cap C_0$ is open. Take $R>0$ at least as large as their individual evaluation bounds. [Translated form](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/TwistOf.lean#L9) · [Bound for the family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/TwistBd.lean#L23)

Apply compact-group polynomial separation to $\varphi$, the open subgroup $C\cap c_{v'}^{-1}(K_v)$ containing its kernel, and tolerance $\alpha=\varepsilon/R$. This gives a finite set of representatives $c_q\in C$ and polynomials $P_q$ in matrix entries. For each $c\in C$ there is an index $q_0$ with $c_{q_0}^{-1}c\in C\cap c_{v'}^{-1}(K_v)$ and $|\varphi(c_{q_0}^{-1}c)-1|_\ell\le\alpha$ entrywise, while
$$
|P_{q_0}(\varphi(c))-1|_\ell\le\alpha,\qquad
|P_q(\varphi(c))|_\ell\le\alpha\quad(q\ne q_0).
$$
[Separation for compact-group pieces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/Pieces.lean#L24)

Let $\Delta_j(H)$ be the determinant of the upper left $j\times j$ submatrix of $H$. Use the highest-weight coefficient
$$
\delta_\nu(H)=(\det H)^{\nu_{a-1}}
 \prod_{j=1}^{a-1}\Delta_j(H)^{\nu_{j-1}-\nu_j}.
$$
For integral $H,H^{-1}$, both determinants are integral and inverse to each other, so $|\det H|_\ell=1$. Every other factor is integral, proving $|\delta_\nu(H)|_\ell\le1$. An integer polynomial on integral coordinates changes by at most $\alpha$ if its input changes entrywise by at most $\alpha$. Integer powers of a norm-one scalar $u$ satisfy $|u^m-1|_\ell\le |u-1|_\ell$ for every $m\in\mathbb Z$, by a telescoping sum for positive powers and the identity $u^{-1}-1=-(u-1)/u$ for negative powers. Products of integral near-one factors stay near $1$. Consequently $|\delta_\nu(H)-1|_\ell\le\alpha$ when $H$ is within $\alpha$ of the identity, uniformly in $\nu$. [Uniform highest-weight bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/DeltaNearH.lean#L25)

Define
$$
 B(y_1,y_2)v(g)=\sum_q P_q(A(g)y_2)\,
 \delta_\nu\big(\varphi(c_q)^{-1}A(g)y_1\big)\,F_{c_q}(v)(g).
$$
At $y_1=y_2=M(g)$, $A(g)M(g)=\varphi(r(g))$. Choose $q_0$ as above for $c=r(g)$. The form $F_{c_{q_0}}$ agrees with $f$ at $g$, by the original fixedness. Its multiplier differs from $1$ by at most $\alpha$. For all other $q$ the multiplier has norm at most $\alpha$. The ultrametric inequality on the finite sum and the common bound $R$ now give error at most $\alpha R=\varepsilon$. [Family formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfApply.lean#L80) · [Diagonal estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamExOf.lean#L50)

## Weight and finite-dimensionality

The preliminary forms $F_{c_q}$ carry the original weight $W$. The transformation law for $A(gx)$ proves the archimedean covariance. The upper triangular covariance follows from $\delta_\nu(Hb)=\prod_i b_{ii}^{\nu_i}\,\delta_\nu(H)$, using the leading submatrix determinants and triangularity. For fixed $\nu$, the translates in $y_1,y_2$ lie in the finite span obtained by expanding polynomials in the entries of each argument, along with the single determinant power in $y_1$. The same finite-span construction supplies archimedean finiteness, and the functions are continuous in the archimedean variable by their formulas. Left rational and right $C$-invariance, together with those two properties, give automorphic forms. [Finite-span input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfA.lean#L9) · [Family covariances](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfOf.lean#L9)

Under $t_k(z)$, the polynomial factor contributes exponents between $0$ and $\deg P_q$. The original coefficient representation contributes exponents between $-d_0$ and $d_0$ for some $d_0$ independent of all $q$. The matrix coefficient of highest weight $\nu$ contributes exponents at most $s_\nu(k)$. One way to see the last bound is to expand the leading $j$-row and $j$-column minors in the three matrices of $H_1t_k(z)H_2$. A minor has exponents at most $\min(j,k)$ by Cauchy–Binet. Hence the full upper bound is $k\nu_{a-1}+\sum_{j<a}\min(j,k)(\nu_{j-1}-\nu_j)=s_\nu(k)$. With $y_1=1$ held fixed the highest-weight coefficient contributes exponent $0$. Taking $d=\max_q\deg P_q+d_0$ proves both claims about the Laurent exponents, independently of $\nu$. [Laurent exponent bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfOf.lean#L39)

## Lean correspondence

- `UpperTheory.Gal.Wt.famEx_of` constructs and estimates the family. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamExOf.lean#L13)
- `UpperTheory.Gal.Wt.deltaNear_h` supplies the weight-independent matrix coefficient estimate. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/DeltaNearH.lean#L25)
- `UpperTheory.Gal.Wt.famOf_of` packages the invariances, finite span and Laurent support. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/FamOfOf.lean#L9)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof. The initial common evaluation frame comes from the locally integral operators. See the [projection argument](projecting-a-weight-family-gives-new-hecke-eigenvalues.md) for its use.
