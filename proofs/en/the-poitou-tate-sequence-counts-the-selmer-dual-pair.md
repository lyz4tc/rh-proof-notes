# The Poitou–Tate sequence counts the Selmer dual pair

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be totally imaginary and let $S$ be a finite set of finite places containing all those above $\ell$. Let $M$ be a finite continuous $G_{F,S}$-module killed by a power $\ell^a$, $a\ge1$, and let $M^D=\operatorname{Hom}(M,\mu_{\ell^a})$ be the cyclotomic dual. Write $P^i(M)=\prod_{v\in S}H^i(F_v,M)$, and use $H^i(M)$ for global cohomology. Fix subgroups $L_v\subseteq H^1(F_v,M)$ and take their exact annihilators $L_v^\perp\subseteq H^1(F_v,M^D)$ under the local cup-to-invariant pairing. The Selmer group for $M$ consists of the global classes restricting into each $L_v$; the dual Selmer group uses the $L_v^\perp$.

**Proposition.** Both Selmer groups are finite, and with $r_2$ the number of complex places,

$$
\#\operatorname{Sel}(M)\,\#H^0(M^D)\,
 \prod_{v\in S}\#H^0(F_v,M)\,(\#M)^{r_2}
=\#\operatorname{Sel}(M^D)\,\#H^0(M)\,\prod_{v\in S}\#L_v.
$$

**Proof.** All cohomology groups used in degrees zero through two are finite. By Poitou–Tate duality the sequence

$$
0\longrightarrow H^0(M)\longrightarrow P^0(M)\longrightarrow H^2(M^D)^\vee
\longrightarrow H^1(M)\xrightarrow{f}P^1(M)
 \xrightarrow{t}H^1(M^D)^\vee
$$

is exact at each displayed term before the final one. Here $A^\vee=\operatorname{Hom}(A,\mathbb Q/\mathbb Z)$, and $t$ sends a tuple to the sum of its local pairings with the restrictions of the dual class. Complex places have trivial modified local terms. The exact sequence is in Theorem I.4.10 of the cited reference. [Milne, *Arithmetic Duality Theorems*](https://www.jmilne.org/math/Books/ADTnot.pdf)

Put $K_1=\ker f$ and $L=\prod_vL_v$. The first part of the sequence gives
$\# K_1=\#H^2(M^D)\,\#H^0(M)/\#P^0(M)$. The image of $\operatorname{Sel}(M)$ under $f$ is $\ker(t|_L)$ by exactness. The annihilator of $t(L)$ in $H^1(M^D)$ is $\operatorname{Sel}(M^D)$, because one can test independently with a tuple supported at one place. A finite group and its character group have the same size, and the annihilator of a subgroup has the size of the quotient. Consequently

$$
\#\ker(t|_L)=\frac{\#L\,\#\operatorname{Sel}(M^D)}{\#H^1(M^D)}.
$$

Multiply it by $\#K_1$ to obtain $\#\operatorname{Sel}(M)$. The global Euler characteristic in the totally imaginary case gives
$\#H^1(M^D)=\#H^0(M^D)\,\#H^2(M^D)(\# M^D)^{r_2}$. Since $\# M^D=\#M$, substitution and cancellation give the result. The global Euler formula is Theorem I.5.1 in the same reference.

**Lean correspondence.** `card_five` counts the kernel of localization from the first half of the displayed sequence. `card_comap` counts the Selmer preimage, and `ker_flip_eq` identifies the annihilator of the transpose of the restricted local pairing with the dual Selmer group. `greenbergWiles_totallyComplex` combines these with the Euler formula. The translation above uses the usual finite-group character dual. On groups killed by $\ell^a$ it identifies with the source's linear dual into $\mathbb Z/\ell^a\mathbb Z$ by choosing the corresponding coefficient character. Source-based reconstruction. [Cardinality in the exact sequence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GreenbergWilesTotallyComplex.lean#L25) · [The annihilator is the dual Selmer group](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GreenbergWilesTotallyComplex.lean#L76) · [The Greenberg–Wiles count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GreenbergWilesTotallyComplex.lean#L110).
