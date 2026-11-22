# Low coefficients of a truncated Wach–Frobenius image

*Source-based reconstruction draft; not a Lean replay.*

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Proposition (local Frobenius expansion congruence)

**Local data.** Fix the source's period and Wach datum $(PD,W)$ at the prime $\ell=\mathrm{PD}.p$, with coefficient field $L$, coefficient ring $O\hookrightarrow L$, normalized additive valuation $v$ with $v(\ell)=1$, and nonzero letter length $n$. In the concrete application $K/\mathbb Q_\ell$ and $L/\mathbb Q_\ell$ are finite, $O=O_L$, $K_0$ is the unramified part of $K$, and $n=[K_0:\mathbb Q_\ell]$. Use `CaseA`: $K_0\to K$ is bijective, $W.s=1$, and $\ell\ne2$; assume $\ell\ge11$. We use the `LocWach` structure, in particular its scalar and lattice expansion maps, semilinear Frobenius, stability of its lattice under $\Gamma$, and the fact that a power of $W.Q$ carries a Frobenius image back to that lattice.

**Comparison and regularity hypotheses.** Assume the source's étale and comparison data `EtTie` and `CmpTie`, with the period-ring inclusion $B\hookrightarrow B_{\mathrm{dR}}$ and induced $L$-linear tensor injection $\iota_V$. Assume `P4W` and `P9W` for this datum (their exact uses are below), and assume the distinguished generator $\gamma=W.\mathrm{gam}$ has character value $\chi_\Gamma(\gamma)\in O^\times$ of infinite multiplicative order. The abstract Lean argument `tHor_of` takes this last condition under `CaseA`, and explicitly takes injectivity $O\hookrightarrow L$.

**Representation and truncation hypotheses.** Let $T$ be a lattice representation with crystalline rational representation $V=T.V$. Set $A=\mathrm{LetA}(O,n)$, $D(T)=W.DD(T)$, $N(T)=W.N(T)$, $\pi_0=W.\pi_0$, $q=\mathrm{qp}(W)=\pi_0+\ell$. The symbol $\pi_0$ is not the basic scalar variable `letπ`, and $q$ is not by definition $W.Q$. Choose $i\in\mathbb Z/n\mathbb Z$, write $\Phi=\varphi_D^j$, $\psi=\varphi_A^j$, and take $j,M,X,\sigma\in\mathbb N$ satisfying `TCase`:
$$
\begin{aligned}
&j=1,\ M\ge1,\quad \sigma=\left\lceil (M+X)/(\ell-1)+1\right\rceil;\quad\text{or}\\
&j=2,\ M=1,\quad \sigma=\left\lceil X/(\ell-1)^2+1\right\rceil .
\end{aligned}
$$
Take $w\in N(T)$ satisfying `InI`: $e_iw=w$ for the letter idempotent $e_i$, $w$ is fixed by the finite tame group $W.\mathrm{DelF}$, its poles are bounded by a finite product of the prescribed Frobenius factors (`PolesFin`), and $(\gamma-1)w\in\pi_0 N(T)^\Delta$, where $\Delta=W.\mathrm{DelF}$ and the notation means the image of the indicated lattice under multiplication. Take $z\in D(T)$ with a witness of `IsTrunc` at $(i,j,M,X,\sigma,w)$. Explicitly, the witness consists of $c_y\in N(T)^\Delta$ supported at $i$, $c_0=0$, and $r_y,s_y\in A$, for all $y\in\mathbb N$. Set $e_y=\lceil y\ell/(\ell-1)\rceil$. Require:
1. For every $h_0\in\mathbb N$, there is $j_0\in\mathbb N$ such that, with $J=j_0+e_{h_0}$, the element
   $$
   h=\ell^Jw-\sum_{y<h_0}\ell^{J-e_y}\pi_0^y c_y
   $$
   satisfies $(\gamma-1)h\in\pi_0^{h_0}N(T)^\Delta$. This is `IsSer` written with the denominators cleared inside $\gamma-1$; $\gamma$ fixes the integer scalars and $J\ge e_y$ in the sum.
2. $r_y$ is a polynomial in $\pi_0$ with coefficients from $O$ of degree less than $M+X$, and
   $$
   \psi(\pi_0)^y-r_y\in\pi_0^M q^X A,\qquad
   \ell^{e_y}s_y=\ell^\sigma r_y .
   $$
3. With $H=\max(M,X)+1$, $z=\ell^\sigma\Phi w-\sum_{y<H}s_y\Phi c_y$.

**Output hypotheses and conclusion.** Choose $k\in\mathbb N,\ a\in A$ with $u=(q^ka)z\in N(T)$. Either choose a primitive $\ell$-th root $\zeta\in L$ and put $R=k+X$, or choose $\zeta=1$ and put $R=(\ell-1)M$. Write $S$ for the power-series variable (distinct from $X$), $\lambda=\operatorname{lev}_{i+j,\zeta}:A\to L[[S]]$, and $v_w=\operatorname{cmp}(w)\in V\otimes_{\mathbb Q_\ell}B$. The lattice expansion $\operatorname{levN}_{i+j,\zeta}(u)$ has no negative coefficients and, for $0\le r<R$,
$$
 \operatorname{levN}_{i+j,\zeta}(u)_r =
 [S^r]\lambda(q^ka)\,\ell^\sigma\,
 \iota_V(\varphi_B^j v_w).
 \tag{1}
$$
Here $\varphi_B$ denotes the $L$-linear tensor Frobenius (identity on $V$, Frobenius on the crystalline factor). The conclusion is about $u$, not a claim that $z\in N(T)$.

**How the concrete wrapper supplies the hypotheses.** `frobenius_power_congruence_local` assumes $D:\mathrm{D7}$, Wach system `HW`, étale-functor package `F`, comparison package `Cm` and `RamifiedCoefficientChains.adm1` for these packages. At every good level-one pair $K,L$ (`Good K 1 L`) with $n\ne0$, the wrapper takes the comparison tie from `Cm`, the injection $O_L\hookrightarrow L$, `P4W` and `P9W` from `adm1`, and the character assertion from `RToolNum_holds` followed by `χ_pow_ne_one`. It then gives `THor`, whose local premises are as above. The wrapper needs this `adm1`, not the whole `admitted` checklist. [Local and uniform statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/CrystallineLiftingInputs.lean#L117-L191) · [Case A](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LiftingTheory.lean#L67-L74) · [Comparison and local theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L480-L520) · [Uniform wrapper](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L713-L722) · [Global checklist projection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/UsedLocalConclusion.lean#L15-L32).

## 1. Which comparisons and local inputs are used?

For a letter $b$ and root $\xi$, write $\lambda_{b,\xi}=\operatorname{lev}_{b,\xi}$ for the scalar map, $E_{b,\xi}=\operatorname{levB}_{b,\xi}$ for the crystalline coefficient map defined on $N(T)$, and $\operatorname{levN}_{b,\xi}$ for the de Rham coefficients on the same lattice. The étale tie lives at a different layer: it maps $A$ into the integral coefficient ring, extends the scalar map to the étale coefficient ring, and embeds $D(T)$ in the étale tensor, respecting multiplication, Frobenius and the Galois action. The coefficient argument uses the stipulated `CmpTie` compatibilities, **not** an identification of the three coefficient rings or an extension of $E_{b,\xi}$ to all of $D(T)$.

The maps $E_{b,\xi}$ are additive, their sequences are bounded below, and $\operatorname{levN}_{b,\xi}(x)_r=\iota_V(E_{b,\xi}(x)_r)$. Tensoring the injective period-ring map over the base field preserves injectivity. Thus the scalar convolution rule for $\operatorname{levN}$ implies
$$
 E_{b,\xi}(a x)=\lambda_{b,\xi}(a)E_{b,\xi}(x).
$$
The right side is multiplication of a power series and a bounded-below sequence; each degree uses only a finite sum. The constant term at $(b,1)$ is $\operatorname{cmp}(e_bx)$; in particular it is $v_w$ at $(i,1)$ for $x=w$. Finally $\lambda_{b,\xi}(\varphi_A a)=\lambda_{b-1,\xi^\ell}(a)(\ell S)$; its vector counterpart compares $E_{b,\xi}(W.Q^m\varphi_D x)$ with $E_{b-1,\xi^\ell}(x)$ by tensor Frobenius, degree rescaling and multiplication by $\lambda_{b,\xi}(W.Q^m)$, when the displayed source and target vectors belong to the lattices. The $\Gamma$ rule at root $1$ keeps the root $1$ and multiplies degree $r$ by $\chi^r$, where $\chi$ is the image of $\chi_\Gamma(\gamma)$ in $L$. These rules are used separately.

In this proof **`P4W`** applies to a crystalline $T$ and to the trivial root: $W.X=\mathrm{let}\pi$ at twist level one, and $\lambda_{b,1}(W.X)$ has zero constant term. The first clause of `p4` then kills **all negative coefficients** of $\operatorname{levN}_{b,1}(x)$ for any $x\in N(T)$. Injectivity of $\iota_V$ transfers this to $E_{b,1}$. The filtration and span parts of `p4` are not used in this argument. Do not use this step to assert target nonnegativity at a primitive root; that is proved after transport and cancellation.

**`P9W`** gives, in the `CaseA` specialization $[K:K_0]=1$, `RingA` and a tame-invariant module clause. Only `RingA` is taken here. In particular $\pi_0$ is a unit times $(\mathrm{let}\pi)^{\ell-1}$, and $W.Q=W.q$ at level one is a unit times the evaluation of the polynomial $Z+\ell$ at $\pi_0$, namely $q$. Thus the expansion of $\pi_0$ at root $1$ is divisible by $S^{\ell-1}$, and $q$ has constant coefficient $\ell$ there. At a primitive $\ell$-th root the scalar evaluation of $W.q$ has a simple zero; `expRing_of` divides by the image of the unit to obtain $\lambda_{b,\zeta}(q)=S\,U(S)$ with $U(S)$ a unit. In particular $W.Q$ has nonzero scalar expansion at either root. The needed ring orders are not consequences of `P4W`.

[Étale and comparison ties](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DataNLoc.lean#L1050-L1068) · [Coefficient comparison, Frobenius and $\Gamma$](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DataNLoc.lean#L1163-L1197) · [Wach evaluation and scalar law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DataNLoc.lean#L278-L300) · [Injectivity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientImageDivisibility/RkMulVBFilCris.lean#L91-L101) · [`p4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L159-L175) · [`p9` and ring relations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L217-L242) · [The simple zero](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientImageDivisibility/ExistsXPowMul.lean#L96-L125).

## 2. The horizontal block and the exact role of infinite order

Take $h_0=H$ in the witness, and let $h,J$ be as in the proposition. Wach-lattice stability gives $h\in N(T)$, and the witness gives $(\gamma-1)h=\pi_0^H\nu$ for $\nu\in N(T)^\Delta$. For any $0<r<(\ell-1)H$, apply $E_{i,1}$ to this identity. By `P4W`, $E_{i,1}(\nu)$ has no negative degrees; multiplying by $\lambda_{i,1}(\pi_0)^H$, divisible by $S^{(\ell-1)H}$, makes the coefficient at $r$ zero. The $\Gamma$ rule therefore gives
$$
 (\chi^r-1)\,E_{i,1}(h)_r = 0.
$$
This is where infinite order is used: $\chi_\Gamma(\gamma)^r\ne1$ in $O^\times$, hence $\chi^r-1\ne0$ in $L$ by injectivity. Nonzero scalars act injectively on the $L$-vector space, so $E_{i,1}(h)_r=0$. The argument does not kill the constant term, for which $\chi^0-1=0$.

In the concrete wrapper the non-torsion assertion is proved, not inferred just because $\gamma$ is called a generator. For $\chi\in L^\times$ as above put
$$
 c_R(m)=\frac{\chi^{-m}-1}{-\ell}.
$$
`RToolNum_holds` transports a valuation identity from $\mathbb Z_\ell$: the character value comes from a cyclotomic value in $1+\ell\mathbb Z_\ell$ with valuation $1$ on its difference from $1$, and the odd-prime power valuation formula gives $v(c_R(m)-c_R(m'))=v_\ell(m-m')$ for $m\ne m'$, with $c_R(0)=0$. In particular, if $\chi^r=1$ for a positive integer $r$, then $c_R(-r)=c_R(0)=0$ and the valuation would be $+\infty$ instead of the finite $v_\ell(r)$. This is the argument of `χ_pow_ne_one`.

For degree zero, every correction with $y>0$ has a factor divisible by $S$ multiplying a nonnegative series, and $c_0=0$. Hence
$$
 E_{i,1}(h)=\ell^J v_w+O(S^{(\ell-1)H}).
 \tag{2}
$$
Here $O(S^m)$ means no coefficients of degree below $m$, not a bound in the $\ell$-adic norm. [Character valuation input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LevelClauseOfOpenTool.lean#L367-L369) · [Concrete construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LevelClauseOfOpenTool.lean#L388-L456) · [Non-torsion proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LocalClauseOfFrobeniusHyps.lean#L645-L653) · [Positive-degree vanishing and constant term](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L370-L429).

## 3. Transport through Frobenius without dividing in a lattice

For a bounded-below sequence $d$, define $(\mathcal Fd)_r=\ell^r\varphi_B(d_r)$. It never shifts degrees, and $\mathcal F(gd)=g(\ell S)\mathcal F(d)$ for $g\in L[[S]]$: in the convolution at degree $r$, the scalar term at degree $s$ and the vector term at $r-s$ acquire factors $\ell^s$ and $\ell^{r-s}$. Starting with a multiplier $b$ making an intermediate vector $b x$ integral, choose $m$ supplied by `N_φ` and take the next multiplier $b'=W.Q^m\varphi_A(b)$. Semilinearity gives the requisite next lattice vector. Its scalar expansion is nonzero if the preceding one is: multiplication by a power of the nonzero expansion of $W.Q$ and rescaling by the nonzero $\ell$ preserve this. Apply the comparison rule in Section 1, taking root $1$ until the final step. The last root may be $\zeta$ because $\zeta^\ell=1$.

For each $x=h,c_0,\ldots,c_{H-1}$ this constructs a multiplier $b_x$ such that $b_x\Phi x\in N(T)$ and $E_{i+j,\zeta}(b_x\Phi x)=\lambda(b_x)\mathcal F^j E_{i,1}(x)$, with $\lambda(b_x)\ne0$. Multiply the multipliers together to get $b_*$, and use scalar compatibility to obtain the same identity with $b_*$ for every such $x$. The series $\lambda(b_*)$ is nonzero; there is no claim that $b_*$ is invertible in $A$, or even that this series has nonzero constant term.

The exact subtraction obtained from the definitions of $h$ and $z$ is
$$
 \ell^J z=\ell^\sigma\Phi h+
 \sum_{y<H}\ell^{\sigma+J-e_y}\big(\psi(\pi_0)^y-r_y\big)\Phi c_y.
$$
Indeed $\ell^Js_y=\ell^{\sigma+J-e_y}r_y$ follows directly from the witness and $J\ge e_y$, without dividing in $A$. Apply $E_{i+j,\zeta}$ after multiplying the identity by $q^ka b_*$. All terms are then lattice elements. Cancel $\lambda(b_*)$ in the space of bounded-below sequences: if a difference sequence were nonzero, its first nonzero term multiplied by the leading nonzero coefficient of the scalar series would remain nonzero. This yields
$$
\begin{aligned}
 \ell^J E_{i+j,\zeta}(u)
 =\lambda(q^ka)\Big[&
 \ell^\sigma \mathcal F^j E_{i,1}(h)\\
 &+\sum_{y<H}\lambda\!\left(\ell^{\sigma+J-e_y}
      (\psi(\pi_0)^y-r_y)\right)\mathcal F^j E_{i,1}(c_y)\Big].
 \tag{3}
\end{aligned}
$$
Every term on the right has nonnegative degrees, so cancellation of $\ell^J$ in the $L$-vector space gives the same for the left expansion. [Frobenius rescaling](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L28-L55) · [One step and iteration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L148-L259) · [Exact subtraction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L321-L361) · [Common multiplier and cancellation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L527-L612).

## 4. Three different orders

- $H=\max(M,X)+1$ is the number of correction indices; $(\ell-1)H$ is the source expansion order in (2). Neither is the output cutoff.
- $R_0$ is the guaranteed order of the difference between the bracket in (3) and the degree-zero sequence with value $\ell^{\sigma+J}\varphi_B^j(v_w)$. The error factors lie in the image of $\pi_0^M q^X A$. At a primitive root, $q$ contributes $S^X$, so take $R_0=X$. At $1$, $\pi_0^M$ contributes at least $S^{(\ell-1)M}$, so take $R_0=(\ell-1)M$. In both cases $R_0\le(\ell-1)H$; thus the Frobenius-transported error of (2) also starts no lower than $R_0$.
- $R$ is the order **after multiplying by $\lambda(q^ka)$**. At the primitive root its factor $q^k$ supplies another $S^k$, so $R=k+X$, even when $R>(\ell-1)H$. At $1$, $q$ has nonzero constant coefficient $\ell$, so no extra order is asserted and $R=(\ell-1)M$. The order of $a$ may improve the bound but is not used. These are guaranteed lower orders, not a claim that the first omitted coefficient is nonzero.

For every $0\le r<R$, replacing the bracket in (3) by its indicated degree-zero sequence leaves the coefficient unchanged. Divide by the scalar $\ell^J$ in the coefficient field and apply $\iota_V$ to obtain (1). [Remainder and cutoff argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowerCongruenceOfAdmitted.lean#L613-L705).

## Scope and remaining dependencies

This is the conditional congruence `THor`. It does not construct the `IsSer` or `IsTrunc` witness, prove the two stated costs are attainable, construct the Wach and comparison data, or prove `P4W`/`P9W`. It does not turn the vanishing of negative coefficients at a primitive root into a lattice-membership test: `ExpCrit` needs separate hypotheses and the `expCrit_D'` route. Likewise Theorem B's arc criterion `LevC.secCrit_all` and the full Theorem C lifting bound are separate. [Truncation interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/CrystallineLiftingInputs.lean#L130-L179) · [Assembly and neighboring membership test](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/UniformizerClauseOfAdmitted.lean#L69-L96) · [Arc result](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/SecCritAll.lean#L168-L181).

For orientation, Jimmie Adriazola's [21 November 2026 revision, §§4.6 and 11](https://github.com/jimjamzola/RH-Alpoge-Reconstruction/blob/932c30f8c4d7eb5f36fd2f87438cd984bf7e553c/RH_Route_Notes.pdf) places this in PC-3, the shared Wach-module layer for Theorems B and C. The proof here follows the pinned Lean bodies, not that overview. No claim about PC-1, ClosedPhi's Breuil–Kisin frame limit, or external verification is made.
