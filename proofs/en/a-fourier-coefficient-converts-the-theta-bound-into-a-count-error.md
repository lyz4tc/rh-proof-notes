# A Fourier coefficient converts the theta bound into a count error

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the quadratic form, Gaussian and averaging family from the [weighted theta comparison](cuspidal-cancellation-bounds-the-weighted-theta-difference.md). Thus $F$ is totally real of degree $f$, $B$ is nondegenerate of size $2n$, $n\ge3$, $q(x)=x^TBx/2$, and the isometries $g_\omega$ satisfy the average count bound stated there. Put $\kappa_F=|\operatorname{disc}F|^{-1/2}$. Let $L_f=\prod_{v<\infty}\mathcal O_{F_v}^{2n}$, let $a$ be any positive integer and $\phi_a=\mathbf1_{a^{-1}L_f}$. The unweighted finite Haar measure gives $\prod_v\mathcal O_{F_v}$ mass one in each scalar coordinate. Let $D_f(a,b)$ be the continuous density, at $b\in\mathbb A_{F,f}$, of the pushforward by $q$ of the finite coordinate measure restricted to $a^{-1}L_f$. Let $D_\infty(t)$ be the analogous density for archimedean Lebesgue measure times $G_{i\mathbf1}$. In these statements density is relative to the base Haar measure at finite places and Lebesgue measure at infinity.

For $\beta\in F^\times$, define
$$
 I(a,\beta)=\int_\Omega\sum_{\substack{x\in F^{2n}\\q(x)=\beta}}
        \phi_a(g_{\omega,f}x)\,G_{i\mathbf1}(g_{\omega,\infty}x)\,d\mathbb P(\omega).
$$
Then with one constant $C$ independent of $a,\beta$,
$$
 \big| I(a,\beta)-\kappa_F^{2n-1}D_f(a,\beta)D_\infty((\beta_w)_w) \big|
 \le C a^{fn}.
\tag{1}
$$

### Obtain a bound uniform over the denominator $a$

Apply the weighted comparison to the one fixed finite test $\phi_1$, at $\tau_w=(x_w+i)/a^2$. Rational scaling changes $\phi_1(u)$ to $\phi_1(au)=\phi_a(u)$ and changes $\tau$ to $a^2\tau$. Both $\Theta$ and $E$ satisfy this scaling identity with no multiplier. For $\Theta$, substitute $x\mapsto ax$ in the rational sum, using $G_{a^2\tau}(X)=G_\tau(aX)$ and linearity of every $g_\omega$. For $E$, make the same change of variables in the finite integrals and reindex the rational series by $b\mapsto a^2 b$. The finite modulus of $a$ on $2n$ coordinates cancels the real modulus by the product formula. Explicitly, $F_{\phi_a}(b)=a^{2nf}F_{\phi_1}(b/a^2)$, and $C_G(a^2\tau+b)=a^{-2nf}C_G(\tau+b/a^2)$. The value at zero stays fixed. The weight at $\tau$ is $a^{-fn}$. Thus for every real $x=(x_w)_w$,
$$
 |\Theta_{\phi_a}(x+i\mathbf1)-E_{\phi_a}(x+i\mathbf1)|\le C a^{fn}.
\tag{2}
$$
In particular the constant does not depend on the changing test $\phi_a$.

### Read the two coefficients at $\beta$

Enlarge a positive integer $N$ until $N\beta$ is integral, $Nq(u)$ is integral on the support of $\phi_a$ in the finite adeles, and $F_{\phi_a}$ has additive period $N\widehat{\mathcal O}_F$. Such an $N$ exists because the test has compact support and $\psi_f$ has an open kernel. For example after clearing the denominators of $q(u)$ on that support, any sufficiently divisible $N$ makes $\psi_f(Ntq(u))=1$ for all integral finite adeles $t$. At infinity let $D$ be a fundamental cell of the image of $N\mathcal O_F$ in $\mathbb R^f$, of volume $V=N^f/\kappa_F$. The covolume is the absolute determinant of the integral embedding matrix, namely $\sqrt{|\operatorname{disc}F|}$, times $N^f$.

Integrate (2) on $D$ after multiplying the difference by $e^{-2\pi i\sum_w\beta_w x_w}$. The integrals are absolute on this cell by the count bound and the absolutely summable Eisenstein estimate. In the theta part the invariance of $q$ under $g_\omega$ makes the $x$-dependent phase of a rational vector equal to the character of $q(x)$. Every nonzero summand has integral $Nq(x)$. Thus the difference $q(x)-\beta$ defines a character of the real torus with period $N\mathcal O_F$, trivial exactly when it is zero. Character orthogonality leaves the coefficient $V I(a,\beta)$.

In the Eisenstein part the constant term disappears because $\beta\ne0$. By the period condition the arithmetic factor $F_{\phi_a}(b)$ depends only on $b\bmod N\mathcal O_F$. The exponential introduced by translating the test from $D$ to $D+b$ is $e^{2\pi i\operatorname{Tr}(b\beta)}=\psi_f(-b\beta)$ and also depends only on that residue class. In each coset the cells $D+b+\lambda$, $\lambda\in N\mathcal O_F$, unfold the archimedean integral to $\mathbb R^f$. The rational cosets $F/N\mathcal O_F$ parametrize the finite adele quotient by $N\widehat{\mathcal O}_F$: approximation by rational numbers with a common denominator, then the Chinese remainder theorem, gives every class, with kernel $N\mathcal O_F$. Each coset has mass $N^{-f}$. Therefore the unnormalized Eisenstein coefficient is
$$
 N^f\!
 \left(\int_{\mathbb A_{F,f}}F_{\phi_a}(b)\psi_f(-b\beta)\,db\right)
 \left(\int_{\mathbb R^f} C_G(x+i\mathbf1)e^{-2\pi i\sum_w\beta_w x_w}\,dx\right).
\tag{3}
$$
Absolute convergence for this unfolding follows from the finite and archimedean Fourier integrability used below, or directly by the denominator and Gaussian estimates.

By definition $F_{\phi_a}$ is the finite transform of $D_f(a,\cdot)$ multiplied by $\kappa_F^{2n}|\mathrm N\det B|^{-1/2}$, the ratio between the self-dual vector measure and the finite coordinate measure. Inverting the scalar transform with the *coordinate* measure in (3) contributes the further factor $\kappa_F^{-2}$, since its self-dual scalar measure for $\psi_f$ is $\kappa_F\,db$. This yields $\kappa_F^{2n-2}|\mathrm N\det B|^{-1/2}D_f(a,\beta)$. The real integral is the inverse Fourier transform of the Gaussian pushforward, times $|\mathrm N\det B|^{1/2}$, so equals $|\mathrm N\det B|^{1/2}D_\infty((\beta_w)_w)$. Together the two factors in (3), after division by $V=N^f/\kappa_F$, give the main term of (1). The density existence and Fourier inversion here use the stated positive real Gaussian and local finite oscillatory transforms. The original bound (2) gives an integrated error of at most $V C a^{fn}$. Division by $V$ gives (1).

### The Hermitian application

For a Hermitian form over a CM extension, use its trace form $B$ in the $F$-coordinates. Then $x^TBx/2=h(x,x)$, so the local densities in (1) are norm densities. The real coordinate measure has scalar $\kappa_F$ relative to Lebesgue measure on $F_\infty$, both on the norm line and in every vector coordinate. Hence $\kappa_F^{2n-1}D_\infty(\beta)$ is exactly the coordinate fibre integral of the real Gaussian. The finite Haar product gives $D_f(a,\beta)=\prod_{v<\infty}\omega_{v,\beta}(a^{-1}L_v)$. Consequently (1) is the Gaussian-count input to the [one-vector normalization by dilation](a-dilation-fixes-the-scalar-in-the-one-vector-siegel-mean.md).

### Source and scope

The uniform dilation is [`bounded_a`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/BoundedA.lean#L36); [`core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/BoundedA.lean#L70) integrates the difference and compares the two coefficients. The theta coefficient is [`fourier_coefficient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RealQuadraticFormLemma.lean#L307), and the Eisenstein unfolding is [`fourier_coeff_eis`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SchurFunctionSmoothRightInvariant.lean#L209). The density and inversion rules in (3) are [`schur_function_whittaker_equivariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/SchurFunctionWhittakerEquivariantStatement.lean#L7) and [`quadratic_level_set_density`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/QuadraticLevelSetDensityStatement.lean#L7). The Hermitian coordinate transfer and finite product are used in [`bound_hermitian`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/HaarFundamentalDomainRankOneDensity.lean#L29). The density regularity and average count hypotheses have separate proofs in the source.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
