# Notes on Pratt Trees

Recursive prime trees, arithmetic coordinates, generating polynomials, probability models, and a new Hadamard-type arithmetic on the natural numbers.

This repository collects a connected series of research notes built around **Pratt trees**. A Pratt tree starts with a prime \(p\), factors \(p-1\), and repeats the same process below every prime divisor. For a general positive integer, the corresponding **Pratt forest** is obtained from the Pratt trees of its prime factors, with multiplicity.

The central idea of the project is that these recursive trees can be converted into several useful mathematical languages:

- sparse arithmetic coordinates;
- recursively defined polynomials;
- combinatorial generating functions;
- finite probability spaces;
- multivariate root-label models;
- and a new coordinatewise product on natural numbers.

The manuscripts are written as self-contained research notes, but they are designed to be read together. Readers interested in arithmetic, combinatorics, algebra, probability, Galois theory, or experimental mathematics are warmly invited to explore them.

---

## Start here

A quick example already shows the three main viewpoints.

For the prime \(5\),

\[
5-1=2^2,
\]

so the Pratt tree of \(5\) has one root labelled \(5\) and two terminal children labelled \(2\).

This gives:

- the Pratt-coordinate vector
  \[
  M(5)=2e_2+e_5;
  \]
- the recursive polynomial
  \[
  f_5(x)=1+x^2;
  \]
- two complete fronts: either stop at the root \(\{5\}\), or select both terminal vertices \(\{2,2\}\).

The same object can therefore be read arithmetically, algebraically, combinatorially, or probabilistically.

---

## The manuscripts

| Manuscript | Main theme | Suggested audience |
|---|---|---|
| [Complete Node Fronts of Pratt Forests](./Complete_Node_Fronts_of_Pratt_Forests_Probabilistic.pdf) | A direct combinatorial and probabilistic interpretation of the polynomials \(f_n(x)\) | Readers who want the most concrete introduction |
| [Pratt Coordinates for Natural Numbers and Monic Rational Polynomials](./pratt_polynomial_coordinates.pdf) | Reconstruction formulas, polynomial Pratt coordinates, Hilbert-space embeddings, and Mason–Stothers | Number theorists and algebraists |
| [Hadamard–Pratt Arithmetic](./Hadamard-Pratt_Arithmetic.pdf) | Coordinatewise multiplication of Pratt vectors, a new product on \(\mathbb N\), semiring structure, completion, and spectrum | Readers interested in algebraic structure and new arithmetic operations |
| [Root-Label Fields on Pratt Forests](./Root_Label_Fields_on_Pratt_Forests_v0.3_empirically_verified.pdf) | A multivariate synthesis: complete fronts, coordinate transport, arithmetic fibres, monodromy, inequalities, and probability geometry | Readers looking for the broadest and most application-oriented treatment |

---

## Recommended reading paths

### A gentle first reading

1. **Complete Node Fronts of Pratt Forests**
2. **Hadamard–Pratt Arithmetic**
3. **Pratt Coordinates for Natural Numbers and Monic Rational Polynomials**
4. **Root-Label Fields on Pratt Forests**

This route begins with finite trees and explicit generating functions before moving to the more structural algebra.

### Arithmetic and algebra

1. **Pratt Coordinates for Natural Numbers and Monic Rational Polynomials**
2. **Hadamard–Pratt Arithmetic**
3. **Root-Label Fields on Pratt Forests**

### Combinatorics and probability

1. **Complete Node Fronts of Pratt Forests**
2. Sections on front statistics and positive root-label fields in **Root-Label Fields on Pratt Forests**

### Galois theory and monodromy

1. The polynomial family in **Pratt Coordinates for Natural Numbers and Monic Rational Polynomials**
2. The monodromy applications in **Root-Label Fields on Pratt Forests**

---

# 1. Pratt trees, forests, and coordinates

Let \(p\) be prime.

- The Pratt tree \(T_2\) consists of one vertex labelled \(2\).
- For odd \(p\), factor
  \[
  p-1=\prod_q q^{v_q(p-1)}.
  \]
  The root is labelled \(p\), and for every prime divisor \(q\mid p-1\), it has \(v_q(p-1)\) children carrying copies of \(T_q\).

For

\[
n=\prod_p p^{v_p(n)},
\]

the Pratt forest \(F_n\) is the disjoint union of \(v_p(n)\) copies of \(T_p\).

The **Pratt exponent** \(m_q(n)\) counts all vertices labelled \(q\) in \(F_n\). The full Pratt vector is

\[
M(n)=(m_q(n))_{q\in\mathbb P}.
\]

Unlike the ordinary valuation vector, \(M(n)\) records not only the prime factors of \(n\), but also the full recursive multiplicity profile of the factorizations below them.

The coordinates are completely additive:

\[
M(ab)=M(a)+M(b).
\]

Thus ordinary multiplication of integers becomes vector addition.

---

# 2. The recursive polynomial family

Define

\[
f_1(x)=1,\qquad f_2(x)=x,
\]

and for every odd prime \(p\),

\[
f_p(x)=1+\prod_{q\mid p-1} f_q(x)^{v_q(p-1)}.
\]

For arbitrary

\[
n=\prod_p p^{v_p(n)},
\]

set

\[
f_n(x)=\prod_p f_p(x)^{v_p(n)}.
\]

Basic properties include

\[
f_{ab}(x)=f_a(x)f_b(x)
\]

and

\[
f_n(2)=n.
\]

The family therefore turns multiplication of positive integers into multiplication of monic polynomials while retaining the recursive Pratt structure.

---

# 3. Complete fronts and the meaning of \(f_n(x)\)

A **node front** of a rooted forest is an antichain: it never contains both a vertex and one of its descendants. A front is **complete** when it meets every root-to-leaf path exactly once.

For a finite rooted tree \(T\), let \(C_T(x)\) count complete fronts by the number of selected leaves. If the root has child-subtrees \(T_1,\dots,T_k\), then

\[
C_T(x)=1+\prod_{i=1}^k C_{T_i}(x),
\]

while disjoint union of forests corresponds to multiplication.

Since the leaves of a Pratt forest are exactly the vertices labelled \(2\), one obtains

\[
f_n(x)=\sum_{A\in \operatorname{CF}(F_n)}
 x^{\#\{v\in A:\ell(v)=2\}}.
\]

So the coefficient of \(x^j\) counts complete fronts selecting exactly \(j\) terminal \(2\)-vertices.

After normalization,

\[
G_n(s)=\frac{f_n(s)}{f_n(1)}
\]

is the probability generating function of the number of selected terminal \(2\)-vertices in a uniformly random complete front.

The manuscript derives:

- exact probability laws;
- expectation and variance;
- factorial moments and cumulants;
- independent-sum decompositions under multiplication of integers;
- complete additivity of the mean, variance, and every cumulant.

The statistic is a **front-width statistic**, not the height of a Pratt tree and not the cost of a primality certificate.

---

# 4. Numerical and polynomial reconstruction

The numerical Pratt coordinates satisfy a telescoping reconstruction formula of the form

\[
n=\prod_{p\in\mathbb P}
\left(\frac{p}{p-1}\right)^{m_p(n)}.
\]

The polynomial-coordinate manuscript develops an analogue for monic rational polynomials. For a monic irreducible polynomial \(\varphi\), a predecessor operation \(D\varphi\) is introduced, and recursive polynomial Pratt exponents \(M_\varphi(f)\) are defined.

The resulting reconstruction has the form

\[
f=\prod_\varphi
\left(\frac{\varphi}{D\varphi}\right)^{M_\varphi(f)}.
\]

Among the main consequences are:

- sparse coordinate embeddings for positive integers and monic rational polynomials;
- multiplicative-to-additive Hilbert-space embeddings;
- irreducibility of the prime-index polynomials \(f_p\);
- recovery of the numerical formula by specialization at \(x=2\);
- a Pratt-coordinate proof of the Mason–Stothers theorem.

The manuscript also explains an important limitation: the terminal coordinate plays a distinguished role because it equals polynomial degree. Replacing it naively by an arbitrary internal coordinate is false. A valid capacity bound is proved instead.

The possible transfer to the integer \(abc\) problem remains obstructed by the **addition defect**

\[
f_a+f_b-f_{a+b}.
\]

No classical integer \(abc\) theorem is claimed.

---

# 5. Hadamard–Pratt arithmetic

The newest focused development asks a simple question:

> If two natural Pratt vectors are multiplied coordinate by coordinate, is the result again the Pratt vector of a natural number?

For arbitrary nonnegative vectors, the answer is no. Natural Pratt vectors satisfy recursive boundary inequalities, and the manuscript proves that this constrained cone is closed under the Hadamard product.

For vectors \(x=(x_p)\) and \(y=(y_p)\), define

\[
(x\circ y)_p=x_py_p.
\]

The main closure theorem states that

\[
M(a)\circ M(b)=M(c)
\]

for a unique \(c\in\mathbb N\). This defines the **Hadamard–Pratt product**

\[
a\star_P b=c.
\]

Equivalently,

\[
m_p(a\star_P b)=m_p(a)m_p(b)
\]

for every prime \(p\).

## Explicit prime exponents

The ordinary exponent of a prime \(q\) in \(a\star_P b\) is

\[
v_q(a\star_P b)
=
 m_q(a)m_q(b)
-
\sum_p v_q(p-1)m_p(a)m_p(b).
\]

The expression looks like a difference, but the Hadamard-closure theorem proves that it is always a nonnegative integer for natural inputs.

## Semiring structure

Define

\[
a\oplus_P b:=ab,
\qquad
 a\otimes_P b:=a\star_P b.
\]

Then \(\mathbb N\) becomes a commutative semiring without multiplicative identity:

- ordinary multiplication acts as the additive operation;
- \(1\) is the additive zero;
- \(\star_P\) is associative and commutative;
- \(1\) is absorbing for \(\star_P\);
- \(\star_P\) distributes over ordinary multiplication;
- no natural number has the infinite Pratt support required to be a \(\star_P\)-identity.

## Forest interpretation

The two products have complementary meanings:

| Integer operation | Pratt-coordinate operation | Forest interpretation |
|---|---|---|
| \(ab\) | \(M(a)+M(b)\) | disjoint union |
| \(a\star_P b\) | \(M(a)\circ M(b)\) | multiplicative overlap of shared labels |

The support satisfies

\[
\operatorname{supp}M(a\star_P b)
=
\operatorname{supp}M(a)\cap\operatorname{supp}M(b).
\]

## Small examples

\[
3\star_P5=4,
\]

because the two Pratt trees share only the terminal label \(2\).

\[
5\star_P5=20,
\qquad
7\star_P7=28,
\qquad
7\star_P11=64,
\qquad
12\star_P18=1152.
\]

The values can be much larger than either input and are generally very different from ordinary products.

## Direct algorithm

Given \(a,b\in\mathbb N\):

1. Compute \(M(a)\) and \(M(b)\).
2. Form \(z_p=m_p(a)m_p(b)\).
3. Apply the Pratt boundary:
   \[
   e_q=z_q-\sum_p v_q(p-1)z_p.
   \]
4. Return
   \[
   a\star_P b=\prod_q q^{e_q}.
   \]

The closure theorem guarantees \(e_q\ge 0\).

## Completion and spectrum

After Grothendieck completion, the coordinate system becomes the nonunital ring

\[
\mathbb Z^{(\mathbb P)}
\]

with pointwise multiplication. Equivalently, this transports a ring structure to \(\mathbb Q_{>0}\), where ordinary multiplication plays the role of addition.

The canonical unitization is the ring of eventually constant integer sequences. Its prime spectrum is

\[
\operatorname{Spec}(\widehat R_P)
\cong
(\mathbb P\cup\{\infty\})\times\operatorname{Spec}(\mathbb Z).
\]

This classification is explicit, but it also reveals a limitation: the diagonal ring alone does not remember the directed ancestry relation \(q\mid p-1\). That information remains in the natural Pratt cone and in the boundary or transition operator.

The manuscript explicitly makes **no claim of priority** for the Hadamard construction; its aim is to record the structure, proofs, examples, and consequences in a reusable form.

---

# 6. Root-label fields and the master polynomial

The largest manuscript introduces a joint root-label generating polynomial

\[
\mathcal M_n((z_{p,q})),
\]

where

- the first index \(p\) records the root type of a component;
- the second index \(q\) records the label of a selected vertex.

It unifies two complementary marginal viewpoints.

## View A: root-separated evaluation

Each root-prime type receives its own variable. This view is suited to:

- arithmetic fibres;
- Euler products;
- Galois-theoretic questions;
- monodromy and branched covers.

## View B: fully label-marked fronts

Each selected prime label receives its own variable, independently of the root component. This view is suited to:

- complete-front statistics;
- exact label distributions;
- means and covariances;
- conservation laws.

## Four main applications

The manuscript is organized around four concrete outputs.

### 1. Exact front statistics

The master polynomial yields exact distributions, expectations, covariances, Gram matrices, and Newton polytopes for selected labels in complete fronts.

### 2. Coordinate transport

The incidence matrix

\[
C_{q,p}=m_q(p)
\]

transports ordinary prime-factor data to full recursive Pratt data:

\[
m(n)=Cv(n).
\]

This allows large families of Pratt forests to be studied without redrawing every tree.

### 3. Arithmetic fibres

The root-evaluation family contains every completely multiplicative arithmetic function as an algebraic fibre. The Liouville function appears from a distinguished choice of fibre values, and the prime number theorem becomes a cancellation statement for the corresponding partial-sum polynomials.

This is an exact reformulation, not a new proof of the prime number theorem.

### 4. Galois groups and monodromy

The recursion

\[
f_p(X)-1=
\prod_{q\mid p-1}f_q(X)^{v_q(p-1)}
\]

turns the factorization of \(p-1\) into branching data for the cover \(f_p(X)-T\). Discriminants and functional decompositions give practical tests for symmetric or imprimitive monodromy.

## Probability and information geometry

For positive parameters, the finite front models become exponential families. Logarithmic derivatives give expectations and covariances, while Hessians produce Fisher-information and Gram matrices.

Terms such as *field*, *energy*, *temperature*, *partition function*, *state*, *susceptibility*, *density matrix*, and *modular Hamiltonian* are used as precise mathematical analogies only. The manuscript does not claim that the constructions describe a physical system.

---

# 7. What is proved, what is computed, and what remains open

These notes deliberately distinguish three levels of evidence.

## Proved statements

The manuscripts include proofs of, among other things:

- numerical and polynomial reconstruction formulas;
- complete additivity of Pratt coordinates;
- the complete-front interpretation of \(f_n(x)\);
- the induced probability generating functions and moment formulas;
- irreducibility of the prime-index polynomials \(f_p\);
- the Pratt-coordinate form of Mason–Stothers;
- the intrinsic boundary characterization of the natural Pratt cone;
- Hadamard closure of natural Pratt vectors;
- the semiring laws for \(\star_P\);
- the rational completion and spectrum of the canonical unitization;
- multivariate coordinate-transport and reconstruction identities.

## Computational checks

The root-label manuscript contains a reproducibility and verification ledger. Finite symbolic and numerical checks are used to detect errors and test examples.

A recorded `PASS` means that a stated finite test found no counterexample in its declared range. It does **not** replace a proof and does not establish an asymptotic result.

## Open directions

The manuscripts propose a broad research programme, including:

- classification and asymptotics of \(a\star_P b\) in special families;
- interaction of \(\star_P\) with divisibility and the Pratt order;
- operator algebras retaining both diagonal coordinates and the transition operator;
- a polynomial analogue of Hadamard closure;
- Pratt-sensitive geometric spectra;
- characterization of the image of polynomial Pratt coordinates;
- transition matrices and polynomial Pratt orders;
- Galois information encoded by polynomial Pratt vectors;
- the addition defect and modified \(abc\)-type questions;
- Newton polytopes of the root-label master polynomial;
- exact rank of the Fisher metric;
- recoverability of a Pratt forest from its generating polynomials;
- density questions for symmetric, Morse, or decomposable Pratt polynomials;
- critical-value collisions and discriminant factorization;
- analytic properties of Pratt-deformed zeta functions;
- infinite-dimensional limit geometry.

---

# 8. A compact conceptual map

```text
ordinary valuations v(n)
          |
          |  recursive incidence transport
          v
Pratt coordinates M(n)  <---->  Pratt forests F_n
          |                         |
          |                         | complete fronts
          |                         v
          |                    generating polynomial f_n(x)
          |                         |
          |                         | normalize at x = 1
          |                         v
          |                    finite probability law
          |
          | coordinatewise product
          v
Hadamard–Pratt arithmetic a ★_P b
```

A second bridge connects the integer and polynomial theories:

```text
monic polynomial Pratt coordinates
          |
          | specialize to the family f_n
          v
recursive polynomials f_n(x)
          |
          | evaluate at x = 2
          v
positive integers n
```

---

# 9. Why read these notes?

The project offers several unusual connections:

- a recursively enriched coordinate system for ordinary integers;
- a polynomial family satisfying \(f_n(2)=n\);
- a direct interpretation of polynomial coefficients as counts of tree cuts;
- additive arithmetic functions arising as moments and cumulants;
- a natural cone closed under both addition and coordinatewise multiplication;
- a new semiring operation on \(\mathbb N\);
- a bridge from recursive factorization trees to Mason–Stothers;
- a multivariate framework linking combinatorics, probability, arithmetic fibres, and monodromy.

Some readers may be drawn to the elementary examples, others to the algebraic structures or open problems. The manuscripts are intended to make all of these entry points possible.

---

# 10. Status of the project

The files in this repository are research notes and evolving drafts dated August 2026.

- They are not presented as a finished monograph.
- They have not been advertised here as peer-reviewed publications.
- Some parts are foundational and fully proved.
- Some parts formulate open research directions.
- Computational evidence is labelled separately from proof.
- Priority is not claimed for the Hadamard construction.
- Physical terminology in the root-label manuscript is explicitly analogical.

Critical reading, independent verification, corrections, references to related work, and suggestions for clearer exposition are welcome.

---

# 11. How to cite

Please cite the individual manuscript you use, including its title, author, version, and date as printed in the PDF.

Current files:

- Orges Leka, *Pratt Coordinates for Natural Numbers and Monic Rational Polynomials: Reconstruction, Hilbert-Space Embeddings, and a Pratt-Coordinate Form of Mason–Stothers*, Version 0.2, August 3, 2026.
- Orges Leka, *Hadamard–Pratt Arithmetic: A Coordinatewise Product on Pratt Coordinates, a Semiring on \(\mathbb N\), and the Spectrum of Its Unitization*, Draft, August 4, 2026.
- Orges Leka, *Complete Node Fronts of Pratt Forests: Generating Polynomials and a Probabilistic Interpretation of \(f_n(x)\)*, August 5, 2026.
- Orges Leka, *Root-Label Fields on Pratt Forests: An Application-First Multivariate Theory of Complete Fronts, Coordinate Transport, Arithmetic Fibres, and Monodromy*, Version 0.3, August 6, 2026.

---

# 12. Feedback and discussion

Questions that are especially useful include:

- Is a proof unclear or missing a hypothesis?
- Is a construction already known under another name?
- Can an example be simplified or strengthened?
- Can one of the open problems be connected to an existing theory?
- Are there computational counterexamples outside the tested ranges?
- Can the notation or reading order be improved?

Please use GitHub issues or discussions to report corrections, related references, computational observations, and possible extensions.

---

## Invitation

These notes begin with a very elementary recursive object—the factorization of \(p-1\)—and follow it into several different areas of mathematics. The aim of this repository is not only to record results, but to make the underlying structures visible enough that other readers can test them, reinterpret them, and develop them further.

**Choose the manuscript closest to your interests and start reading.**
