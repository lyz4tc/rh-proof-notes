# Ultrametric polynomials separate compact sets and level cosets

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $k$ be a field with a nonarchimedean absolute value, let $I$ be a finite set, and give $k^I$ the maximum norm. If $Z_1,Z_2\subset k^I$ are disjoint compact sets and $\varepsilon>0$, there is a polynomial $P\in k[X_i:i\in I]$ with
$$
 |P(z)-1|\le\varepsilon\quad(z\in Z_1),\qquad
 |P(z)|\le\varepsilon\quad(z\in Z_2).
$$
The unitary weight argument needs this theorem for compact images of two disjoint pieces of a finite adelic level. [Polynomial separation statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/DeltaNear.lean#L158) · [Lean proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/SepPoly.lean#L45)

## Separating a neighborhood of zero

Fix $\delta>0$ and $0<e\le1$. Start with $p=1$. Given finitely many centers $c\in k$ with $|c|\ge\delta$, process them in nondecreasing order of their norms. On the step at $c$, multiply the current polynomial by $(1-X/c)^n$. On the ball $|x-c|\le|c|/2$, the quantity $|1-x/c|$ is at most $1/2$. Since $|x|\le |c|$ there, $p$ is bounded there by $\sum_i|p_i||c|^i$ for $p(X)=\sum_i p_iX^i$. Choose $n$ so that multiplying this bound by $2^{-n}$ gives at most $e$.

Every earlier ball lies inside $|x|\le|c|$, where the new factor has norm at most $1$. So any bound already achieved remains valid. The new factor has norm at most $1$ also on $|x|\le\delta$. For $|x|\le\delta e$, it differs from $1$ by at most $e$, using $(1-x/c)^n-1=(-x/c)\sum_{j=0}^{n-1}(1-x/c)^j$. A finite product of factors within $e$ of $1$ remains within $e$ by the ultrametric inequality and $e\le1$. Induction gives $p$ bounded by $1$ on $|x|\le\delta$, bounded by $e$ on each chosen ball, and within $e$ of $1$ on $|x|\le\delta e$. [Finite ball construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/KaplFin.lean#L58)

For a compact set $Y\subset k$, its closed subset $\{y\in Y:|y|\ge\delta\}$ is covered by finitely many of the balls $|x-c|\le |c|/2$ centered at its members. Each ball has positive radius and contains a neighborhood of its center. The preceding construction therefore gives a polynomial $p$ of norm at most $1$ on $Y$, of norm at most $e$ on its part with norm at least $\delta$, and within $e$ of $1$ for $|x|\le\delta e$. [Compact shell argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/KaplOf.lean#L8)

## Separating two compact sets

The claim is immediate with $P=0$ or $P=1$ when one set is empty. Otherwise fix $0<\delta\le\inf\{\|z-z'\|:z\in Z_1,\ z'\in Z_2\}$, positive by disjoint compactness. Set $e=\min(1,\varepsilon)$. Cover $Z_1$ by finitely many balls of radius $\delta e$ centered at points $b\in Z_1$. Take $Y$ to be the union of all scalar coordinate differences $z_i-b_i$ as $z\in Z_1\cup Z_2$, $i\in I$, and $b$ is a chosen center. This is a finite union of continuous images of compact sets. Apply the scalar construction to $Y$. Then
$$
 Q_b(X)=\prod_{i\in I}p(X_i-b_i)
$$
has norm at most $1$ on $Z_1\cup Z_2$, is within $e$ of $1$ in the ball centered at $b$, and has norm at most $e$ on $Z_2$. The last assertion uses one coordinate at distance at least $\delta$ from $b_i$. Set $P=1-\prod_b(1-Q_b)$. At $z\in Z_1$ one factor $1-Q_b(z)$ has norm at most $e$, and all the others have norm at most $1$. At $z\in Z_2$ all factors are within $e$ of $1$. These bounds give the two claims. [Multivariable construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/SepPoly.lean#L45)

## Compact level groups

Let $\Gamma$ be a compact topological group, let $\varphi\colon\Gamma\to\mathrm{GL}_a(k)$ be a homomorphism with continuous entries, and assume $\varphi(g),\varphi(g)^{-1}$ have all entries of norm at most $1$. Let $\Gamma'\subseteq\Gamma$ be an open subgroup containing $\ker\varphi$, and fix $\varepsilon>0$. Let
$$
 H=\{g\in\Gamma:\|\varphi(g)-1\|_{\max}\le\varepsilon\},\qquad K=H\cap\Gamma'.
$$
The entrywise maximum norm is submultiplicative by the ultrametric inequality. The identities $AB-1=(A-1)B+(B-1)$ and $A^{-1}-1=-A^{-1}(A-1)$ show that $H$ is a subgroup. An ultrametric closed ball of positive radius is open, so $H$ is open by continuity of entries. Thus $K$ is an open subgroup containing $\ker\varphi$. It is closed, and the open cosets cover the compact group, so there are finitely many cosets $c_qK$. [Near-identity subgroup](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/NearSub.lean#L18)

The images of $c_qK$ and its complement under $\varphi$, viewed as sets of matrices, are compact. They are disjoint because equal images of $g,g'$ imply $g^{-1}g'\in\ker\varphi\subseteq K$. Separate those two images with a polynomial $P_q$ as above. Given $g$, the unique coset $c_{q_0}K$ containing $g$ gives
$$
 c_{q_0}^{-1}g\in\Gamma',\qquad
 \|\varphi(c_{q_0}^{-1}g)-1\|_{\max}\le\varepsilon,\qquad
 |P_{q_0}(\varphi(g))-1|\le\varepsilon .
$$
All other $P_q(\varphi(g))$ have norm at most $\varepsilon$. This is the piecewise polynomial approximation used in the [weight family](coset-polynomials-change-the-weight-at-one-infinite-place.md). In the Lean application $k=\overline{\mathbb Q}_\ell$. Coefficients are transported to $\mathbb C$ by $\iota$. [Level coset construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/Pieces.lean#L24)

## Lean correspondence

- `UpperTheory.Gal.Wt.kaplFin_of` and `kapl_of` build the scalar polynomial on finitely many balls and then on a compact shell. [Finite construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/KaplFin.lean#L58) · [Compactness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/KaplOf.lean#L8)
- `UpperTheory.Gal.Wt.sepPoly_of` separates disjoint compact subsets of finite coordinate space. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/SepPoly.lean#L45)
- `UpperTheory.Gal.Wt.nearSub_of` and `pieces_of` apply the construction to a compact group. [Subgroup](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/NearSub.lean#L18) · [Cosets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/WeightCharacters/Pieces.lean#L24)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
