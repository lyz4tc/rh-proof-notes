# Finite integral operators give denominator decay for the quadratic integral

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be totally real, $d=2M$ with $M\ge1$, and use the finite quadratic space and operators of [the Heisenberg covariance proof](heisenberg-covariance-determines-the-finite-weil-operators-up-to-a-phase.md). Fix a Schwartz–Bruhat function $\phi$. For $b\in F$ put $I(b)=\{t\in\mathcal O_F:tb\in\mathcal O_F\}$ and $D(b)=\mathrm N I(b)$. Then
$$
 \left|J_\phi(b)\right|\le C_\phi D(b)^{-M},
 \qquad J_\phi(b)=\int_{\mathbb A_f^{2M}}
      \psi_f(b\,u^{\mathsf T}Bu/2)\phi(u)\,d_f u.
\tag{1}
$$
This is the finite oscillatory integral used in the Eisenstein series. Also every operator attached to $k\in\mathrm{SL}_2(\widehat{\mathcal O}_F)$ sends $\phi$ to a bounded linear combination of one fixed finite family of Schwartz–Bruhat coset indicators. Both the family and the coefficient bound are independent of $k$ and of the choice of its phase. [Uniform compact-orbit bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/OrbitAdelic.lean#L54) · [Finite oscillatory decay](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/OrbitAdelic.lean#L76)

## Constrain the transformed support and level

Choose a common lattice $L=N\widehat{\mathcal O}_F^{2M}$ small enough that $H_{x,y}\phi=\phi$ for every $x,y\in L$. To obtain it, first take $N$ divisible enough that $L$ is inside the common translation subgroup of $\phi$. Take it also inside the annihilator of a compact open lattice containing the support of $\phi$. Finally enlarge $N$ so the half-pairing character $\psi_f(x^{\mathsf T}By/2)$ is trivial on $x,y\in L$. This is possible by continuity of the pairing at zero and the open kernel of $\psi_f$. The assumed covariance now gives $H_{x,y}T_k\phi=T_k\phi$, since every entry of $k$ preserves the lattice $L$ and hence $(x,y)k\in L^2$.

Taking $y=0$ proves invariance under translations by $L$. Taking $x=0$ proves support in $L^\perp$, because every $y\in L$ must have character value one at a point where $T_k\phi\ne0$. Therefore $T_k\phi$ is a linear combination of the fixed coset indicators of $L\cap L^\perp$ in $L^\perp$, a finite quotient. Each coefficient is bounded by $\|\phi\|_2/d_f u(L)^{1/2}$: if $T_k\phi$ takes the value $c$ at $u$, translation by $L$ makes it equal to $c$ on all of $u+L$, so its squared $L^2$ norm is at least $|c|^2d_f u(L)$. This establishes both the uniform coefficient bound and a uniform bound on the value at zero. [Finite span and coefficient bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/SqPosOfNe.lean#L205)

## Isolate the finite modulus of the denominator

At each finite place $v$ of $F$ the bottom row of $w n(b)$ is $(-1,-b)$. Choose $a_v\in F_v^\times$ with $|a_v|_v=\max(1,|b|_v)^{-1}$. Then $(-a_v,-a_v b)$ is an integral primitive row, so complete it to a matrix $k_v\in\mathrm{SL}_2(\mathcal O_{F_v})$. Comparing bottom rows shows $w n(b)= n(y_v)m(a_v) k_v$ for some $y_v$: the product $w n(b) k_v^{-1}$ is upper triangular with diagonal $(a_v,a_v^{-1})$. For $b$ integral at $v$ take $a_v=1$, $k_v=w n(b)$, $y_v=0$. Thus the choices give $a,y,k$ adelically, with $a$ an invertible idele, $k$ integral, and $|a|_f=D(b)^{-1}$ by the valuations defining $I(b)$. [Local and adelic decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/SpectralGeometry/LocalGlobalProofs/AdelicAnalysis/IwasawaDecompositionAdelicSL2.lean#L157)

Consequently $k=m(a^{-1})n(-y)w n(b)$, whose operator can be taken to be $D_{a^{-1}}U_{-y}\mathcal F U_b$. Evaluate at zero. The multiplier from $U_{-y}$ is $1$ there, and the argument scaling from $D_{a^{-1}}$ preserves zero. Its norm factor is $|a|_f^{-M}=D(b)^M$, and $(\mathcal F U_b\phi)(0)=J_\phi(b)$ by Fourier definition. Thus the absolute value of this operator at zero is $D(b)^M|J_\phi(b)|$. The uniform bound from the preceding paragraph gives (1).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
