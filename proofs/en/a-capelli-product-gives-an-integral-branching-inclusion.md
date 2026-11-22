# A Capelli product gives an integral branching inclusion

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix $n\ge1$ and nonincreasing nonnegative integer lists $\lambda_1,\ldots,\lambda_n,\lambda_{n+1}=0$ and $\gamma_1,\ldots,\gamma_n$, with $\lambda_i\ge\gamma_i\ge\lambda_{i+1}$ for every $i$. Write $\nabla_\gamma(R)$ for the polynomial module of column multidegree $\gamma$ invariant under adding earlier columns to later columns, on an $n\times n$ matrix $X$ over $R=\mathbb Z$ or $\mathbb Q$. Write $\nabla_\lambda(R)$ for the analogous module on the $(n+1)\times n$ matrix obtained by appending a row $z$ to $X$, using column multidegree $(\lambda_1,\ldots,\lambda_n)$. Put
$$
b_i=\lambda_i-\gamma_i,\qquad d=\sum_i b_i,\qquad
d_0=\sum_i(\gamma_i-\lambda_{i+1}),\qquad
R_i=[\lambda_{i+1},\min(\lambda_i,\lambda_{i+1}+d_0)]\cap\mathbb Z .
$$
Let $\Delta_i$ be the leading $i\times i$ minor of $X$ and let $\Gamma_i$ be the minor using rows $1,\ldots,i-1,n+1$ and columns $1,\ldots,i$. Define the polynomials and integer
$$
\begin{aligned}
h_\gamma&=\prod_{i=1}^n\Delta_i^{\gamma_i-\gamma_{i+1}},&
\xi_\gamma&=\prod_{i=1}^n\Delta_i^{\gamma_i-\lambda_{i+1}}\Gamma_i^{b_i},\\
c_\gamma&=\prod_{i=1}^n\prod_{v\in R_i\setminus\{\gamma_i\}}
\prod_{j=1}^n(v-i+j-\gamma_j),&&\gamma_{n+1}=0.
\end{aligned}
$$
There is a $\mathbb Q$-linear map $J:\nabla_\gamma(\mathbb Q)\to\nabla_\lambda(\mathbb Q)$ intertwining $\mathrm{GL}_n(\mathbb Q)$ in the top rows, taking the integral polynomials of $\nabla_\gamma(\mathbb Z)$ to integral polynomials, and satisfying $J(h_\gamma)=c_\gamma\xi_\gamma$. Its output always has total degree $d$ in $z$. This supplies the integral realization of the transpose branching map.

### Lift a polynomial with a prescribed highest last-row coefficient

Put $s(\beta)=\sum_{i=1}^n i\beta_i$ for an exponent of $z$. First, for $F\in\nabla_\gamma(R)$ construct $G\in\nabla_\lambda(R)$ of total $z$ degree $d$ with
$$
G=z^b F(X)+\text{terms with last-row score less than }s(b).
\tag{1}
$$
The standard monomial span theorem over an integral domain identifies the indicated matrix polynomial module of column multidegree $\gamma$ with the span of products of initial-column minors. A factor of height $i$ uses the first $i$ columns and a list of $i$ rows. In a product of shape $\gamma$, exactly $\gamma_i$ factors have height at least $i$. Empty minors are $1$, a repeated row gives zero, and sorting a list of distinct rows changes only its sign. We use the theorem over $\mathbb Z$ and $\mathbb Q$. [Standard monomial spanning](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FinalC.lean#L37)

For a product of minors of shape $\gamma$, remove a factor of height $s$. The remaining shape is $\gamma'_i=\gamma_i-\mathbf1_{i\le s}$. If $\gamma_s>\lambda_{s+1}$, remove a column of height $s$ from $\lambda$ as well, meaning $\lambda'_i=\lambda_i-\mathbf1_{i\le s}$. The inequalities $\lambda'_i\ge\gamma'_i\ge\lambda'_{i+1}$ follow from the original ones, with the strict inequality at $s$ providing $\gamma_s-1\ge\lambda_{s+1}$. Lift this factor as the same minor.

If $\gamma_s=\lambda_{s+1}$, then $s<n$ since $\gamma_s\ge1$. A factor of height $s$ means $\gamma_s>\gamma_{s+1}$, so $\lambda_{s+1}-1\ge\gamma_{s+1}$. Remove a column of height $s+1$ from $\lambda$, meaning $\lambda'_i=\lambda_i-\mathbf1_{i\le s+1}$. At $s$ both $\gamma_s$ and $\lambda_{s+1}$ fall by one, and at $s+1$ the new $\lambda'_{s+1}$ still bounds $\gamma'_{s+1}$ from above. At all other positions the inequalities compare as before. Lift the factor by appending the last row of $(X,z)$ to its row set and taking the first $s+1$ columns. Expansion by its last row has leading term $z_{s+1}$ times the original factor with positive sign. All remaining terms use $z_i$ with $i\le s$, of strictly smaller score.

By induction the remainder has a lift of the form (1) for $\lambda',\gamma'$. Multiply by the chosen lift of the factor. In the first case the difference exponent $\lambda'-\gamma'$ is still $b$, and in the second it is $b$ with one subtracted at $s+1$. Thus the product has the asserted leading term. Products of initial-column minors are column-invariant and have the stated column degrees. If no factors remain, $\gamma=0$ forces $\lambda_i=0$ for $i>1$ and the remaining lift is $z_1^{\lambda_1}$. This proves (1) for a product and hence for a linear combination over $R$.

### The constituents and their leading last-row terms

Work over $\mathbb Q$ in the space of fixed total $z$ degree $d$ in $\nabla_\lambda(\mathbb Q)$. For each top row substitution by $g\in\mathrm{GL}_n(\mathbb Q)$, the transpose substitution is its adjoint for the factorial pairing. Therefore the orthogonal complement of a stable subspace is stable, and positivity allows repeated splitting into irreducible subspaces over $\mathbb Q$.

Each nonzero stable subspace contains a vector homogeneous in the top row degrees and invariant under adding earlier top rows to later top rows. For homogeneity, project successively with rational polynomials in the diagonal substitution scaling one row by $2$, whose eigenvalues $2^k$ at the possible degrees are distinct. From the nonzero weights that occur, choose one minimizing the sum of each top row degree times its row index. Positive divided operators adding earlier rows to later ones would send it to lower weight score, so they vanish. Those operators preserve any stable subspace since they are coefficients of polynomial substitutions by unipotent matrices, and interpolation expresses each coefficient as a rational combination of such substitutions.

Take such a highest vector, of top row degrees $\mu_1,\ldots,\mu_n$. On the set where all leading minors of $X$ are nonzero, earlier top row additions and earlier column additions reduce $X$ to the diagonal pivots $\Delta_i/\Delta_{i-1}$, with $\Delta_0=1$. In the last row the new entry at column $i$ is $\Gamma_i/\Delta_{i-1}$, since $\Gamma_i$ is invariant under these operations and on the reduced matrix equals the product of the first $i-1$ pivots times that entry. On a diagonal top block the row and column multidegrees leave only the monomial in the diagonal entries of exponents $\mu_i$ and last-row entries of exponents $\lambda_i-\mu_i$. Thus a nonzero highest vector forces $\mu_i\le\lambda_i$, and by substitution its value on the open set is a nonzero scalar times
$$
\prod_{i=1}^n\Delta_i^{\,\mu_i-\lambda_{i+1}}\Gamma_i^{\,\lambda_i-\mu_i}.
\tag{2}
$$
The polynomials $\Delta_i,\Gamma_i$ are irreducible and pairwise nonassociate. To prove irreducibility of a generic determinant, induct on its size. A determinant of size one is a single variable. As a linear polynomial in the last row, a larger determinant is irreducible over the fraction field of the coefficient ring. Its coefficients are distinct smaller determinant minors with no common factor, so it is irreducible over the coefficient ring as well. The two minors of the same size here use different row sets, so they are nonassociate. Consequently (2) can be polynomial only if $\mu_i\ge\lambda_{i+1}$ for each $i$. Conversely for these inequalities (2) gives a nonzero polynomial of the required multidegrees, invariant under earlier column additions and earlier top row additions. The determinants in each factor have precisely the initial columns and initial top rows needed for that invariance. This proves that the highest weight line for each admissible $\mu$ is one-dimensional with generator $\xi_\mu$ obtained by replacing $\gamma$ by $\mu$ in the formula above.

The irreducible subspace generated by $\xi_\mu$ therefore occurs at most once. On $\xi_\mu$, selecting the last-row entry in column $i$ from each factor $\Gamma_i$ gives the leading last-row term, with exponent $\beta_i=\lambda_i-\mu_i$ and coefficient $h_\mu$. On every vector of that subspace the terms have lower score or this same exponent, because top row action commutes with last-row extraction. Moreover the coefficient at that exponent is injective on the constituent, since its kernel is a stable subspace and the generator has nonzero coefficient. It follows that if a sum of constituents has no term of score at least $s(b)$, then it has zero $\gamma$ constituent. To see this, take the largest score among its nonzero constituents. The leading exponents $\lambda-\mu$ at that score are distinct, and each has a nonzero coefficient, so the sum has that score.

### The integral selector and independence of the lift

Use the Capelli operator $C(u)$ of [the shifted determinant calculation](the-shifted-column-determinant-commutes-with-column-operators.md) on $X$. It preserves the space of prescribed last-row degree, commutes with top row substitution and preserves each last-row exponent. Hence on each highest line it acts by a scalar. Comparing the coefficient of $z^{\lambda-\mu}$ on $\xi_\mu$ computes it. That coefficient is $h_\mu$, which is killed by the derivations $D_{ij}$ for $i<j$ by its column invariance and is an eigenvector for each $D_{ii}$ of eigenvalue $\mu_i$. The determinant calculation gives $\prod_j(u+j-1-\mu_j)$, and equivariance gives the same scalar on the constituent generated by $\xi_\mu$.

Every constituent in this fixed last-row degree has $\sum_i\mu_i=\sum_i\gamma_i$. Hence $\sum_i(\mu_i-\lambda_{i+1})=d_0$, the summands are nonnegative, and $\mu_i\in R_i$. Define
$$
Z=\prod_{i=1}^n\prod_{v\in R_i\setminus\{\gamma_i\}}C(v-i+1).
$$
If $\mu\ne\gamma$, select $i$ with $\mu_i\ne\gamma_i$. The factor with $v=\mu_i$ has zero eigenvalue on this constituent, because its factor at $j=i$ vanishes. The scalar on the remaining $\gamma$ constituent is exactly $c_\gamma$. This scalar is nonzero. For $j>i$, $\gamma_j-j\le\lambda_{i+1}-j<v-i$, and for $j<i$, $\gamma_j-j\ge\lambda_i-j>v-i$. For $j=i$, $v\ne\gamma_i$ by the choice of the product.

Now choose a lift $G$ as in (1) and put $J(F)=ZG$. The difference of two lifts has score strictly below $s(b)$, so it has no $\gamma$ constituent. The selector $Z$ annihilates that difference. Thus $J$ is well-defined, is linear by adding or scaling the lifts, and is equivariant by applying the block row action to a lift. The integral lift construction and the integral coefficients of $Z$ prove the integrality of $J(F)$ for integral $F$. For $F=h_\gamma$ the polynomial $\xi_\gamma$ itself is a lift, so $J(h_\gamma)=c_\gamma\xi_\gamma$.

### Lean correspondence

- [`bmLift` and `bmZop`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L70) define the lift condition and selector. [`bmG_bidet` and `bmLift_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L2068) construct integral lifts by removing one minor at a time.
- [`bm_eig`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L1511) computes the scalar on a highest last-row component. [`bmK_kill` and `bmK_key`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L2483) implement the annihilation and lift independence using the degree filtration. The rational constituent proof above gives these properties through the same last-row scores and scalar formula.
- [`bmK_xi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L2537) identifies the scalar on $\xi_\gamma$, and [`bmK_io` and `branch_map_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/BranchSandwichDivisors/BranchIsometryProofs/BranchMap.lean#L2608) assemble the map. [`inB_capInt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/InterlaceDifferenceShiftInvariant.lean#L3503) proves integrality for the map over $\mathbb Q$ by using integral lifts and compatibility with the integer differential operators.

Status. Source-based reconstruction draft. The integral standard monomial spanning theorem is the remaining upstream input stated above. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
