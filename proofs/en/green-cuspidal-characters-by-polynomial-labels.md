# Green's cuspidal characters with polynomial labels

[Proof map](../../PROOF-MAP.md) · [Review status](../../STATUS.md)

## The statement used in the proof

Fix a prime $p$, an algebraic closure $\overline{\mathbb F}_p$, and the following labelling data. Let $\iota:\overline{\mathbb F}_p\to\mathbb C$ preserve multiplication and $1$ and be injective on nonzero elements. For every integer $m\ge1$, choose $\gamma_m$ of multiplicative order $p^m-1$, with

$$
\gamma_{mn}^{(p^{mn}-1)/(p^m-1)}=\gamma_m\qquad(m,n\ge1).
$$

These are the data of Lean's `LabelDatum`. The compatibility between generators at different degrees belongs to the datum. In the proof below we work at one degree at a time.

Fix an integer $d\ge1$ and write $K=\mathbb F_{p^d}\subset\overline{\mathbb F}_p$ and $G=\mathrm{GL}_d(\mathbb F_p)$. Since $\gamma_d^{p^d-1}=1$, the element $\gamma_d$ is fixed by the $p^d$th power map and lies in $K^\times$. Its order makes it a generator. For $x,z\in K^\times$, write $z=\gamma_d^a$ and set

$$
\theta_x(z)=\iota(x)^a .
$$

Changing $a$ by a multiple of $p^d-1$ leaves the value unchanged because $x^{p^d-1}=1$. This is the restriction of the project's `thetaOf` to the elements used in the formula.

Call $P\in\mathbb F_p[T]$ a label if it is monic, irreducible, of degree $d$, and $P(0)\ne0$. A cuspidal character of $G$ is the character of an irreducible complex representation with zero invariants under the unipotent radical of each proper parabolic subgroup. For `IsCusp` in the project it suffices to check the block-parabolic types $(a,d-a)$, $0<a<d$. The corresponding subgroup is

$$
U_a=\left\{\begin{pmatrix}I_a&B\\0&I_{d-a}\end{pmatrix}: B\in\operatorname{Mat}_{a\times(d-a)}(\mathbb F_p)\right\}.
$$

The operator $|U_a|^{-1}\sum_{u\in U_a}\rho(u)$ projects a representation $\rho$ onto its $U_a$-invariant vectors. Its trace is exactly the character average in the project's cuspidality test. Every proper parabolic is contained in a maximal parabolic whose unipotent radical is contained in its own. Vanishing for the maximal types therefore gives the usual condition.

**Proposition (`GlobalTheory.GLq.Green`).** For every $p$, labelling datum, and $d$ as above, there exists a family of functions $\tau_P:G\to\mathbb C$, indexed by polynomials $P\in\mathbb F_p[T]$, with the following properties on the labels.

- Each $\tau_P$ is a cuspidal character of dimension $\prod_{i=1}^{d-1}(p^i-1)$. For every root $x$ of $P$, every $A\in G$ with irreducible characteristic polynomial, and every root $z$ of that characteristic polynomial,

  $$
  \tau_P(A)=(-1)^{d-1}\sum_{i=0}^{d-1}\theta_x(z^{p^i}).
  $$

- Two labels with the same character are equal, and every cuspidal character of $G$ occurs.

All the roots in the formula belong to $K^\times$. The nonzero constant term is part of the definition of a label. For the characteristic polynomial of $A$ it follows from the invertibility of $A$.

## Classical input

We use Green's classification and character formula for the finite general linear group in the following form. A multiplicative character $\vartheta:K^\times\to\mathbb C^\times$ is regular if the $d$ characters $\vartheta^{p^i}$, $0\le i<d$, are distinct. Regular characters, modulo the action $\vartheta(z)\mapsto\vartheta(z^p)$, parametrize the cuspidal characters $\chi_\vartheta$ of $G$ bijectively. The degree is $\chi_\vartheta(1)=\prod_{i=1}^{d-1}(p^i-1)$. If $A\in G$ has irreducible characteristic polynomial with root $z\in K^\times$, then

$$
\chi_\vartheta(A)=(-1)^{d-1}\sum_{i=0}^{d-1}\vartheta(z^{p^i}).
$$

The original character theorem is Green, *The characters of the finite general linear groups*, §8, Theorem 14. Prasad, §2 and Theorem 2, gives the cuspidal classification and a formula from which the displayed cases follow. At $A=1$ the kernel dimension in that formula is $d$ and the generated field has size $p$. When the characteristic polynomial is irreducible, the $d$ eigenvalues are distinct, so the kernel dimension is one and the sum runs over the $d$ conjugates of $z$. [Green (1955)](https://www.ams.org/tran/1955-080-02/S0002-9947-1955-0072878-2/S0002-9947-1955-0072878-2.pdf) · [Prasad (2000), §2](https://www.math.iitb.ac.in/~dprasad/imrn.pdf#page=3)

## Proof

Put $M=p^d-1$. A character on the cyclic group $K^\times$ is determined by its value on $\gamma_d$, which can be any complex $M$th root of unity. The map $x\mapsto\iota(x)$ is an injection from $K^\times$ into those roots of unity and both sets have $M$ elements. Thus $x\mapsto\theta_x$ is a bijection onto the characters of $K^\times$. Moreover, for every $j\ge0$,

$$
\theta_{x^{p^j}}(z)=\theta_x(z)^{p^j}=\theta_x(z^{p^j}).
$$

In particular, the Frobenius orbit of $\theta_x$ has the same length as that of $x$. The Frobenius orbit of $x\in K$ consists of the roots of its minimal polynomial over $\mathbb F_p$, and has length equal to its degree. A root $x$ of a label therefore gives a regular character $\theta_x$. Conversely, a regular character is $\theta_x$ for a unique $x\in K^\times$ of degree $d$, whose minimal polynomial is a label.

For each label $P$, choose one root $x_P$ and set $\tau_P=\chi_{\theta_{x_P}}$. Extend the family by zero on the other polynomials. Another root has the form $x_P^{p^j}$, so the classical classification gives the same cuspidal character for either choice. It also gives the stated dimension. If $x=x_P^{p^j}$ and $z$ is a root of the characteristic polynomial of $A$, then

$$
\sum_{i=0}^{d-1}\theta_x(z^{p^i})
=\sum_{i=0}^{d-1}\theta_{x_P}(z^{p^{i+j}})
=\sum_{i=0}^{d-1}\theta_{x_P}(z^{p^i}).
$$

The last equality reindexes the full orbit, using $z^{p^d}=z$. Thus the classical value formula gives the project's value for every allowed $x,z$.

If $\tau_P=\tau_{P'}$, the classical classification puts $\theta_{x_P}$ and $\theta_{x_{P'}}$ in the same Frobenius orbit. By the equivariant bijection above, $x_P$ and $x_{P'}$ are then conjugate over $\mathbb F_p$ and have the same minimal polynomial, so $P=P'$. Finally, if $\chi$ is cuspidal, write $\chi=\chi_\vartheta$ with $\vartheta$ regular. The bijection gives $x\in K^\times$ with $\vartheta=\theta_x$, and regularity forces the minimal polynomial $P$ of $x$ to have degree $d$. Its chosen root $x_P$ is conjugate to $x$, so $\tau_P=\chi$. This proves all the assertions.

## Lean correspondence and review

- The labelling datum, cuspidality test, and theorem are `LabelDatum`, `IsCusp`, `IsCuspOf`, and `Green`. [Lean definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/LabelDatum.lean#L47-L112)
- The cyclic-group bijection and regularity test are `th_inj`, `th_surj`, and `regular_iff`. The root reindexing uses `sum_range_eq_roots` and `thetaOf_pow`. The construction, uniqueness and exhaustion of the polynomial labels are the three parts of `GlobalTheory.GreenBridge.green_of_regular`. [Lean proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SumRangeEqRoots.lean#L137-L304)
- The published starting statement is `GlobalTheory.Published.GreenRegularCharacters`. The main Lean proof supplies it via `GlobalTheory.greenRegularCharacters_holds`. Its last step proves exhaustion of the cuspidal characters by counting, using the construction for regular characters in every rank up to $d$. The present note takes the classical theorem as its starting point. O’Desky's catalogue was used to locate and compare that statement. [The exhaustion argument](counting-exhausts-the-cuspidal-characters.md) · [Lean proof of the starting statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GreenCuspidalCharsByRegularCharsProof.lean#L137) · [O’Desky catalogue entry](https://andrewodesky.com/rh/s/finite-field-cuspidals.html)
- At the main proof junction, `shape_closed_link_n_of_green` supplies the comparison template from this finite-field input. The definite-side construction supplies the data to which the template applies, giving `TopG`. [Use in the main proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/TopPlug.lean#L12-L18)

The deduction was checked against the pinned Lean source for this draft. Lean was not recompiled for this note. No named human review is recorded.
