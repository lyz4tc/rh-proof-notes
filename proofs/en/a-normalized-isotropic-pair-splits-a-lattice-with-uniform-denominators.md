# A normalized isotropic pair splits a lattice with uniform denominators

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $W,h$ be a nondegenerate Hermitian space over a CM extension $E/F$, with $h$ conjugate-linear in its first argument. Fix $D\ge1$. Consider any full integral $\mathcal O_E$-lattice $\Lambda$ with $[\Lambda^\#:\Lambda]\le D$ and any rational isotropic line $l$ in $W$. There are two finite sets of fractional ideals of $E$ and a positive integer $N$, depending only on $D,E$, with the following property. One can choose $v\in l\setminus\{0\}$, $w\in W$ with $h(v,w)=1$, $h(v,v)=h(w,w)=0$, such that
$$
 I=\{a:av\in\Lambda\},\qquad J'=\{b:bw\in\Lambda\}
$$
belong to the two finite sets. With $W_0=(Ev+Ew)^\perp$ and $\Lambda_0=\Lambda\cap W_0$, one has
$$
 I v+\Lambda_0+J'w\ \subseteq\ \Lambda,\qquad
 N\Lambda\ \subseteq\ I v+\Lambda_0+J'w .
\tag{1}
$$
The bound on $N$ is uniform in both the lattice and the line. This is the normal form used to reduce the orbit problem by two dimensions. [Line normal form statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/StLineNormalForm.lean#L16) · [Construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L90)

## Normalize the image of the pairing

Use one nonzero fractional ideal $J$ from each ideal class of $E$. There are finitely many by the ideal class finiteness theorem for a number field. For every chosen $J$ fix $j_0\in J\setminus\{0\}$, and take one positive integer $d$ such that $dJ\subseteq\mathcal O_E$ and $d j_0^{-1}\in\mathcal O_E$ for every member of this finite list. Put $m=D!$, so $m\Lambda^\#\subseteq\Lambda$.

Take any $v_1\in l\setminus\{0\}$. The image $h(v_1,\Lambda)$ is a nonzero fractional ideal because the pairing is nonzero on the full lattice and the image is a finitely generated $\mathcal O_E$-submodule of $E$. Write it as $cJ$ for $c\in E^\times$. Replace $v_1$ by $v=\bar c^{-1}v_1$, so that $h(v,\Lambda)=J$. Choose $x_1\in\Lambda$ with $h(v,x_1)=j_0$. For $I$ this gives
$$
 md\,\mathcal O_E\subseteq I\subseteq d^{-1}\mathcal O_E .
\tag{2}
$$
Indeed $dv\in\Lambda^\#$ because $dJ$ is integral, so $md\,v\in\Lambda$. Conversely $av\in\Lambda$ implies $\bar a j_0=h(av,x_1)\in\mathcal O_E$. Multiply by $d j_0^{-1}$ and conjugate to get $da\in\mathcal O_E$. [Uniform denominators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L126) · [Rescaling the first vector](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L152) · [First ideal bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L206)

## Construct the partner and clear the projections

Take $y=j_0^{-1}x_1$ and $q=h(y,y)\in F$, so $h(v,y)=1$. Set $w=y-(q/2)v$. Then $h(v,w)=1$ and $h(w,w)=q-q=0$. Moreover $d^2 q=h(x_1,x_1)(d j_0^{-1})\overline{d j_0^{-1}}$ is integral. With $k=2md^3$, the first term of $kw$ belongs to $\Lambda$ by $d j_0^{-1}\in\mathcal O_E$, and the second does by $kq/2=md(d^2 q)$ and (2). In the other direction $bw\in\Lambda$ implies $b=h(v,bw)\in J\subseteq d^{-1}\mathcal O_E$. Thus
$$
 k\mathcal O_E\subseteq J'\subseteq d^{-1}\mathcal O_E .
\tag{3}
$$
Each of (2) and (3) gives a finite list of ideals, as the quotient of the two bounding lattices in $E$ is finite. [Corrected Witt partner](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L228) · [Second ideal bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L256)

For $x\in\Lambda$ write its coordinates in $Ev\oplus W_0\oplus Ew$ as $h(w,x),x_\perp,h(v,x)$. The two functionals satisfy
$$
 d h(v,x)\in\mathcal O_E,\qquad
 2d^3 h(w,x)
 =2d^2\overline{d j_0^{-1}}\,h(x_1,x)-(d^2q)\,(d h(v,x))
 \in\mathcal O_E .
$$
Take $N=kd=2md^4$. Then $Nh(v,x)\in k\mathcal O_E\subseteq J'$ and $Nh(w,x)\in md\,\mathcal O_E\subseteq I$. The two projected line terms of $Nx$ are therefore in $\Lambda$, and their difference from $Nx$ is in $\Lambda\cap W_0$. This proves the second inclusion of (1), and the first follows by definition of the intersections. [Both cleared line projections](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/GroundTheory/HeightsAndTheta/Heights/FiniteCovolume/PLineNormalForm.lean#L279)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
