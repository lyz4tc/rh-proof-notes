# The three kinds of real places fit the same interlacing estimate

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $0<\varepsilon<1/52$ and $c_D,c_h\ge0$. For $x>1$ put
$$
 L=x^\varepsilon,\quad B=e^L,\quad A=xB,\quad
 B'=\frac{A}{\exp(x^{\varepsilon/3})},\quad D=\lceil x^{c_D}\rceil,\quad H=2\lceil x^{c_h}\rceil .
$$
Take integers $n,f,k,m\ge1$ with $m\ge2$, $k\ge m+3$, $n\le2x^{2+8\varepsilon}$, $k\ge x^{9/2+10\varepsilon}$, $n\le f\le x^3$, $m\le x$ and $k\le x^5$. At each real place assume the following profile.

- The common $v_i=(k-2-i)4D$ has length $k-1$. The length-$k$ list $u$ interlaces it, and $u_{k-1}>-b_0$. The positive-block data $b_j=b_0+jH$, $w_j=b_j+H/2$ have length $m$.
- At a top place there are integers $a,c$ with $A\le a\le A+A/(kx^{\alpha/2})$ for a fixed $\alpha\ge0$, and $B'\le c\le B'+2n x^{-\varepsilon/8}L\Lambda B'/k$. Here $\Lambda\ge0$ satisfies $\Lambda\le C_\varepsilon L(\log x)^2$ for a fixed constant. The endpoints are $u_0=a+(k-1)/2$, $u_{k-1}=-c-(k-1)/2$, and $b_0=c+\lfloor B'/x\rfloor$.
- Away from the top places the endpoints are $u_0=v_0+4kD+1/2$ and $u_{k-1}=-1/2$. At a thick place $\lceil B\rceil\le b_0<\lceil B\rceil+w_E$, where $w_E\le8f^2$ is the number of roots of unity of the host field. At a thin place $b_0=\lceil B'/(xn)\rceil$.

For sufficiently large $x$, every such profile satisfies [the place hypotheses](interlacing-bounds-the-vandermonde-ratio-at-one-place.md) with $\Delta=D$. The threshold depends on the fixed constants and is common to all places and words. These clauses are the part of `ChOK` that enters the local Vandermonde bound. [The archimedean weight profile](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/PairRowIffQdRows.lean#L95) · [Family data and common top endpoints](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/SetUnipotentTranslate.lean#L37) · [Top-place windows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/ThinScalesIffHostBound.lean#L143) · [Conversion to place data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L69)

Since $B'/B=x e^{-x^{\varepsilon/3}}\to0$, we have $3B'\le B$ eventually. Also
$$
 B'/(xn)=e^{L-x^{\varepsilon/3}}/n
$$
eventually exceeds each fixed power of $x$, using $n\le x^3$. In particular $B'/(xn)\ge x(4kD+H)$. The polynomial bound $mH+8f^2+2\le B$ holds eventually, since $H\le4x^{c_h}$ and $B$ exceeds every fixed power. The bound $w_E\le8f^2$ used here is the degree-$2f$ torsion bound. Indeed a root of unity of maximum order $w_E$ generates a field of degree $\varphi(w_E)\le2f$, while $\varphi(N)\ge\sqrt{N/2}$. The latter follows from the product of the prime-power formulae: for odd $p$, $p^{e-1}(p-1)\ge p^{e/2}$, and for $p=2$ the same bound holds with a factor $1/\sqrt 2$. [Exponential scales dominate the polynomial parameters](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L323) · [Torsion and size bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L25)

The relative excess of the bottom top-place endpoint above $B'$ is at most
$$
 \frac{2n x^{-\varepsilon/8}L\Lambda}{k}
 \le 4C_\varepsilon x^{-5/2-\varepsilon/8}(\log x)^2 .
$$
In particular $c\le2B'$ eventually. At a top place, $b_0$ is therefore between $B'/(xn)$ and $3B'$. At a thick place $b_0$ is at least $B$ and at most $B+8f^2+1$. At a thin place it lies between $B'/(xn)$ and $B'/(xn)+1$. Combining the three cases gives
$$
 x(4kD+H)\le b_0,\qquad b_0+mH\le2B .
$$
All weights satisfy $b_j\ge b_0>0$, $w_j-b_j=H/2\le b_j/x$, and $b_{j+1}-w_j=H/2\ge1$. The terminal $w_{m-1}$ is at most $b_0+mH$. Hence all the conditions on the negative block and target weights hold. [Bottom top-place window length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L379) · [Verify the negative-block conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DimVRowPos.lean#L248)

At the top places $u_0\le 3A/2+k/2\le2A$ eventually, using $k\le x^5\le A$ and $k\ge2$. Also $-u_{k-1}\le2B'+k/2\le A$, using $3B'\le B$, $k\le B$ eventually and $x\ge2$. Away from the top places $u_0-v_0=4kD+1/2\in[4kD,8kD]$, and $u_{k-1}=v_{k-2}-1/2$ since $v_{k-2}=0$. The $v_i$ themselves have the required bounds and step by their formula. This proves the other clauses of the place estimate. [Check the endpoint cases](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WindowLower.lean#L69)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
