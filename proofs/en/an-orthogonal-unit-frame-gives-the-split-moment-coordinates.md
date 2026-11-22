# An orthogonal unit frame gives the split moment coordinates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the setup $d,\mathcal O,H,B,\Lambda$ of [the Hermitian dual-basis theorem](a-prime-to-q-multiple-clears-the-hermitian-dual-basis.md). Thus $B=(\sqrt d/2)H$ is positive definite, $B(\Lambda,\Lambda)\subseteq\mathcal O$, and the imaginary part of $H$ identifies $\Lambda$ with its integral dual lattice. If $q$ is prime and $q\nmid d$, there are $g$ mutually $B$-orthogonal vectors $x_i\in\Lambda$ with $B(x_i,x_i)=a_i\in\mathbb Z_{>0}$ and $q\nmid a_i$.

If $q$ splits in $K=\mathbb Q(\sqrt{-d})$, choose one embedding $\iota:K\hookrightarrow\mathbb Q_q$. For any local moment basis $b_1,\ldots,b_r$ of $\Lambda$ from the dual-basis theorem, the map
$$
         T:\mathbb Z_q^r\longrightarrow\mathbb Z_q^g,\qquad
         T(A)_i=\sum_j A_j \,\iota(B(x_i,b_j))
\tag{1}
$$
is an invertible $\mathbb Z_q$-linear map. Thus a measure on the orthogonal moment coordinates can be transported to the basis $b$ with the same norm. [Orthogonal frame `exists_orthFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsOrthogonalFrameNormsCoprimeOfUnimodular.lean#L388) · [Integral change of frame `frameChange`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsPadicIntFrameChangeEtaleBasis.lean#L63)

## Proof

### Choose the frame by reduction modulo $q$

The $\mathcal O$-module $\Lambda$ is finite and torsion-free, with rank $g$ because its rank over $\mathbb Z$ is $2g$. Reducing $B$ modulo $q$ gives a Hermitian form on $\Lambda/q\Lambda$ over the finite étale algebra $\mathcal O/q\mathcal O$. Its radical is zero. In fact, if $B(z,\Lambda)\subseteq q\mathcal O$ for a lift $z\in\Lambda$, then $\operatorname{Im}H(\Lambda,z/q)\subseteq\mathbb Z$, by Hermitian symmetry and the formula for the imaginary part of elements of $\mathcal O$. Integral self-duality gives $z/q\in\Lambda$. The reduced module is free of rank $g$ over $\mathcal O/q\mathcal O$ by local freeness of torsion-free modules over the Dedekind ring $\mathcal O$.

In any nonzero nondegenerate orthogonal summand of this Hermitian module there is a vector of nonzero norm in $\mathbb F_q$. Otherwise for every $v,w$ in that summand and $c\in\mathcal O/q\mathcal O$, the norm of $v+cw$ would give
$$
     \operatorname{Tr}_{(\mathcal O/q\mathcal O)/\mathbb F_q}
                  (\bar c\,B(v,w))=0.
$$
The trace form is nondegenerate for either a quadratic finite field or the split product $\mathbb F_q\times\mathbb F_q$, where the trace is the sum. Thus every pairing would vanish. This contradicts nondegeneracy. The argument also works for $q=2$.

Suppose $x_1,\ldots,x_l$ have been chosen with unit Gram diagonals $a_i$, with $l<g$. Their reductions split off a nondegenerate submodule, and its orthogonal complement is nonzero of rank $g-l$. Choose a lift $v\in\Lambda$ of an element of nonzero norm in that complement. With $P=\prod_{i=1}^l a_i$ (the empty product is $1$), set
$$
      x_{l+1}=P v-\sum_{i=1}^l(P/a_i)B(v,x_i)x_i .
$$
This lies in $\Lambda$ by integrality of the pairings. It is exactly orthogonal to every $x_i$. Its reduction is $P\bar v$, since the coefficients $B(v,x_i)$ vanish modulo $q$. Its norm is therefore nonzero modulo $q$. The norm belongs to $\mathcal O\cap\mathbb R=\mathbb Z$, and positive definiteness gives a positive integer. Repeating the construction gives the asserted frame.

### Read the change of coordinates at the conjugate split component

For each $y\in\Lambda$, the complex expansion in the orthogonal basis is $y=\sum_i B(y,x_i)x_i/a_i$. The coefficients belong to $\mathcal O$ after multiplication by $\prod_i a_i$, which is prime to $q$. Hence the $x_i$ are a basis after completing $\Lambda$ at $q$. The original $b_j$ are also a basis there, by their clearing condition and independence over $\mathcal O$. In particular $r=g$. Write $b_j=\sum_i S_{ij} x_i$ in the completed lattice, so $S\in \operatorname{GL}_g(\mathcal O\otimes\mathbb Z_q)$. Hermitian symmetry gives $B(x_i,b_j)=a_i\overline{S_{ij}}$. The matrix of $T$ is therefore the product of $\operatorname{diag}(a_i)$ and the image of $\bar S$ in the chosen split component $\mathbb Z_q$. Both are invertible over $\mathbb Z_q$. This proves (1) and explains why the conjugate of the basis-change coefficient occurs.

If $\mu$ acts on continuous functions on the $x_i$-coordinate space, put $\mu_b(f)=\mu(f\circ T^{-1})$. Since $T$ is a bijective continuous linear map with continuous inverse, composition with $T^{-1}$ is a surjective isometry for the supremum norm. Consequently $\|\mu_b\|=\|\mu\|$. This is the coordinate transfer used in [the invariance of theta measure norm](prime-to-p-translation-preserves-theta-measure-norm.md). [Moment transport with the invertible frame](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CmLatticeTranslationOperatorEqPhaseMulNegComp.lean#L288)

## Source and verification

The conclusions and uses of the frame were checked against the pinned source. The proof constructs it by the equivalent projective lattice and residue form argument. The self-dual lattice conditions are explicit hypotheses. No Lean replay or axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
