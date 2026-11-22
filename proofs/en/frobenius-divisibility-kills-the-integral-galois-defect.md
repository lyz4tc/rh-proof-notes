# Frobenius divisibility kills the integral Galois defect

**Status: Source-based reconstruction draft.** This gives the invariant-section step between the uniform Frobenius section and the construction of an invariant period basis. No Lean build or human review.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Setup and claim

Fix a prime $\ell$, a finite local field $K/\mathbb Q_\ell$, and Breuil–Kisin data with power-series ring $\mathfrak S$, evaluation into $A_{\inf}$, Eisenstein element $E$ and formal variable $X$. Write $R=A_{\rm cris}$, and let $u$ be the image of the evaluation of $X$ in $R$. Use the compatible Frobenius $\phi$ and, for each fixed $g\in G_K$, the ring automorphism $\sigma$ of $R$ induced by $g$. The input period evaluation in the section theorem is fixed. Let $\rho:G_K\to{\rm GL}_d(\mathbb Z_\ell)$ and take a crystalline Breuil–Kisin frame of height bound $N$ for $\rho$. In particular it comes with Frobenius matrices $A,A'$ over $\mathfrak S$ satisfying $AA'=E^{2N}I_d$, and a Galois cocycle matrix $\varepsilon_g$ over $A_{\inf}$ with $\varepsilon_g\equiv I_d$ modulo the evaluated variable.

Write $f:\mathfrak S\to R$ for evaluation followed by Frobenius, and $f_0$ for $f$ applied to constant terms. Put
$$
B=f(A),\quad B'=f(A'),\qquad C_0=f_0(A),\quad C'_0=f_0(A'),\qquad
e=f(E),\quad e_0=f_0(E).
$$
Let $\varepsilon$ be the image of $\varepsilon_g$ after Frobenius and inclusion into $R$. An integral section $Q,Q'$ at exponent $k$ means
$$
QQ'=\ell^{2k}I_d,\qquad Q,Q'\equiv\ell^k I_d\pmod u,\qquad
e^N Q C_0=e_0^N B\phi(Q).
$$
The claim, exactly the conclusion of InvQ, is
$$
\varepsilon\,\sigma(Q)=Q
$$
for every $g\in G_K$. The claim applies to every section with these identities, not just to one chosen by the preceding recurrence.

The source gives the following concrete period-ring inputs for the frame. The ring is $\ell$-torsion-free and $\ell$-adically separated, $\phi$ and $\sigma$ commute and fix $\ell$, and $\phi(u)=u^\ell$, $u\mid\sigma(u)$. The constants $C_0,e_0$ are fixed by $\sigma$. Both $e,e_0$ are $\ell$ times units. The cocycle and crystalline-frame identities give
$$
 e^N\varepsilon\,\sigma(B)=\sigma(e)^N B\phi(\varepsilon),
 \qquad \varepsilon\equiv I_d\pmod u .
$$
The latter congruence follows by applying the coefficient Frobenius to $\varepsilon_g-I_d$: the evaluated variable goes to its $\ell$th power, hence the ideal $(u)$ still divides it. The input about eventual divisibility is: for every nonnegative $c,M$ there is an $n_0$ such that $\ell^{cn+M}\mid u^{\ell^n-1}$ for every $n\ge n_0$.

## The correct integral defect

Take
$$
D=Q'\varepsilon\,\sigma(Q)-\ell^{2k}I_d.
$$
The section congruences and $u\mid\sigma(u)$ give $\sigma(Q)\equiv\ell^k I_d$ modulo $u$. Thus $D$ is entrywise divisible by $u$. This calculation never divides by $\ell$ in $R/(u)$.

We next prove the integral equation
$$
 e_0^{2N}D=C_0\phi(D)C'_0.
 \tag{1}
$$
Here is a shorter equivalent verification of the scalar-cancellation calculation in Lean. Temporarily work in $R[1/\ell]$, into which $R$ injects. Set $U=C_0/e_0^N$ and $V=B/e^N$. They and $Q$ are invertible there: the products $C_0C'_0=e_0^{2N}I_d$, $BB'=e^{2N}I_d$ and $QQ'=\ell^{2k}I_d$ have invertible scalars. The section and frame equations become
$$
QU=V\phi(Q),\qquad \varepsilon\,\sigma(V)=V\phi(\varepsilon),\qquad \sigma(U)=U .
$$
Write $M=Q^{-1}\varepsilon\,\sigma(Q)$. Applying $\sigma$ to the first equation and using its commutation with Frobenius gives
$$
\begin{aligned}
 M U &=Q^{-1}\varepsilon\,\sigma(V)\phi(\sigma(Q))\\
 &=Q^{-1}V\phi(\varepsilon)\phi(\sigma(Q))
  =U\phi(M).
\end{aligned}
$$
The last equality uses $Q^{-1}V=U\phi(Q)^{-1}$. The matrix $D=\ell^{2k}(M-I_d)$ consequently satisfies $DU=U\phi(D)$. Since $C_0C'_0=e_0^{2N}I_d$, multiplying by the cleared inverse of $U$ gives (1), which descends along the injection $R\hookrightarrow R[1/\ell]$. Lean proves (1) in the integral ring by multiplying by non-zero-divisor scalars, avoiding localization. In either check the defect is $Q'\varepsilon\sigma(Q)-\ell^{2k}I_d$, not a defect obtained by assuming $Q$ integral-invertible.

## Divisibility at all precisions

Write $e_0=\ell w_0$ with $w_0$ a unit. Equation (1) gives
$$
\ell^{2N}D=C_0\,\phi(D)\,(w_0^{-2N}C'_0).
$$
The coefficients of the two outer matrices are integral. For any $D$ that satisfies an equation of this form with $\ell^c$ on the left and starts in $uM_d(R)$, induction gives
$$
\ell^{cn}D\in u^{\ell^n}M_d(R)\qquad(n\ge0).
$$
At the inductive step apply $\phi$ to an integral factorization of $\ell^{cn}D$, use that $\phi(\ell)=\ell$ and $\phi(u)=u^\ell$, and multiply by the two outer matrices. Given $M$, take $n$ large enough for $\ell^{cn+M}\mid u^{\ell^n-1}$. Retaining the additional factor of $u$ and cancelling $\ell^{cn}$ in the torsion-free ring shows $D\in\ell^M M_d(R)$. Since $M$ was arbitrary, separatedness gives $D=0$.

Finally multiply $Q'\varepsilon\,\sigma(Q)=\ell^{2k}I_d$ on the left by $Q$, and cancel the non-zero-divisor $\ell^{2k}$ in $R$. This proves the desired Galois identity, without assuming that $u$ is cancellable or that $(u)$ is closed.

## Source correspondence and remaining input

- [InvQ, the interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L30-L33) and [invQ_holds, its proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvQHolds.lean#L16-L121). Lines 19–60 turn the frame relation into the displayed normalized equations; lines 69–121 establish divisibility modulo $u$ and conclude.
- [frobenius_defect_eq](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusEquationOfTwistedCocycleDefect.lean#L67) proves (1) by adjugates and scalar cancellation; [acris_frob_eq_zero](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AcrisFrobeniusMatrixEqZeroOfDvd.lean#L31) is the divisibility argument. The uniform divisibility input is [AcrisPow.main](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PrimePowDvdTiltUniformizerPowAcrisEventually.lean#L70-L83).
- The frame supplies the cocycle relation, and the crystalline period interface supplies the units, separatedness and commutation; the argument above does not reconstruct the period-ring foundations. The next use is [invU_holds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvUHolds.lean#L16), where the invariant section combines with the integral preframe to give an invertible rational period matrix.
- Comparative source: rh-lean-roadmap, sixth book version (22 November 2026, commit 32b37eda73ced0174240bd183e5a0d54edd26eed), [appendix proof of Lemma 40.44, printed pp. 1010–1011](https://github.com/rh-lean-roadmap/rh-lean-roadmap/blob/32b37eda73ced0174240bd183e5a0d54edd26eed/docs/book.pdf). It gives a related derivation using the direct defect $\varepsilon\,\sigma(Q)-Q$. This note instead follows the scaled conjugated defect actually used in InvQ; the calculation in $R[1/\ell]$ is explicitly the equivalent presentation of its integral scalar-cancellation step.
