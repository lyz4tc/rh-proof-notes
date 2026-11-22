# How linked frames recover the Hodge jumps at one embedding

**Status: Source-based reconstruction draft.** Read against the pinned Lean source; not human-reviewed or rebuilt.

Draft reconstructed from the pinned Lean sources with AI assistance from Dot and checked against the cited source by Codex.

## Statement and scope

Let $\ell$ be prime, put $\Omega=\overline{\mathbb Q}_\ell$ and $G_K=\operatorname{Gal}(\Omega/K)$, and let $K,L_0\subset\Omega$ be finite extensions of $\mathbb Q_\ell$. Assume every $\mathbb Q_\ell$-embedding $K\hookrightarrow\Omega$ takes values in $L_0$. Fix the compatible period data $(P,AI,T)$ of the source. Let $a\ge1$, let $r:G_K\to\mathrm{GL}_a(\Omega)$, and let a source `Cover` of $r$ by a family $\mathcal C$ be given. In particular it supplies a continuous integral target representation $\rho_\infty$, continuous integral layer representations $\rho_m$, and rectangular comparisons $\Pi_m$ from layer $m$ to target, as well as the matrix readings and unit/trace estimates below. No existence of a cover is asserted here.

Write $J(\iota)$ for a multiset of integers for each embedding $\iota:K\hookrightarrow\Omega$. Assume for **every** member of $\mathcal C$ and **every** finite coefficient model $(L,s,S)$ over $L\supset L_0$ that $S$ is semistable and
$$
\operatorname{mult}_V(S,\tau,h)=\operatorname{count}_{J(\operatorname{incl}_L\circ\tau)}(h)
\quad(\tau:K\hookrightarrow L,\ h\in\mathbb Z).
$$
Here a model means a matrix homomorphism $s:G_K\to\mathrm{GL}_a(L)$ whose entries are exactly those of the given member after inclusion into $\Omega$, and the representation $S$ acting on $L^a$ by these matrices. It is not only an equality of traces. The notation $\operatorname{mult}_V$ uses $(P.\mathrm{PD}\,K)$ and the indexing of the source, without a sign change.

**Conclusion.** Any given finite model $(L,r_L,R)$ of $r$ with $L\supset L_0$ is de Rham and has those same multiplicities. If, additionally, every finite model of every member of $\mathcal C$ as above is crystalline, then $R$ is crystalline. This is [`CovClose.closed_of_cover`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L157-L193). In particular, the equality of jumps does not require crystallinity, and the theorem does not assert that the target is semistable.

The point of this note is the step from linked integral frames to the trace of the Hodge operator **at a specified embedding**. The companion frame note concerns constructing the frames and the divisibility condition for their crystalline branch. The existing catalogue entry *Operator power sums pass along the lattice tower* proves the abstract limiting-trace step, which we use without repeating.

## 1. The three outputs use different arguments

Choose a Breuil–Kisin datum $bk$, a period $\tau_p\in A_{\inf}$ of that datum, and a fitted comparison core $C$. Write $E=bk.E$, $\xi=bk.ev(E)\in A_{\inf}$ and $\Theta=\theta_D\circ aDp:A_{\inf}\to\mathbb C_\ell$, where $aDp:A_{\inf}\to B_{\mathrm{dR}}^+$ and $\theta_D:B_{\mathrm{dR}}^+\to\mathbb C_\ell$ are the source maps. The residue map $\Theta$ kills $\xi$. Choose a single integer $N$ bounding $|h|$ for all $h\in J(\iota)$ using the finite embedding set and finite multisets. This common bound is used to construct frames, not as an assumption on the target jumps.

The semistable models give semistable rational layers $q\operatorname{Rep}(\rho_m)$, with uniformly bounded de Rham filtration. The height-$N$ frame theorem gives frames $F_m$ which are de Rham and are crystalline whenever the corresponding rational layer is crystalline. The linked limit theorem supplies a de Rham height-$N$ frame $F_\infty$ of $\rho_\infty$. It also supplies $(\forall m,\ F_m.\mathrm{IsCr})\Rightarrow F_\infty.\mathrm{IsCr}$ and, for every precision $n$, a layer $m\ge n$ with a `Link`. In this note we only use the first congruence of `Link`:
$$
\iota_W(\Pi_m) F_m.T \equiv F_\infty.T\,bk.ev_W(D)\pmod{\ell^n}
$$
for a rectangular $D$ over the Breuil–Kisin base $bk.S$. Here $\iota_W(\Pi_m)$ abbreviates the integral coefficient map into the large Witt ring. The approximate right inverse in `Link` is not needed for this congruence to yield the Hodge-operator estimate; it is used in the crystalline stability argument. Separately, the tower gives $\Pi_m\rho_m(g)\equiv\rho_\infty(g)\Pi_m\pmod{\ell^m}$ for every $g$.

The de Rham frame comparison gives $\operatorname{IsDR}(q\operatorname{Rep}(\rho_\infty))$. To see why this reaches $R$, write the target reading as $\Phi(x)=\sum_i x_i b_i$ with $b_i\in M_a(\Omega)$ and $\Phi(e)=I$. By equivariance, $\Phi(q\operatorname{Rep}(\rho_\infty)(g)x)=r(g)\Phi(x)$. Choose an $L$-linear retraction $p:\Omega\to L$ of the inclusion. For each $v\in L^a$, the map $F_v(x)=p^{\oplus a}(\Phi(x)v)$ is $\mathbb Q_\ell$-linear, is equivariant by $L$-linearity of $p$ and the model identity, and sends $e$ to $v$. In particular one need not assume $b_i\in M_a(L)$ or claim that a single reading is surjective. The source transports invariant spanning expressions of the rational lattice to each pure tensor $v\otimes c$ through these maps and adds the resulting expressions. For $B_{\mathrm{dR}}$ this gives the de Rham spanning criterion, and for $B_{\mathrm{cris}}$ it gives crystalline spanning, using the regular period-ring criterion of the tied data. The actual proofs are [`exists_read_map`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DeRhamCrystallineOfLatticeReads.lean#L19-L75), [`crys_pass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DeRhamCrystallineOfLatticeReads.lean#L85-L115) and [`dr_pass` / `dr_pass_rat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DeRhamCrystallineOfLatticeReads.lean#L117-L222).

Thus de Rham-ness of $R$ is established before the weight computation. If all seed models are crystalline, the layer theorem gives crystalline rational layers, hence crystalline $F_m$, crystalline $F_\infty$, and crystalline $q\operatorname{Rep}(\rho_\infty)$ by the frame comparison. The same reading carries this to $R$. Neither argument identifies the coefficient-field embedding components of the jumps. For those we need a different comparison.

[Cover, readings, and links](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L78-L157) · [The layer and limit calls](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L161-L193) · [Frame-to-de Rham comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsDeRhamOfBreuilKisinFrameIsDeRhamStatement.lean#L10-L12) · [Frame-to-crystalline comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsCrysOfCrystallineBreuilKisinFrameStatement.lean#L10-L12).

## 2. Fix the embedding before comparing the operators

Fix $\tau_K:K\hookrightarrow L$ and let $\iota=\operatorname{incl}_L\circ\tau_K$. Extend $\iota$ to a $\mathbb Q_\ell$-automorphism of $\Omega$ and take its inverse $\sigma$, so $\sigma\circ\iota$ is the given inclusion of $K$. If a layer seed has coefficient field $L_{m,k}$, then $L_{m,k}\supset L_0$ contains $\iota(K)$. The same $\iota$ therefore corestricts to $\tau_{m,k}:K\hookrightarrow L_{m,k}$, and **the same** $\sigma$ works for this embedding too. Thus the seed multiplicities on this component are the counts of the one prescribed multiset $J(\iota)$. The coefficient conjugation by $\sigma$ is not a conjugation of the argument $g\in G_K$. The rational lattice matrices have entries in $\mathbb Z_\ell$ and are unaffected by this coefficient conjugation.

The source also takes one $g\in G_K$ and one $z\in\mathbb C_\ell$ with no positive power equal to $1$. Their normalization is
$$
g(\xi)=\xi w,\qquad z\,\Theta(w)=1
$$
for some $w\in A_{\inf}$, so $z\ne0$. This is the particular `IsZ` scalar of the source; it should not be replaced merely by an arbitrary non-torsion scalar or by an unspecified convention for the cyclotomic character. Here is the calculation producing it. Let $u$ be the Teichmüller lift of the compatible roots of a uniformizer, $\mu=[\epsilon]-1$ the cyclotomic period difference, and $f$ the coefficient-lifted Eisenstein polynomial with $f(u)=\xi$. The period relation is $\mu=\eta^{-1}\xi\tau$ with $\eta$ a unit and $\tau$ a Breuil–Kisin period; put
$$
c=\Theta(\eta^{-1}\tau u f'(u))\ne0.
$$
Nonvanishing uses the unit $\eta$, the nonzero residues of $\tau,u$, and the nonzero derivative at the uniformizer. Choose $k$ so $1+\ell^k c$ is nonzero and not a root of unity, by the small nonzero $\ell$-adic perturbation lemma. The moving-roots theorem gives $g(u)=[\epsilon]^{\ell^k}u$ and the coefficient lifts of $f$ are fixed by $G_K$. Expand $[\epsilon]^{\ell^k}-1=\mu(\ell^k+\mu s)$ and expand $f(g(u))$ to first order in that difference. Since $\xi\mid\mu$, terms beyond the linear term disappear after dividing by $\xi$ and applying $\Theta$:
$$
\Theta\bigl(g(\xi)/\xi\bigr)=1+\ell^k c.
$$
This denotes the residue of the integral quotient $w$ just constructed, not division by $\Theta(\xi)=0$. The inverse $z=(1+\ell^k c)^{-1}$ has the required properties.

[Inverse of an embedding extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L38-L46) · [Corestriction and multiplicities on each seed](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L233-L249) · [`IsZ` normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L182-L183) · [Choice of non-torsion residue](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsGaloisElemCyclotomicPeriodNotRootOfUnity.lean#L108-L162).

## 3. One residue operator, two descriptions

Consider one rational lattice, target or layer, its de Rham frame $F$, and an adapted invariant Hodge basis $H$ for it. The source description of $H$ uses a matrix $V_H\in\mathrm{GL}_d(B_{\mathrm{dR}}^+)$, an invariant basis $Q_H$ over $B_{\mathrm{dR}}$, and nonnegative integers $p_j,q$ such that, with $x=aDp(\xi)$,
$$
x^q(Q_H)_{ij}=x^{p_j}(V_H)_{ij}.
$$
The degree is the integer $p_j-q$. The residue matrix $v_H=\theta_D(V_H)$ is invertible. The basis is supplied from the de Rham rational representation; it is not claimed to be the reduction of a Breuil–Kisin frame.

The bounded-pole theorem gives $Y,Y^\ast$ over $A_{\inf}$ with $\iota_W(Y)=\iota_W(\tau_p)^N F.T$ and $YY^\ast=\tau_p^{2N}I$. Set $y=\Theta(Y)$, $y^\ast=\Theta(Y^\ast)$ and $s=\Theta(\tau_p^{2N})\ne0$. Thus $y$ is invertible and $y^{-1}=s^{-1}y^\ast$. Let $E_g=\Theta(F.\epsilon(g))$. The operator $U$ satisfies
$$
U y=y E_g,\qquad Uv_H=v_H\operatorname{diag}(z^{p_j-q}).
\tag{1}
$$
The first identity implies $U=yE_gy^{-1}$; the second is the Hodge eigenvalue formula. To see why they are compatible, put $a_0=\Theta(\tau_p)$, $b_0=\Theta(g(\tau_p))$, and $w_0=\Theta(w)=z^{-1}$. The source compares the invariant frame-basis to $Q_H$ before reduction. It defines the intermediate matrix $V_0=aDp(\tau_p)^{-N}aDp(Y^\ast)V_H$. The key residue fact is that $v_0=\theta_D(V_0)$ is $G_K$-fixed. This is not automatic from the definition: for column $j$ the approximation argument obtains an $s_{ij}\in bk.S$ entrywise after scaling, with
$$
\ell^b\,x^{N+p_j}(V_0)_{ij}-aDp(bk.ev(s_{ij}))
\in\operatorname{Fil}^{N+p_j+1} B_{\mathrm{dR}}^+
$$
for a suitable $b$ and entry-dependent $s_{ij}$. Eisenstein divisibility descends the factor $x^{N+p_j}$ to the chart, leaving $\ell^b$ times the residue in the image of the chart at level one, hence fixed by $G_K$. Dividing by nonzero $\ell^b$ proves the residue assertion.

Now let $y_g=\Theta(gY)$, $v_g=\theta_D(g V_H)$, and let $M_g$ be the rational lattice matrix of $g$ embedded in $\mathbb C_\ell$. The source reduces the frame action, the Hodge action, and $aDp(Y)V_0=aDp(\tau_p)^N V_H$ to
$$
a_0^N M_g y_g=b_0^N y E_g,\qquad
M_g v_g\,\operatorname{diag}(w_0^{p_j})=w_0^q v_H,\qquad
y_g v_0=b_0^N v_g.
$$
Also $y v_0=a_0^N v_H$. Then $y E_g v_0=a_0^N M_g v_g$ by the first and third identities, and $U v_H=a_0^{-N} y E_g v_0=M_g v_g$. Since $w_0=z^{-1}$, this is exactly the second identity of (1). The nonzero residues $a_0,b_0$ justify the divisions. In particular (1) comes from the same $g,z$ used at every layer and the target, although their Hodge bases and dimensions can differ.

[Hodge basis fields](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L159-L180) · [Bounded poles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinPreframeBoundedPoles.lean#L13-L79) · [Comparison and fixed residues](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AdaptedBasisThetaGaloisFixedPoles.lean#L33-L132) · [Filtration congruence implies fixed residue](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ThetaGaloisFixedOfCongrBreuilKisin.lean#L16-L71) · [The residue matrix identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HodgeTateOperatorOfGaloisRelations.lean#L4-L49).

## 4. The frame link is a dimension-free estimate for the operators

Fix a requested precision $n$ and choose its layer $m\ge n$ and link $D$. Use the notation $y,y_m$ for the two residue frame matrices, $E_g,E_{g,m}$ for the residue cocycles, $P_m$ for the image of $\Pi_m$ in $\mathbb C_\ell$, and $D_\Theta=\Theta(bk.ev(D))$. Here $P_m$ is a rectangular matrix, not the local prime datum $P$. The two errors
$$
A=P_m y_m-yD_\Theta,\qquad B=E_gD_\Theta-D_\Theta E_{g,m}
$$
both have entrywise norms at most $\ell^{-n}$.

For $A$, multiply the Witt link by the common scalar $\iota_W(\tau_p)^N$. The difference now comes from $A_{\inf}$ and remains divisible by $\ell^n$ in the Witt ring. Saturation of $A_{\inf}$ inside the Witt ring transfers that divisibility to $A_{\inf}$. The residue map sends all integral entries to norm at most one and sends $\ell$ to norm $\ell^{-1}$; its restriction to $\mathbb Z_\ell$ is the given coefficient map. This proves the bound. For $B$, combine $\Pi_m\rho_m(g)\equiv\rho_\infty(g)\Pi_m$ and the Witt frame link with each frame's semilinear Galois identity. To see the congruence explicitly, work first in the Witt ring modulo $\ell^n$. Write $T,T_m$ for the frames, $D_W=bk.ev_W(D)$, and $P_W$ for $\Pi_m$ there. In this paragraph let $\varepsilon,\varepsilon_m$ denote the Witt images of the cocycles and suppress the coefficient embeddings on the representation matrices. Then
$$
T\varepsilon\,g(D_W)=\rho_\infty(g)\,g(TD_W)
 \equiv \rho_\infty(g) P_W g(T_m)
 \equiv P_W\rho_m(g) g(T_m)=P_W T_m\varepsilon_m
 \equiv T D_W\varepsilon_m.
$$
This uses that the rational matrix $P_W$ is fixed by $g$. Cancel the invertible $T$ and descend the divisibility to $A_{\inf}$. When applying $\Theta$, an entry of $bk.ev(D)$ has residue in the image of the integers of $K$ by the defining chart quotient; $g\in G_K$ fixes this residue. Thus the $g$ on the coefficient $D$ disappears **after** reduction and the bound for $B$ follows. One need not assume $g$ fixes $D_W$ itself.

All of $y,y_m,y^\ast,y_m^\ast,E_g,E_{g,m}$ have norm at most one in entry maximum norm. By (1), $\|U\|,\|U_m\|\le |s|^{-1}$ with the same $s=\Theta(\tau_p^{2N})$ for all layers. Combine the errors by the exact identity
$$
(UP_m-P_m U_m)y_m = U A + y B - A E_{g,m}.
$$
Each term on the right is bounded by $|s|^{-1}\ell^{-n}$ since $0<|s|\le1$; the ultrametric inequality does not count matrix entries or layers. Multiply by $y_m^{-1}=s^{-1}y_m^\ast$ to obtain
$$
\|UP_m-P_m U_m\|\le |s|^{-2}\ell^{-n}.
$$
Thus one may take the uniform bound $B_d=|s|^{-2}$, independent of $n,m$ and of the layer dimension. This is the compatibility input to the trace theorem; it is approximate commutation with a specific rectangular matrix, not convergence of the matrices $U_m$ to $U$ in a fixed square matrix space.

[Linked cocycles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BreuilKisinLatticeFrameCocyclesLinked.lean#L13-L76) · [Norm, residue fixedness, and saturation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ThetaConjBoundedCompatibleBreuilKisinFrames.lean#L21-L115) · [Uniform estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ThetaConjBoundedCompatibleBreuilKisinFrames.lean#L117-L228) · [Application to the specific tower](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L204-L229).

## 5. Reading a Hodge operator is a separate naturality statement

Consider a single matrix reading $(b_i,e_i)$ of a rational lattice in the target representation $r$ or in one seed $r_{m,k}$. Denote the read representation by $r_{\mathrm{rd}}$. Let $f:\Omega\hookrightarrow\mathbb C_\ell$ be inclusion after $\sigma$ and $Z:\mathbb Z_\ell\hookrightarrow\mathbb C_\ell$ the natural coefficient map. On coordinate vectors define
$$
\mathcal B(x)=\sum_i x_i f(b_i),\qquad v=(Z(e_i))_i .
$$
Here $f$ acts on matrix entries. Then $\mathcal B(v)=I$. Fix a Hodge basis for the finite model at the selected embedding, conjugate the coefficient matrices by $\sigma$, and denote its operator by $u$. If $W$ is the invertible residue basis matrix, the definition is
$$
u = W\,\operatorname{diag}(z^{h_j}) W^{-1},
\qquad h_j=p_j-q.
$$
The embedding-basis theorem constructs this basis from the $\tau$-component of the filtered de Rham module and ensures that the number of indices with $h_j=h$ is exactly $\operatorname{mult}_V(R_{\mathrm{rd}},\tau,h)$. More precisely it projects an adapted basis using the specialisation $l\otimes b\mapsto\sigma(l)b$ (with $\sigma(l)$ mapped into the local period ring); for the idempotent of the chosen $\tau$-component the specialisation is $1$ because $\sigma\circ(\operatorname{incl}\circ\tau)$ is the inclusion of $K$. A normalised element annihilating the specialisation kernel gives independence of the projected vectors, and specialised filtered spanning of the coordinate vectors gives spanning. Over a finite $K'\supset K$ whose Galois group fixes the needed conjugated coefficients, the projected basis is invariant. The basis conversion preserves the filtered degrees. These are the reasons the count applies to the chosen component, not the aggregate over all embeddings.

The naturality needed here is
$$
u\,\mathcal B(x)=\mathcal B(Ux).
\tag{2}
$$
One cannot simply deduce (2) by comparing arbitrary eigenvectors over $\mathbb C_\ell$. Use the period-ring lift of each column reading. For a column index $k$, let $B_k$ be the rectangular matrix with $i$th column the $k$th column of $f(b_i)$. Lift its entries to $B_{\mathrm{dR}}^+$ using the section $C.o$ applied to $\sigma(b_i)$. Their coefficients are fixed under the subgroup fixing a finite extension generated by those finitely many conjugated entries (intersect with $G_K$). Applying this lifted map to the $j$th $Q_H$ column gives a read vector invariant under this subgroup: equivariance is precisely `Reads.equi`, with the $\mathbb Z_\ell$ scalars fixed by $\sigma$. Applying it to the $j$th $V_H$ column gives its companion integral vector with the **same** relation involving $x^{p_j},x^q$. After $\theta_D$ the latter column is $B_k(v_H)_j$. The source characterization `IsHT` of $u$ applies to all such invariant column pairs, even after this finite enlargement, and says this residue column has eigenvalue $z^{p_j-q}$. Hence
$$
uB_kv_H=B_kv_H\operatorname{diag}(z^{p_j-q})=B_kUv_H.
$$
Cancel $v_H$ to get $uB_k=B_kU$ for every column $k$, which is (2). The target and seed $u$ are proved to satisfy `IsHT` by the diagonal adapted-basis theorem applied with the matching coefficient conjugation. Induct on the power, starting with the identity reading $\mathcal B(v)=I$, to obtain
$$
u^j=\mathcal B(U^j v)\qquad(j\ge0).
\tag{3}
$$
In a layer one uses the same $U_m$ on its lattice and a different reading for each seed. Equation (3) does not equate different seed operators as matrices; it lets their traces be compared.

[Hodge basis at a chosen embedding](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsHodgeBasisAtEmbedding.lean#L22-L74) · [Definitions of `IsHT` and `Hodge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/TrivIsCr.lean#L159-L180) · [Diagonal characterization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsHodgeTateIffDiagonalAdaptedBasis.lean#L41) · [Lifting the readings and proving (2)–(3)](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HodgeTateOperatorPowEqSum.lean#L15-L114).

## 6. From the seed traces back to multiplicities

For any seed $k$ in any layer $m$, its finite model is semistable and hence de Rham. Its embedding-basis degrees, counted with repetitions, give $J(\iota)$. By (3) and similarity to the diagonal matrix, every such reading yields exactly
$$
S_j=\sum_{h\in J(\iota)}(z^h)^j
$$
as the trace of its $j$th operator power. The proof does not silently assume a nonempty seed layer in order to assert $S_0=a$: it obtains a seed at layer $1$. If there were none, linear independence of the layer basis in the empty product would force layer rank zero. Its comparison cannot then be onto modulo $\ell$ for positive target lattice rank. And target lattice rank zero contradicts its identity reading since $a\ge1$. Thus a layer-$1$ seed exists and its zeroth power has trace $a$.

For the transfer to the target take $t_i=\operatorname{tr}(f(b_i))$ and $v=(Z(e_i))$ there, and use the analogous seed rows $t_{m,k}$ and unit vector $v_m$ in the layer. The target identity reading gives $tv=a$. The cover's unit condition gives $\|v-P_m v_m\|\le\ell^{-m}$. The trace condition gives
$$
\left\|t P_m-\sum_k f(c_{m,k})\,t_{m,k}\right\|\le\ell^{-m}.
$$
Here $c_{m,k}$ are the original layer trace coefficients, and the norm estimate survives $f$ since $\sigma$ preserves the $\ell$-adic norm and fixes the rational coefficients in $\Pi_m$. We have $\|v_m\|\le1$, the bound and commutation estimate in §4, and by (3) each $t_{m,k}U_m^jv_m=S_j$. These are precisely the hypotheses of the abstract lattice trace theorem. It yields $tU^jv=S_j$ for every $j\ge0$; no positivity or exact sum-to-one assumption is imposed on the coefficients $c_{m,k}$.

Finally use (3) for the given model $R$ of the target. If $J_R$ is its actual multiset of basis degrees at $\tau_K$, the target trace is $\sum_{h\in J_R}(z^h)^j$. Hence both multisets have the same power sums. Since $z\ne0$ has infinite multiplicative order, $h\mapsto z^h$ is injective on $\mathbb Z$ including negative degrees. In characteristic zero the multiplicity differences vanish by independence of the finitely many characters $j\mapsto(z^h)^j$ (equivalently, the Vandermonde system on the union of the two supports). Thus $J_R=J(\iota)$, and the basis's degree counts prove the asserted equality of multiplicities. The initial choice of $\tau_K$ was arbitrary.

[Nonempty layer at index 1](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L126-L151) · [Seed traces and target recovery](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean#L231-L300) · [Application of the abstract trace theorem to the cover estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TracePowEqAlongLatticeTowerCover.lean#L145-L250) · [Power sums determine the degree multiset](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MultisetEqOfPowerSumsZpowEq.lean#L12-L67).

## Where the argument fits

[`ClosedAtL.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ClosedAtL.lean#L36-L101) pulls the cover back to the local Galois group, transports its family hypotheses to the finite models above, and applies `closed_of_cover`. The [finite-model and embedding argument](a-finite-coefficient-model-retains-the-chosen-hodge-embedding.md) packages the result at each prescribed embedding. This note does not construct the starting cover, the fitted core, or the frames. It uses the invariant basis, invariant matrix ratio and approximation theorems in §3, the moving-roots and small-perturbation theorems in §2, and the specialised filtered-basis and diagonal characterization theorems in §5 as source inputs. It does not expand the abstract trace theorem or identify the crystalline Weil operator, which is a separate comparison.

*Status: source-based reconstruction draft. References point to the pinned release; this note is not an additional Lean verification or a proof of the global endpoint.*
