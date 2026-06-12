# CatMAP — Microkinetic Modeling & Volcano Analysis
## Based on: "Computational Study of CO₂ Hydrogenation to Methanol via the Formate Pathway"
### (Suchetan Karloopia, NIT Srinagar, June 2026)

> **Exam pattern from midterm:** Given a catalytic reaction → identify descriptors, transition states, approximations, rate-limiting steps, and interpret a volcano plot.  
> This section teaches you exactly how to answer such questions for **any** heterogeneous catalytic system.

---

## PART 1 — CATMAP FRAMEWORK: CORE CONCEPTS

### 1.1 What is CatMAP?

CatMAP (**Cat**alysis **M**icrokinetic **A**nalysis **P**ackage) is a Python-based software framework developed by Nørskov's group at Stanford (Medford et al., 2015) that:

1. Takes a **reaction network** (elementary steps) as input
2. Uses **linear scaling relations** + **BEP correlations** to estimate all energy barriers from just 2 descriptor energies
3. Solves **mean-field microkinetic equations** to get TOF (turnover frequency) at every descriptor point
4. Outputs **volcano plots** — maps of activity vs. descriptor energies

**Core philosophy:** Reduce the dimensionality of catalyst screening from N unknowns (one per surface intermediate) to just **2 descriptors** that parameterize everything else through linear scaling.

---

### 1.2 The Sabatier Principle and the Volcano Shape

The **Sabatier principle** states:

> The best catalyst binds intermediates **not too strongly, not too weakly**.

- **Too weak binding** (right side of volcano): reactants don't adsorb → rate limited by adsorption/activation
- **Too strong binding** (left side of volcano): products/intermediates don't desorb → surface poisoning

This produces the characteristic **volcano shape** when TOF is plotted against a binding energy descriptor.

**Example — CO₂ Hydrogenation:**
- Ag (weak binding): CO₂* adsorption endergonic → inactive
- Ni/Co (strong binding): CH₃O* deep well → surface poisoning → inactive
- Cu (near apex): balanced binding → highest TOF

---

### 1.3 Descriptors

**Definition:** A descriptor is a small set of adsorption energies that, through linear scaling relations, can predict the adsorption energies of all other surface intermediates in the reaction network.

**Why only 2 descriptors work:** The d-band center of transition metals correlates with all adsorbate binding energies, and adjacent adsorbates scale linearly with each other.

**Choice of descriptors for CO₂→MeOH:**

| Descriptor | Physical meaning | Units |
|-----------|-----------------|-------|
| E_f(CO*) | Formation energy of CO adsorbed on surface | eV |
| E_f(O*) | Formation energy of O adsorbed on surface | eV |

**Why CO* and O*?**
- CO* represents the carbon chemistry (how strongly C-containing species bind)
- O* represents the oxygen chemistry (how easily O is removed as water)
- Together they span the 2D space needed to predict all intermediates via scaling

**Energy reference scheme** (your paper):
$$E_f(\text{CO}_2, g) = 0, \quad E_f(\text{H}_2, g) = 0, \quad E_f(\text{H}_2\text{O}, g) = 0$$

Elemental chemical potentials:
$$\mu(H) = \frac{1}{2}\Delta H^\circ(H_2), \quad \mu(O) = \Delta H^\circ(H_2O) - \Delta H^\circ(H_2), \quad \mu(C) = \Delta H^\circ(CO_2) - 2\mu(O)$$

---

### 1.4 Linear Scaling Relations

**Key equation:**
$$E_f(X^*) = a\cdot E_f(\text{CO}^*) + b\cdot E_f(\text{O}^*) + c$$

The intercept c is **fixed by the exact Cu(111) DFT value**, so scaling passes through Cu exactly.

**Scaling coefficients for CO₂→MeOH formate pathway (your paper, Table 2):**

| Species | a (CO* slope) | b (O* slope) | E_f^Cu (eV) |
|---------|-------------|-------------|-------------|
| CO* | 1.00 | 0.00 | +0.192 |
| O* | 0.00 | 1.00 | +0.797 |
| H* | 0.22 | 0.00 | −0.154 |
| CO₂* | 0.80 | 0.00 | −0.020 |
| OH* | 0.00 | 0.50 | +0.037 |
| H₂O* | 0.00 | 0.30 | −0.135 |
| HCOO* | 0.40 | 0.50 | −0.368 |
| H₂COO* | 0.50 | 0.50 | +0.445 |
| CH₃O* | 0.10 | 0.60 | −0.499 |
| CH₃OH* | 0.00 | 0.50 | −0.707 |

**Physical interpretation of slopes:**
- HCOO* (formate): a=0.40, b=0.50 → bidentate, bonded through two oxygens → strong O* dependence ✓
- CH₃O* (methoxy): a=0.10, b=0.60 → binds exclusively through one oxygen lone pair → dominated by O* ✓
- CO*: a=1.00, b=0.00 → pure C-bonded adsorbate → scales only with CO* descriptor ✓

**Validation:** R² > 0.95 for both HCOO* and CH₃O* scaling with CO* and O* across 8 metals ✓

---

### 1.5 Brønsted–Evans–Polanyi (BEP) Correlations

For surface reactions with a transition state, the activation barrier correlates linearly with the reaction energy:

$$E_a = \alpha\,\Delta E_{rxn} + \beta$$

- α = BEP slope (0 to 1)
- β = intrinsic barrier

**For the formate pathway (your paper):**

| Reaction | BEP slope α | Physical interpretation |
|---------|------------|------------------------|
| CO₂* + H* → HCOO* (TS1) | **0.60** | Late transition state (product-like); initial_state BEP constraint applied |
| HCOO* + H* → H₂COO* (TS2) | **0.50** | Symmetric (mid-point) TS; **Rate-Determining Step on Cu** |

**BEP constraint type in your paper:**
- TS1: `initial_state` constraint → activation energy scales with energy of CO₂* + H* (reactant state)
- TS2: `initial_state` constraint → scales with HCOO* + H* energy

**Why α = 0.60 for TS1 (early BEP)?**
An α close to 0.5–0.6 indicates a transition state that resembles both reactants and products — moderate. α → 0 = early TS (reactant-like), α → 1 = late TS (product-like).

---

## PART 2 — THE FORMATE MECHANISM (YOUR SYSTEM)

### 2.1 Overall Reaction
$$\text{CO}_2 + 3\text{H}_2 \rightarrow \text{CH}_3\text{OH} + \text{H}_2\text{O}, \quad \Delta H^\circ = -49.5\,\text{kJ/mol}$$

Industrial conditions: T = 493–523 K, P = 50–100 bar, Cu/ZnO/Al₂O₃ catalyst, 15–25% per-pass conversion.

### 2.2 The 11 Elementary Steps (Table 1, your paper)

| Step | Elementary Reaction | Type | Notes |
|------|---------------------|------|-------|
| 1 | CO(g) + * ⇌ CO* | Dummy | Anchors CO* descriptor; P(CO) = 10⁻²⁰ atm → negligible coverage |
| 2 | CO₂(g) + * ⇌ CO₂* | Reversible | First adsorption step |
| 3 | H₂(g) + 2* ⇌ 2H* | Dissociative, barrierless | H₂ dissociation (no barrier assumed) |
| 4 | H₂O* ⇌ H₂O(g) + * | Reversible | Water desorption |
| 5 | CH₃OH* ⇌ CH₃OH(g) + * | Reversible | Methanol desorption (last step) |
| 6 | CO₂* + H* →[TS1] HCOO* + * | BEP, α=0.60 | Formate formation — first hydrogenation |
| 7 | HCOO* + H* →[TS2] H₂COO* + * | BEP, α=0.50 | **RATE-DETERMINING STEP** on Cu |
| 8 | H₂COO* + H* → CH₃O* + O* | C–O scission | Dioxymethylene → methoxy |
| 9 | CH₃O* + H* → CH₃OH* + * | — | Final hydrogenation |
| 10 | O* + H* ⇌ OH* + * | — | O* removal, step 1 |
| 11 | OH* + H* ⇌ H₂O* + * | — | O* removal, step 2 |

### 2.3 Pathway Diagram

```
CO₂(g) + 3H₂(g)
    ↓ [Step 2] adsorb CO₂
   CO₂* + 2H*
    ↓ [Step 6, TS1, α=0.60] first hydrogenation
   HCOO* + H*             ← Formate intermediate
    ↓ [Step 7, TS2, α=0.50] ← RDS on Cu
   H₂COO*                 ← Dioxymethylene
    ↓ [Step 8] C–O scission
   CH₃O* + O*             ← Methoxy + Oxygen
    ↓ [Step 9]             ↓ [Steps 10, 11]
   CH₃OH*                 OH* → H₂O* → H₂O(g)
    ↓ [Step 5]
   CH₃OH(g)
```

---

## PART 3 — APPROXIMATIONS IN CATMAP

### 3.1 Mean-Field Langmuir–Hinshelwood Kinetics

**What it means:**
- All surface sites are **equivalent** (no lateral interactions between adsorbates)
- Surface coverage of each species follows **Langmuir adsorption** (no island formation)
- The rate of each elementary step = k_forward × (product of reactant coverages) − k_reverse × (product of product coverages)

**Rate equation for step i:**
$$r_i = k_{f,i}\prod_j\theta_j^{\nu_{j,i}} - k_{r,i}\prod_j\theta_j^{\nu'_{j,i}}$$

where θ_j = fractional coverage of species j, ν = stoichiometric coefficient.

**Site balance:**
$$\sum_i\theta_i + \theta_* = 1 \quad \text{(total sites = 1)}$$

**Limitations of mean-field approximation:**
- Neglects adsorbate–adsorbate interactions
- Breaks down at high coverages
- Cannot capture island effects or lateral repulsion
- May overestimate TOF at high coverage conditions

### 3.2 Frozen Adsorbate Approximation

**For surface species:** Entropy contributions from frustrated translations and rotations are neglected — the adsorbate is treated as "frozen" (no vibrational zero-point energy or thermal corrections to the free energy).

**For gas-phase species:** Full thermochemical corrections applied via Shomate equations (from NIST/JANAF tables).

**Implication:** Free energy of surface intermediates ≈ DFT formation energy (temperature-independent surface terms).

### 3.3 Pseudo-Steady-State Approximation

The steady-state coverage of each surface intermediate is found by setting all dθ_i/dt = 0 simultaneously:

$$\sum_j r_j\nu_{ij} = 0 \quad \forall\, i \quad \text{(MASI not changing)}$$

This gives a system of nonlinear algebraic equations solved numerically by CatMAP using Newton-Raphson iteration with arbitrary-precision arithmetic (mpmath, precision = 100 decimal digits).

### 3.4 The Dummy CO Adsorption Step (Step 1)

**Problem:** CO* is used as a descriptor but does NOT appear naturally in the formate mechanism (CO₂ goes directly to HCOO*, not through CO*).

**Requirement:** CatMAP's generalized linear scaler needs every descriptor to appear in at least one elementary step to build the coefficient matrix.

**Solution:** Add a **dummy reversible step**: CO(g) + * ⇌ CO*

**How to prevent physical effect:** Set P(CO) = 10⁻²⁰ atm → equilibrium CO* coverage ≪ 10⁻²⁰ ML → physically immaterial.

**Precedent:** Same dummy step used in the official CatMAP CO oxidation tutorial.

---

## PART 4 — VOLCANO PLOT ANALYSIS

### 4.1 How to Read a CatMAP Volcano Plot

The volcano plot is a **2D contour map** of log₁₀(TOF) as a function of:
- x-axis: E_f(CO*) [eV]  
- y-axis: E_f(O*) [eV]

**Color scale:** log₁₀(TOF) from ~−25 (blue, inactive) to ~+3 (yellow, very active)

**Key features:**
1. **Activity ridge:** Diagonal band of high activity running from lower-left to upper-right
2. **Left/strong-binding side:** Intermediates too stabilized → surface poisoning (HCOO* or CH₃O* accumulates)
3. **Right/weak-binding side:** CO₂* adsorption endergonic → reactant cannot activate
4. **Apex:** Optimal descriptor values → maximum TOF

### 4.2 Metal Positions and Activity Ranking (Your Paper, Table 4)

| Metal | E_f(CO*) | E_f(O*) | log₁₀(TOF) | Limitation |
|-------|---------|---------|------------|-----------|
| **Cu** | **+0.192** | **+0.797** | **−5 to −3** | **HCOO*+H* TS (RDS)** |
| PdIn | −0.500 | +0.250 | −9 to −7 | CO* slightly strong |
| Pt | −0.595 | +0.360 | −10 to −8 | CO* over-binding |
| Co | −0.505 | −0.060 | −14 to −12 | Deep CH₃O* + O* poison |
| Ni | −0.465 | −0.090 | −14 to −12 | CH₃O* well + O* poison |
| Pd | −0.905 | +0.260 | −16 to −14 | CO* severe poisoning |
| Rh | −0.835 | −0.230 | < −20 | HCOO* + O* poison |
| Ag | +0.835 | +1.140 | < −20 | Endergonic CO₂* ads. |

**Cu sits near the volcano apex** at (+0.192, +0.797) eV — confirmed by industrial dominance.

**Why Ni and Co fail:** E_f(O*) ≈ −0.09 eV → O* is nearly thermoneutral → O* removal is uphill → water formation blocked → O* poisoning + deep CH₃O* wells.

**Why Ag fails:** CO* binding too weak (+0.84 eV) → CO₂* formation endergonic (E_f(CO₂*) ≈ +0.06 eV after scaling) → cannot activate CO₂ at all.

**PdIn improvement over Pd:** Alloying with In shifts E_f(CO*) from −0.91 eV (Pd) to −0.50 eV (PdIn) — a +0.41 eV shift along CO* axis → 4–6 orders of magnitude improvement in TOF.

### 4.3 Topology of the Volcano

**Activity ridge direction:** Runs diagonally because both HCOO* and CH₃O* scale with BOTH CO* and O* (see Table 2). A move along the ridge keeps both intermediates at moderate binding energy.

**Unsolved (dark blue) region (lower left):** Near-unity co-coverages of multiple adsorbates → mean-field equations become ill-conditioned (multiple solutions or no convergence).

**Asymmetry:** The volcano is wider on the weak-binding side than the strong-binding side because surface poisoning (strong binding) is more catastrophic than weak activation.

---

## PART 5 — DEGREE OF RATE CONTROL (DRC)

### 5.1 Definition

The degree of rate control (DRC) for elementary step i on overall rate r is:

$$X_{RC,i} = \left(\frac{\partial\ln r}{\partial\ln k_i}\right)_{K_{eq}, k_{j\neq i}}$$

**Interpretation:**
- X_RC,i = +1: Step i is **fully rate-limiting** — increasing k_i by 1% increases TOF by 1%
- X_RC,i = 0: Step i has no effect on overall rate
- X_RC,i = −1: Species i is a **MASI (Most Abundant Surface Intermediate)** — it blocks sites
- X_RC,i = −2: Very strong inhibitor

**Sum rule:** $\sum_i X_{RC,i} = 1$ for all rate-limiting steps.

### 5.2 DRC Results for Your System (Figure 7, your paper)

**At Cu descriptor coordinates (+0.192, +0.797):**

| Step/Species | X_RC | Meaning |
|-------------|------|---------|
| HCOO*+H* → H₂COO* (TS2) | **≈ +1** | **Primary rate-limiting step on Cu** |
| CO₂*+H* → HCOO* (TS1) | **≈ +0.5** | Partially co-limiting |
| CH₃O* (as MASI) | ≈ 0 | Not a problem for Cu |

**In the Ni/Co/Pt/PdIn zone (strong CO* binding):**

| Species | X_RC | Meaning |
|---------|------|---------|
| CH₃O* | **≈ −1 to −2** | Primary inhibitor (MASI) |
| HCOO* | ≈ 0 | Not rate-limiting here |

**In the Rh/Pd zone (very strong binding):**

| Species | X_RC | Meaning |
|---------|------|---------|
| HCOO* | ≈ −1 | HCOO* poisoning |

**Key mechanistic insight:** The boundary between positive HCOO-H TS DRC and negative CH₃O DRC **exactly coincides with the volcano activity ridge** — mechanistically explaining the volcano shape.

### 5.3 MASI (Most Abundant Surface Intermediate)

**Definition:** The surface species with the highest steady-state fractional coverage under reaction conditions.

**In your system (Figure 6, your paper):**

| Descriptor region | MASI | Why |
|------------------|------|-----|
| Cu, Ag (weak binding) | CH₃OH* | Methanol desorption is rate-limiting at low P |
| Ni, Co, Pt, PdIn, Pd | **CH₃O*** | Deep CH₃O* well (E_f = −0.84 to −1.22 eV) → site blocking |
| Rh, Pd (very strong) | **HCOO*** | Very deep HCOO* well → site blocking |
| Ag (weak) | **H*** | CO₂* endergonic → H* is spectator |

**The two-MASI model:** The system is governed by either CH₃O* or HCOO* as MASI depending on which side of the volcano apex the metal sits.

---

## PART 6 — FREE ENERGY DIAGRAMS

### 6.1 How to Construct an FED

A Free Energy Diagram shows the Gibbs free energy of each intermediate along the reaction pathway.

**Energy reference:** CO₂(g) + 1.5H₂(g) = 0 eV (starting materials)

**For Cu(111) at T = 513 K (your paper):**

| State | G (eV) | Notes |
|-------|--------|-------|
| CO₂(g) + 1.5H₂(g) | 0.000 | Reference |
| CO₂* + 3H* | −0.020 + 3(−0.154) = −0.482 | After adsorption |
| TS1 | ~+0.63 (from gas ref.) | E_a ≈ 0.80 eV from CO₂*+H* |
| HCOO* + 2H* | −0.368 + 2(−0.154) = −0.676 | Formate intermediate |
| TS2 (RDS) | ~+1.01 eV | **E_a ≈ 1.4 eV from HCOO*+H*** |
| H₂COO* + H* | +0.445 + (−0.154) = +0.291 | High-energy intermediate |
| CH₃O* + O* | −0.499 + 0.797 = +0.298 | After C–O scission |
| CH₃OH* + O* (etc.) | −0.707 + ... | Methanol adsorbed |
| CH₃OH(g) + H₂O(g) | ~−1.0 eV | Final state |

**Kinetic bottleneck:** The largest barrier in the FED = TS2 height − HCOO*+H* energy = 1.4 eV → rate-determining step ✓

### 6.2 Cu vs. Ni FED Comparison (Figure 3, your paper)

| Feature | Cu(111) | Ni(111) |
|---------|---------|---------|
| CO₂* | E_f = −0.020 eV (thermoneutral) | E_f ≈ −0.20 eV (stabilized) |
| HCOO* | −0.368 eV (shallow well) | **−1.074 eV (very deep well)** |
| CH₃O* | −0.499 eV | **−1.097 eV (deepest well)** |
| Primary limitation | TS2 barrier (kinetic) | Deep CH₃O* well (thermodynamic poisoning) |
| Product selectivity | CH₃OH ✓ | CH₄ (methanation) |

The deep CH₃O* on Ni (1.097 eV below reference) traps the surface — it cannot proceed to CH₃OH desorption. Combined with O* ≈ 0, water removal is also blocked.

---

## PART 7 — CATALYST DESIGN PRINCIPLES

### 7.1 Three Quantitative Design Rules (from your paper)

**Rule 1 — Target the optimal descriptor window:**
$$E_f(\text{CO}^*) \in [-0.2, +0.2]\,\text{eV}, \quad E_f(\text{O}^*) \in [+0.5, +1.0]\,\text{eV}$$

This is the volcano apex region where Cu sits. Any modification should shift descriptors into this window.

**Rule 2 — Use intermetallic alloying to weaken strong-binding metals:**

$$\text{Pd} \xrightarrow{+\text{In}} \text{PdIn}: \Delta E_f(\text{CO}^*) = +0.41\,\text{eV} \rightarrow +4\text{–}6 \text{ orders of magnitude improvement}$$

Similarly: Ni + Ga → NiGa (Studt et al., Nat. Chem., 2014); Pd + Zn → PdZn

**Rule 3 — O* removal is a co-limiting constraint:**

Metals with E_f(O*) < 0 (Ni, Co, Rh) are deactivated regardless of CO* position because OH* and H₂O* formation is endergonic → O* accumulates → poisons sites.

**Implication:** Bifunctional catalysts where O* removal occurs on a separate oxide phase (e.g., ZnO in Cu/ZnO) can break the transition metal scaling line.

### 7.2 ZnO Promotion of Cu

The industrial Cu/ZnO/Al₂O₃ catalyst achieves activity above pure Cu because:
1. ZnO surface provides additional sites for CO₂ activation
2. Cu-Zn interface stabilizes HCOO* in a more reactive geometry
3. Effectively shifts E_f(CO*) by ~−0.1 to −0.3 eV while keeping E_f(O*) > +0.5 eV
4. This moves the effective descriptor position **closer to the volcano apex**

---

## PART 8 — EXAM QUESTION TEMPLATES

### 8.1 "Given a Reaction — Find Descriptors"

**Template answer structure:**

**Step 1:** Identify the surface intermediates in the mechanism.

**Step 2:** Apply the Abild-Pedersen universal scaling principle:
- C-bonded species (CO*, CHx*) → scale primarily with E_f(CO*)
- O-bonded species (O*, OH*, H₂O*) → scale with E_f(O*)
- Mixed species (HCOO*, CH₃O*) → scale with both, with b > 0 if oxygen-bonded

**Step 3:** Choose descriptors = {E_f(CO*), E_f(O*)} or equivalent pair that spans the chemistry of all intermediates.

**Step 4:** Verify by checking that all intermediates can be expressed via Eq. (3): $E_f(X^*) = a\,E_f(\text{CO}^*) + b\,E_f(\text{O}^*) + c$

### 8.2 "Identify the Transition States"

For each bond-breaking/forming step:

1. **TS exists** if the step has an activation barrier (endergonic or has a kinetic barrier)
2. **BEP relation** relates E_a to ΔE_rxn: E_a = α·ΔE_rxn + β
3. **α = 0.50** → symmetric TS (typical for hydrogenation steps)
4. **α = 0.60** → late TS (product-like) — used for HCOO* formation
5. **Barrierless** steps (like H₂ dissociation on metals) → no TS needed

**In the formate mechanism, 2 transition states:**
- TS1: CO₂* + H* → HCOO* (α = 0.60)
- TS2: HCOO* + H* → H₂COO* (α = 0.50) **← RDS**

### 8.3 "What Approximations Are Used?"

Always list ALL of these for CatMAP problems:

| Approximation | What it means | When it breaks down |
|--------------|--------------|-------------------|
| **Mean-field** | All sites equivalent, no lateral interactions | High coverage, island formation |
| **Langmuir adsorption** | Single-layer adsorption, non-interacting | Multi-layer or cooperative adsorption |
| **Pseudo-steady-state** | dθ_i/dt = 0 for all intermediates | Oscillating or transient systems |
| **Frozen adsorbate** | No entropy of surface species | High-T or flexible adsorbates |
| **Linear scaling** | E_f(X*) = aE_f(CO*) + bE_f(O*) + c | Non-universal adsorbates, alloys |
| **BEP** | E_a = αΔE + β (linear) | Very exo/endothermic reactions |
| **Ideal gas** | Gas-phase species follow p-T thermodynamics | High pressure (>100 bar) |
| **Shomate gas thermochemistry** | Standard NIST Shomate equations for G(T,P) | Non-standard conditions |

### 8.4 "Explain the Volcano Shape"

**Template answer (5 sentences):**

1. The volcano arises from the **Sabatier principle**: optimal catalysts bind intermediates moderately.
2. On the **weak-binding side** (right), CO₂* adsorption becomes endergonic, preventing the first hydrogenation step.
3. On the **strong-binding side** (left), key intermediates (CH₃O* on Ni/Co, HCOO* on Rh/Pd) are excessively stabilized, blocking active sites.
4. The **activity ridge** runs diagonally because both HCOO* and CH₃O* scale with both CO* and O*, so moving along the ridge keeps both at moderate binding.
5. The DRC analysis confirms: positive X_RC for TS2 at the apex transitions to negative X_RC (CH₃O* or HCOO* MASI) away from the apex, explaining the volcano topology mechanistically.

### 8.5 "What is the Rate-Determining Step?"

**For Cu(111) under industrial conditions (513 K, 0.2 atm CO₂, 0.6 atm H₂):**

**Answer:** The **HCOO* + H* → H₂COO*** step (Step 7, TS2, BEP slope α = 0.50) is the primary rate-determining step.

**Evidence:**
1. DRC analysis: X_RC(TS2) ≈ +1 at Cu descriptor coordinates
2. FED: TS2 has the highest apparent barrier (~1.4 eV from HCOO*+H* state)
3. High HCOO* coverage predicted by mean-field model (consistent with Grabow & Mavrikakis, 2011)
4. Consistent with CO₂ + H* → HCOO* (TS1) being partially co-limiting (X_RC ≈ +0.5)

---

## PART 9 — SURFACE COVERAGE MAPS (Key Findings)

### 9.1 MASI Map Results

**CH₃O* coverage (Figure 6B):** High coverage (0.4–0.9 ML) across a large region encompassing Ni, Co, Pt, PdIn, Pd (E_f(CO*) ∈ [−1.1, +0.1] eV). This deep CH₃O* well creates thermodynamic sinks that block active sites.

**HCOO* coverage (Figure 6C):** High in the strong-binding zone (Rh, lower Pd region). The 0.4–1.0 ML coverage confirms HCOO* poisoning.

**H* coverage:** Accumulates on Ag because CO₂* formation is endergonic → CO₂ cannot activate → H* just accumulates as a spectator species.

**CO₂*, H₂COO*, O*, OH*:** All show near-zero coverage (≪ 0.1 ML) everywhere → these are transient intermediates, not MASIs. The formate pathway kinetics are governed by a **two-MASI model**: either CH₃O* or HCOO* dominates.

---

## PART 10 — OPERATING CONDITIONS & SETUP

| Parameter | Value | Rationale |
|-----------|-------|-----------|
| Temperature | 513 K (240°C) | Lower bound of industrial window |
| P(CO₂) | 0.2 atm | Stoichiometric 1:3 ratio |
| P(H₂) | 0.6 atm | Stoichiometric 1:3 ratio |
| P(CH₃OH) | 10⁻³ atm | Near-zero initial products |
| P(H₂O) | 10⁻³ atm | Near-zero initial products |
| Descriptor grid | 20×20 | Ef(CO*) ∈ [−1.2, +1.0], Ef(O*) ∈ [−0.5, +1.4] eV |
| Solver precision | 100 digits (mpmath) | Convergence in ill-conditioned regions |
| Max iterations | 100 | Root-finding per grid point |

**Gas-phase free energy correction for partial pressure:**
$$G = G^\circ + k_BT\ln(P/P^\circ), \quad P^\circ = 1\,\text{atm}$$

---

## PART 11 — QUICK REFERENCE SHEET FOR EXAM

### The 5 things you must know cold:

1. **Descriptors:** E_f(CO*) and E_f(O*) — represent carbon and oxygen chemistry of the surface

2. **Linear scaling:** E_f(X*) = a·E_f(CO*) + b·E_f(O*) + c — all intermediates from 2 numbers

3. **BEP:** E_a = α·ΔE_rxn + β — transition state energy from reaction energy

4. **RDS on Cu:** HCOO* + H* → H₂COO* (Step 7, TS2, α=0.50), DRC ≈ +1

5. **Volcano interpretation:** Left = strong binding/poisoning; Right = weak binding/no activation; Apex = optimal (Cu)

### Descriptor values to memorize:

| Metal | E_f(CO*) | E_f(O*) | Activity |
|-------|---------|---------|---------|
| Cu | **+0.19** | **+0.80** | **Best (apex)** |
| Ag | +0.84 | +1.14 | Inactive (too weak) |
| Ni | −0.47 | −0.09 | Low (CH₃O* + O* poison) |
| PdIn | −0.50 | +0.25 | Moderate |

### Key equations:

$$E_f(X^*) = a\,E_f(\text{CO}^*) + b\,E_f(\text{O}^*) + c \quad \text{(linear scaling)}$$

$$E_a = \alpha\,\Delta E_{rxn} + \beta \quad \text{(BEP)}$$

$$X_{RC,i} = \left(\frac{\partial\ln r}{\partial\ln k_i}\right)_{K_{eq},k_{j\neq i}} \quad \text{(degree of rate control)}$$

$$\sum_i\theta_i + \theta_* = 1 \quad \text{(site balance, PSS)}$$

$$\text{Sabatier principle: } \text{TOF} = f(E_f^{binding}) \text{ peaks at intermediate binding}$$
