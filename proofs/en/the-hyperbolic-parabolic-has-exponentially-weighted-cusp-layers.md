# The hyperbolic parabolic has exponentially weighted cusp layers

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic CM extension of number fields, $f=[F:\mathbb Q]$, and $W=Ee\oplus W'\oplus Ee'$ a nondegenerate Hermitian space with $e,e'$ isotropic, $h(e,e')=1$, and $W'=(Ee+Ee')^\perp$ of rank $n-2$. Let $G=U(W)$, $P=\operatorname{Stab}_G(Ee)$ and suppose $U(W')(F)\backslash U(W')(\mathbb A_F)$ has finite Haar volume. Let $a_s\in\mathbb A_E^\times$ equal $e^s$ at every infinite place and $1$ at every finite place. Then $G(\mathbb A_F)=P(\mathbb A_F)C$ for a compact $C$. There is a measurable cover modulo left $P(F)$ by sets $S_j\subset P(\mathbb A_F)$, $j\in\mathbb Z$, and a fixed compact $\mathcal B\subset\mathbb A_E^\times$, such that
$$
  p e=a_j b e\ (p\in S_j,\ b\in\mathcal B),\qquad
  \mu_P(S_j)\ \le\ C_P e^{-2f(n-1)j}.
$$
Here $\mu_P$ is left Haar measure on $P(\mathbb A_F)$, and $C_P$ does not depend on $j$. These are the parabolic inputs for [the average isotropic count](the-isotropic-line-count-sums-over-a-parabolic-flow.md).

### Coordinates on the line stabilizer

Use the Hermitian pairing linear in the second variable. The Levi part consists of maps
$$
 m(a,U)=\operatorname{diag}(a,U,\bar a^{-1}),
 \qquad a\in\mathbb A_E^\times,\quad U\in U(W')(\mathbb A_F).
$$
The unipotent radical has coordinates $z\in W'(\mathbb A_F)$, $b\in\mathbb A_F$, using a fixed nonzero $\epsilon\in E$ with $\bar\epsilon=-\epsilon$:
$$
 n(z,b)e=e,\quad
 n(z,b)w=w-h(z,w)e \ (w\in W'),\quad
 n(z,b)e'=e'+z+(\epsilon b-h(z,z)/2)e.
$$
The mixed pairings agree with those of $e,W',e'$: for instance the pairing of $n(z,b)e'$ with $n(z,b)w$ is $h(z,w)-h(z,w)=0$, and the norm of $n(z,b)e'$ is $h(z,z)-h(z,z)=0$. Thus these maps are unitary. Conversely a line stabilizer induces $U$ on $e^\perp/Ee$ and acts by $a$ on $e$. After removing $m(a,U)$, preservation of the pairings forces the remaining map to have the displayed form. This gives unique $n(z,b)m(a,U)$ coordinates.

Multiplying two such $n$'s adds the horizontal coordinates and adds the central coordinates up to a bilinear correction in the horizontal variables. Explicitly the correction in $\epsilon b$ is $\tfrac12(h(z',z)-h(z,z'))$ when multiplying $n(z,b)n(z',b')$. This follows by applying the product to $e'$ and comparing with the expression for $n(z+z',b+b')e'$. Therefore the product of additive Haar measures $dz\,db$ is left invariant: for fixed horizontal coordinates the central change is a translation. A compact set of representatives modulo $N(F)$ can be obtained by reducing $z$ modulo $W'(E)$, then the adjusted $b$ modulo $F$. Both additive adele quotients have compact representative sets. Reducing $b$ after $z$ accounts for the bilinear correction.

### The Haar exponent

Conjugation by $m(a,U)$ sends $z$ to $\bar a\,U z$ and $b$ to $a\bar a\,b$. This follows by applying the conjugate to $e'$; the other coordinates of the unitary map are then fixed by the pairing identities above. The $U$-part preserves additive Haar volume by its trace pairing. Define $|a|_{\mathbb A_E}=\prod_{w\mid\infty}|a_w|^2\prod_{v<\infty}|a_v|_v$, with standard normalized nonarchimedean factors over $E$. The horizontal volume factor is $|a|_{\mathbb A_E}^{n-2}$. The central volume factor is $|a\bar a|_{\mathbb A_F}=|a|_{\mathbb A_E}$, by the modulus formula for a local field norm. Thus the total volume factor is $\delta(a)=|a|_{\mathbb A_E}^{n-1}$. In particular $\delta(a_j)=e^{2f(n-1)j}$.

In the $n m$ coordinates left Haar measure is proportional to
$$
   \delta(a)^{-1}\,dz\,db\,d^\times a\,dU.
$$
Indeed left multiplication by $n_0$ preserves $dz\,db$. Left multiplication by $m(a_0,U_0)$ scales it by $\delta(a_0)$, which cancels the change of $\delta(a)^{-1}$; the Haar measure of the Levi is invariant under the left multiplication. These two kinds of elements generate $P$, proving the formula.

The norm-one idèle class group of $E$ is compact. In the present coordinates this can be seen using the finite ideal class set to restrict the finite valuations to finitely many representatives, then using Dirichlet's unit theorem on the real logarithms of the archimedean moduli with their sum fixed. At the finite places the remaining coordinates range over the compact local units, and at the infinite places the phases range over circles. It follows that every idèle can be reduced by $E^\times$ into $a_j\mathcal B$ with $\mathcal B$ compact: subtract the integer part of $\log |a|_{\mathbb A_E}/(2f)$ and include the remaining $a_s$, $0\le s\le1$, in the compact set.

For a point in $P(\mathbb A_F)$, first reduce the Levi coordinates by rational Levi elements, placing $a$ in $a_j\mathcal B$ and $U$ in a measurable fundamental set of finite volume. This acts on the unipotent coordinates by the corresponding conjugations. Then reduce these new coordinates by rational unipotent elements into their compact set of representatives. The resulting product sets $S_j$ cover modulo $P(F)$. Their measure in the formula above is bounded by the product of the unipotent compact volume, the complementary quotient volume and the compact multiplicative measure, times
$$
 \sup_{b\in\mathcal B}\delta(a_j b)^{-1}
    = e^{-2f(n-1)j}\sup_{b\in\mathcal B}\delta(b)^{-1}.
$$
This gives the asserted uniform constant and multiplier on $e$.

### A compact set outside the parabolic

At a real or finite place, the space of isotropic lines is compact. Over the nonsplit quadratic algebra it is a closed subset of projective space. Over a split algebra an isotropic free rank-one subspace is a pair of lines annihilating each other under the perfect pairing. This is a closed incidence subset of a product of projective spaces. In either case the unitary group acts transitively by extending an isotropic vector and a dual vector to a hyperbolic basis. The local orbit maps have local sections. For example vary the isotropic vector in a projective chart, normalize its Hermitian pairing with a fixed dual vector to one, and subtract half the dual vector’s norm times the isotropic vector to obtain an isotropic partner. Project a fixed complementary frame into their orthogonal complement. Near the initial line its Gram matrix is close to the original complementary Gram matrix. A near-identity change of basis taking the two matrices to each other is obtained by the inverse square root of their ratio, which is self-adjoint for the original Gram matrix. The binomial series converges over the local field after restricting sufficiently near the identity. The resulting unitary basis gives the section. Compactness and finitely many local neighborhoods therefore give a compact set of representatives in the local group.

At almost all finite places one can instead use the compact integral stabilizer. The extension $E/F$ is split or unramified there, the standard lattice and hyperbolic plane are integral self-dual, and the residue characteristic can be taken odd. Each line has a primitive generator in the integral lattice, or a generator primitive in each component in the split case. Hermitian self-duality supplies an integral dual vector with pairing one. Make this dual vector isotropic by subtracting half its norm times the line generator. The resulting integral hyperbolic plane splits off, with self-dual complement. The integral frame classification identifies that complement with the standard complementary lattice. Thus an integral unitary map sends the standard hyperbolic plane and line to the new ones. The local compact stabilizers give a restricted product of compact representatives at almost all places. Combining these with the finitely many other compact local sets gives $C$, using the orbit of the inverse image of $Ee$ to obtain the order $P C$.

### Lean correspondence

The multiplication, dilation, Haar density and rational reduction for the layer sets are combined in [`nu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/ActWSmul.lean#L24), exported as [`exists_nu_siegel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicParabolicSiegelSetBound.lean#L18). Compactness outside the line stabilizer is [`iwasawa`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicUnitaryStabilizerCocompact.lean#L249). Those are used together by [`integral_isotropic_lines_le_flow_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicFundamentalDomainCover.lean#L27). The finite volume of the complementary unitary quotient enters at the choice of the $U$-fundamental set.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
