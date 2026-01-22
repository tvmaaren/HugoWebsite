+++
date = '2026-01-21T13:36:43+01:00'
title = 'Chapter 11 Proof Complexity'
+++

We know that any propositional formula has a proof. Now we are interested if every propositional formula has a "short" proof. Where "short" means polynomial given the size of the propositional formula. 

<!--more-->

# 11.1 Propositional proof systems

We let VALID be the set of all valid propositional formulas. The difference between this and SAT is that with SAT we required the formula to have an assignments such that the formula is true, but with VALID we require it to be true for all assignments. We know that SAT is NP. From this we can quite easily show that VALID is co-NP. Recall that co-NP are all the problems with which a certificate can be determine in polynomial if the input is not part of the problem. We can basically say that a problem is in NP if and only if it's complement is CO-NP. Observe that the complement of VALID is equivalent to SAT, because we only need to give one input to show that a formula is not valid, thus VALID \(\in\) co-NP. If VALID \(\in\) NP this would imply co-NP=NP which seems unlikely. Hence it is likely that VALID $\notin$ NP meaning that not every true propositional formula has a short proof.

**Definition** A *propositional proof system* is any polynomial time computable function \(F:\{0,1\}^*\to \text{VALID}\).

**Remark** If we would not require \(F\) to be polynomial we would have too much freedom in choosing \(F\). Let us say that for a propositional formula \(\varphi\) we have a polynomial representation \(\rho(\varphi)\), then we can simply define \(F(x)=\varphi\) if \(x=\rho(\varphi)\) for some formula \(\varphi\) and otherwise \(F(x)=\top\) where \(\top\) is the trivial valid propositional formula.

Here we understand for \(x\in \{0,1\}^*\) to be a proof that \(F(x)\) is correct.

**Remark** We can require without loss of generality that \(F\) is surjective. Note that VALID and \(\{0,1\}^*\) are both countably infinite. We can therefore create a new function \(F'\) defined as \(F'(1,x)=F(x)\) and \(F'(0,x)=\text{The }x\text{'th element of VALID}\). Note that \(F'\) is surjective and it has the same complexity for elements in \(\text{im}(F)\).

The simplest prove system is a prove table, but then prove size grows exponentially.

As stated earlier if NP\(\neq\)co-NP then it cannot be the case that every propositional formula has a polynomial proof. Thus for any propositional proof system \(F\) and any \(c\) there must exist a \(\varphi\in \text{VALID}\) such that \(F(x)\neq \varphi\) for all \(x\in \{0,1\}^{|\phi|^c}\). Then it would trivially be the case that any proposition has a polynomially sized proof.

\[\forall F \forall c \exists \varphi \in \text{VALID}\forall x\in \{0,1\}^{|\varphi|^c}(F(x)\neq \varphi).\]

**Theorem** The above statement is equivalent to NP\(\neq\) co-NP

**Proof**
First assume that NP\(\neq\)co-NP. Then either SAT\(\notin\)co-NP or VALID\(\notin\)NP which are both equivalent to VALID\(\notin\)NP. Meaning that for every nondeterministic turing machine \(T\) for VALID and c there exists a formula \(\varphi\) that takes more than \(n\) steps to compute. Given a propositional proof system \(F\) we can give a nondeterministic turing machine that nondeterministicly picks an element of \(x\in\{0,1\}^*\) and check if \(F(x)=\varphi\). If this is the case we accept. By what we said earlier for all \(c\) there exists a \(\varphi\) that takes more than \(n\) steps to compute implying that if \(F(x)=\varphi\), that \(F(x)\) takes superpolynomial time to compute in terms of of \(\varphi\). Because \(F(x)\) takes polynomial time to compute in terms of \(x\) this implies that \(x\) must have superpolynomial size in therms of \(\varphi\)

For the converse assume that NP=co-NP, then we have VALID\(\in\)NP meaning that there exists a nondeterministic turing machine that accepts elements in VALID in polynomial time. I can now define F as follows. As input F takes \((\varphi,c\) where \(\varphi\) is a propositional formula and \(c\) a polynomially sized certificate. Then we can check in polynomial time using our turing machine that certificate \(c\) accepts \(\varphi\) in polynomial time. If it accepts we simply say \(F(\varphi,c)=\varphi\) and otherwise \(F(\varphi,c)=\top\). 

**End Proof**

**Above formula is equivalent to NP\(\neq\)co-NP (11.4.3)**

# 11.2 Pidgeon hole principle

The pidgeon hole principle is the idea that if there are \(m\) pidgeons in
\(n\) holes where \(m>n\) then one hole has more than one pidgeon.
We will now formulate this principle as a boolean formula. Note that because we will only be looking at finite sets we can freely use \(\exists\) and \(\forall\) as a substitute for just using a lot of \(\land\)'s and \(\lor\)'s. For \(1\leq i\leq n\) and \(1\leq j\leq m\) \(x_{i,j}\) will have the meaning pidgeon \(i\) sits in hole \(j\). 

\[\exists i,\exists i'\neq i, \exists j, x_{i,j}\land x_{i',j}\] 
It was once believed that this statement would only have superpolynomial size proofs, but this turned out to be incorrect.
