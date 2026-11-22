# The isotropic-line count sums over a parabolic flow

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic CM extension, $f=[F:\mathbb Q]$, and $W$ a nondegenerate Hermitian space of rank $n\ge3$. For a compact set $\Omega\subset W(\mathbb A_F)$, let $a_s$ denote scalar multiplication by $e^s$ at each infinite place and by $1$ at each finite place. Take any Haar measure on $G(\mathbb A_F)=U(W)(\mathbb A_F)$ and its quotient by $G(F)$. Then the unnormalized mean number of nonzero rational isotropic vectors $x$ with $g^{-1}x\in a_{\log R}\Omega$ is $O_\Omega(R^{2f(n-1)})$ for every $R>0$. The constant can depend on the form and Haar measure. The result uses finite volume of the base unitary group of the hyperbolic complement and the parabolic covering stated below.

If no rational nonzero isotropic vector exists, the count is zero. Otherwise choose one $e$. Nondegeneracy gives $e'$ with $h(e,e')=1$, and replacing $e'$ by $e'-\tfrac12 h(e',e')e$ makes it isotropic. Thus $Ee+Ee'$ is a hyperbolic plane and $W$ is its orthogonal sum with a nondegenerate rank-$(n-2)$ space. Let $P$ be the stabilizer of $Ee$ in $G$.

### The parabolic covering used here

The source’s covering theorem supplies a compact set $Y$ of pairs $(u,v)$ of adelic vectors with $h(v,u)=1$, and a finite constant $K$, with the following property. For a nonnegative measurable function $\Phi$ on $W(\mathbb A_F)$ invariant under multiplication by $E^\times$, choose a bound $g_j$ for $\Phi(a_{-j}u)$ on all $(u,v)\in Y$, for each integer $j$. Then for any set $\mathcal L$ of nonzero rational isotropic vectors with at most one representative per rational line,
$$
 \int_{G(F)\backslash G(\mathbb A_F)}
       \sum_{x\in\mathcal L}\Phi(g^{-1}x)\,dg
 \ \le\ K\sum_{j\in\mathbb Z}g_j e^{-2f(n-1)j}.
 \tag{1}
$$
For a complete set $\mathcal L$, the sum is a well-defined quotient function because $\Phi$ is scalar-invariant. For a subset, the inequality is on a measurable fundamental domain.

In the proof of this covering estimate, the rational isotropic lines form one orbit, by Witt extension of the line isometry. Opening the sum along $P(F)\backslash G(F)$ gives the integral over $P(F)\backslash G(\mathbb A_F)$, by Tonelli. The group has $G(\mathbb A_F)=P(\mathbb A_F)C$ for a compact set $C$. The parabolic has a measurable cover modulo $P(F)$ on layers $j$, with left Haar volumes at most a constant times $e^{-2f(n-1)j}$. On layer $j$ its action on $e$ is multiplication by $a_j b$ with $b$ in a fixed compact set of adelic units. Comparing the integral over $P(F)\backslash G(\mathbb A_F)$ to the layer integrals and the compact $C$ gives (1). The vector pair associated to $c\in C$ and $b$ is $(b^{-1}c^{-1}e,\bar b\,c^{-1}e')$; its Hermitian pairing is one. This explains both the compactness and the pairing condition needed below. The [parabolic layer calculation](the-hyperbolic-parabolic-has-exponentially-weighted-cusp-layers.md) derives the compact covering and the layer volumes from finite covolume for the complementary unitary group.

### Count the rational scalars on one line

Fix $R>0$ and define
$$
 \Phi_R(y)=\sum_{\lambda\in E^\times}
              \mathbf1_\Omega(a_{-\log R}\lambda y).
$$
This is measurable and $E^\times$-invariant by reindexing. Choose $\mathcal L$ to contain one nonzero representative of every rational isotropic line. Every vector to be counted is $\lambda x$ for a unique $\lambda\in E^\times$ and $x\in\mathcal L$, so applying (1) to $\Phi_R$ bounds the desired mean.

If $\lambda$ contributes to $\Phi_R(a_{-j}u)$, put $y=a_{-(j+\log R)}\lambda u\in\Omega$. Pair with the second vector $v$ of the compact pair to obtain
$$
 h(v,y)=a_{-(j+\log R)}\lambda ,
$$
taking the pairing linear in the second variable. As $(u,v)$ ranges over $Y$ and $y$ over $\Omega$, the right hand expression lies in one fixed compact subset of $\mathbb A_E$. Its finite coordinates are therefore contained in a fixed fractional-ideal box, and its infinite coordinates in a fixed bounded box. On diagonal rational scalars this means $\lambda$ belongs to a fixed fractional ideal of $E$, with all archimedean coordinates bounded by $C_1 e^{j+\log R}$. This is an ordinary lattice of real rank $2f$. Its shortest nonzero vector gives a threshold $x_0$ below which there is no $\lambda$ when $j+\log R<x_0$. Above threshold, a packing argument bounds the number by $C_2 e^{2f(j+\log R)}$: place disjoint fundamental-volume small balls about the lattice points and compare with the volume of an enlarged ball. Thus one may choose $g_j=0$ below threshold and $g_j=C_2 R^{2f}e^{2fj}$ above it.

Let $j_0=\lceil x_0-\log R\rceil$. The sum in (1) is at most
$$
 KC_2 R^{2f}\sum_{j\ge j_0}e^{-2f(n-2)j}
 =KC_2 R^{2f}\frac{e^{-2f(n-2)j_0}}{1-e^{-2f(n-2)}}.
$$
Since $n\ge3$, the series converges, and $e^{-2f(n-2)j_0}\le e^{-2f(n-2)x_0}R^{2f(n-2)}$. This proves the stated $R^{2f(n-1)}$ bound. The complementary rank $n-2>0$ provides precisely the excess decay after paying for the field-scalar count.

### Lean correspondence

The hyperbolic parabolic cover is [`exists_nu_siegel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicParabolicSiegelSetBound.lean#L18), and unfolding with the compact group set and the paired vectors gives [`integral_isotropic_lines_le_flow_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicFundamentalDomainCover.lean#L27). The bound for rational points in a dilated compact set is [`count_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/FlowLatticeCountBounded.lean#L78). [`mean_isotropic_count_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HyperbolicFiniteVolumeIntegralBound.lean#L21) combines it with (1), using [`geom_sum_int_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/GeomSumIntLe.lean#L7) for the tail. Splitting the original form and transporting the chosen boxes occur in [`mean_isotropic_box`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/CountingRationalVectorsBoxBound.lean#L82).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
