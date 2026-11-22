# A majorant involution diagonalizes the archimedean Gaussian

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be totally real with embeddings $\sigma$, $B$ an invertible symmetric $d\times d$ matrix over $F$, and $P_\sigma$ real symmetric positive matrices with $P_\sigma B_\sigma^{-1}P_\sigma=B_\sigma$, where $B_\sigma=\sigma(B)$. For $\tau=(\tau_\sigma)$ in the product of upper half-planes, define
$$
 G_\tau(x)=
 \exp\biggl(\pi i\sum_\sigma\Re(\tau_\sigma)x_\sigma^{\mathsf T}B_\sigma x_\sigma
            -\pi\sum_\sigma\Im(\tau_\sigma)x_\sigma^{\mathsf T}P_\sigma x_\sigma\biggr)
$$
on the product of the real vector spaces, and set $c(\tau)=|\mathrm N_{F/\mathbb Q}\det B|^{1/2}\int G_\tau(x)\,dx$, with ordinary product Lebesgue measure. Put $S\tau=(-1/\tau_\sigma)_\sigma$. Then
$$
 |\mathrm N_{F/\mathbb Q}\det B|^{1/2}
  \int G_\tau(x)\exp\!\left(2\pi i\sum_\sigma
              x_\sigma^{\mathsf T}B_\sigma y_\sigma\right)\,dx
 = c(\tau)G_{S\tau}(y),
\tag{1}
$$
$$
 |c(\tau)|=\prod_\sigma|\tau_\sigma|^{-d/2},
 \qquad c(\tau)c(S\tau)=1 .
\tag{2}
$$
The project uses this for $d=2M$. [Gaussian Fourier theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ArchimedeanGaussianFourier.lean#L52) · [The flattened real coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/GaussianFourierTransformFormula.lean#L62)

For one $\sigma$ set $S_\sigma=P_\sigma^{-1/2} B_\sigma P_\sigma^{-1/2}$, a real symmetric involution by the majorant identity. In the transformed coordinates $z=P_\sigma^{1/2}x_\sigma$, use an orthogonal matrix diagonalizing $S_\sigma$, and apply the same coordinate changes in $y_\sigma$. In a coordinate with eigenvalue $\epsilon\in\{1,-1\}$, the Gaussian is $e^{-\pi a z^2}$ with $a=\Im\tau_\sigma-i\epsilon\Re\tau_\sigma$, so $\Re a>0$. The Fourier character is $e^{2\pi i\epsilon z u}$. The one-dimensional Gaussian integral gives
$$
 \int_{\mathbb R}e^{-\pi a z^2}e^{2\pi i\epsilon z u}\,dz
     = a^{-1/2}e^{-\pi u^2/a},
$$
using the square root positive for real $a>0$ and continued on the right half-plane. This identity follows for positive real $a$ by the ordinary real Gaussian Fourier transform and then for $\Re a>0$ by holomorphic continuation, with absolute convergence locally uniform in $a$. Now $a^{-1}=\Im(S\tau)_\sigma-i\epsilon\Re(S\tau)_\sigma$. Thus the transformed Gaussian is exactly the Gaussian for $S\tau$, multiplied by its integral factor at $u=0$. This establishes (1) after taking all coordinates and places.

The determinant of the majorant equation gives $\det P_\sigma=|\det B_\sigma|$. Therefore the Jacobian $\prod_\sigma(\det P_\sigma)^{-1/2}$ from the coordinate changes cancels $|\mathrm N\det B|^{1/2}$. The scalar $c(\tau)$ is the product of the $a^{-1/2}$ factors. Since $|a|=|\tau_\sigma|$, its modulus is as in (2). In the same coordinates each factor of $c(S\tau)$ is $(a^{-1})^{-1/2}$, with the same choice of branch. Their product is $1$ because both $a$ and $a^{-1}$ are in the right half-plane and their arguments are opposite. This proves (2). All Gaussians are integrable since the real quadratic form in the exponent is negative definite. [One real place](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/RealGaussianFourierTransform.lean#L122)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
