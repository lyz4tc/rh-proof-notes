# The isotropic vector quotient gives a weighted ellipsoid

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the archimedean group $G$ and majorant $M=(P_w)_w$ of [the shortest-vector proof](a-shortest-vector-has-bounded-index-in-its-saturated-line.md), with $n=\dim_E W$ and $f=[F:\mathbb Q]$. Take $x\in\Lambda\setminus\{0\}$ with $h(x,x)=0$, so $n\ge2$. Write $H=\{g\in G:g_w x_w=x_w\text{ for all }w\}$ and $\Gamma_x=H\cap\Gamma$, where $\Gamma$ is the image in $G$ of the rational lattice stabilizer. For every Haar measure $\mu$ on $G$, there is a $0<C_x<\infty$ such that for all $t>0$, in any measurable fundamental domain $D_x$ for $\Gamma_x$ in $G$,
$$
 \mu\{g\in D_x:\ell_g(x)<t\}=C_x\,t^{2f(n-1)}.
$$
The proof below uses two inputs given by the source, the archimedean parabolic coordinates and finite covolume of $\Gamma_x$ in $H$. The full arithmetic argument applies them to lattices with a fixed bound on their dual index. [Vector unfolding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/Statements.lean#L74) · [Deduction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnfoldingIntegral.lean#L44)

## The two inputs and the quotient integral

Put $K=\{k\in G:k_w^*P_wk_w=P_w\text{ for all }w\}$, the compact stabilizer of the majorant. For a fixed $\mu$, the Haar-coordinate theorem gives a Haar measure $\nu$ on $H$, probability Haar measure $dk$ on $K$ and a measurable map $\tau:\mathbb C^f\to G$ with $\tau(b)^{-1}x=(b_wx_w)_w$ when each $b_w\ne0$. For every nonnegative measurable $A$,
$$
 \int_G A(g)\,d\mu(g)=\int_{\mathbb C^f}\int_K\int_H
   A(h\tau(b)k)\,d\nu(h)\,dk\,\prod_w |b_w|^{2(n-2)}\,db .
\tag{1}
$$
Here $db$ is the real Lebesgue measure on the complex coordinates in the theorem. The exceptional coordinate hyperplanes have measure zero. The second input gives a measurable fundamental domain $D_H\subset H$ for $\Gamma_x$ with $0<\nu(D_H)<\infty$. [Exact Haar-coordinate input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StatementsHaarParabolicCoordinates.lean#L16) · [Stabilizer-volume input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StatementsStabilizerCovolume.lean#L16)

Apply (1) to $A(g)=1_{D_x}(g)1_{\ell_g(x)<t}$. The length condition is invariant under left translation by $H$ because $H$ fixes $x$. For each $b,k$, split the $H$-integral into translates of $D_H$. The sum of $1_{D_x}(\gamma h\tau(b)k)$ over $\gamma\in\Gamma_x$ equals $1$ for almost every $h,b,k$ in the product coordinates, by the fundamental-domain property and (1) applied to the exceptional null set in $G$. Thus the integral over the stabilizer factor contributes $\nu(D_H)$. Since $k$ is an isometry for $M$, the condition becomes $\sum_w q_w|b_w|^2<t^2$ with $q_w=x_w^*P_wx_w>0$. Integration in $k$ contributes $1$. We obtain exactly
$$
 \nu(D_H)\int_{\sum_w q_w|b_w|^2<t^2}\prod_w |b_w|^{2(n-2)}\,db .
\tag{2}
$$
All exchanges use nonnegative measurable functions and countable translates. This argument also gives the same measure for any choice of fundamental domain. [Subgroup unfolding](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PUnfoldingTorus.lean#L84) · [Unfolding with a measurable section](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StatementsUnfoldAlongSubgroup.lean#L12)

## Dilation of the ellipsoid

Substitute $b_w=t u_w$. The Jacobian is $t^{2f}$, and the weight contributes $t^{2f(n-2)}$. The integral over $\sum q_w|u_w|^2<1$ is finite since the set is bounded and the weight is bounded there. It is positive since it contains an open set where every $u_w\ne0$ and the weight is positive. Multiplying this integral by $\nu(D_H)$ gives $C_x$. The power $2f(n-1)$ includes both the $2f$ real scalar coordinates and the unipotent weight. [Homogeneity and finiteness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PTorusIntegralHomogeneous.lean#L80)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
