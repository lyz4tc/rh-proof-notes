# A uniform Frobenius section over the integral crystalline period ring

**Status: Source-based reconstruction draft (Galois batch 02).** The proof below follows the pinned Lean bodies of `coreU_holds` and `secU_holds`. It constructs the correction matrices used before the Galois invariance and period-basis steps; it does not reprove the frame link or the final operator comparison.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement and role

Let $\ell$ be prime, let $K/\mathbb Q_\ell$ be a finite local extension, and fix its chosen Breuil–Kisin package. Write $\mathfrak S$ for its power series ring, $E$ for its distinguished Eisenstein series, $\psi:\mathfrak S\to A_{\mathrm{cris}}$ for the Breuil–Kisin evaluation followed by the inclusion from $A_{\inf}$, and $\varphi$ for Frobenius on $A_{\mathrm{cris}}$. Put
$$
u=\psi(X),\quad f=\psi\circ\varphi_{\mathfrak S},\quad
f_0=f\circ\operatorname{const},
$$
where $\operatorname{const}$ regards the constant term as a constant series. Apply all ring maps entrywise to matrices.

For every height parameter $N\ge0$, there is an integer $k\ge0$ **before** any matrix dimension or matrices are chosen, such that, for every $d$ and $A,A'\in M_d(\mathfrak S)$ with $AA'=E^{2N}I$, there are $Q,Q'\in M_d(A_{\mathrm{cris}})$ with
$$
QQ'=\ell^{2k}I,\qquad Q\equiv Q'\equiv\ell^k I\pmod u,
$$
and
$$
 f(E)^N Q f_0(A)=f_0(E)^N f(A)\varphi(Q).
$$
The congruences are entrywise. This is `SecU`, with the conclusion packaged as `IsSecQ`. The order of quantifiers is what lets `opEx_holds` choose the same $k$ for the target and for all lattice layers, despite their varying dimensions.

## The abstract section construction

First work over any commutative ring $R$ complete and separated for powers of $(\ell)$, where multiplication by the image of $\ell$ is injective. The abstract lemma only needs $\ell$ to be a natural number with these properties. Let $\varphi:R\to R$ be a ring endomorphism and suppose $\varphi(u)=u^q$ for a positive integer $q$. In particular $\varphi(\ell)=\ell$. Assume given four square matrices of size $d$ and a defect matrix $\Gamma$:
$$
\alpha\alpha'=\beta\beta'=\ell^{2N}I,\qquad
\ell(\alpha-\beta)=u^q\Gamma .
$$
Assume moreover that an integer $n_0\ge0$ satisfies the following for all $n\ge n_0$:
$$
 \ell^{(2N+1)(n+1)+1}\mid u^{q^{n+1}-1}. \tag{1}
$$
Set $k=(2N+1)n_0$. The abstract output is the same product and congruences as above, with the intertwining identity $Q\beta=\alpha\varphi(Q)$.

### The successive differences

Define $P_0=I$ and $P_{n+1}=\alpha\varphi(P_n)\beta'$. Write $D_n=P_{n+1}-\ell^{2N}P_n$. At $n=0$,
$$
 \ell D_0=\ell(\alpha-\beta)\beta'=u^q\Gamma\beta'.
$$
For $n\ge0$, $\ell D_{n+1}=\alpha\varphi(\ell D_n)\beta'$. Induction and $\varphi(u)=u^q$ give $\ell D_n=u^{q^{n+1}}M_n$ for integral matrices $M_n$. Two consequences are needed; they concern different ranges of indices.

For every $n\ge0$, the finite iterate satisfies
$$
 \ell^n(P_n-\ell^{2Nn}I)\in uM_d(R). \tag{2}
$$
This holds at $0$. For the step, write the expression inside the next parentheses as
$D_n+\ell^{2N}(P_n-\ell^{2Nn}I)$. After multiplication by $\ell^{n+1}$ the first term is divisible by $u$, since $\ell D_n$ already is, and the second is divisible by $u$ by the inductive hypothesis. No cancellation modulo $u$ is used here.

For $n\ge n_0$, factor one $u$ **before** using (1), then cancel one $\ell$ in $R$, not in a quotient:
$$
 D_n=\ell^{(2N+1)(n+1)}u C_{n-n_0} \tag{3}
$$
for some integral matrices $C_j$. The extra $+1$ in (1) pays for that cancellation; the exponent $-1$ on the right keeps the factor $u$ available for the eventual congruence.

### Construct the normalized limit integrally

Rather than assume that normalized quotients are integral, construct them by finite sums. Define
$$
 S_j=P_{n_0}+u\sum_{i=0}^{j-1}\ell^{k+i+1}C_i.
$$
Then $P_{n_0+j}=\ell^{2Nj}S_j$ for every $j$. It holds at $0$, and (3) gives it at $j+1$ because
$$
 (2N+1)(n_0+j+1)-2N(j+1)=k+j+1.
$$
The series $T=\sum_{i\ge0}\ell^{k+i+1}C_i$ converges entrywise by $\ell$-adic completeness. Take $S=P_{n_0}+uT$. In particular $S-S_j$ is entrywise divisible by $\ell^j$; the source constructs a limit for the series **after factoring out** $u$. Thus $S-P_{n_0}=uT$ exactly, not just in the closure of $(u)$. Multiplying this by $\ell^{n_0}$ and using (2) at $n_0$ gives $\ell^{n_0}S\equiv\ell^k I\bmod u$.

Repeat this construction for $P'_0=I$, $P'_{n+1}=\beta\varphi(P'_n)\alpha'$, interchanging the two pairs and using the defect $-\Gamma$. This gives $S'_j$ and $S'$ with the same bounds and congruence.

### Product and intertwining survive the limit

We also have $\beta'\beta=\ell^{2N}I$ integrally. Indeed $\det(\beta)\det(\beta')=\ell^{2Nd}$, so $\det(\beta)$ is a nonzerodivisor; applying the adjugate on the left of $\beta\beta'\beta=\ell^{2N}\beta$ permits canceling $\det(\beta)$. The equality is not justified by declaring $\ell$ invertible in $R$.

The recurrences now give $P_nP'_n=\ell^{4Nn}I$ by induction. In the step the middle product is $\beta'\beta=\ell^{2N}I$, Frobenius preserves the preceding scalar power, and the remaining $\alpha\alpha'$ contributes the second $\ell^{2N}$. Substitution of the two normalized sequences and cancellation of $\ell^{4Nj}$ give $S_jS'_j=\ell^{4Nn_0}I$, hence $SS'=\ell^{4Nn_0}I$. Indeed the difference is divisible by $\ell^j$ for every $j$ and the ring is separated.

Similarly the recurrence multiplied on the right by $\beta$ gives
$$
 S_{j+1}\beta=\alpha\varphi(S_j)
$$
after canceling the common factor $\ell^{2N(j+1)}$. Frobenius preserves divisibility by $\ell^j$, so separatedness gives $S\beta=\alpha\varphi(S)$. Set $Q=\ell^{n_0}S$, $Q'=\ell^{n_0}S'$. The product exponent is $2n_0+4Nn_0=2k$, the congruences were proved by (2), and Frobenius fixes the rescaling. This proves `CoreU`.

## Specialize to the Breuil–Kisin evaluations

For $R=A_{\mathrm{cris}}$ and $q=\ell$, the period-ring inputs give $\ell$-torsion-freeness, $\ell$-adic completeness and $\varphi(u)=u^\ell$. They also give units $v,w_0\in R^\times$ such that
$$
 f(E)=\ell v,\qquad f_0(E)=\ell w_0.
$$
The first is the Frobenius evaluation input. The second uses the Eisenstein constant coefficient, which is $\ell$ times a unit before evaluation, and both maps preserve units. Write $a=v^{-1}$ and $b=w_0^{-1}$. Set
$$
 \alpha=a^N f(A),\quad \alpha'=a^N f(A'),\qquad
 \beta=b^N f_0(A),\quad \beta'=b^N f_0(A').
$$
Each product with its primed matrix is then $\ell^{2N}I$.

For every power series $s$, its nonconstant part is divisible by $X$. Since $\varphi_{\mathfrak S}(X)=X^\ell$, we get $f(s)-f_0(s)\in u^\ell R$. In particular write
$$
 f(A)-f_0(A)=u^\ell G,\quad
 \ell(v-w_0)=u^\ell z .
$$
Choose $t$ with $w_0^N-v^N=(w_0-v)t$, by the difference-of-powers identity. The inverse unit factors have difference $a^N-b^N=a^Nb^N(w_0^N-v^N)$, so
$$
 \ell(\alpha-\beta)
 =u^\ell\bigl(\ell a^N G-a^Nb^N zt\,f_0(A)\bigr).
$$
The sign of the second term follows from the order $v-w_0$ in the Eisenstein evaluation difference. In particular this comparison does not divide by $\ell$ in $A_{\mathrm{cris}}$.

The eventual crystalline divisibility estimate, with slope $2N+1$ and offset $1$, yields $n_0$ with $\ell^{(2N+1)m+1}\mid u^{\ell^m-1}$ for all $m\ge n_0$. Substituting $m=n+1$ gives (1) throughout its required range. This choice depends on the fixed ring data and $N$, not $d,A,A'$. Applying `CoreU` gives $Q,Q'$ with the claimed common $k$. Finally its intertwining equation reads
$$
 b^N Q f_0(A)=a^N f(A)\varphi(Q).
$$
Multiplying by the common scalar $\ell^Nv^Nw_0^N$ puts $f(E)^N$ on the left and $f_0(E)^N$ on the right, as required for `IsSecQ`. This proves `SecU`.

## Lean anchors and boundary

- [`CoreU` and `SecU` statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L17-L28); [`IsSecQ` and the evaluation maps](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/JointApproxOfMem.lean#L54-L74).
- [Adic series existence and adjugate cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoreUHolds.lean#L38-L89); [recurrence, finite congruence, and quotient-sum limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoreUHolds.lean#L91-L214); [product and intertwining](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoreUHolds.lean#L216-L302).
- [Crystalline specialization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/SecUHolds.lean#L12-L86); [crystalline divisibility estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PrimePowDvdTiltUniformizerPowAcrisEventually.lean#L70-L76); [use of the common exponent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72-L84).
- The period-ring package providing torsion-freeness, completeness and Frobenius compatibility and the eventual divisibility estimate are explicit inputs. After this lemma, [`InvQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvQHolds.lean#L61-L121) proves the Galois cocycle identity and [`InvU`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/InvUHolds.lean#L16-L92) constructs the rational invariant period basis. Neither assertion follows merely from invertibility up to a scalar; neither is proved here.
