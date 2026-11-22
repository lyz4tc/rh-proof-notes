# Polarized cocycle evaluations span when the representations differ

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $G$ be a group with an involutive automorphism $\sigma$, $L\triangleleft G$ a $\sigma$-stable normal subgroup, and $K$ a field. Let $T_1,T_2:G\to\operatorname{GL}_r(K)$ be trivial on $L$. Suppose $T_1$ and $T_2\circ\sigma$ both span $M_r(K)$ and are inequivalent. Assume $z\in G$ is central modulo $L$ and

$$
 T_1(z)=dI,\quad T_2(z)=eI,\quad
 T_1(\sigma z)=eI,\quad T_2(\sigma z)=dI
$$

with $d\ne e$ and $d,e\ne1$. Let $x_i,y_j$ be cocycles of $T_1,T_2$, respectively, representing linearly independent families of classes. For $h\in L$ let $M(h)$ be the matrix with entry
$\langle x_i(h),y_j(h)\rangle-\langle x_i(\sigma h),y_j(\sigma h)\rangle$, where the pairing is the standard dot product.

**Proposition.** The matrices $M(h)$, $h\in L$, linearly span the space of all matrices of this size.

**Proof.** A linear functional on these matrices has a coefficient array $c_{ij}$. Assume it vanishes on every $M(h)$, and put $B(u,v)=\sum_{i,j}c_{ij}\langle u_i,v_j\rangle$. The cocycles restrict to additive functions on $L$. Evaluate the zero identity at $hk$ and subtract the identities at $h,k$. In each of the two terms for $M$ this leaves the two cross terms of the bilinear form. Replace $k$ by $gkg^{-1}$, still in $L$. Since $x_i(gkg^{-1})=T_1(g)x_i(k)$ and similarly for $y_j$, the resulting relation is

$$
\begin{aligned}
B(x(h),T_2(g)y(k))+B(T_1(g)x(k),y(h))&\\
-B(x(\sigma h),T_2(\sigma g)y(\sigma k))
-B(T_1(\sigma g)x(\sigma k),y(\sigma h))&=0 .
\end{aligned}
$$

Replace $g$ by $gz$. The first and last terms are multiplied by $e$, and the middle two by $d$. Subtract $e$ times the original equation and divide by $d-e$. This gives the identity of matrix coefficients

$$
B(T_1(g)x(k),y(h))=B(x(\sigma h),T_2(\sigma g)y(\sigma k)).
$$

For fixed $h,k$, the two sides are linear functionals of the respective matrices. The [matrix coefficient separation](a-central-scalar-keeps-cocycle-classes-visible-on-a-small-subgroup.md) makes the functional on the left identically zero on $M_r(K)$. Substituting the matrix unit $E_{pq}$ now gives
$\sum_j(\sum_i c_{ij}x_i(k)_q)y_j(h)_p=0$, for all $p,q,h,k$. The restrictions $y_j|_L$ are independent by the same central-scalar note, applied with scalar $e$. Thus $\sum_i c_{ij}x_i(k)_q=0$ for each $j,q,k$. Independence of the restrictions $x_i|_L$, using scalar $d$, forces every $c_{ij}$ to vanish. In a finite-dimensional space the absence of a nonzero annihilating functional is equivalent to spanning.

In the Selmer application the second representation is the cyclotomic dual. The scalar values are $d,d^{-1}$, and the tame choice makes $d^2-1\ne0$. The integral conjugate-dual relation and trivial cyclotomic value at $z$ exchange the two scalars at $\sigma z$. The residual matrix-span hypothesis persists on extending the coefficient field because each matrix unit already has an expression over the original residue field.

**Lean correspondence.** `span_abstract` proves the polarization, scalar separation and matrix-unit argument. `spanOdd` supplies the four scalar identities, the spanning hypotheses, and the inequivalence in this case. Source-based reconstruction. [Polarization and scalar separation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleFormsSpanOddResidueChar.lean#L96) · [Specialization to the cyclotomic dual](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleFormsSpanOddResidueChar.lean#L231).
