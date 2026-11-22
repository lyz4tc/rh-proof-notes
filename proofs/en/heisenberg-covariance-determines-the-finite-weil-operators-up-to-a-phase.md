# Heisenberg covariance determines the finite Weil operators up to a phase

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the finite quadratic space $V=\mathbb A_f^d$, pairing $B$, character $\psi_f$ and self-dual measure of [the finite Fourier calculation](the-finite-fourier-transform-exchanges-a-lattice-and-its-annihilator.md). For $x,y\in V$ write
$$
 H_{x,y}\phi(u)=\psi_f(u^{\mathsf T}By+x^{\mathsf T}By/2)\phi(u+x).
$$
Call a linear bijective $L^2$-isometry $T_g$ of the Schwartz–Bruhat space an operator for $g\in\mathrm{SL}_2(\mathbb A_f)$ if
$$
 H_{x,y}T_g=T_g H_{(x,y)g}.
\tag{1}
$$
Here $(x,y)$ is a row with vector entries. Products of operators correspond to products of matrices, and two such operators for the same matrix differ by a scalar of modulus one. The matrices
$$
 n(b)=\begin{pmatrix}1&b\\0&1\end{pmatrix},\quad
 m(a)=\begin{pmatrix}a&0\\0&a^{-1}\end{pmatrix},\quad
 w=\begin{pmatrix}0&1\\-1&0\end{pmatrix}
$$
have operators $U_b\phi(u)=\psi_f(b\,u^{\mathsf T}Bu/2)\phi(u)$, $D_a\phi(u)=|a|_f^{d/2}\phi(au)$ and $\mathcal F$, respectively, for $b\in\mathbb A_f$ and an invertible finite idele $a$. Here $|a|_f$ is the modulus of scalar multiplication on $\mathbb A_f$. The source calls (1), together with the conditions on $T_g$, `Impl`. [Operator convention](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/CountingDefinitions/AdelicEulerProducts/CountData.lean#L53) · [Composition and generators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L59)

## Check the three operators

Each operator preserves compact support and local constancy, and is invertible. These facts for $\mathcal F$ and its $L^2$ identity were proved in the finite Fourier calculation. For $U_b$, the phase has modulus one, and continuity makes it locally constant because the additive character has an open kernel. For $D_a$, multiplying the argument by $a$ has measure modulus $|a|_f^d$, so the scalar makes the $L^2$ norm unchanged by change of variables.

For $U_b$, expand the quadratic term at $u+x$. Its difference from the value at $u$ is $b\,u^{\mathsf T}Bx+b\,x^{\mathsf T}Bx/2$, which changes $y$ to $y+bx$ in $H$. For $D_a$ substitute $au$, so the translation in the argument is $ax$, and the phase agrees with the phase at $(ax,a^{-1}y)$. For $\mathcal F$, apply the integral definition to $H_{-y,x}\phi$ and substitute $v=z+y$ in the integral. Its integrand becomes
$$
 \phi(z)\,\psi_f(z^{\mathsf T}B(u+x)+y^{\mathsf T}Bu+x^{\mathsf T}By/2),
$$
which is exactly $H_{x,y}\mathcal F\phi(u)$ after integration. This proves (1) for all three generators. Applying (1) twice shows that $T_gT_{g'}$ is an operator for $gg'$. [Unipotent phase](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L75) · [Dilation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L90) · [Fourier operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L118)

## Determine the commutant from coset indicators

An operator commuting with all $H_{x,y}$ commutes with translations $H_{x,0}$ and multiplications by characters $H_{0,y}$. For a compact open additive subgroup $L$, the indicator $1_L$ is invariant under translations by $L$ and multiplication by the characters of $L^\perp$. Any Schwartz–Bruhat function with these two invariances is supported on $(L^\perp)^\perp=L$ and constant there. Thus the image of $1_L$ under a commuting linear operator is a scalar $c_L1_L$. By translation, the same scalar works on every coset of $L$. For any smaller compact open $L'\subseteq L$, $1_L$ is a finite sum of indicators of cosets of $L'$, so $c_L=c_{L'}$. Taking intersections shows the scalar is the same for all $L$. Coset indicators span the Schwartz–Bruhat space, proving scalarity on the whole space.

For two operators $T_g,T'_g$ for the same $g$, $T'_gT_g^{-1}$ commutes with each $H_{x,y}$ by (1). The preceding argument makes it scalar, and its norm is one since both operators are $L^2$-isometries and the space has nonzero functions of positive $L^2$ norm. This proves the phase assertion. [Scalar commutant](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/IsOpenCoset.lean#L307) · [Uniqueness of the unitary operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L147)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
