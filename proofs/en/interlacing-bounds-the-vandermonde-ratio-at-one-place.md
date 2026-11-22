# Interlacing bounds the Vandermonde ratio at one place

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $\varepsilon>0$, $x\ge1$, integers $k\ge2,m\ge1$ and a real number $\Delta\ge1$. Write $L=x^\varepsilon$, $B=e^L$, $A=xB$ and $P=4k\Delta$. Let $u=(u_0,\ldots,u_{k-1})$, $v=(v_0,\ldots,v_{k-2})$, $b=(b_0,\ldots,b_{m-1})$ and $w=(w_0,\ldots,w_{m-1})$ be real lists. Assume the following conditions, called `PlaceData`.

- $0\le v_i\le P$, successive differences of $v$ are $4\Delta$, and $u_i>v_i>u_{i+1}$ for every $0\le i\le k-2$. Also $u_{k-1}>-b_0$.
- Either $u_0\le2A$ and $u_{k-1}\ge-A$, or $P\le u_0-v_0\le2P$ and $u_{k-1}=v_{k-2}-1/2$.
- For every $j$, $b_j<w_j$ and $w_j-b_j\le b_j/x$. For $j+1<m$, $w_j<b_{j+1}$ and $b_{j+1}-b_j\ge1$. Finally $P\le b_0/x$ and $w_{m-1}\le2B$.

Write $R=(v_0,\ldots,v_{k-2},-b_0,\ldots,-b_{m-1})$, and let $V(s)=\prod_{i<j}(s_i-s_j)$ for a decreasing list $s$. Then $V(R),V(u)>0$, and
$$
 \log V(R)-\log V(u)\ge
 (k-1)\sum_j\log b_j-2k\log(8A)-2k(1+\log k).
\tag{1}
$$
[Place data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogRatioLowerBound.lean#L15) · [One-place bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/VandPlace.lean#L7) · [Lean proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/VandNSuccRight.lean#L205)

First, $b_0>0$ and the $b_j$ increase by at least one. All the lists used in $V$ are strictly decreasing, with the negative block of $R$ below $v$. The factors between $v_i$ and $-b_j$ are at least $b_j$, and differences within the negative block are at least one. Hence
$$
 V(R)\ge V(v)\prod_j b_j^{k-1}.
\tag{2}
$$
The diameter of $u$ is at most $8A$. In the first case this follows from $u_0-u_{k-1}\le3A$. In the second, the diameter is at most $3P+1/2$. Since $P\le b_0/x\le b_{m-1}<w_{m-1}\le2B$, it is at most $6B+1/2\le8A$. We used $A\ge B\ge1$.

Among the factors of $V(u)$, at most $2k-3$ involve either endpoint of the list. Bound their product by $(8A)^{2k-3}$. Every remaining pair $1\le i<j\le k-2$ satisfies $u_i-u_j\le v_{i-1}-v_j$ by the two interlacing inequalities. These are distinct nonadjacent factors in $V(v)$, and all adjacent factors there equal $4\Delta\ge1$. Thus the product of the remaining factors of $V(u)$ is at most $V(v)$. The conclusion includes $k=2$ and $k=3$, when the remaining pair set is empty. Combining this estimate with (2) gives (1), even with error $(2k-3)\log(8A)$ alone. The displayed error is the one used by the next Lean theorem. [Attach the negative block](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/VandNSuccRight.lean#L66) · [Compare the interlacing determinants](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/VandNSuccRight.lean#L112)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
