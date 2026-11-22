# Euler characteristics count the residual Selmer obstructions

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $F$ be a totally imaginary number field, $r_2$ its number of complex places, and $S$ a finite set of finite places containing every place above $\ell$. Write $G_{F,S}$ for the Galois group of the maximal extension unramified at finite places outside $S$. Let $A$ be a finite discrete continuous $G_{F,S}$-module killed by $\ell$, with $H^0(G_{F,S},A)=0$. Suppose $H^0(G_{F,S},A^D)=0$, where $A^D=\operatorname{Hom}(A,\mu_\ell)$ with its contragredient cyclotomic action. At each $v\mid\ell$, fix $L_v\subseteq H^1(F_v,A)$ such that

$$
\prod_{v\mid\ell}\# L_v=\left(\prod_{v\mid\ell}\# H^0(F_v,A)\right)\,( \#A)^{r_2}.
$$

Let $\operatorname{Sel}(A)$ be the kernel of $H^1(G_{F,S},A)\to\prod_{v\mid\ell} H^1(F_v,A)/L_v$. Let $Q^1(A)$ be the cokernel of that same map, and $S^2(A)$ the kernel of $H^2(G_{F,S},A)\to\prod_{v\mid\ell}H^2(F_v,A)$.

**Proposition.** These groups are finite and $\#\operatorname{Sel}(A)=\#S^2(A)\,\#Q^1(A)$.

**Proof.** The global and local finiteness theorems and Euler characteristic formulas used here have the following cardinality form. Let $m=(\#A)^{r_2}$, and abbreviate the global groups by $H^i_{\mathrm g}$ and the local groups at $v$ by $H^i_v$. Then

$$
 \#H^1_{\mathrm g}=\#H^2_{\mathrm g}\,m,\qquad
 \#H^1_v=\#H^0_v\,\#H^2_v\,(\# A)^{[F_v:\mathbb Q_\ell]}.
$$

For the local formula see Theorem I.2.8, and for the global formula and the end of the duality sequence see Theorem I.5.1 and Remark I.5.2(c) in the cited reference. The first equality uses the zero global invariant group, of cardinality one. [J. S. Milne, *Arithmetic Duality Theorems*, second edition](https://www.jmilne.org/math/Books/ADTnot.pdf) The sum of the local degrees above $\ell$ is $[F:\mathbb Q]=2r_2$, so the product of the last local factors is $m^2$.

By the last part of Poitou–Tate duality, the cokernel of $H^2_{\mathrm g}\to\prod_{v\in S}H^2_v$ injects into $H^0(G_{F,S},A^D)^\vee$. The latter group is zero by hypothesis. Thus restriction is surjective, and projection onto the factors at $v\mid\ell$ is also surjective. Counting kernel and image yields

$$
 \#H^2_{\mathrm g}=\# S^2(A)\prod_{v\mid\ell}\# H^2_v.
$$

On the other hand, for the degree-one restriction modulo the local conditions, counting kernel and cokernel gives

$$
\#\operatorname{Sel}(A)
 =\frac{\#H^1_{\mathrm g}\,\prod_{v\mid\ell}\#L_v}{\prod_{v\mid\ell}\#H^1_v}
   \,\#Q^1(A).
$$

Insert the global count, the assumed local condition product, and the product of the local Euler equalities. The factors $\prod_v\#H^0_v$ and $m^2$ cancel, and the factor that remains is $\#H^2_{\mathrm g}/\prod_v\#H^2_v=\#S^2(A)$.

In the source the dual vanishing is obtained from a stronger hypothesis on additive maps. It says that for any abelian group $D$, a map $\varphi:A\to D$ satisfying $\varphi(ghx)=\varphi(hgx)$ for all $g,h$ and $x$ must vanish. A dual invariant $\varphi:A\to\mu_\ell$ is equivariant for the cyclotomic character. Since the cyclotomic actions of $g$ and $h$ commute, such a map satisfies that identity and vanishes. This is the step that makes the degree-two restriction surjective.

**Lean correspondence.** `card_sel_of_euler` performs the abstract cardinality calculation and `card_sel` supplies its global and local inputs. `global_euler_char` and `localEulerChar_above` give the finite-cardinality formulas. `loc2_surjective` uses the commutation condition with Poitou–Tate. Source-based reconstruction. [Cardinalities and cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SelmerObstructionLeResidualSelmerSimpleExtension.lean#L213) · [Arithmetic Selmer count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SelmerObstructionLeResidualSelmerSimpleExtension.lean#L260) · [Global Euler formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GlobalEulerChar.lean#L19) · [Local Euler formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NonemptySubquotEquiv.lean#L22) · [Surjectivity of degree-two localization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/H0TwDualEqZero.lean#L38).
