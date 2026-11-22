# A nonzero theta value matches the Eisenstein inversion phase

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the setup and notation of [absolute convergence](denominator-classes-and-lattice-translates-bound-the-eisenstein-series.md). Set $S\tau=-1/\tau$ componentwise. For $b\in F$ and $a\in F^\times$ put $U_b\phi(u)=\psi_f(b\,u^{\mathsf T}Bu/2)\phi(u)$ and $D_a^0\phi(u)=\phi(au)$. If $\mathcal F$ is the self-dual finite Fourier transform, the comparison series satisfies
$$
 \begin{aligned}
 E_{U_b\phi}(\tau+b)&=E_\phi(\tau),\\
 E_{D_a^0\phi}(a^2\tau)&=E_\phi(\tau),\\
 c(\tau) E_{\mathcal F\phi}(S\tau)&=E_\phi(\tau).
 \end{aligned}
$$
The first two identities use reindexing. For the third, a nonzero summand indexed by $b$ is matched with the one at $-b^{-1}$. [Three Eisenstein transformations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/FstarDil.lean#L59)

## The scalar for a reciprocal pair

Fix $b\ne0$, and write $t=-b^{-1}$, $a=b^{-1}$. In the convention of [the finite operators](heisenberg-covariance-determines-the-finite-weil-operators-up-to-a-phase.md), matrix multiplication gives $n(b)w=w n(t)m(a)w n(t)$. The normalized diagonal operator is $|\mathrm N a|^{-M}D_a^0$ by the rational product formula. The two operator products for this matrix therefore agree up to phase:
$$
 U_b\mathcal F=g\,\mathcal F U_tD_a^0\mathcal F U_t,\qquad
 g=\gamma|\mathrm N b|^M,\quad |\gamma|=1.
\tag{1}
$$
Let $\tau_1=\tau+t$ and $\tau_4=a^2 S\tau_1+t$. All intermediate parameters are in the upper half-planes. The matrix identity gives $S\tau_4=S\tau+b$.

We determine $g$ without computing the phase of a finite Gauss integral. Use the theta function $\Theta$ with all isometries equal to the identity in [the Poisson transformation](poisson-summation-matches-the-finite-fourier-and-real-theta-factors.md). For any test $h$, set $h_1=\mathcal F U_t h$ and $h_4=\mathcal F U_tD_a^0 h_1$. Apply translation then inversion to get $\Theta(h,\tau)=c(\tau_1)\Theta(h_1,S\tau_1)$. Apply dilation, translation and inversion to the latter theta value to obtain
$$
 \Theta(h,\tau)=c(\tau_1)c(\tau_4)\Theta(h_4,S\tau_4).
$$
Alternatively, inversion followed by translation by $b$ and then (1) gives $\Theta(h,\tau)=c(\tau)g\,\Theta(h_4,S\tau_4)$. To cancel the common theta value, take $h=1_{N\widehat{\mathcal O}_F^d}$ for a sufficiently large positive integer $N$. Its identity theta sum tends to one as $N\to\infty$: it includes zero, and every nonzero term on $N\mathcal O_F^d$ is dominated by a summable Gaussian on the integral lattice and eventually disappears. Thus this theta value is nonzero for some $N$, and then so is $\Theta(h_4,S\tau_4)$. Since $c(\tau_4)c(S\tau_4)=1$, cancellation yields
$$
 c(\tau)g\,c(S\tau+b)=c(\tau_1).
\tag{2}
$$
[Use a nonzero theta value to determine the multiplier](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/IntFou.lean#L18)

Now take any Schwartz–Bruhat test $\phi$ and integrate (1). For any such test $h$, $\int\mathcal Fh\,d_f u=h(0)$ by Fourier inversion at zero. Both $U_t$ and $D_a^0$ fix the value at zero. Thus $J_{\mathcal F\phi}(b)=g J_\phi(t)$. Multiplying by (2) proves $c(\tau) J_{\mathcal F\phi}(b)c(S\tau+b)=J_\phi(t)c(\tau+t)$, the reciprocal identity. The same inversion formula shows that the constant $(\mathcal F\phi)(0)$ after multiplication by $c(\tau)$ becomes the $b=0$ term of $E_\phi(\tau)$. The $b=0$ term of $c(\tau) E_{\mathcal F\phi}(S\tau)$ becomes $\phi(0)$ since $c(\tau)c(S\tau)=1$. Absolute convergence permits the reindexing $b\mapsto-b^{-1}$ on $F^\times$. This proves inversion. [Integral of the Fourier transform](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/IntFou.lean#L13) · [Pass to the full Eisenstein series](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/FstarDil.lean#L59)

## The two rational changes of variable

The phase identity gives $J_{U_b\phi}(s)=J_\phi(s+b)$, so change the summation variable to $s+b$. At zero the test is unchanged. For dilation, substitute $v=au$ in the finite integral to get $J_{D_a^0\phi}(a^2s)=|\mathrm N a|^{2M}J_\phi(s)$, since $d=2M$ and the finite modulus of $a$ is $|\mathrm N a|^{-1}$. The real Gaussian change of variables gives $c(a^2(\tau+s))=|\mathrm N a|^{-2M}c(\tau+s)$. These cancel term by term upon reindexing by $s\mapsto a^2s$, and $D_a^0$ also preserves the value at zero. [Scale the real Gaussian](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/FstarDil.lean#L11) · [Scale the finite integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/CompanionTheory/AutomorphicTheory/ThetaDilations/FstarDil.lean#L38)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
