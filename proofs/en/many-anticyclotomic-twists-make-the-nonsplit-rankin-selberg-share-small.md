# Many anticyclotomic twists make the nonsplit Rankin–Selberg share small

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be a CM field unramified over $E^+$ at every finite place. Let $\pi$ be a unitary cuspidal automorphic representation of $\mathrm{GL}_a(\mathbb A_E)$, $a\ge1$, and let $(P_j)_{j\in J}$ be a finite family of unitary cuspidal representations of $\mathrm{GL}_{a_j}(\mathbb A_E)$, $a_j\ge1$. Assume that, at all but finitely many split places of $E/E^+$, all these representations are spherical and
$$
 \operatorname{Sat}(\pi_w)=\bigsqcup_{j\in J}\operatorname{Sat}(P_{j,w}).
$$
Then $P_j$ is isomorphic to $\pi$ for some $j$, including $a_j=a$. This is the split-place rigidity used twice in [definite unitary descent](split-place-rigidity-upgrades-weak-unitary-descent-to-all-split-places.md). [Hypotheses and conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/SplitRigidAlt.lean#L11) · [Assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/ListOfMultiset.lean#L43)

## Euler logarithms and the analytic input

For a finite family of representations we may remove one finite set of places so that all representations are spherical. Use normalized Satake roots $\alpha_{x,w,b}$ in the unitary normalization of each cuspidal class $x$, and put $A_x(w,k)=\sum_b\alpha_{x,w,b}^k$ for $k\ge1$. If $B$ is a set of the remaining places, define
$$
 L_B(x,y;s)=\sum_{w\in B}\sum_{k\ge1}
   \frac{A_x(w,k)\overline{A_y(w,k)}}{kq_w^{ks}}\qquad(1<s\le2).
$$
The overline gives the Satake parameters of the contragredient for unitary cuspidal forms. Write $L(x,y;s)$ for the sum over all remaining places, and $T(s)=-\log(s-1)$.

The analytic input for these sums is the Rankin–Selberg pole theorem for unitary cuspidal representations. After taking a sufficiently large finite set of omitted places, the product for $x\times y^\vee$ continues meromorphically to $\Re s>0$, is holomorphic at $s=1$ for $x\ne y$, and has a simple pole there for $x=y$. The project uses the logarithm from the unramified Euler expansion, absolutely convergent for real $s>1$. For the diagonal, the coefficients are nonnegative and the convergence down to $1$ follows by Landau's theorem from the holomorphic Euler-product continuation for real $s>1$; the off-diagonal series is then absolutely convergent by Cauchy–Schwarz. Equivalently one may use the precise Euler-logarithm convergence theorem in the Lean proof. On the positive real line $\Re L(x,y;s)$ is the logarithm of the absolute value of the Euler product. Thus
$$
 L(x,x;s)=T(s)+O_x(1),\qquad
 \Re L(x,y;s)\le O_{x,y}(1)\quad(x\ne y).
$$
Only an upper bound is needed off the diagonal. On a subset of the prime powers Cauchy–Schwarz gives
$$
 |L_B(x,y;s)|^2\le L_B(x,x;s)L_B(y,y;s).
$$
[Rankin–Selberg pole and rigidity in Jacquet–Shalika, *On Euler Products and the Classification of Automorphic Representations I*](https://www.math.columbia.edu/~hj/On%20Euler%20products%20I.pdf) · [Lean logarithms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/JacquetShalikaBounds/AbsoluteRigidity/NewtonLow.lean#L14) · [Convergence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/JacquetShalikaBounds/AbsoluteRigidity/DiagonalTermNorms/ConvergenceOfLandauEuler.lean#L92) · [Diagonal and cross bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/GL1SpectralBounds/LogTwo.lean#L8) · [Cross upper bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/GL1SpectralBounds/CrossUp.lean#L8)

## Distinct twists with the same nonsplit parameters

The project constructs a unitary Hecke character $\mu$ of $E$ whose restriction to the ideles of $E^+$ is the quadratic character of $E/E^+$, and which is unramified at the nonsplit finite places. There the Frobenius value is $-1$, since a uniformizer of the unramified quadratic local extension can be chosen in the base field. At each complex place the angular exponent $e$ is odd, because restriction to the real sign character is nontrivial. Write $\chi=\mu^2$, so $\chi(w)=1$ at nonsplit places and $|\chi(w)|=1$ at all remaining places. The twists $z_i=\pi\otimes\chi^i$ for $i\ge0$ are all unitary and pairwise distinct. At a chosen complex embedding, the infinitesimal multiset of $z_i$ is that of $\pi$ translated by $ie$, with $e\ne0$. The sum of its $a$ entries changes by $aie$, which detects $i$. [Construction of $\mu$](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/ArchimedeanBaseChange/ArchimedeanBaseChangeProof/SatakeExponents/UniformizerValuations/QuadraticCharacterNorms/QuadCharNorm.lean#L24) · [Distinct twists](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/AntiTw.lean#L30)

## A small diagonal contribution from nonsplit places

Take $M\ge16(|J|+1)^2$ of the twists, and let $I$ be the set of nonsplit places remaining after the finite removals for this whole finite family. Sum all $M^2$ logarithms $L(z_i,z_j;s)$. At the prime-power coordinate $(w,k)$ the sum of the numerators is
$$
 \sum_{i,j}A_{z_i}(w,k)\overline{A_{z_j}(w,k)}
 =\left|\sum_{i=0}^{M-1}\chi(w)^{ik}\right|^2|A_\pi(w,k)|^2.
$$
It is always nonnegative and is $M^2|A_\pi(w,k)|^2$ on $I$. Absolute convergence permits the sum of the $M^2$ logarithms to be evaluated termwise. Since the twists are distinct, the total sum has real part at most $M T(s)+O(1)$ by the diagonal and off-diagonal bounds. Consequently
$$
 L_I(\pi,\pi;s)\le T(s)/M+O(1).
$$
Even higher prime powers are included in this estimate. The averaging only uses exact equality of the nonsplit twist characters there. [Share bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/ShareBd.lean#L22)

## Comparing the diagonal with the proposed summands

Assume each $P_j\ne\pi$. Let $S$ denote the complement of $I$ among the remaining places. For each $j$, Cauchy–Schwarz and the preceding bound give
$$
 |L_I(\pi,P_j;s)|^2
 \le (T(s)/M+O(1))(T(s)+O(1)).
$$
For example, for all $s$ sufficiently near $1$ the positive $T(s)$ satisfies $|L_I(\pi,P_j;s)|\le T(s)/(3(|J|+1))+O(1)$, since $1/\sqrt M\le1/(4(|J|+1))$. Using $\Re L(\pi,P_j;s)\le O(1)$, we obtain
$$
 \Re L_S(\pi,P_j;s)\le T(s)/(3(|J|+1))+O(1).
$$
On the other hand $L_S(\pi,\pi;s)\ge(1-1/M)T(s)-O(1)$. At each split place, the multiset equality gives $A_\pi(w,k)=\sum_j A_{P_j}(w,k)$ for every $k$. Hence
$$
 L_S(\pi,\pi;s)=\sum_{j\in J} L_S(\pi,P_j;s).
$$
The right side has real part at most $T(s)/3+O(1)$, whereas $1-1/M\ge 15/16$ and $T(s)\to\infty$ as $s\downarrow1$. This contradiction proves the assertion. [Absorbing the nonsplit contribution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/AbsShare.lean#L34) · [Power-sum equality deduced from the Satake multiset](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/ListOfMultiset.lean#L143)

## Lean correspondence

- `UpperTheory.V.Z.Tf.SR.antiTw` gives the distinct twists and their nonsplit values. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/AntiTw.lean#L30)
- `UpperTheory.V.Z.Tf.SR.shareBd` and `absShare` prove the diagonal share bound and the contradiction. [Share bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/ShareBd.lean#L22) · [Contradiction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/AbsShare.lean#L34)
- `UpperTheory.V.Z.Tf.SR.splitRigid_of` packages the analytic assertions for the finite family of automorphic representations. [Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/TraceFormula/SplitRigidity/ListOfMultiset.lean#L43)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof. The Rankin–Selberg pole and Euler-product inputs are used as stated. The Hecke character existence theorem used by `antiTw` is linked above.
