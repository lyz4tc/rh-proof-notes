# Constructing the additive phase at a twist prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be a number field, $P$ a nonzero prime of $\mathcal O_E$ of prime norm $q$, and $A=\mathcal O_{E,P}$. Suppose $q\notin P^2$, so $q$ generates the maximal ideal of $A$. Let $K$ be the coefficient number field, $\sigma_0:K\hookrightarrow\mathbb C$ the embedding used to identify the character values, and $\xi_0\in A^\times$. Fix $D\ge1$ and suppose $K$ contains $\zeta$ with $\sigma_0(\zeta)=e^{2\pi i/q^D}$. For every $a\in q^{-D}A$, there exists $b\in\mathbb Z$ such that
$$
\xi_0a-\frac{b}{q^D}\in A,\qquad \psi(a)=\zeta^b.
$$
The formula defines an additive character of $q^{-D}A$ with kernel $A$. In particular $\psi(q^{-1})\ne1$. If $s\in K$ satisfies $s^2=q$, one may pair this character with $s$ as the local square-root normalization. For the project’s twist places, $D=2m$, and the additive, normalization and complex exponential identities are the assertions of `TwCstQ`.

### Proof

The canonical map $\mathbb Z/q^D\mathbb Z\to A/q^DA$ is a ring isomorphism. To see surjectivity, take $y\in A$. For $D=0$ there is only one residue. At depth $D+1$, the residue field of $A$ is the prime field $\mathbb F_q$, so choose an integer $b_0$ reducing to $y$ modulo $qA$. Then $(y-b_0)/q\in A$. Represent this quotient modulo $q^DA$ by an integer $b_1$. It follows that $y-(b_0+qb_1)\in q^{D+1}A$. For injectivity, if $u/q^D\in A$ for $u\in\mathbb Z$ and $D>0$, then $u$ reduces to zero modulo $qA$. The map $\mathbb Z\to\mathbb F_q$ has kernel $q\mathbb Z$, so $u=qu_1$. Apply induction to $u_1/q^{D-1}\in A$ to get $q^D\mid u$.

Apply this isomorphism to $y=q^D\xi_0a\in A$. The desired $b$ is any integer representing $y$ modulo $q^DA$. Its residue class modulo $q^D$ is unique, and $\zeta$ has exact order $q^D$ by the prescribed complex embedding. Hence $\zeta^b$ is independent of the representative. If $b,b'$ represent $q^D\xi_0a,q^D\xi_0a'$, their sum represents $q^D\xi_0(a+a')$. This proves $\psi(a+a')=\psi(a)\psi(a')$. The value is $1$ exactly when $q^D\mid b$, which is equivalent to $\xi_0a\in A$, and thus to $a\in A$ because $\xi_0$ is a unit. More explicitly, for an integer $u$ representing $\xi_0\bmod qA$ one has $\sigma_0(\psi(q^{-1}))=e^{2\pi i u/q}$ with $q\nmid u$. For every valid representative $b$, applying $\sigma_0$ gives precisely $\sigma_0(\psi(a))=e^{2\pi i b/q^D}$. The Lean function extends the phase by the value $1$ outside $q^{-D}A$, while the character law applies on $q^{-D}A$.

### How the coefficient-field hypotheses enter

For the fixed coefficient field $K$ the construction takes the required roots and the unit $\xi_0$ as input. In the passage from an already valid project datum with twist depth $D'\ge 2m$ to the canonical datum, those roots can be recovered from the old constants. The old square-root datum already supplies $s^2=q$. For the root of unity, insert
$$
a=\frac{\xi_0^{-1}}{q^{2m}},\qquad b=q^{D'-2m}
$$
into the old exponential identity. Indeed $q^{D'}a\in A$ and $\xi_0a-b/q^{D'}=0$. This gives $\sigma_0(\psi_{\rm old}(a))=e^{2\pi i/q^{2m}}$. The change of datum therefore retains the requisite roots in the same coefficient field.

The character is used in the [support and period calculation for bounded twist charts](the-twist-chart-bounds-give-the-entry-support-and-period.md) and the [large-depth unfolding](why-the-twist-unfolding-stabilizes-as-the-box-grows.md). Its exponential identity also records that the local phase agrees with the prescribed scale $\xi_0$ after embedding into $\mathbb C$.

### Lean correspondence

- [`twZeta`, `twPsiQ` and `twSqrt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L194) choose the root, the phase and the square root. [`twCst`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTw.lean#L217) sets $D=2m$ at twist places and $D=1$ at type places, with box depths $A_{\rm box}=B_{\rm box}=m+1$ and period exponent $M=m$.
- [`twDvd_of_intAt` and `twRes_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwPsi.lean#L15) give uniqueness and existence of the integer residue. [`twPsiQ_eq` and `twPsiQ_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwPsi.lean#L94) justify the representative formula. [`twCstQ_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwPsi.lean#L128) establishes the local axioms for the input data.
- [`TwCstQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwOk.lean#L101) lists the required twist local identities. [`sqrt_of_ok` and `root_of_ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/IsTwIffCanonEq.lean#L84) recover the roots from the old datum.

Status. Source-based reconstruction draft. The local argument assumes a prime norm, $q$ generating the maximal ideal, an integral unit $\xi_0$, and the indicated roots in $K$. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
