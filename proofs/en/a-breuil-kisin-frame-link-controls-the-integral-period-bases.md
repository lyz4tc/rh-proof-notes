# A Breuil–Kisin frame link controls the integral period bases

**Status: Source-based reconstruction draft.** This note proves the intermediate comparison used by the operator construction, not the construction of the frames or the final operator identity. Its source statement is LinkZ.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement and notation

Fix the local field $K$, Breuil–Kisin datum $\mathrm{bk}$, and period $\tau$ satisfying $\mathrm{bk.IsPer}(\tau)$. Write $S=\mathrm{bk.S}$, $I=A_{\inf}$, $W=\mathrm{WCb}$, and $C=A_{\mathrm{cris}}$. Let $j:I\to W$ and $i:I\to C$ be the indicated inclusions, and put $\mathrm{ev}_W=j\mathrm{ev}$, where $\mathrm{ev}:S\to I$ is the frame evaluation. Write $\psi$ for Frobenius on $S$, $\varphi$ for Frobenius on $C$, and $E$ for the frame's Eisenstein element. Define
$$
 f_I=i\varphi_I,\quad f_A=i\,\mathrm{ev}\,\psi=f_I\mathrm{ev},\quad
 f_0=f_A\circ\mathrm{const},\quad u=i\,\mathrm{ev}(X),
$$
where $\mathrm{const}$ replaces a power series by its constant term as a constant series. Use $z_W,z_I,z_C$ for the images of the integral coefficient ring $\mathbb Z_\ell$ in these rings.

Fix nonnegative integers $N,M$. There is a threshold $n$ depending only on the fixed local data, $N,M$, with the following property. Take any common $k$, frames $(T,A)$ and $(T_1,A_1)$ of height parameter $N$ (possibly different sizes), a rectangular matrix $\Pi$ over $\mathbb Z_\ell$ and a compatible-size rectangular matrix $R$ over $S$. Suppose integral lifts $Y,Y_1$ and admissible corrections $(Q,Q^\ast),(Q_1,Q_1^\ast)$ satisfy the hypotheses below:
$$
 j(Y)=j(\tau)^N T,\quad j(Y_1)=j(\tau)^N T_1,\qquad
 z_W(\Pi)T_1-T\mathrm{ev}_W(R)\equiv0\pmod{\ell^n W}.
$$
The corrections satisfy IsSecQ for $A,A_1$, respectively, with the same $N,k$. Then, writing $Z=f_I(Y)Q$ and $Z_1=f_I(Y_1)Q_1$, one has
$$
 z_C(\Pi) Z_1-Z f_0(R)\equiv0\pmod{\ell^M C}.
 \tag{1}
$$
All ring maps on matrices and all congruences are entrywise. In particular (1) is integral and is asserted before passing to $B_{\mathrm{cris}}$.

## From a frame link to two congruences

Temporarily let $h$ be the available precision in $W$. From the defining equations for the lifts,
$$
 j(z_I(\Pi)Y_1-Y\mathrm{ev}(R))
 =j(\tau)^N\bigl(z_W(\Pi)T_1-T\mathrm{ev}_W(R)\bigr).
$$
The inclusion $j$ reflects $\ell^h$-divisibility, so the left-hand matrix before applying $j$ is divisible by $\ell^h$ in $I$. Apply $f_I$ and use $f_I z_I=z_C$ to get
$$
 z_C(\Pi) f_I(Y_1)-f_I(Y)f_A(R)\equiv0\pmod{\ell^h C}.
 \tag{2}
$$

A second consequence comes from the Frobenius equations for the two frames. Put $P=z_W(\Pi)$, $R_W=\mathrm{ev}_W(R)$, $A_W=\mathrm{ev}_W(A)$, $A_{1,W}=\mathrm{ev}_W(A_1)$, and let $\Phi$ be Frobenius on $W$. The frame equations are $T A_W=e\,\Phi(T)$ and $T_1 A_{1,W}=e\,\Phi(T_1)$, with the **same** $e=\mathrm{ev}_W(E)^N$. Since $\Phi(P)=P$, for $\Delta=P T_1-T R_W$ the exact identity is
$$
 T(R_W A_{1,W}-A_W\Phi(R_W))=e\,\Phi(\Delta)-\Delta A_{1,W}.
$$
Both terms on the right are divisible by $\ell^h$, because $\Phi(\ell)=\ell$. The frame matrix $T$ is invertible over $W$, so cancellation preserves this divisibility. Evaluation intertwines Frobenius, and $\mathrm{ev}_W$ reflects $\ell^h$-divisibility. Thus
$$
 RA_1-A\psi(R)\equiv0\pmod{\ell^h S}.
 \tag{3}
$$
The latter reflection is the composition of the reflection for $j$ with that for $\mathrm{ev}$. For $\mathrm{ev}$, reflection modulo $\ell$ and $\ell$-torsion-freeness of $I$ suffice: divide in $S$ once, cancel the imaged factor of $\ell$ in $I$, and repeat. No inverse to $T$ in $I$ or $C$ is used.

## Correcting the right-hand coefficient map

The two maps $f_A,f_0$ commute with the designated Frobenius maps, and $f_A(s)-f_0(s)\in uC$ for $s\in S$: the nonconstant part is divisible by $X$, which maps under $f_A$ to $u^\ell$. The period-ring inputs give units $v,w\in C^\times$ such that $f_A(E)=\ell v$ and $f_0(E)=\ell w$; the second follows from the Eisenstein constant coefficient. Define
$$
 \alpha=f_A(A),\quad \beta=f_0(A),\quad
 \alpha_1=f_A(A_1),\quad\beta_1=f_0(A_1),\quad
 R_A=f_A(R),\quad R_0=f_0(R).
$$
Put $s=(\ell v)^N$, $t=(\ell w)^N$. The required correction identities give
$$
 sQ\beta=t\alpha\varphi(Q),\qquad
 sQ_1\beta_1=t\alpha_1\varphi(Q_1).
$$
Moreover the frame provides $A_1A_1^\ast=E^{2N}I$, so $\beta_1 B_1=(\ell w)^{2N}I$ for $B_1=f_0(A_1^\ast)$. Finally $Q,Q_1\equiv\ell^k I\bmod u$ by IsSecQ. The matrix
$$
 D=R_A Q_1-Q R_0
$$
is therefore divisible by $u$ entrywise. Applying $f_A,f_0$ to (3) gives modulo $\ell^h C$ the relations $\alpha\varphi(R_A)\equiv R_A\alpha_1$ and $\beta\varphi(R_0)\equiv R_0\beta_1$. These imply
$$
 t\alpha\varphi(D)
 \equiv s R_A Q_1\beta_1-s Q R_0\beta_1
 =s D\beta_1\pmod{\ell^h}.
$$
Right multiply by $B_1$, then multiply by the scalar unit $(v^N w^{2N})^{-1}$. We obtain
$$
 \ell^{3N}D\equiv F\varphi(D)B_1\pmod{\ell^h},\qquad
 F=(v^N w^{2N})^{-1}t\alpha.
 \tag{4}
$$
The multiplier $\ell^{3N}$ is essential data here: no cancellation of a nonunit modulo $\ell^h$ was made.

To extract the smallness of $D$ from (4), write $b=3N$. The period-ring power estimate says that for sufficiently large $q$ (depending on the datum, $b$ and $M$), $\ell^{bq+M}$ divides $u^{\ell^q-1}$ in $C$. Fix one such $q$ and set $h=bq+M$. Since $\varphi(u)=u^\ell$, induction on $j$ using (4) shows
$$
 \ell^{bj}D\equiv u^{\ell^j} D_j\pmod{\ell^h}
$$
for integral matrices $D_j$: start with $D=uD_0$; for the next step apply $\varphi$ to the congruence and multiply on the left by $F$ and on the right by $B_1$. For $j=q$ the right side is divisible by $\ell^h$. The ring $C$ has no $\ell$-torsion, so from $\ell^{bq}D\in\ell^{bq+M}C$ we may cancel $\ell^{bq}$ in the ring and infer $D\in\ell^M C$. The threshold is uniform in the matrix sizes, the frames, the chosen lifts and $k$. This is why feedback under Frobenius suffices despite the apparent loss of $3N$ powers of $\ell$ at each iteration.

## Assembly and handoff to the operator comparison

Use an input precision at least $\max(h,M)$. Combining (2) with $D\equiv0\bmod\ell^M$ gives (1) directly:
$$
 z_C(\Pi) Z_1-ZR_0
 =\bigl(z_C(\Pi) f_I(Y_1)-f_I(Y)R_A\bigr)Q_1+f_I(Y)D.
$$
The operator existence proof needs this only along arbitrarily late layers. It requests a frame link at precision $\max(n,M)$, so the supplied layer index is at least $M$, and applies (1) with the weakened precision $n$. The [additional coefficient-fixing result](an-invariant-section-gives-a-rational-crystalline-basis.md#fixing-constant-evaluations-before-comparing-operators), FixW, says that $\varphi^{n_i}$ fixes every entry of $R_0$ when FixUr holds for $n_i$; the integral coefficient entries of $\Pi$ are likewise fixed. Hence applying $\varphi^{n_i}$ to (1) gives the comparisons required by [the separate integral operator identity](./compatible-period-bases-give-compatible-integral-frobenius-operators.md). This note does not rebuild the bounded-pole lifts $Y$, solve the correction equations for $Q$, establish invariance or FixW, or derive that final identity.

## Lean correspondence

- [LinkZ and OpEx2](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IsOp2One.lean#L36), [frame and link structures](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L67), [coefficient maps and IsSecQ](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/JointApproxOfMem.lean#L54).
- [Working across the two evaluations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/PowDvdOfEv.lean#L12), [reflection for evaluation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinEvWIsUnitInjectiveDvd.lean#L61).
- [Comparison of corrections](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/DvdMulEntriesRight.lean#L36), [the recursion identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/LinkRec.lean#L5), [iteration and torsion cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ZeroAp.lean#L8). The ring inputs are [Frobenius and torsion-freeness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AcrisTorsionFreeCompleteFrobeniusPropertiesStatement.lean#L11) and [the tilt-uniformizer power estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PrimePowDvdTiltUniformizerPowAcrisEventuallyStatement.lean#L12).
- [Product comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/LinkZHolds.lean#L12), [fixed coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/FixWHolds.lean#L13) and [use in the operator existence theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72). No compilation or independent human review was performed for this draft.
