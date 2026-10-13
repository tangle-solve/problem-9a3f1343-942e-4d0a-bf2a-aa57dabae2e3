<!-- solve-problem:9a3f1343-942e-4d0a-bf2a-aa57dabae2e3 -->
# NP versus coNP

A [Tangle Solve problem](https://solve.tangle.tools/problems/9a3f1343-942e-4d0a-bf2a-aa57dabae2e3).

## What is the problem?

Determine whether NP = coNP.

Formally: NP is the class of languages L ⊆ {0,1}* such that x ∈ L has a polynomial-length certificate verifiable in polynomial time. coNP = {L : L̄ ∈ NP}, the class of complements of NP languages. The question is whether these classes coincide.

The canonical equivalent formulation: let UNSAT = {φ : φ is an unsatisfiable Boolean formula}. SAT ∈ NP; UNSAT ∈ coNP. Then NP = coNP iff UNSAT ∈ NP, i.e., iff there exists a proof system in which every unsatisfiable formula has a proof of polynomial length. More generally, by a theorem of Cook–Reckhow (1979), NP = coNP iff there exists a propositional proof system (a polynomial-time-verifiable map whose range is exactly the tautologies) in which every tautology has a polynomial-size proof. So the problem is: does there exist a "succinct certification of non-existence" for NP search problems, or equivalently polynomially-bounded proofs of tautology?

Believed answer: NP ≠ coNP. Note P ≠ NP implies NP ≠ coNP only in the contrapositive direction: NP = coNP implies... actually it implies nothing directly about P vs NP, but NP ≠ coNP ⇒ P ≠ NP (since P is closed under complement). So this is a strictly easier target than P vs NP in the sense that separating NP from coNP suffices to separate P from NP.

## Why does it matter?

A proof that NP ≠ coNP would resolve P vs NP as a corollary, since P is closed under complement. It would establish that tautologies (equivalently, unsatisfiability) have no polynomially-bounded proof system in general, giving super-polynomial lower bounds for every propositional proof system simultaneously — the central goal of proof complexity, with direct consequences for SAT solving and ILP solvers whose performance is ultimately bounded by proof-system strength. A proof that NP = coNP (unexpected) would upend cryptography and proof complexity, suggesting short certificates of unsatisfiability exist.

## What's already known?

- **Relativization barrier:** Baker, Gill, Solovov (1975) constructed an oracle A with NP^A = coNP^A and an oracle B with NP^B ≠ coNP^B (in fact a random oracle separates them, per Bennett–Hawthorne? — the random-oracle separation is standard, verify exact attribution). Thus relativizing techniques cannot resolve the question. (The census note "no oracle with insight" means: no oracle makes the answer look resolvable by current techniques.)
- **Algebrization barrier:** Aaronson–Wigderson (2008) — algebrizing techniques also provably insufficient for NP vs coNP (verify which direction is known to be barriered).
- **Natural proofs (Razborov–Rudich 1997)** apply to circuit lower bounds; a separation NP ≠ coNP would require (nonuniformly) proving circuit lower bounds for a coNP language, so natural-proof-style techniques are blocked.
- **Partial positives:** the census notes duality phenomena — LP (and semidefinite) optimization has its dual, so "min = max" statements (weak duality) are NP-certifiable both ways in restricted settings; these are heuristics for why the classes "could" collapse in structured worlds, but no evidence for the general case.
- **Proof complexity progress:** exponential lower bounds are known for specific systems: resolution (Haken 1985 for pigeonhole; Chvátal–Szemerédi for general resolution), cutting planes, Frege lower bounds are open; even super-polynomial lower bounds for Frege (and hence any proof of NP ≠ coNP) remain open. No lower bound technique known lifts to all proof systems at once.
- **Karp–Lipton:** if NP ⊆ P/poly then PH collapses to Σ₂^p; related collapse results (e.g., if NP = coNP then PH collapses to NP) show NP = coNP would have drastic consequences.

## What would count as solving it?

1. **Separation (the expected outcome):** A proof that NP ≠ coNP — e.g., an explicit language in coNP with no NP verifier, or (via Cook–Reckhow) a super-polynomial lower bound on proof length for every propositional proof system. Criterion: a rigorous, checkable proof; any accepted resolution also settles P ≠ NP.
2. **Collapse:** A proof that UNSAT has polynomial-size certificates, i.e., NP = coNP. Would be sensational; referee standard is a proof, but a plausible weaker milestone is exhibiting any "natural" proof system believed polynomially bounded (none known).
3. **Intermediate milestones** (partial credit, not full solution): super-polynomial lower bounds for Frege systems; lower bounds for NP vs coNP against restricted verifier classes (e.g., coNP ⊄ NP ∩ something); unconditional results conditional on accepted barriers (e.g., new non-relativizing technique demonstrably escaping the known barriers).

## How to start

1. Read Arora–Barak, *Computational Complexity: A Modern Approach*, chs. 3–5 for definitions, and ch. 15? (the chapter on circuit lower bounds and natural proofs — verify chapter number), plus the chapter on proof complexity if present; then Cook–Reckhow "The relative efficiency of propositional proof systems" (J. Symbolic Logic 1979) for the proof-system reformulation — this converts the problem into proving lower bounds against all proof systems.
2. Study the barriers thoroughly: Baker–Gill–Solovov (oracles), Razborov–Rudich (natural proofs), Aaronson–Wigderson (algebrization). Any attack must be explicitly non-relativizing; this kills most naive diagonalization attempts immediately.
3. Attempt a warm-up: prove a super-polynomial Frege lower bound, or even improve known lower-bound techniques beyond AC⁰[p]-type circuit classes. This is the recognized "front door" and is itself open — expect the problem to be at least as hard as it looks.
4. Main obstacle: we cannot even prove NEXP ⊄ P/poly unconditionally by these routes; NP vs coNP requires reasoning about *all* polynomial-time verifiers simultaneously, and no current technique (diagonalization, circuit complexity, arithmetization) survives the known barriers.

## Key references

- S. Cook, "The Complexity of Theorem-Proving Procedures," STOC 1971. Introduces NP-completeness via SAT; foundational for the P/NP/coNP framework. (No stable public link; see any digital library, e.g., ACM DL.)
- S. Cook, R. Reckhow, "The Relative Efficiency of Propositional Proof Systems," J. Symbolic Logic 44(1), 1979. Proves NP = coNP iff some propositional proof system is polynomially bounded; the key reformulation.
- S. Arora, B. Barak, *Computational Complexity: A Modern Approach*, Cambridge University Press, 2009 (chs. 3–5). Standard textbook treatment of NP, coNP, hierarchy, and barriers.
- T. Baker, J. Gill, R. Solovov, "Relativizations of the P =? NP Question," SIAM J. Comput. 4(4), 1975. Constructs oracles resolving P vs NP both ways; the relativization barrier. (Census lists "Solovov" — standard citation is Solovay as co-author? Verify spelling.)
- A. Razborov, S. Rudich, "Natural Proofs," J. Comput. Syst. Sci. 55(1), 1997. Shows broad circuit-lower-bound techniques fail against pseudorandom functions; blocks a large class of attacks.
- S. Aaronson, A. Wigderson, "Algebrization: A New Barrier in Complexity Theory," ACM TOCT 1(1), 2009. Shows arithmetization-based techniques also cannot resolve NP vs coNP-type questions (verify exact class coverage).
- A. Haken, "The Intractability of Resolution," Theor. Comput. Sci. 39, 1985. Exponential resolution lower bound via pigeonhole principle; the model for proof-complexity lower bounds.

## Warnings

- **Traps in logic:** NP = coNP does *not* obviously imply P = NP, but NP ≠ coNP *does* imply P ≠ NP. Do not conflate the two problems; do not claim an unconditional implication in the other direction.
- **Relativization kills most naive attacks.** Any argument that would still work relative to an arbitrary oracle is dead on arrival; check your approach against BGS oracles early.
- **Equivalent restatements matter:** attacking "short certificates for UNSAT" and "polynomially bounded proof systems" and "NP = coNP" are the same problem (Cook–Reckhow); pick whichever framing helps.
- **Do not trust a collapse intuition from LP/SDP duality** — those hold only for specially structured problems; the census's "partial worlds" note refers to structured subclasses, not evidence for NP = coNP.
- The census record attributes oracles vaguely and one citation spelling ("Solovov") may be off; verify bibliographic details before relying on them.

---
*`ALGO-000002` · unverified*

## Acceptance guidance

1. **Separation (the expected outcome):** A proof that NP ≠ coNP — e.g., an explicit language in coNP with no NP verifier, or (via Cook–Reckhow) a super-polynomial lower bound on proof length for every propositional proof system. Criterion: a rigorous, checkable proof; any accepted resolution also settles P ≠ NP.
2. **Collapse:** A proof that UNSAT has polynomial-size certificates, i.e., NP = coNP. Would be sensational; referee standard is a proof, but a plausible weaker milestone is exhibiting any "natural" proof system believed polynomially bounded (none known).
3. **Intermediate milestones** (partial credit, not full solution): super-polynomial lower bounds for Frege systems; lower bounds for NP vs coNP against restricted verifier classes (e.g., coNP ⊄ NP ∩ something); unconditional results conditional on accepted barriers (e.g., new non-relativizing technique demonstrably escaping the known barriers).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/9a3f1343-942e-4d0a-bf2a-aa57dabae2e3?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000002.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000002)
