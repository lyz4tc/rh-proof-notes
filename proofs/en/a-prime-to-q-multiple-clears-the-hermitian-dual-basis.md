# A prime-to-q multiple clears the Hermitian dual basis

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $d$ be prime with $d\equiv7\bmod16$, put $\eta=(1+i\sqrt d)/2$, and let $\mathcal O=\mathbb Z+\mathbb Z\eta$. Take a positive definite Hermitian form $H$ on $\mathbb C^g$, linear in its first argument, and write $B=(\sqrt d/2)H$. Let $\Lambda\subset\mathbb C^g$ be a discrete full real lattice stable under $\eta$, with $B(\Lambda,\Lambda)\subseteq\mathcal O$. Assume the converse imaginary-pairing test
$$
  \bigl(\operatorname{Im}H(x,y)\in\mathbb Z\text{ for all }x\in\Lambda\bigr)
       \quad\Longrightarrow\quad y\in\Lambda .
\tag{1}
$$
The form and lattice conditions are `Setup.Ok`. Take any prime $q$ and a list $b_1,\ldots,b_r\in\Lambda$ independent over $\mathcal O$, with the property that for each $x\in\Lambda$ some positive integer $s_x$ prime to $q$ satisfies $s_x x\in\sum_i\mathcal O b_i$. This is `NNBasis`. Then there exist a positive integer $s$ prime to $q$ and $c_1,\ldots,c_r\in\Lambda$ with
$$
    B(c_j,b_i)=s\,\mathbf 1_{i=j},\qquad
    s x=\sum_j B(x,b_j)c_j\quad(x\in\Lambda).
\tag{2}
$$
The prime $q$ need not be split for this basis statement. These are the scaled dual vectors used to make the finite good-lift coordinates. [Lattice data `Setup.Ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/DeterminantCokernelCount/CokernelIndexFactors/StatementB.lean#L43) · [Basis data `NNBasis`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/DeterminantCokernelCount/CokernelIndexFactors/StatementB.lean#L79) · [Dual-basis existence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsDualBasisOfUnimodularLatticeAtPrimeStatement.lean#L8)

## Proof

Because $\Lambda$ is full in the real vector space underlying $\mathbb C^g$, its rank over $\mathbb Z$ is $2g$. The $2r$ vectors $b_i,\eta b_i$ in $\Lambda$ are independent over $\mathbb Z$: a relation over $\mathbb Z$ would give a relation among the $b_i$ with coefficients $u_i+v_i\eta$, forcing $u_i=v_i=0$ by $\mathcal O$-independence. It follows that $r\le g$. On the other hand the complex span of the $b_i$ contains $\Lambda$, because $s_x x$ belongs to that span and $s_x\ne0$. It therefore contains the full real span $\mathbb C^g$, and $r\ge g$. Thus the list is a complex basis.

In this basis the matrix $B(b_i,b_j)$ is positive definite and hence invertible. Choose its Hermitian dual vectors $c_j^*$ with $B(c_j^*,b_i)=\mathbf1_{i=j}$. This is possible by inverting the matrix on the first coordinate, where $B$ is linear. For every complex vector $x$, the unique expansion in this dual basis is $x=\sum_j B(x,b_j)c_j^*$, as can be checked by pairing on the right with each $b_i$. Also $B(b_i,c_j^*)=\mathbf1_{i=j}$ by Hermitian symmetry.

Now choose any integral basis of the lattice $\Lambda$. For each of its members pick a clearing integer $s_x$ as in the hypothesis. Let $s$ be the product of these finitely many positive integers. The product is prime to $q$ and clears all the original basis vectors at once, so $s\Lambda\subseteq\sum_i\mathcal O b_i$. Given $x\in\Lambda$, write $s x=\sum_i a_i b_i$ for $a_i\in\mathcal O$. Then $B(x,s c_j^*)=B(sx,c_j^*)=a_j$. If $a_j=u+v\eta$, with $u,v\in\mathbb Z$, its imaginary part is $v\sqrt d/2$. Consequently $\operatorname{Im}H(x,s c_j^*)=v\in\mathbb Z$ for every $x\in\Lambda$. By (1), $c_j=s c_j^*$ lies in $\Lambda$. These vectors and the common $s$ satisfy both equations (2). [Complex dual frame and clearing denominators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsDualBasisOfUnimodularLatticeAtPrime.lean#L60)

## Source and verification

The construction was checked against the pinned source. The full lattice, basis, Hermitian form, and imaginary-pairing test are hypotheses. In particular the prime-to-$q$ clearing of the dual vectors comes from the same clearing property for the original basis and the duality test. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
