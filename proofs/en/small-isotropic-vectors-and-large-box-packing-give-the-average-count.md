# Small isotropic vectors and large-box packing give the average count

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a quadratic CM extension with $f=[F:\mathbb Q]$. Let $W$ be a nondegenerate Hermitian space of rank $n\ge3$, with a fixed rational coordinate system and finite coordinate lattices $L_v\subset W_v$. Fix an integer $N>0$. For $R>0$ and $g\in U(W)(\mathbb A_F)$, let $C_g(R)$ be the number of nonzero $x\in W$ such that
$$
     g_v^{-1}x\in N^{-1}L_v \ (v<\infty),\qquad
     \max_{w\mid\infty}\|(g^{-1}x)_w\|\le R.
$$
Use any fixed Euclidean coordinate norms at infinity. Assume the positive finite volumes of the rational quotients of the unitary groups in this calculation. Then for a constant $C>0$,
$$
 \operatorname{mean}_{U(W)(F)\backslash U(W)(\mathbb A_F)} C_g(R)
 \ \le\ C(R^{fn}+R^{2fn})
 \qquad(R>0).
\tag{1}
$$
This is the count hypothesis in the [weighted theta bound](cuspidal-cancellation-bounds-the-weighted-theta-difference.md). The proof below uses the isotropic count from the parabolic calculation and the elementary nonzero norm unfolding.

### Small boxes force isotropic vectors

The Hermitian norm of a rational vector $x$ lies in $F$, and equals the norm of $g_v^{-1}x$ at every place. By the finite coordinate conditions it lies in a fixed fractional ideal of $F$. To see this, expand the form in the coordinates. Denominators of its rational matrix and of the coordinate basis are bounded by one integer away from all places, and the finite boxes add at most the denominator $N^2$. At the real places $|h(g_w^{-1}x,g_w^{-1}x)|\le cR^2$ for one $c>0$ by continuity of the fixed bilinear forms in finite dimension. The fractional ideal is discrete in the product of real coordinates, so for some fixed $R_0\in(0,1]$ the only such norm for $R\le R_0$ is zero. Equivalently, the field norm of a nonzero element with fixed denominator has a positive lower bound, whereas the product of its real moduli here is at most $(cR^2)^f$.

Thus for $R\le R_0$ only the nonzero isotropic vectors contribute. Apply [the isotropic-line estimate](the-isotropic-line-count-sums-over-a-parabolic-flow.md) to the compact box $\Omega$ with these finite coordinates and real radius one. Its dilation by the common real factor $R$ is exactly the radius-$R$ box. The mean is $O(R^{2f(n-1)})$, and $2f(n-1)\ge fn$ with $R\le1$, giving the $R^{fn}$ bound in (1).

### Why the count at a fixed radius has finite mean

More generally, in a fixed compact set of adelic vectors the rational norms of any contributing vector are in $F$ intersected with a compact subset of $\mathbb A_F$. This subset is the image of the compact set under the Hermitian norm map. The intersection is finite since diagonal $F$ is closed and discrete. The isotropic part again has a finite integral by the previous estimate after putting the compact set in one fixed finite coordinate box and real ball.

For each remaining nonzero norm $\beta$ represented by a rational vector $x_0$, unfold along the vector stabilizer $H=U(x_0^\perp)$. All rational vectors of this norm form one orbit by Witt extension. Tonelli gives the integral over $H(F)\backslash G(\mathbb A_F)$, and integrating its $H(F)\backslash H(\mathbb A_F)$ fibres multiplies the orbital integral by the finite quotient volume of $H$. The orbital integral is finite on the chosen compact set. In fact the regular fibre $Q=\beta$ is a homogeneous space of the unitary group with a locally finite quotient measure. Local transitivity and local sections follow by the constructions in [the norm-orbit comparison](finite-projections-determine-the-adelic-norm-orbit-measure.md). At almost all places $x_0$ has integral unit norm, and any integral vector of that norm can be moved by the integral stabilizer: both lines split off with self-dual orthogonal complements. This supplies the restricted-product sections at almost all places that identify the adelic fibre with the adelic quotient. Hence a compact subset of the fibre has finite orbital measure. No normalization of the orbital measure by the Siegel mean is needed. The finite sum over $\beta$, with the isotropic bound, proves finiteness at the radius $R_0$.

### Packing in real coordinates

Fix $g$ and consider the additive subgroup of $W_\infty$ obtained by taking rational vectors satisfying the finite coordinate conditions and mapping them by $g_\infty^{-1}$. It is a real lattice. Indeed the finite conditions define a full rational lattice in $W$ between two fractional coordinate lattices, since $g_v$ is integral invertible at almost all finite places. The map at infinity is invertible. If $R\ge R_0$, select a maximal $R_0/2$-separated set among the lattice points with real norm at most $R$, including zero in the starting set. The open balls of radius $R_0/4$ around its members are disjoint and contained in the ball of radius $R+R_0/4$. In real dimension $2fn$ the number of centers is at most $(1+4R/R_0)^{2fn}\le(5R/R_0)^{2fn}$. By maximality each lattice point in the large ball is within $R_0/2$ of a center. Subtract that center. This sends the points assigned to each center injectively into lattice points of radius $R_0$, including zero. Thus
$$
    C_g(R)\le(5R/R_0)^{2fn}\bigl(1+C_g(R_0)\bigr).
$$
Taking the mean, the factor in parentheses has finite expectation by the fixed-radius result, so (1) follows also for $R\ge R_0$.

### Lean correspondence

The compact norm separation and small threshold are [`small_length`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SmallBoxGramScalarZero.lean#L26). Compact count finiteness is [`cntI_nonzero_lt_top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaCountCompactFinite.lean#L55). For nonzero norms it uses `finite_volume_induction_compact_sum`, the finite complement volume and the unfolding along one vector. The packing bound is [`box_packing`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/AdelicBoxLatticeCountRatio.lean#L60), applied at large radii in [`cnt_large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/CountingVectorsBoundedLargeRadius.lean#L61). The two ranges are combined in [`mean_count_box`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaMeasureNonzeroVectorsBound.lean#L36); [`main_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SiegelWeilArchimedeanDensity.lean#L70) puts this into the real trace coordinates. Equivalent norms at the real places change only the constant in (1).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
