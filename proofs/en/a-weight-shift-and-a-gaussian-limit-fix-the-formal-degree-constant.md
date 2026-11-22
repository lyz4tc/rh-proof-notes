# A weight shift and a Gaussian limit fix the formal-degree constant

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $p,q\ge1$, $N=p+q$, signs with these counts, and an integral Harish–Chandra parameter $\lambda$ as in [the degree comparison](the-compact-and-noncompact-roots-bound-the-row-formal-degree.md). Let $h$ bound all opposite-sign gaps from below, and suppose
$$
 h>1+\max\bigl(Npq+1,\ 16N\min(p,q)+8\sqrt{2\min(p,q)}\bigr).
\tag{1}
$$
With polar measure $c_{pq}\,dk\,J(z)\,dz$ as in [the Schur inequalities](schur-orthogonality-sandwiches-the-formal-degree-between-two-integrals.md), the project proves that the discrete-series degree at $\lambda$ is $V(\lambda)/F(N)$. Three representation inputs below specify where the large-gap proof uses existence, coefficients and translation. The limit argument after those inputs is given in full. [Assemble the large-gap degree theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdCons.lean#L17) · [Analytic limit and constant](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/ThmFD.lean#L21)

- For each regular integral parameter $\mu$ with these signs and opposite-sign gaps at least $h$, there is a discrete series. Its degree depends only on $\mu$ in the fixed measure. Its lowest compact type of dimension $d_K(\mu)$ has a model satisfying (1) of [the Schur inequalities](schur-orthogonality-sandwiches-the-formal-degree-between-two-integrals.md). The [right regular construction and uniqueness argument](the-right-regular-model-realizes-the-polar-coefficient-on-its-lowest-type.md) give this input at all the shifted parameters below. [Uniqueness of the degree](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdConsA.lean#L95) · [Existence of the degree model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdConsA.lean#L120)
- If $\mu$ and $\mu+e_i$ are both regular integral parameters with opposite-sign gaps at least $h$, then the positive degrees satisfy
$$
 d(\mu+e_i)=d(\mu)\frac{V(\mu+e_i)}{V(\mu)}.
\tag{2}
$$
The [two-direction tensor comparison](forward-and-dual-tensor-shifts-force-the-exact-degree-ratio.md) proves this shift ratio by finding the shifted series in the defining and dual tensors and comparing their projection traces. It is used to keep one ratio constant as the weights grow. [Degree translation by one coordinate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/TensorRepresentations/Sandwich.lean#L17) · [Apply the translation to the chosen degrees](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdConsA.lean#L128)
- For $\lambda_{t,i}=\lambda_i+t(N-1-i)$, write $\mathcal A_t$ for the corresponding model operator and $w_t$ for its unit highest weight vector. For each $y\in\mathbb C^{\mathcal P}$ the small-argument coefficient satisfies
$$
 \langle w_t,\mathcal A_t(y/\sqrt t)w_t\rangle
       \longrightarrow \exp\!\left(-\tfrac12\sum_{(i,j)\in\mathcal P}(j-i)|y_{ij}|^2\right).
\tag{3}
$$
The source gets (3) from its highest-weight tangent estimate, expanded in [the Casimir and differential-equation proof](the-casimir-bound-and-a-small-time-ode-give-the-coefficient-gaussian.md). The linear phase vanishes because $X(y)$ has zero diagonal. The quadratic trace counts one off-diagonal root with coefficient $j-i$. This input supplies the lower estimate on the degree integral. [Evaluate the quadratic trace](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdPointwise.lean#L95) · [Scaled coefficient limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdPointwise.lean#L120)

## The degree-to-Vandermonde ratio along the shift

To reach $\lambda_t$, add coordinate vectors one at a time while keeping the accumulated natural integer vector decreasing in the weak sense. Such an order exists because any nonnegative decreasing integer vector can be reduced by subtracting one at its last nonzero index. All intermediate ordered parameters remain regular and each gap increases weakly, so the hypotheses of (2) hold at every stage. Hence $d(\lambda_t)/V(\lambda_t)=d(\lambda)/V(\lambda)$. [Iterate the one-coordinate step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdStep.lean#L134)

Put $B_{\mathcal P}=\prod_{(i,j)\in\mathcal P}(j-i)>0$. The ratio to compute is
$$
 H_t=\frac{t^{pq}d_K(\lambda_t)}{d(\lambda_t)}.
$$
In the product for $d_K(\lambda_t)$, every same-sign shifted gap divided by the corresponding gap in $V(\lambda_t)$ tends to one. Indeed that gap grows as $t(j-i)+O(1)$ and the root shift is fixed. Each opposite-sign factor in the denominator contributes $t/(\lambda_{t,i}-\lambda_{t,j})\to1/(j-i)$. Combining with the constant degree-to-Vandermonde ratio shows
$$
 H_t\longrightarrow
 \frac{V(\lambda)}{d(\lambda)F(p)F(q)B_{\mathcal P}} .
\tag{4}
$$
[Compute the limit by Weyl factors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdConst.lean#L78)

## Identify that limit by the polar integrals

By the right inequality of (2) in the Schur calculation and [the Gaussian integral limit](the-rescaled-polar-potential-has-a-gaussian-integral-limit.md),
$$
 \limsup H_t\le c_{pq}\frac{\pi^{pq}}{B_{\mathcal P}} .
$$
By the left inequality there, the substitution $z=y/\sqrt t$ gives $H_t\ge c_{pq}\int |\langle w_t,\mathcal A_t(y/\sqrt t)w_t\rangle|^2 J(y/\sqrt t)\,dy$. The factor $t^{pq}$ cancels the real Jacobian. The integrand is nonnegative, and by (3) and $J(y/\sqrt t)\to1$ its pointwise limit is the Gaussian with integral $\pi^{pq}/B_{\mathcal P}$. Fatou's lemma therefore gives the opposite inequality for $\liminf H_t$. Thus (4) equals $c_{pq}\pi^{pq}/B_{\mathcal P}$. Substituting the value of $c_{pq}$ and cancelling the positive factors proves $d(\lambda)=V(\lambda)/F(N)$. [Fatou lower bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdLower.lean#L18) · [Solve for the normalized degree](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdConst.lean#L78) · [Recover the degree of any representation in the fixed measure](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdCons.lean#L54)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
