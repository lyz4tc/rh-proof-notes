# The row dimension keeps the prime window center above the target scale

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $0<\varepsilon<1/52$, $x>1$, $L=x^\varepsilon$, and use the numerical hypotheses and notation of [the dimension lower bound](mass-factorials-cancel-the-weyl-denominators-in-the-window-lower-bound.md) with $C_0=5$. Fix the constant $C$ in its error term and a real constant $C_\Gamma\ge0$. Assume
$$
 g_i\ge (ke^L)^8\quad(i=1,2),\qquad
 2|C|\le m,\quad m^2\le k,\quad 2C_\Gamma m^4\le k.
$$
For $\Gamma=\exp(C_\Gamma m^5 f L)$ define the adjusted window center for the word represented by $d^*$ as
$$
 X=(D^*/d^*)^{1/(fk)}\,\Gamma^{-2/(fk)}.
$$
Then $X>0$ and $\log X\ge mL$. On the family route the same threshold works for all words. [Uniform rank bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L144) · [Adjusted window lower bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L177)

Each $w_{\rho,j}\ge1$ by the place hypotheses and $v_E\ge\pi$, so the weight logarithms in (2) of the dimension lower bound have a nonnegative sum. Each generator prime contributes $\log g_i\ge8L$, and the error $C(L+m^2L/k)$ is at most $2|C|L\le mL$. Consequently $\log(D^*/d^*)/(fk)\ge15mL$. Subtracting $2\log\Gamma/(fk)=(2C_\Gamma m^4/k)mL\le mL$ leaves at least $14mL$, in particular at least $mL$. The positive lower dimension bound already proves $D^*>0$, and the exact column factor proves $d^*>0$, so these are ordinary positive logarithms.

## Inputs supplied by the family

On the source route the scale satisfies $m\ge x^{1/2-\varepsilon/16}$, $m\le x$ eventually, and $x^{9/2+10\varepsilon}\le k\le x^5$. Hence the three required numerical inequalities hold for large $x$, since $m$ grows and $k$ grows faster than $x^{17/4}$ and $x^2$. The defining generator bound is already among the host validity conditions. The [three place profiles](the-three-kinds-of-real-places-fit-the-same-interlacing-estimate.md) give the place conditions at that threshold. The host factor satisfies $v_E\ge\pi$ and eventually $\log v_E\le L$. The same row weight is used for every word, so the lower bound for $D^*$ and the mass ratio apply simultaneously. Only the interlacing column list and the exact $d^*$ vary with the word. The [finite level computation](counting-the-row-level-matrices-gives-the-exact-generator-index-ratio.md) gives the two index factors of (1) in the dimension comparison. The Lean theorem takes the maximum of the thresholds for the place data, the size bounds, the rank bounds and the host bounds. The [word-prime estimate](the-logarithmic-window-bounds-give-the-word-prime-size.md) is a related family statement after a prime has been placed in its recorded window. [Produce the place profiles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L69) · [Use the mass and index ratios at a common threshold](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L177) · [Combine the two local index bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L124)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
