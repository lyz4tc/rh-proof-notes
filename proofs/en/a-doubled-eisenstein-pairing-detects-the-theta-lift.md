# A doubled Eisenstein pairing detects the theta lift

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$, the base $B$, the definite pair $X,W$ of ranks $n,d\ge1$, the characters $\chi_X,\chi_W$, the model $M$, and its Weil action $\omega$ satisfy the certified Weil-pair conditions of the [stable-range lift](a-definite-theta-lift-in-the-stable-range.md). The argument here allows nonscalar Gram matrices, keeping the signatures $(n,0)$, $(d,0)$ of $X$ and $iW$ respectively and all the lattice-model conditions. Let $G=U(X)(\mathbb A_F)$ and $H=U(W)(\mathbb A_F)$, and let $e:G\times G\to U(X\oplus(-X))(\mathbb A_F)$ be the doubled embedding. Take the Siegel stabilizer and height $a$ of the model. Assume $A(g)^t=a(e(g,1))^t$ is integrable on $G$ for all $t\ge t_0$, with $t_0<d/2$. For any additive Haar measure on $M_{n,d}(\mathbb A_F)$, any $\Phi$ in the span of pure tensors of archimedean polynomial Schwartz functions and finite Schwartz functions with vacuum tails, and any continuous left $U(X)(F)$-invariant $\phi$, put
$$
C_\Phi(g)=\langle\omega(g,1)\Phi,\Phi\rangle,\qquad
m_\phi(g)=\int_{[G]} \phi(yg)\overline{\phi(y)}\,dy .
$$
Here the Weil pairing is the integral against the chosen additive Haar measure, linear in its first argument. The product $C_\Phi(g)\overline{m_\phi(g)}$ is integrable. If the theta lift $\Theta(\Phi,\phi)$ vanishes identically on $H$, then
$$
\int_G C_\Phi(g)\overline{m_\phi(g)}\,dg=0 .
$$
The hypothesis on $\phi$ here does not require it to belong to an irreducible automorphic representation. The implication, by its contrapositive, is the analytic input to [nonvanishing](finite-place-bumps-make-the-stable-range-theta-lift-nonzero.md). [Certified pair](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThetaBasicK.lean#L17) · [Statement of `Rallis_k`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/GalTPDefs.lean#L61) · [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGRallis.lean#L99)

## Turning the Weil coefficient into a section

Set $s_0=(d-n)/2$. In the doubled Schrödinger coordinates, the two-factor Schwartz function $Q$ built from $\Phi$ and $\overline\Phi$ is obtained from $\Phi\otimes\overline\Phi$ by the model's identification. If $\omega_2$ is the doubled Weil action and $l$ its section functional, write $f(x)=l(\omega_2(x)Q)$. At the special point this is a continuous Siegel section, with parabolic character $\chi_W$ and real absolute-value exponent $s_0+n/2=d/2$. Its deformation at $z$ is $f_z(x)=a(x)^{z-s_0}f(x)$. The doubling identities give a constant $c'>0$ such that
$$
f(e(1,g))\,\chi_W(\det g)^{-1}=c'C_\Phi(g^{-1}).
$$
In this formula $\det g$ is an $E$-idele. Indeed $e(1,g)=e(g,g)e(g^{-1},1)$. The first factor is parabolic and has determinant of absolute value $1$, so its character is canceled by $\chi_W(\det g)^{-1}$. Evaluation against $l$ on the second factor gives the Weil pairing via the positive normalization $c'$ between the section functional and additive Haar integration. The same factorization gives $a(e(1,g))=A(g^{-1})$. [Section statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThkBaseStmtX.lean#L25) · [Doubled model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThkBaseDblW.lean#L26) · [Coefficient and height identities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGRallis.lean#L126)

Continuity on the compact Siegel stabilizer and the parabolic transformation law give $|f(x)|\le C a(x)^{d/2}$ for a constant $C$. The identity therefore bounds $|C_\Phi(g)|$ by $(C/c')A(g)^{d/2}$. The compact quotient $[G]$ gives a uniform bound on $|m_\phi|$ by Cauchy–Schwarz. It follows that
$$
Z(z)=\int_G A(g)^{z-s_0}C_\Phi(g)\overline{m_\phi(g)}\,dg
$$
is absolutely convergent and holomorphic on $\operatorname{Re}z>t_0+s_0-d/2$. In detail, the norm bound on any sufficiently small closed parameter disk is a constant times $A(g)^{t_1}+A(g)^{t_2}$, where $t_1,t_2$ are the minimum and maximum of $\operatorname{Re}(z-s_0)+d/2$ on the disk. Both exponents are beyond the integrability threshold, and the two terms bound the powers whether $A(g)\le1$ or $A(g)\ge1$. The locally dominated holomorphic parameter integral is therefore holomorphic. In particular it is absolutely convergent at $s_0$. [Estimate and convergence in the proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGRallis.lean#L149)

## Continuing the unfolded integral to the special value

Use the following normalized Siegel–Weil and continuation input for the doubled model. With $K$ the model's Siegel stabilizer and $D_H$ a finite-volume fundamental domain for $U(W)(F)$ in $H$, there is an open parameter set $\Omega$ with discrete complement, containing $s_0$ and a right half-plane. The continuous family $\widehat E(z,x)$ is holomorphic in $z$ on $\Omega$ at each $x$, is locally of uniform polynomial growth in the group height, and equals the Eisenstein sum of $f_z$ on the right half-plane. At $s_0$ its value is $b$ times the mean over $D_H$ of the doubled theta kernel of $Q$, where $b=1$ if $n<d$ and $b=2$ otherwise. This statement is supplied in Lean by `SWFullX_k` for the polynomial Schwartz box, the definite target and the doubled coordinates used here. [Normalized Siegel–Weil statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThkBaseStmtX.lean#L33) · [Continuation conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/ThetaLifts/LatticeBasics/Hypotheses2.lean#L53) · [Proof interface supplying the normalized statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThkBaseNormZeta.lean#L17)

Pair this family with $\phi$ on both copies of the compact source quotient:
$$
K(z)=\int_{[G]^2}\widehat E(z,e(x,y))\,\chi_W(\det y)^{-1}
                 \phi(y)\overline{\phi(x)}\,dx\,dy .
$$
The Eisenstein kernel is invariant under the two rational source groups on the right half-plane where it is a sum. Holomorphic continuation preserves that invariance. The compact quotients admit compact sets of representatives, on which joint continuity bounds the integrands uniformly for $z$ in compact parameter disks. Thus $K$ is holomorphic on $\Omega$. On a sufficiently far right half-plane the unfolding identity for the doubled Eisenstein sum gives
$$
K(z)=\int_G f_z(e(1,g))\,\chi_W(\det g)^{-1}m_\phi(g)\,dg.
$$
In this identity the rational-pair orbit is the one of the diagonal source group, since the source form is anisotropic. The unfolded integration first gives $\phi(xg)\overline{\phi(x)}$ on $[G]$ and then integrates over $g\in G$. Integrability follows on this half-plane from the same section bound with shifted exponent. Substitute the section identity, use $m_\phi(g^{-1})=\overline{m_\phi(g)}$ by unitarity, and change $g$ to $g^{-1}$. This gives $K(z)=cc'Z(z)$, where $c\ne0$ is the Haar factor from inversion. The half-plane of holomorphy of $Z$ stays connected after removing the discrete complement of $\Omega$, since a polygonal path between two interior points can detour around the finitely many removed points along it. The identity theorem gives $K(s_0)=cc'Z(s_0)$. [Holomorphy and unfolding of the paired family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/ThkBaseKPair.lean#L21) · [Separate unfolds-to-pair integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/Unfold0K.lean#L18) · [Continuation of the identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGRallis.lean#L186)

At $s_0$ the doubled kernel factors into the theta kernels of $\Phi$ and its conjugate, with a factor $\chi_W(\det y)$ that cancels the character in the pairing. The normalization $b$ remains. Since $[G]$ and $[H]=U(W)(F)\backslash H$ are compact and the kernels and $\phi$ are continuous, Fubini gives
$$
K(s_0)=\frac{b}{\operatorname{vol}([H])}\int_{[H]}
 \left|\int_{[G]}\theta_\Phi(x,h)\overline{\phi(x)}\,dx\right|^2\,dh .
$$
This is zero if the lift vanishes. As $cc'\ne0$ and $A(g)^{s_0-s_0}=1$, $Z(s_0)=0$ is the desired equation. [Special-value comparison with the squared lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/ThetaKernels/TPGRallis.lean#L210)

The construction of the doubled Weil model and section, the normalized Siegel–Weil theorem and its Eisenstein continuation, and the rational orbit unfolding remain internal inputs. Their exact interfaces are linked at the steps where they are needed.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
