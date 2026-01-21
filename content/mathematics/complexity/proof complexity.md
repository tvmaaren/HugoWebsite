+++
date = '2026-01-21T13:36:43+01:00'
title = 'Proof Complexity'
+++

We know that any propositional formula has a proof. Now we are interested if every propositional formula has a "short" proof. Where "short" means polynomial given the size of the propositional formula. 

<!--more-->

# 11.1 Propositional proof systems

We let VALID be the set of all valid propositional formulas. The difference between this and SAT is that with SAT we required the formula to have an assignments such that the formula is true, but with VALID we require it to be true for all assignments. We know that SAT is NP. From this we can quite easily show that VALID is co-NP. Recall that co-NP are all the problems with which a certificate can be determine in polynomial if the input is not part of the problem. We can basically say that a problem is in NP if and only if it's complement is CO-NP. Observe that the complement of VALID is equivalent to SAT, because we only need to give one input to show that a formula is not valid, thus VALID \(\in\) co-NP. If VALID \(\in\) NP this would imply co-NP=NP which seems unlikely. Hence it is likely that VALID $\notin$ NP meaning that not every true propositional formula has a short proof.

**Definition** A *propositional proof system* is any polynomial time computable function \(F:\{0,1\}^*\to \text{VALID}\).

Here we understand for \(x\in \{0,1\}^*\) to be a proof that \(F(x)\) is correct.

**Remark** We can require with loss of generality require that \(F\) is surjective. **Show this (Exercise 11.4.2)**

The simplest prove system is a prove table, but then prove size grows exponentially.

As stated earlier if NP\(\neq\)co-NP then it cannot be the case that every propositional formula has a polynomial proof. Thus for any propositional proof system \(F\) and any \(c\) there must exist a \(\varphi\in \text{VALID}\) such that \(F(x)\neq \varphi\) for all \(x\in \{0,1\}^{|\phi|^c}\). 

\[\forall F \forall c \exists \varphi \in \text{VALID}\forall x\in \{0,1\}^{|\varphi|^c}(F(x)\neq \varphi).\]

**Above formula is equivalent to NP\(\neq\)co-NP (11.4.3)**

# 11.2 Pidgeon hole principle

The pidgeon hole principle is the idea that if there are \(m\) pidgeons in
\(n\) holes where \(m>n\) then one hole has more than one pidgeon.
We can formulate this principle as a boolean formula as follows **(11.4.4)**. It was once believed that this statement would only have superpolynomial size proofs, but this turned out to be incorrect.
