# Spacing the negative weights provides the discrete-series gap

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $r=k-1+m$, with $m\ge2$ even, $f\ge1$ and $k\ge m+3$. Let the row Harish–Chandra parameter be $\lambda=(v_0,\ldots,v_{k-2},-b_0,\ldots,-b_{m-1})$, where $v_0>\cdots>v_{k-2}\ge0$ and $0<b_0<\cdots<b_{m-1}$. Put the positive sign on the whole $v$-block and on $-b_j$ for even $j$. Put the negative sign on $-b_j$ for odd $j$. There are $p=k-1+m/2$ positive signs and $q=m/2$ negative signs. For $x>1$, $\varepsilon>0$, $C_0>0$, write $L=x^\varepsilon$ and suppose
$$
 b_{j+1}-b_j\ge r^{19} f^5 L/C_0\qquad (0\le j<m-1).
$$
For any fixed $C_3\ge0$, whenever $L\ge9 C_3 C_0$, every pair of opposite signs satisfies
$$
 |\lambda_i-\lambda_j|\ge 9 C_3 r\min(p,q)(pq)^3\log r .
\tag{1}
$$
The right side is the source's gap at the error parameter $1/3$. [Negative-block spacing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLattice.lean#L494) · [Uniform gap bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean#L17)

If both weights are in the negative block, the difference of their $b$'s is at least one adjacent spacing. If the positive-sign weight is in the $v$-block, the other weight is $-b_j$ with $j\ge1$. Then $v_i+b_j\ge b_1\ge b_1-b_0$. So every required separation is at least $r^{19} f^5 L/C_0$. Using $\min(p,q)\le r$, $pq\le r^2$, and $\log r\le r$, the right side of (1) is at most $9C_3r^9$. This is bounded by the spacing hypothesis since $r,f\ge1$ and $L\ge9C_3C_0$. For fixed $C_3,C_0,\varepsilon$, choosing an $x$-threshold to make this last inequality true works at all places simultaneously. In Lean the positive sign of $C_0$ follows from $k>1$ and $k\le x^{C_0}$ with $x>1$. [Exponent and gap estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ThickPlacesCorollaryOfAnyTranslate.lean#L476) · [Check all opposite-sign pairs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ThickPlacesCorollaryOfAnyTranslate.lean#L511)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
