# The rescaled polar potential has a Gaussian integral limit

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix signs on $0,\ldots,N-1$ with $p,q\ge1$ signs of the two kinds. Let $\mathcal P=\{(i,j):i<j,\ \mathrm{sign}(i)\ne\mathrm{sign}(j)\}$, so $\#\mathcal P=pq$. For $z\in\mathbb C^{\mathcal P}$ let $X(z)$ be the Hermitian matrix with $X(z)_{ji}=z_{ij}$, $X(z)_{ij}=\overline{z_{ij}}$ on these pairs, and zero entries elsewhere. For $a=1,\ldots,N-1$, define $F_a(X)=\log\det((e^X)_{[0,a)})$, the logarithm of the principal $a$-by-$a$ determinant. For a decreasing real list $\lambda$, put $\lambda_{t,i}=\lambda_i+t(N-1-i)$ for $t\ge0$, and let
$$
 \Phi_{\lambda_t}(X)=\sum_{a=1}^{N-1}(\lambda_{t,a-1}-\lambda_{t,a}+1)F_a(X),\qquad
 J(z)=\prod_{i<j} \frac{\sinh(\nu_i-\nu_j)}{\nu_i-\nu_j},
$$
where the $\nu_i$ are the eigenvalues of $X(z)$ and the quotient at zero is one. Then
$$
 \lim_{t\to\infty} t^{pq}\int_{\mathbb C^{\mathcal P}}
              e^{-2\Phi_{\lambda_t}(X(z))}J(z)\,dz
       = \prod_{(i,j)\in\mathcal P}\frac{\pi}{j-i}.
\tag{1}
$$
Lean uses the upper bound in (1), with separate near and far estimates. The following direct log-determinant calculation gives the same bound. [Jacobian and principal-minor potential](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/PmatIsHermitian.lean#L42) · [Upper limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdUpper.lean#L95) · [Near and far bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdUpperB.lean#L54)

## The quadratic term

For real $s$ near zero, expand $e^{sX}$, then its leading block, and use the Taylor series for $\log\det(I+Z)=\operatorname{tr}\log(I+Z)$. Its linear term is $s\operatorname{tr}(X_{[0,a)})=0$. The quadratic term is
$$
 \tfrac{s^2}{2}\operatorname{tr}\big((X^2)_{[0,a)}-(X_{[0,a)})^2\big)
 = \tfrac{s^2}{2}\sum_{i<a\le j}|X_{ij}|^2 .
$$
This traces exactly the terms joining the two sides of the block boundary. When summed over $a$, the entry indexed by $i<j$ appears $j-i$ times. Write $Q(y)=\sum_{(i,j)\in\mathcal P}(j-i)|y_{ij}|^2$. For fixed $y$ set $s=t^{-1/2}$. Since every coefficient of $\Phi_{\lambda_t}$ is $t+\lambda_{a-1}-\lambda_a+1$, the expansion gives $2\Phi_{\lambda_t}(X(y/\sqrt t))\to Q(y)$. Also $J(y/\sqrt t)\to1$.

## A common integrable majorant

Each $F_a(X(z))$ is nonnegative and convex on rays from zero. Indeed, the leading minor of $e^{sX}$ equals the diagonal coefficient of $\bigwedge^a e^{sX}=e^{s\,d(\wedge^a)(X)}$ at the unit wedge of the first $a$ basis vectors. The latter is a weighted sum of real exponentials with nonnegative weights summing to one, since the generator is Hermitian. Its log is convex by Cauchy–Schwarz on its first two derivatives. The value and derivative at zero vanish, which proves nonnegativity. The expansion above is uniform for $X(y)$ with $\|y\|=1$, by compactness of the unit sphere and smoothness of the finite-dimensional matrix functions on a neighborhood of zero. Since $Q(y)\ge\|y\|^2$, there are $c,r_0>0$ such that
$$
 \sum_a F_a(X(z))\ge
 \begin{cases}
   c\|z\|^2,&\|z\|\le r_0,\\
   cr_0\|z\|,&\|z\|\ge r_0 .
 \end{cases}
$$
The second bound follows from convexity and $F_a(X(0))=0$, on the ray through $z$ and the point of radius $r_0$. Since each coefficient of $\Phi_{\lambda_t}$ is at least $t$, the rescaled exponent $2\Phi_{\lambda_t}(X(y/\sqrt t))$ is at least $2c\min(\|y\|^2,r_0\sqrt t\|y\|)$.

For real $u$, $1\le\sinh(u)/u\le e^{|u|}$ with the usual convention at zero. The eigenvalue gaps of $X(z)$ are bounded by a fixed multiple of $\|z\|$, so $J(z)\le e^{C\|z\|}$. Take $t$ sufficiently large that $r_0\sqrt t\ge1$ and $C/\sqrt t\le c$. Then outside $\|y\|\le1$ the rescaled integrand is at most $e^{-c\|y\|}$, and on the ball it is at most $e^C$ for $t\ge1$. This is an integrable bound. The real dimension is $2pq$, so the substitution $z=y/\sqrt t$ has Jacobian $t^{-pq}$. Dominated convergence yields (1), since each complex coordinate contributes $\int_{\mathbb C}e^{-(j-i)|z|^2}\,dz=\pi/(j-i)$. [Jacobian bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/JacobianLeExp.lean#L97) · [Use the same Gaussian in the lower limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/DiscreteSeries/FormalDegree/FdLower.lean#L18)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
