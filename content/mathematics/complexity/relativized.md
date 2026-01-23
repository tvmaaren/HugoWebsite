+++
date = '2026-01-22T15:24:10+01:00'
title = 'Chapter 4 Relativized computation and the polynomial hierarchy'
+++

# Relativized computation

An oracle Turing machine is a machine which has a lookup table (oracle) which has constant lookup time. This lookup table can be read from and written to. 

**Definition** Given oracle turing machine \(M\), we let \(M^B\) be the function computed using oracle \(B\).

**Definition** A set \(A\) *Turing reduces* to \(B\) denoted \(A\leq_T^p B\), if \(A=M^B\) for some machine \(M\) working in polynomial time.

**Proposition** \(A\leq_m^p B \implies A\leq_T^p B\)

**Proof**

Assume that \(A\leq_m^p B\), then there exists a polynomial time function \(f\) such that \(a\in A \iff f(a)\in B\). If we let \(M\) be the machine that computes \(f\) and then checks if it is part of the oracle, we see that \(A=M^B\).

**End Proof**

**Proposition** 
1. \(\leq_T^p\) is reflexive and transitive
2. \(A\leq_T^p \iff \overline{A}\leq_m^p \overline{B}\).
3. If \(A\in P\) then \(A\leq_m^p B\) for every set \(B\) that is not empty or equal to \(\{0,1\}^*\).
4. \(A\leq_T^p C \land B\leq_T^p C \implies A\oplus B \leq_T^p C\).
5. \(A\leq_T^p B \implies \overline{A}\leq_T^p B\).

All these properties are also met by \(\leq_m^p\) except of 5. We have this now because taking the complement of our machine \(M\) is still is a polynomial time machine.

**Proposition**
\[\text{NP}(\text{P}^{\mathcal{C}})=\text{NP}(\mathcal{C}).\]
**Proof**
\[
\begin{aligned}
\text{NP}(\text{P}^{\mathcal{C}}) &= \bigcup \{\text{NP}^C\mid C\in P^\mathcal{C}\} \\
&= \bigcup \{\text{NP}^C\mid C\in P^D \exists D\in \mathcal{C}\}\\
&= \bigcup \{\text{NP}^C\mid C\in P^D \exists D\in \mathcal{C}\}\\
&= \bigcup \{\text{NP}^{M^D}\mid \exists D\in \mathcal{C},M\text{ polynomial}\}\\
&= \bigcup \{\text{NP}^{M^D}\mid \exists D\in \mathcal{C},M\text{ polynomial},N\text{ nondeterministic polynomial}\}\\
&= \bigcup \{N^{M^D}\mid \exists D\in \mathcal{C},M\text{ polynomial},N\text{ nondeterministic polynomial}\}\\
&= \bigcup \{M^D\mid \exists D\in \mathcal{C},M\text{ nondeterministic polynomial}\}\\
&= \text{NP}^\mathcal{C}
\end{aligned}
\]
**End Proof**

# The polynomial hierarchy

We inductively define the polynomial hierarchy as follows

- \(\Sigma_0^p=\Pi_0^p=P\)
- \(\Sigma_{n+1}^p=\text{NP}(\Sigma_n^p)\)
- \(\Pi_{n}^p=\text{CO-}\Sigma_{n}^p\)
- \(\Delta_{n+1}^p=P(\Sigma_n^p)\)
- \(PH=\bigcup_{n\geq 0}\Sigma_n^p\)

Observe \(\Sigma_{n}^p,\Pi_{n}^p \subset \Delta_{n+1}^p \subset \Sigma_{n+1}^p,\Pi_{n+1}^p\)

**Proposition**
1. \(\Delta_1^p = P\)
1. \(\Pi^p_{n+1} = (\text{co-NP})(\Sigma_n^p)\)
1. \(\Sigma^p_{n+1} = \text{NP}(\Pi_n^p)\)
1. \(\Delta^p_{n+1} = \text{P}(\Pi_n^p)\)
1. \(\Sigma^p_{n+1} = \text{NP}(\Delta_{n+1}^p)\)

**Definition**
- \(\exists^{p(n)}xR(x)\iff \exists x, |x|\leq p(n) \land R(x)\) 
- \(\forall^{p(n)}xR(x)\iff \forall x, |x|\leq p(n) \implies R(x)\) 
- \(\exists \mathcal{C} := \{\{x \mid \exists^{p(|x|)}y,\langle x,y\rangle \in B\}\mid p\text{ polynomial},B\in \mathcal{C}\}\)
- \(\forall \mathcal{C} := \{\{x \mid \forall^{p(|x|)}y,\langle x,y\rangle \in B\}\mid p\text{ polynomial},B\in \mathcal{C}\}\)

**Proposition** \(\text{PH}\subseteq \text{PSPACE}\).

**Proof**
Induction
**End Proof**

**Proposition** If PH=PSPACE then PH collapses.

**Proof**

Apparently there exists problem called QBF\(\in\)PSPACE such that A\(\leq_m^p\) QBF for all A\(\in\)PSPACE. If PH=PSPACE, then QBF\(\in\Sigma_n^p\) for some n and because \(\Sigma_n^p\) is downwardly closed PSPACE=\(\Sigma_n^p\).

**End Proof**

If we take \(\text{QBF}_k\subset \text{QBF}\) as the set of true closed formulas with \(k-1\) quantifier alternations it turns out that \(\text{QBF}_k\) is \(\Sigma_k^p\). In case \(k=1\) this is clearly true as \(\text{QBF}_1=\text{SAT}\) and \(\Sigma_k^1=\text{NP}\)
