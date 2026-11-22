# A quadratic Gauss sum normalizes the type prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $A=\mathcal O_{E,P}$ have residue field $\kappa$ of prime order $q\equiv 1\pmod4$. Fix a coefficient number field $K$ with an embedding into $\mathbb C$ and a nontrivial additive character $\psi_0:\kappa\to K^\times$. Let $\eta:\kappa\to\{0,1,-1\}$ be the quadratic character, extended by $\eta(0)=0$. The type-place constants are
$$
\psi(a)=\psi_0(\overline{qa})\quad(a\in q^{-1}A),\qquad
s=\sum_{x\in\kappa}\eta(x)\psi_0(x).
$$
The first formula is an additive character on $q^{-1}A$, is trivial on $A$, and satisfies $\psi(q^{-1})\ne1$. The second satisfies $s^2=q$ in $K$.

The project keeps $\psi_0$ as an input at each type place. The formula reduces the additive argument of the local unfolding at depth one, and the Gauss sum supplies its square-root normalization in the same coefficient field.

### Proof

The map $q^{-1}A\to\kappa$ given by $a\mapsto\overline{qa}$ is additive, and $qA$ maps to zero. This proves the character law and triviality on $A$. The element $1$ generates the additive group of the prime field. Thus $\psi_0(1)\ne1$, since $\psi_0(1)=1$ would force the character to be identically $1$. Taking $a=q^{-1}$ proves the required nontriviality. The Lean function takes value $1$ outside $q^{-1}A$.

To prove the Gauss sum identity we work in $K$. Since $\psi_0$ is nontrivial, choose $w$ with $\psi_0(w)\ne1$. Translation by $w$ leaves the index set fixed and multiplies $\sum_{v\in\kappa}\psi_0(v)$ by $\psi_0(w)$, so that sum is zero. Consequently
$$
\sum_{y\in\kappa^\times}\psi_0(y(t+1))=
\begin{cases}
q-1,&t=-1,\\
-1,&t\ne -1.
\end{cases}
$$
Expanding $s^2$, only $x,y\in\kappa^\times$ contribute. Substitute $x=ty$, with $t\in\kappa^\times$, and use $\eta(ty)\eta(y)=\eta(t)$. This gives
$$
s^2=\sum_{t\in\kappa^\times}\eta(t)
\sum_{y\in\kappa^\times}\psi_0(y(t+1))
=q\,\eta(-1)-\sum_{t\in\kappa^\times}\eta(t).
$$
Multiplication by a nonsquare permutes $\kappa^\times$ and reverses the sign of $\eta$, so the last sum is zero. In the cyclic group of order $q-1$, the element $-1$ has exponent $(q-1)/2$ relative to a generator. That exponent is even by $q\equiv1\pmod4$. Therefore $\eta(-1)=1$ and $s^2=q$.

### Lean correspondence

- [`ciPsi` and `ciSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainInst.lean#L316) define the constants. [`ciSq_sq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainInst.lean#L341) uses Mathlib’s quadratic Gauss sum identity. [`ciCst_ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainInst.lean#L376) combines the two assertions.
- [`localConstants_psi_depth_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwCst.lean#L67) identifies $\psi(a/q)$ with the residue-field phase. [`twCst_base`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/ChainTwCst.lean#L86) includes this identity in the sharp type-place unfolding input.
- [`qOf_mod_four`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/IsTwIffCanonEq.lean#L57) obtains the needed congruence for the two type primes from the tower condition. Each specified prime norm is congruent to $1$ modulo an integer divisible by $4$.

Status. Source-based reconstruction draft. The Gauss sum identity is proved above using finite-field character orthogonality, and the type-place nontriviality is an input. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
