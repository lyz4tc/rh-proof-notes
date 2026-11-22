# Poisson summation matches the finite Fourier and real theta factors

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the data $F,B,P_\sigma,G_\tau,c(\tau)$ of [the real Gaussian transform](a-hermitian-involution-diagonalizes-the-archimedean-gaussian.md) and the finite transform $\mathcal F$ of [the trace character](the-finite-fourier-transform-exchanges-a-lattice-and-its-annihilator.md). Take a finite-adelic isometry $g_f$ of $B$ and real isometries $g_\sigma$ of $B_\sigma$. For a Schwartz–Bruhat test $\phi$ on $\mathbb A_f^d$, put
$$
 \Theta_g(\phi,\tau)=\sum_{x\in F^d}
   \phi(g_f x)G_\tau((g_\sigma\sigma(x))_\sigma).
$$
For $b\in F$ and $a\in F^\times$, let $U_b\phi(x)=\psi_f(b\,x^{\mathsf T}Bx/2)\phi(x)$, $D_a^0\phi(x)=\phi(ax)$. Then the series converges absolutely and satisfies
$$
\begin{aligned}
 \Theta_g(U_b\phi,\tau+b)&=\Theta_g(\phi,\tau),\\
 \Theta_g(D_a^0\phi,a^2\tau)&=\Theta_g(\phi,\tau),\\
 c(\tau)\Theta_g(\mathcal F\phi,S\tau)&=\Theta_g(\phi,\tau).
\end{aligned}
\tag{1}
$$
The archimedean addition and multiplication in (1) are taken through the real embeddings. These are the three rules used to control the theta average on all upper half-planes. [Translation and dilation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionModularity.lean#L141) · [Fourier inversion law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionAutomorphy.lean#L285)

## Absolute convergence and the rational changes of variable

The preimage under $g_f$ of the support of $\phi$ is compact, hence contained in $N^{-1}\widehat{\mathcal O}_F^d$ for some positive integer $N$. Only the rational lattice $N^{-1}\mathcal O_F^d$ can contribute. Its archimedean images form a Euclidean lattice. Since all $g_\sigma$ are invertible and $P_\sigma$ positive definite, $|G_\tau(g_\infty x)|\le e^{-c_0 \|x_\infty\|^2}$ for some $c_0>0$. This has finite sum on the lattice, by comparing a lattice basis to the ordinary Euclidean norm and summing a product of one-dimensional Gaussian tails. This proves absolute convergence. The same reasoning applies to every transformed test. [Summability on a common denominator lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaSeriesSummable.lean#L197)

In a term of the first transformation, the finite phase is $\exp(-\pi i\operatorname{Tr}(b\,x^{\mathsf T}Bx))$ by the isometry condition on $g_f$. The real shift supplies its inverse, using the trace as the sum of the embeddings and the isometries $g_\sigma$. Thus the terms agree individually. In the second transformation, the quadratic form in the Gaussian and its majorant scale by $\sigma(a)^2$, and the finite argument scales by $a$. The transformed summand is the original one at $ax$. This is a bijection on $F^d$, giving the second rule. [Phase cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionModularity.lean#L76) · [Reindexing a dilation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionModularity.lean#L118)

## The Poisson formula for a finite coset

First take all $g$ equal to the identity, and let $\phi$ be the indicator of $a_0+L_f$ with $a_0\in F^d$, $L_f=N\widehat{\mathcal O}_F^d$, $N>0$. Its rational points are $a_0+N\mathcal O_F^d$. Let $M$ denote the real embedded lattice of $N\mathcal O_F^d$, of covolume $V_M=N^{fd}|\operatorname{disc}(F)|^{d/2}$, and let $B_\infty$ be the block diagonal matrix of $B_\sigma$. The Euclidean dual of $M$ consists exactly of $B_\infty y_\infty$ for
$$
 y\in F^d,\qquad By\in N^{-1}(\mathfrak d_F^{-1})^d.
\tag{2}
$$
Indeed the pairing with $N\mathcal O_F^d$ becomes the trace pairing. Its dual using the trace dual of an integral basis gives a full Euclidean dual basis, proving equality. Condition (2) is also the condition $y_f\in L_f^\perp$ under the finite $\chi$ of the transform. [Dual basis via the trace pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/DualLatticeParametrization.lean#L40) · [Adelic annihilator test](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/DualLatticeMembershipTrace.lean#L36)

Use real Poisson summation with the positive sign in the Fourier kernel. It expresses the sum of $G_\tau$ on $a_{0,\infty}+M$ as $V_M^{-1}$ times the sum of its Fourier transform on the Euclidean dual, multiplied at a dual vector $v$ by $\exp(-2\pi i\,a_{0,\infty}\cdot v)$. The sign follows by applying the Fourier series of the periodization to the negative frequency. The series and its Fourier series converge absolutely for a Gaussian. At $v=B_\infty y_\infty$, (1) of [the real Gaussian calculation](a-hermitian-involution-diagonalizes-the-archimedean-gaussian.md) makes the Fourier transform $c(\tau)G_{S\tau}(y_\infty)/|\mathrm N\det B|^{1/2}$. Its Poisson phase is $\psi_f(a_0^{\mathsf T}By)$. On the finite side the transform of the coset indicator is this same phase times $d_f x(L_f)$, on exactly the set (2). Finally
$$
 d_f x(L_f)=V_M^{-1}|\mathrm N\det B|^{-1/2},
$$
because (1) of [the finite measure calculation](the-finite-fourier-transform-exchanges-a-lattice-and-its-annihilator.md) scales by $N^{-fd}$ at that lattice. The Poisson sum is therefore $c(\tau)\Theta_1(\mathcal F\phi,S\tau)$. Linear combinations give this for every test because each such function is a finite sum of the indicated cosets, and their representatives can be taken rational by density. [Poisson summation for the Gaussian](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionAutomorphy.lean#L96) · [Match the finite and real coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionAutomorphy.lean#L159)

## Reinsert the orthogonal matrices

Absorb $g_f$ into the test by writing $\phi\circ g_f$. The map $g_f$ preserves the finite Haar measure, since the isometry equation implies its determinant has square one and hence unit modulus. It preserves the finite Fourier pairing $\chi$, so $\mathcal F(\phi\circ g_f)=(\mathcal F\phi)\circ g_f$ by change of variables. At each real embedding absorb $g_\sigma$ into the majorant, replacing $P_\sigma$ by $g_\sigma^{\mathsf T}P_\sigma g_\sigma$. This is again a majorant of $B_\sigma$, by the isometry equation, and its Gaussian is $G_\tau\circ g_\infty$. Its Gaussian integral is the same because $|\det g_\sigma|=1$ at each place. Thus $c(\tau)$ is unchanged and the identity for the changed test and majorant is exactly the inversion in (1). [Reinsert the given orthogonal matrices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/ThetaFunctionAutomorphy.lean#L285)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
