# CatMAP — Universal Methodology for ANY Catalytic Reaction
## "My professor will give any reaction" — Complete Exam Preparation Guide

> **How to use this document:**  
> 1. Read Part 1 (the 8-step procedure) until you can reproduce it from memory.  
> 2. Study each worked example (Parts 2–6) using the same 8 steps.  
> 3. Practice with the fill-in-the-blank templates in Part 7 using whatever reaction you're given.

---

# PART 1 — THE UNIVERSAL 8-STEP CATMAP PROCEDURE

No matter what reaction your professor gives you, answer using these 8 steps **in this exact order**.

---

## STEP 1 — Write the Overall Reaction and Balance It

Write the gas-phase stoichiometry and identify:
- All reactants and products
- The standard enthalpy ΔH°rxn (exothermic < 0, endothermic > 0)
- Industrial operating conditions (T, P) if known

**Example template:**
$$\text{A(g)} + \text{B(g)} \rightarrow \text{C(g)}, \quad \Delta H^\circ = \pm X\,\text{kJ/mol}$$

---

## STEP 2 — Propose the Elementary Surface Mechanism

Break the overall reaction into **reversible elementary steps** on the catalyst surface. Each step must involve only **one bond broken or formed**.

**Rules for writing elementary steps:**
| Type | Template | Example |
|------|----------|---------|
| Molecular adsorption | X(g) + * ⇌ X* | CO(g) + * ⇌ CO* |
| Dissociative adsorption | X₂(g) + 2* ⇌ 2X* | H₂(g) + 2* ⇌ 2H* |
| Surface hydrogenation | X* + H* ⇌ XH* + * | N* + H* ⇌ NH* + * |
| Surface reaction | X* + Y* ⇌ Z* + * | CO* + O* ⇌ CO₂* + * |
| Desorption | X* ⇌ X(g) + * | NH₃* ⇌ NH₃(g) + * |

**Notation:** `*` = free surface site; `X*` = species X adsorbed on one site.

**Key principle — Microscopic reversibility:** Every elementary step is written as reversible (⇌). The net direction is determined by thermodynamics (ΔG of overall reaction).

---

## STEP 3 — Identify the Surface Intermediates and Classify Them

List every surface-bound species X* and classify:

| Class | Description | Typical binding | Descriptor dependence |
|-------|-------------|----------------|----------------------|
| **C-bonded** | Bound through carbon (CO*, CHx*, CN*) | Via d-π back-donation | Scales with **E_f(CO*)** |
| **O-bonded** | Bound through oxygen (O*, OH*, COOH*) | Via oxygen lone pairs | Scales with **E_f(O*)** |
| **N-bonded** | Bound through nitrogen (N*, NH*, NO*) | Via nitrogen lone pairs | Scales with **E_f(N*)** |
| **H-bonded** | Bound through hydrogen (H*) | Via σ-bond | Scales with **E_f(H*)** or E_f(CO*) |
| **Mixed** | Bidentate (HCOO*, NO₂*) | Both O and C/N | Scales with **both** descriptors |

---

## STEP 4 — Choose the Two Descriptors

**The universal rule for choosing descriptors:**

> Pick the **two adsorption energies** that (a) appear directly in the mechanism AND (b) correlate best with all other intermediates via linear scaling.

**Standard descriptor pairs for common reaction chemistries:**

| Reaction type | Descriptor 1 | Descriptor 2 | Rationale |
|--------------|-------------|-------------|-----------|
| CO₂/CO hydrogenation | E_f(CO*) | E_f(O*) | C-chemistry + O-chemistry |
| NH₃ synthesis/decomposition | E_f(N*) | E_f(H*) | N-chemistry + H-chemistry |
| CO oxidation | E_f(CO*) | E_f(O*) | Reactant + oxidant |
| NO reduction | E_f(N*) | E_f(O*) | N-chemistry + O-chemistry |
| Water-gas shift | E_f(CO*) | E_f(O*) | CO activation + OH formation |
| Methane activation | E_f(C*) | E_f(H*) | C–H bond breaking |
| HER (H₂ evolution) | **E_f(H*)** | — | Single descriptor (1D volcano) |
| ORR (O₂ reduction) | E_f(O*) or E_f(OH*) | — | Single descriptor or 2D |

**The Abild-Pedersen universal scaling principle (why 2 descriptors are enough):**

All intermediates containing M–C, M–O, M–N, or M–H bonds scale linearly with the binding energy of the "parent" atom (C*, O*, N*, H*), because the same d-band electronic structure governs all bonds to the surface.

$$E_f(X^*) = a\,E_f(\text{desc}_1) + b\,E_f(\text{desc}_2) + c$$

The slope `a` ≈ number of surface bonds made by C in X* divided by total bonds in parent species. The slope `b` is analogous for O.

---

## STEP 5 — Write the Linear Scaling Relations

For each surface intermediate X*, write:
$$E_f(X^*) = a\cdot E_f(\text{desc}_1) + b\cdot E_f(\text{desc}_2) + c$$

**Rules for estimating slopes without DFT:**

| Bond type in X* | Slope rule |
|----------------|-----------|
| X* bonds to surface only through C | a ≈ (bonds to surface)/(total C bonds), b = 0 |
| X* bonds to surface only through O | a = 0, b ≈ (bonds to surface)/(total O bonds) |
| X* bonds through both C and O (bidentate) | Both a and b nonzero |
| H* | a ≈ 0.22 (empirical, Abild-Pedersen) for CO* descriptor |

**Key reference slopes (memorize):**

| Species | a (CO*) | b (O*) | Physical reason |
|---------|--------|-------|----------------|
| CO* | 1.00 | 0.00 | Pure C-bonded reference |
| O* | 0.00 | 1.00 | Pure O-bonded reference |
| H* | 0.22 | 0.00 | Weak H–surface bond, partial C correlation |
| OH* | 0.00 | 0.50 | O-bonded, half the O* slope (one bond instead of two) |
| N* | ~0.00 | ~0.00 | Independent of CO*/O* (use N* as own descriptor) |
| NH* | 0.00 | 0.00 | Scales with N* |
| CO₂* | 0.80 | 0.00 | Weakly C-bonded |
| HCOO* | 0.40 | 0.50 | Bidentate O-bonded formate |
| CH₃O* | 0.10 | 0.60 | O-bonded methoxy |

---

## STEP 6 — Apply BEP Relations to Transition States

For every elementary step with an activation barrier:

$$E_a = \alpha\,\Delta E_{rxn} + \beta$$

**BEP slope α physical meaning:**
- α = 0: "Early" TS — transition state looks like reactants; barrier independent of thermodynamics
- α = 0.5: "Symmetric" TS — equal reactant and product character
- α = 1: "Late" TS — transition state looks like products; barrier = reaction energy

**Standard BEP slopes for common step types:**

| Step type | Typical α | Example |
|-----------|----------|---------|
| H* addition (hydrogenation) | 0.50 | HCOO* + H* → H₂COO* |
| CO₂ activation | 0.60 | CO₂* + H* → HCOO* |
| N₂ dissociation | 0.90–1.00 | N₂ + 2* → 2N* (very late TS) |
| CO dissociation | 0.80 | CO* + * → C* + O* |
| O–H bond formation | 0.50 | O* + H* → OH* |
| N–H bond formation | 0.50 | N* + H* → NH* |
| C–C bond formation | 0.50–0.70 | CH* + CH* → C₂H₂* |

**CatMAP BEP constraint types:**
- `initial_state`: E_a scales with energy of the reactant state
- `final_state`: E_a scales with energy of the product state
- `transition_state`: E_TS given directly

---

## STEP 7 — Identify the Rate-Determining Step (Before Running CatMAP)

**Qualitative rules for predicting the RDS:**

1. **The step with the largest activation barrier** in the FED is a candidate for RDS
2. **For exothermic reactions** (like NH₃ synthesis), the RDS is often the **most endergonic** elementary step (the one that "goes uphill" the most)
3. **N₂ dissociation** is almost always RDS for N-containing reactions on metals (high barrier due to strong N≡N triple bond)
4. **CO₂ activation** (first C–O bond hydrogenation) is often partially rate-limiting
5. Use **DRC analysis** to confirm: X_RC ≈ +1 for the true RDS

**Key insight — MASI prediction:**
The most abundant surface intermediate is the one with the **deepest thermodynamic well** in the free energy diagram. If a species has E_f ≪ 0 (very stable adsorption), it will accumulate and block sites.

---

## STEP 8 — Predict Volcano Shape and Metal Positions

**Universal volcano topology rules:**

| Regime | Condition | What limits rate | DRC signature |
|--------|-----------|-----------------|---------------|
| Weak binding (right side) | E_f(desc) too positive | Reactant cannot adsorb / first bond activation uphill | +1 for first adsorption step |
| Strong binding (left side) | E_f(desc) too negative | Product/intermediate cannot desorb / MASI poisoning | −1 to −2 for MASI |
| Optimal (apex) | Balanced | Actual bond-breaking TS | +1 for kinetic TS |

**Metal activity trends** (general, CO*/O* space):
- **Noble metals** (Au, Ag): top-right (weak binding) → often inactive
- **Platinum group** (Pt, Pd, Rh): middle (moderate binding)
- **Base metals** (Cu, Co, Ni, Fe): varies — Fe is very strong-binding (bottom-left)
- **Early transition metals** (Mo, W, Ru): strong binding (bottom-left)

---

# PART 2 — WORKED EXAMPLE: NH₃ SYNTHESIS (HABER-BOSCH)

## Overview
$$\text{N}_2(g) + 3\text{H}_2(g) \rightarrow 2\text{NH}_3(g), \quad \Delta H^\circ = -92\,\text{kJ/mol}$$
Industrial: Fe or Ru catalyst, T = 400–500°C, P = 150–300 bar.

---

## Step 1 — Overall Reaction
Exothermic (ΔH° = −92 kJ/mol). High pressure favors NH₃ (fewer moles of gas). High T needed for kinetics but thermodynamically unfavorable.

## Step 2 — Elementary Mechanism

| # | Step | Type |
|---|------|------|
| 1 | N₂(g) + 2* ⇌ 2N* | **Dissociative adsorption — RDS** |
| 2 | H₂(g) + 2* ⇌ 2H* | Dissociative adsorption (barrierless on Fe) |
| 3 | N* + H* ⇌ NH* + * | Surface hydrogenation |
| 4 | NH* + H* ⇌ NH₂* + * | Surface hydrogenation |
| 5 | NH₂* + H* ⇌ NH₃* + * | Surface hydrogenation |
| 6 | NH₃* ⇌ NH₃(g) + * | Desorption |

**Note:** Steps 3–5 each have BEP α ≈ 0.50 (symmetric hydrogenation).

## Step 3 — Surface Intermediates

| Species | Bond type | Scales with |
|---------|-----------|------------|
| N* | N–metal bond | **E_f(N*)** — descriptor 1 |
| H* | H–metal bond | **E_f(H*)** — descriptor 2 |
| NH* | N–metal, one H | E_f(N*) (dominant) |
| NH₂* | N–metal, two H | E_f(N*) |
| NH₃* | N–metal, three H (weak) | E_f(N*) |

**Linear scaling for NH_x species:**
$$E_f(\text{NH}_x^*) \approx \frac{3-x}{3}\,E_f(\text{N}^*) + c_x, \quad x = 0, 1, 2, 3$$

Physically: as x increases (more H added), the N–surface bond weakens (N has fewer electrons to donate to surface).

## Step 4 — Descriptors
$$\boxed{\text{Descriptor 1: }E_f(\text{N}^*)} \quad \boxed{\text{Descriptor 2: }E_f(\text{H}^*)}$$

Alternatively, many studies use **only E_f(N*)** as the single descriptor (1D volcano) because H* scaling variation is smaller.

## Step 5 — Linear Scaling Relations

| Species | Scaling |
|---------|---------|
| NH* | E_f(NH*) = (2/3)E_f(N*) + c₁ |
| NH₂* | E_f(NH₂*) = (1/3)E_f(N*) + c₂ |
| NH₃* | E_f(NH₃*) ≈ small constant (weak adsorption) |
| H* | Independent descriptor |

Slopes decrease by 1/3 for each H added — because each added H "uses up" one of the three N lone-pair electrons that bond to the surface.

## Step 6 — BEP / Transition States

| Step | Type | BEP slope α | Notes |
|------|------|-------------|-------|
| N₂ dissociation (Step 1) | Dissociation | **α ≈ 0.90–1.00** | Very late TS; **RDS** |
| N* + H* → NH* (Step 3) | Hydrogenation | α ≈ 0.50 | Symmetric TS |
| NH* + H* → NH₂* (Step 4) | Hydrogenation | α ≈ 0.50 | |
| NH₂* + H* → NH₃* (Step 5) | Hydrogenation | α ≈ 0.50 | |

**Why N₂ dissociation is RDS:** The N≡N triple bond (bond energy 945 kJ/mol) must be broken. This gives a very late, product-like transition state (α ≈ 1). The barrier is enormous on weak-binding metals and decreases on strong-binding metals.

## Step 7 — Rate-Determining Step
**N₂ dissociative adsorption** (Step 1).
- DRC: X_RC(N₂ dissociation) ≈ +1 for most metals
- Evidence: Isotope studies confirm N₂ adsorption is rate-limiting; increasing N₂ pressure increases rate linearly
- On Ru: N₂ dissociation still RDS but activation energy lower than Fe due to better geometric site (B5 sites)

## Step 8 — Volcano Shape and Metal Positions

**1D Volcano (E_f(N*) axis):**

```
log(TOF)  
    ↑          Ru ← optimal
    |       Fe/  \
    |      /      \
    |     /        \ Mo, W (too strong)
    |    /          
    |  Cu,Ag (too weak, N₂ won't dissociate)
    ─────────────────────→ E_f(N*)
        ← strong        weak →
```

**Metal positions on N* binding scale:**

| Metal | E_f(N*) approx. | Activity | Limitation |
|-------|----------------|---------|-----------|
| Mo, W | Very negative | Low | N* too stable → NH₃ desorption blocked |
| Fe | Negative (~−0.4 eV) | **High** | Near apex on strong side |
| Ru | ~−0.1 eV | **Highest** | Nearest volcano apex |
| Co, Ni | ~+0.3 eV | Moderate | Right side of apex |
| Cu, Au | Very positive | Low | N₂ won't dissociate (barrier too high) |

**Why Fe is the industrial catalyst:** Cost and availability vs. Ru. Ru is slightly better catalytically but expensive.

**Why ammonia synthesis is done at high pressure:** On the right side of the volcano (weak binding), increasing P(N₂) shifts equilibrium and increases N₂ surface coverage, partially compensating for the high N₂ dissociation barrier.

**MASI on strong-binding side:** N* accumulates → blocks sites → negative DRC.  
**MASI on weak-binding side:** H* or NH₃* may accumulate.

---

## Summary Box — NH₃ Synthesis

| Item | Answer |
|------|--------|
| Descriptors | E_f(N*), E_f(H*) [or just E_f(N*)] |
| RDS | N₂ dissociative adsorption |
| BEP slope (RDS) | α ≈ 0.90–1.00 (very late TS) |
| MASI (strong side) | N* |
| MASI (weak side) | H* / free surface |
| Optimal metal | Ru > Fe > Co |
| Why volcano? | Sabatier: N₂ dissociation needs strong binding; NH₃ desorption needs weak binding |
| Key approximation | Mean-field, PSS, BEP, linear scaling |



---

# PART 3 — WORKED EXAMPLE: CO OXIDATION

## Overview
$$\text{CO}(g) + \tfrac{1}{2}\text{O}_2(g) \rightarrow \text{CO}_2(g), \quad \Delta H^\circ = -283\,\text{kJ/mol}$$
**Applications:** Automotive catalytic converters (Pt/Pd/Rh), fuel cells (CO removal), air purification.  
**Note:** CO oxidation is the **official CatMAP tutorial reaction** — your professor may use it as a direct example.

---

## Step 1 — Overall Reaction
Strongly exothermic. No thermodynamic limitation at normal temperatures. Purely **kinetically limited** — need catalyst to lower the activation barrier.

## Step 2 — Elementary Mechanism (Langmuir–Hinshelwood)

| # | Step | Notes |
|---|------|-------|
| 1 | CO(g) + * ⇌ CO* | CO adsorption |
| 2 | O₂(g) + 2* ⇌ 2O* | **Dissociative O₂ adsorption** |
| 3 | CO* + O* → CO₂(g) + 2* | **Surface reaction — often RDS** |

**Alternative: Eley–Rideal mechanism** (less common):
- CO(g) + O* → CO₂(g) + * (gas-phase CO reacts directly with adsorbed O*)
- Usually less important than LH at low T

**Alternative: Mars–van Krevelen** (for oxide catalysts):
- CO(g) + O_lattice → CO₂(g) + vacancy (CO reacts with lattice oxygen)
- Important for CeO₂, TiO₂ supports

## Step 3 — Surface Intermediates

| Species | Bond type | Scales with |
|---------|-----------|------------|
| CO* | C–metal bond | E_f(CO*) — descriptor 1 |
| O* | O–metal bond | E_f(O*) — descriptor 2 |
| CO₂ | Gas phase (product, desorbs immediately) | Not a surface intermediate |

**This is why CO*/O* are the natural descriptors for CO oxidation** — the mechanism has exactly these two species and no others!

## Step 4 — Descriptors
$$\boxed{\text{Descriptor 1: }E_f(\text{CO}^*)} \quad \boxed{\text{Descriptor 2: }E_f(\text{O}^*)}$$

## Step 5 — Linear Scaling Relations
Only CO* and O* are intermediates — both are their own descriptors. The scaling matrix is trivially:

| Species | a (CO*) | b (O*) | c (eV) |
|---------|--------|-------|--------|
| CO* | 1.00 | 0.00 | 0 (by definition) |
| O* | 0.00 | 1.00 | 0 (by definition) |

**No BEP needed for steps 1–2** (adsorption steps).  
**For step 3 (surface reaction CO* + O* → CO₂ + 2*):**

$$E_a = \alpha\,(E_f(\text{CO}^*) + E_f(\text{O}^*)) + \beta$$

with α ≈ 0.5–0.7 (empirical). The activation barrier decreases as CO* and O* bind more weakly.

## Step 6 — Transition State for CO* + O* → CO₂

BEP relation with α ≈ 0.7 (late TS, C–O bond formation is product-like):
$$E_{TS} = E_f(\text{CO}^*) + E_f(\text{O}^*) + E_{TS,0}$$

where $E_{TS,0}$ ≈ 1.0 eV (intrinsic barrier on a reference metal like Cu).

## Step 7 — Rate-Determining Step

**Two competing limitations create the volcano:**

| Regime | Rate-limiting process | Condition |
|--------|-----------------------|-----------|
| **Strong binding (left)** | CO* desorption / CO* too stable | E_f(CO*) ≪ 0 → CO* MASI → blocks O₂ adsorption |
| **Weak binding (right)** | O₂ adsorption / CO₂ formation | E_f(O*) ≫ 0 → O* doesn't bind → no reaction |
| **Apex** | CO* + O* → CO₂ surface reaction | Balanced binding |

**DRC at apex:** X_RC(CO*+O*→CO₂) ≈ +1  
**DRC on strong side:** X_RC(CO*) ≈ −1 (CO* is MASI and inhibitor)

## Step 8 — Volcano Shape and Metal Positions

**2D Volcano (CO* vs O* space):**

```
E_f(O*) ↑
 high    | Ag (weak O*)          
         |   Au
         |       Cu ← near optimal        
         |          Pt·PdIn  
         |              Pd·Rh
         |                  Ni·Co
 low     |                        Fe (too strong)
         └─────────────────────────────→ E_f(CO*)
              weak             strong
```

**Metal rankings for CO oxidation:**

| Metal | Activity | Limitation |
|-------|---------|-----------|
| Pt | **Highest** (industrial standard) | Slight CO* over-binding at low T |
| Pd | High | CO poisoning at high [CO] |
| Au nanoparticles | Surprisingly active (size effect!) | Not explained by simple volcano |
| Rh | High | Expensive |
| Cu | Moderate | O* too stable at high T |
| Fe, Ni | Low | CO* and O* too strongly bound |

**Key anomaly — Au nanoparticles:** Bulk Au is inactive (CO* doesn't bind). But Au nanoparticles <5 nm are active at room temperature due to:
1. Under-coordinated edge/corner sites with stronger binding
2. Support effects (O₂ activation at Au-support interface)
3. Quantum size effects changing d-band

This is an example where the simple volcano picture **breaks down** — highlighting the limitations of mean-field scaling.

## Summary Box — CO Oxidation

| Item | Answer |
|------|--------|
| Descriptors | E_f(CO*), E_f(O*) |
| RDS | CO* + O* → CO₂(g) + 2* (surface reaction) |
| BEP slope (RDS) | α ≈ 0.5–0.7 |
| MASI (strong CO* side) | CO* (poisoning) |
| MASI (weak O* side) | Free sites / O* doesn't form |
| Optimal metal | Pt, Pd |
| Key feature | CO poisoning at low T — negative DRC for CO* |
| Mechanism type | Langmuir–Hinshelwood |
| Key approximation | All standard (MF, PSS, BEP, linear scaling) |



---

# PART 4 — WORKED EXAMPLE: NO REDUCTION (DeNOx)

## Overview
$$\text{NO}(g) + \text{CO}(g) \rightarrow \tfrac{1}{2}\text{N}_2(g) + \text{CO}_2(g), \quad \Delta H^\circ = -373\,\text{kJ/mol}$$
$$\text{2NO}(g) + \text{5H}_2(g) \rightarrow \text{2NH}_3(g) + \text{2H}_2\text{O}(g) \quad \text{(SCR alternative)}$$

**Applications:** Catalytic converter (Three-Way Catalyst, TWC: Pt/Pd/Rh), power plant DeNOx (SCR with V₂O₅/TiO₂).

---

## Step 1 — Overall Reaction
NO + CO → ½N₂ + CO₂ is exothermic. The challenge: selectively reduce NO to N₂ (not NH₃ or N₂O) while simultaneously oxidizing CO to CO₂.

## Step 2 — Elementary Mechanism (NO + CO on Rh/Pt)

| # | Step | Notes |
|---|------|-------|
| 1 | NO(g) + * ⇌ NO* | NO adsorption |
| 2 | CO(g) + * ⇌ CO* | CO adsorption |
| 3 | NO* + * → N* + O* | **NO dissociation — often RDS** |
| 4 | N* + N* → N₂(g) + 2* | N₂ formation and desorption |
| 5 | CO* + O* → CO₂(g) + 2* | CO₂ formation (exothermic) |

**Important side reactions (selectivity issue):**
- N* + NO* → N₂O* + * → N₂O(g) + * (N₂O is a potent greenhouse gas)
- N* + H* → NH* → ... → NH₃ (undesired at high H₂)

## Step 3 — Surface Intermediates

| Species | Bond type | Scales with |
|---------|-----------|------------|
| NO* | N–metal (primarily) + O–metal (secondary) | Both E_f(N*) and E_f(O*), but primarily **E_f(N*)** |
| N* | N–metal bond | **E_f(N*)** — descriptor 1 |
| O* | O–metal bond | **E_f(O*)** — descriptor 2 |
| CO* | C–metal bond | E_f(CO*) ≈ correlated with E_f(N*) on transition metals |

## Step 4 — Descriptors
$$\boxed{\text{Descriptor 1: }E_f(\text{N}^*)} \quad \boxed{\text{Descriptor 2: }E_f(\text{O}^*)}$$

**Why N* instead of CO*?** Because the key chemistry is N–O bond activation. N* binding energy controls NO dissociation and N₂ formation. O* controls CO₂ formation side.

## Step 5 — Linear Scaling Relations

| Species | Scaling | Rationale |
|---------|---------|-----------|
| NO* | E_f(NO*) ≈ 0.6·E_f(N*) + 0.4·E_f(O*) + c | Mixed N–O bidentate-like binding |
| N* | E_f(N*) = 1.0·E_f(N*) + 0 | Descriptor itself |
| O* | E_f(O*) = 0 + 1.0·E_f(O*) | Descriptor itself |
| CO* | E_f(CO*) ≈ 0.7·E_f(N*) + c' | CO* correlates with N* via d-band center |

## Step 6 — Transition States

| Step | Type | BEP slope α | Notes |
|------|------|-------------|-------|
| NO dissociation (Step 3) | Bond breaking | α ≈ 0.9 | Very late TS — N=O is strong double bond (630 kJ/mol) |
| N* + N* → N₂ (Step 4) | Bond formation | α ≈ 0.3–0.5 | Early/symmetric TS |
| CO* + O* → CO₂ (Step 5) | Surface reaction | α ≈ 0.5–0.7 | Same as CO oxidation |

**NO dissociation has high BEP slope (late TS)** because the N=O double bond is very strong — similar to N₂ triple bond but somewhat easier to break.

## Step 7 — Rate-Determining Step

**Primary RDS: NO dissociation (Step 3)**

On weak-binding metals: NO barely adsorbs → no dissociation  
On strong-binding metals: N* and O* accumulate → blocks sites → poisoning

**Selectivity challenge** (N₂ vs N₂O):
- At low T: N* + NO* → N₂O (kinetically favored on some metals)
- At high T: N* + N* → N₂ (thermodynamically preferred but requires two N* to meet)
- **Rh is preferred** because it gives high N₂ selectivity — the N* + N* recombination is fast enough relative to N* + NO* pathway

## Step 8 — Volcano Shape and Metal Positions

**Key volcanic features:**
- Strong-binding side: N* + O* accumulate → MASI poisoning → DRC(N*) < 0, DRC(O*) < 0
- Weak-binding side: NO* doesn't form → no reaction
- Apex: Rh sits near optimal

**Metal ranking for NO reduction:**

| Metal | Activity for NO→N₂ | Selectivity | Notes |
|-------|-------------------|-------------|-------|
| Rh | **Highest** | High N₂ | Optimal N* + O* binding — used in TWC |
| Pt | High | Mixed N₂/N₂O | Slight CO* poisoning |
| Pd | Moderate | Lower N₂ | More N₂O at low T |
| Cu | Moderate | Good | Used in zeolite-Cu SCR |
| Fe | Lower | Good | Used in Fe-zeolite SCR |

## Summary Box — NO Reduction

| Item | Answer |
|------|--------|
| Descriptors | E_f(N*), E_f(O*) |
| RDS | NO dissociation (N* + O* formation) |
| BEP slope (RDS) | α ≈ 0.9 (late TS) |
| MASI (strong side) | N* and/or O* |
| MASI (weak side) | Free surface |
| Optimal metal | Rh (Three-Way Catalyst) |
| Selectivity issue | N₂ vs N₂O competition |
| Key difference from NH₃ | Two different atom types produced (N₂ + CO₂) → 2D descriptor space essential |



---

# PART 5 — WORKED EXAMPLE: WATER-GAS SHIFT (WGS)

## Overview
$$\text{CO}(g) + \text{H}_2\text{O}(g) \rightarrow \text{CO}_2(g) + \text{H}_2(g), \quad \Delta H^\circ = -41\,\text{kJ/mol}$$

**Applications:** Hydrogen production (steam reforming + WGS), fuel cells (CO cleanup), ammonia synthesis (feed purification).  
**Industrial catalysts:** Fe₃O₄/Cr₂O₃ (HTS, 300–500°C), Cu/ZnO/Al₂O₃ (LTS, 150–250°C).

---

## Step 1 — Overall Reaction
Mildly exothermic. At **high T**: kinetically fast but thermodynamically limited (equilibrium shifts left).  
At **low T**: thermodynamically favorable but kinetically slow → need a catalyst.  
This is why industry uses a two-stage process: HTS then LTS.

---

## Step 2 — Two Competing Mechanisms

### Mechanism A: Associative (Formate/Carboxyl) Pathway
| # | Step | Notes |
|---|------|-------|
| 1 | CO(g) + * ⇌ CO* | CO adsorption |
| 2 | H₂O(g) + * ⇌ H₂O* | Water adsorption |
| 3 | H₂O* + * → OH* + H* | Water dissociation |
| 4 | CO* + OH* → COOH* + * | **Carboxyl formation — often RDS** |
| 5 | COOH* + * → CO₂* + H* | Carboxyl decomposition |
| 6 | CO₂* → CO₂(g) + * | CO₂ desorption |
| 7 | H* + H* → H₂(g) + 2* | H₂ recombination |

### Mechanism B: Redox (Regenerative) Pathway
| # | Step | Notes |
|---|------|-------|
| 1 | CO(g) + * ⇌ CO* | CO adsorption |
| 2 | H₂O(g) + O* → CO₂(g)... | Uses lattice O on oxide surfaces |
| 3 | CO* + O* → CO₂(g) + 2* | CO oxidation |
| 4 | H₂O* + * → OH* + H* | Water dissociation (re-oxidizes surface) |
| 5 | OH* + H* → H₂O* + * → ... | OH removal |

**Which mechanism dominates?**
- **Cu, Ni, Pt (metals):** Associative (carboxyl) pathway — DFT studies confirm COOH* intermediate
- **Oxide supports (CeO₂, Fe₃O₄):** Redox (Mars–van Krevelen) pathway — lattice O participates

---

## Step 3 — Surface Intermediates (Associative pathway)

| Species | Bond type | Scales with |
|---------|-----------|------------|
| CO* | C–metal | E_f(CO*) — descriptor 1 |
| O* | O–metal | E_f(O*) — descriptor 2 |
| OH* | O–metal (through O) | E_f(O*): E_f(OH*) ≈ 0.5·E_f(O*) + c |
| H₂O* | O–metal (weak) | E_f(O*): E_f(H₂O*) ≈ 0.3·E_f(O*) + c |
| H* | H–metal | E_f(H*) ≈ 0.22·E_f(CO*) + c |
| COOH* | C–metal + O–metal | Mixed: E_f(COOH*) ≈ 0.5·E_f(CO*) + 0.3·E_f(O*) + c |
| CO₂* | Weakly bound | E_f(CO₂*) ≈ 0.8·E_f(CO*) + c |

---

## Step 4 — Descriptors
$$\boxed{\text{Descriptor 1: }E_f(\text{CO}^*)} \quad \boxed{\text{Descriptor 2: }E_f(\text{O}^*)}$$

Same as CO oxidation — CO* and O* describe all intermediates. This makes physical sense because WGS is essentially CO oxidation by water-derived oxygen.

---

## Step 5 — Linear Scaling Relations

Key new species compared to CO oxidation:

$$E_f(\text{OH}^*) \approx 0.5\,E_f(\text{O}^*) + c_1$$
$$E_f(\text{H}_2\text{O}^*) \approx 0.3\,E_f(\text{O}^*) + c_2$$
$$E_f(\text{COOH}^*) \approx 0.5\,E_f(\text{CO}^*) + 0.3\,E_f(\text{O}^*) + c_3$$

**Physical basis for COOH* scaling:**  
COOH* (carboxyl) has a C–metal bond (like CO*) and one O–H group. The C bond dominates (slope ~0.5 from CO*) but there is a modest O contribution (slope ~0.3 from O*).

---

## Step 6 — Transition States

| Step | Type | BEP slope α | Notes |
|------|------|-------------|-------|
| H₂O* → OH* + H* | O–H bond breaking | α ≈ 0.5 | Symmetric TS |
| CO* + OH* → COOH* | C–O bond formation | **α ≈ 0.6** | Late TS; **often RDS** |
| COOH* + * → CO₂* + H* | C–H bond breaking (indirect) | α ≈ 0.5 | |
| H* + H* → H₂(g) | Recombination | α ≈ 0 | Barrierless on metals |

---

## Step 7 — Rate-Determining Step

**On Cu (LTS catalyst):**
- **COOH* formation** (CO* + OH* → COOH*) is the primary RDS
- DRC: X_RC(COOH* TS) ≈ +0.8 to +1.0
- OH* is partially rate-controlling (X_RC(H₂O* dissociation) ≈ 0.2–0.4)

**On Fe₃O₄ (HTS catalyst):**
- Redox mechanism — CO oxidation by lattice O is RDS at low T
- H₂O re-oxidation of surface is RDS at high CO coverage

**MASI:**
- **Strong CO* binding side**: CO* poisons surface → DRC(CO*) < 0
- **Strong O* binding side**: O*/OH* accumulate → DRC(OH*) < 0
- **Optimal**: Cu sits near the balanced apex for LTS

---

## Step 8 — Volcano Shape and Metal Positions

**Two competing sides of the WGS volcano:**

| Regime | Too-strong CO* binding | Too-weak CO* binding |
|--------|----------------------|---------------------|
| Description | CO* poisons → blocks H₂O activation | CO* doesn't bind → no carboxyl forms |
| MASI | CO* | H* or free surface |
| DRC | DRC(CO*) ≈ −1 | DRC(CO*+OH*→COOH* TS) ≈ +1 |

**Metal activity for WGS:**

| Metal | Activity | Optimal T | Limitation |
|-------|---------|-----------|-----------|
| Cu | **High (LTS)** | 150–250°C | Low T kinetics; CO* just right |
| Fe₃O₄/Cr₂O₃ | **High (HTS)** | 300–500°C | Redox mechanism; different volcano |
| Pt | High | 200–350°C | Slightly too strong CO* binding |
| Au (nanoparticles) | High at low T | 80–150°C | Active near support; anomalous |
| Ni | Moderate | Methanation side reaction at high T |
| Rh | Moderate | Expensive |

---

## Summary Box — WGS

| Item | Answer |
|------|--------|
| Descriptors | E_f(CO*), E_f(O*) |
| RDS (Cu/LTS) | CO* + OH* → COOH* (carboxyl formation) |
| RDS (Fe/HTS) | CO oxidation by lattice O (redox) |
| BEP slope (carboxyl TS) | α ≈ 0.6 |
| MASI (strong CO* side) | CO* |
| MASI (strong O* side) | OH* |
| Optimal metal (LTS) | Cu |
| Key new species vs CO oxidation | COOH*, OH*, H*, H₂O* |
| Key approximation | Mean-field, PSS; redox pathway requires Mars–van Krevelen beyond standard scaling |
| Industrial relevance | Two-stage: HTS (Fe) then LTS (Cu) |



---

# PART 6 — WORKED EXAMPLE: HER AND OER (ELECTROCATALYSIS)

## Overview

### Hydrogen Evolution Reaction (HER)
$$2\text{H}^+(aq) + 2e^- \rightarrow \text{H}_2(g), \quad E^\circ = 0\,\text{V vs. RHE}$$

### Oxygen Evolution Reaction (OER) — reverse of ORR
$$2\text{H}_2\text{O}(l) \rightarrow \text{O}_2(g) + 4\text{H}^+ + 4e^-, \quad E^\circ = +1.23\,\text{V vs. RHE}$$

**Applications:** Water electrolysis (H₂ production), fuel cells (ORR at cathode), batteries.  
**Key feature:** These reactions have a **single-descriptor volcano** — simpler than thermal catalysis.

> **Note:** CatMAP can handle electrochemical reactions by incorporating the electrode potential as an additional free energy term: ΔG = ΔG° − neU, where U is the electrode potential and n is the number of electrons transferred.

---

## PART 6A — HYDROGEN EVOLUTION REACTION (HER)

### Step 1 — Overall Reaction
2H⁺ + 2e⁻ → H₂. Pure kinetic challenge: split water to make H₂ cheaply.  
Overpotential η = E_applied − E_equilibrium is the energy wasted as heat.

### Step 2 — Elementary Mechanism

**Volmer–Heyrovsky (or Volmer–Tafel) pathway:**

| # | Step | Name | Notes |
|---|------|------|-------|
| 1 | H⁺ + e⁻ + * → H* | **Volmer step** | Proton–electron transfer to surface |
| 2a | H* + H⁺ + e⁻ → H₂(g) + * | **Heyrovsky step** | Electrochemical H₂ formation |
| 2b | H* + H* → H₂(g) + 2* | **Tafel step** | Chemical H₂ recombination |

**Which pathway (Heyrovsky vs Tafel)?**
- **Tafel dominates** at high H* coverage (strong binding metals: Pt, Ni, Fe) — two H* meet and recombine
- **Heyrovsky dominates** at low H* coverage (weak binding: Au, Ag) — H* reacts with H⁺ from solution

### Step 3 — Surface Intermediate: Only ONE species!
| Species | Bond type | Descriptor |
|---------|-----------|-----------|
| H* | H–metal bond | **E_f(H*)** — the only descriptor |

This makes HER a **1D volcano** with E_f(H*) (also written as ΔG_H* = ΔG_ads(H*)) as the single axis.

### Step 4 — Single Descriptor
$$\boxed{\text{Single descriptor: }\Delta G_{H^*} = E_f(\text{H}^*) + \text{ZPE corrections} - T\Delta S}$$

At standard conditions (T = 298 K, pH 0): ΔG_H* ≈ E_f(H*) + 0.24 eV (ZPE + entropy correction)

**The Sabatier principle for HER:**
- **ΔG_H* ≪ 0** (left side): H* too stable → H* doesn't release as H₂ → **Tafel/Heyrovsky step is RDS**
- **ΔG_H* ≫ 0** (right side): H* too unstable → Volmer step is RDS (H⁺ won't adsorb)
- **ΔG_H* ≈ 0** (apex): Optimal — both Volmer and Tafel/Heyrovsky are equally fast

### Step 5 — No BEP Needed (Electrochemical Steps)
For electrochemical steps, the free energy change with potential is:
$$\Delta G_{\text{step}} = \Delta G^0_{\text{step}} + eU$$

where U is the electrode potential. The barrier is proportional to |ΔG_step|.

**No separate BEP relation needed** — the energy of each electrochemical step shifts linearly with applied potential. The **minimum overpotential** is determined by the most endergonic step in the free energy diagram at U = 0.

### Step 6 — The HER Volcano Plot (Sabatier–Parsons Volcano)

```
Exchange current   ↑
density j₀         |        Pt ← optimal (ΔG_H* ≈ 0)
(log scale)         |     Ir/Rh
                    |   Ni/   \  Pd
                    |  /       \
                    | /         \ Re, Mo
                    |/            \
                    | Fe, W         \ Au, Ag (too weak)
                    ─────────────────────→ ΔG_H* (eV)
                 strong (< 0)    weak (> 0)
```

**Metal positions on HER volcano:**

| Metal | ΔG_H* (eV) | HER activity | Notes |
|-------|-----------|-------------|-------|
| Pt | **≈ 0** | **Highest** | Industrial standard; both Volmer and Tafel fast |
| Ir, Rh | ≈ −0.1 to −0.2 | High | Slightly strong binding |
| Ni | ≈ −0.3 | Moderate | Strong binding; good in alkaline |
| Pd | ≈ −0.1 | High | Similar to Pt; Pd hydride forms |
| MoS₂ (edge sites) | ≈ 0 | High | Non-precious; edges are active |
| Au | ≈ +0.6 | Low | Too weak H* binding |
| Ag | ≈ +0.7 | Inactive | |
| Cu | ≈ +0.4 | Low at low η | Volcano right side |
| Fe, W | < −0.5 | Moderate | Strong binding → Heyrovsky RDS |

**Engineering insight:** MoS₂ edge sites have ΔG_H* ≈ 0 → non-precious HER catalyst!  
This was discovered computationally by screening the volcano plot.

---

## PART 6B — OXYGEN EVOLUTION REACTION (OER)

### Step 1 — Overall Reaction
$$2\text{H}_2\text{O} \rightarrow \text{O}_2 + 4\text{H}^+ + 4e^-, \quad \Delta G^\circ = +4 \times 1.23\,\text{eV} = +4.92\,\text{eV}$$

**Much harder than HER** — involves 4 coupled electron–proton transfers + O=O bond formation.  
Typical overpotential: **0.3–0.5 V** (vs ≈ 0.05 V for HER on Pt).

### Step 2 — Elementary Mechanism (Acid conditions)

| # | Step | Name | ΔG° at U = 1.23 V |
|---|------|------|-------------------|
| 1 | H₂O + * → OH* + H⁺ + e⁻ | Water adsorption/oxidation | ΔG₁ |
| 2 | OH* → O* + H⁺ + e⁻ | OH* dehydrogenation | ΔG₂ |
| 3 | O* + H₂O → OOH* + H⁺ + e⁻ | Hydroperoxy formation | ΔG₃ |
| 4 | OOH* → O₂(g) + * + H⁺ + e⁻ | O₂ release | ΔG₄ |

**Thermodynamic constraint:** ΔG₁ + ΔG₂ + ΔG₃ + ΔG₄ = 4.92 eV (fixed by overall ΔG)

**Ideal case:** All four steps equally endergonic → ΔGᵢ = 1.23 eV each → zero overpotential  
**Reality:** Scaling relations between OH* and OOH* force ΔG₁ + ΔG₂ ≠ 2.46 eV exactly → **minimum overpotential ≈ 0.3–0.4 V**

### Step 3 — Surface Intermediates and Descriptors

| Species | Bond type | Descriptor |
|---------|-----------|-----------|
| OH* | O–metal | E_f(OH*) or ΔG_OH* |
| O* | O–metal | E_f(O*) |
| OOH* | O–O–metal | E_f(OOH*) ≈ E_f(OH*) + 3.2 eV |

**The critical OOH*/OH* scaling relation:**  
$$\Delta G_{\text{OOH}^*} = \Delta G_{\text{OH}^*} + 3.2\,\text{eV} \quad (±0.2\,\text{eV})$$

This universal scaling relation (Rossmeisl et al., 2007) is the **fundamental reason OER is difficult**:
- The 3.2 eV gap means you **cannot independently optimize** OH* and OOH* binding
- This forces ΔG₁+ΔG₂ ≠ 2×1.23 eV → **theoretical minimum overpotential ≈ 0.4 V**
- No known single metal can beat this — it's a **thermodynamic limit from scaling**

### Step 4 — Single Descriptor for OER
$$\boxed{\text{Single descriptor: }\Delta G_{\text{OH}^*} \text{ (or equivalently, } \Delta G_{\text{O}^*} - \Delta G_{\text{OH}^*}\text{)}}$$

### Step 5 — OER Volcano and Metal Positions

**OER volcano shape:** Symmetric around ΔG_OH* ≈ 1.6 eV

| Metal | ΔG_OH* | OER activity | Notes |
|-------|--------|-------------|-------|
| RuO₂ | ≈ 1.6 eV | **Highest** | Near apex; unstable at high E (dissolves) |
| IrO₂ | ≈ 1.8 eV | **Highest stable** | Industry standard (acidic electrolyzer) |
| MnO₂ | ≈ 1.4 eV | Moderate | Earth-abundant |
| Co₃O₄ | ≈ 1.5 eV | Moderate | Alkaline conditions |
| NiFeOx | ≈ 1.6 eV | High | Best non-precious in alkaline |
| Fe₂O₃ | ≈ 1.2 eV | Low | Too strong O* binding |
| SnO₂ | ≈ 2.5 eV | Low | Too weak |

**Why oxides instead of metals for OER?** On pure metals, O* binding is too strong (O* accumulates) and OH* doesn't oxidize to O* efficiently. Oxides have pre-oxidized surface → better OH* → O* energetics.

---

## HER vs OER Comparison

| Property | HER | OER |
|----------|-----|-----|
| Steps | 2 (Volmer + Tafel/Heyrovsky) | 4 (coupled e⁻–H⁺ transfers) |
| Electrons transferred | 2 | 4 |
| Descriptors | 1 (ΔG_H*) | 1 (ΔG_OH*) |
| Key scaling constraint | H*–H₂ thermoneutral at apex | OOH* ≈ OH* + 3.2 eV (fixed gap) |
| Min. theoretical overpotential | ~0 V (achievable with Pt) | ~0.37 V (thermodynamic limit) |
| Optimal material | Pt (metals) | IrO₂ (oxides) |
| RDS (strong binding) | Heyrovsky/Tafel | O* → OOH* |
| RDS (weak binding) | Volmer | H₂O → OH* |

---

## Summary Box — HER/OER

| Item | HER Answer | OER Answer |
|------|-----------|-----------|
| Descriptor | ΔG_H* | ΔG_OH* |
| Optimal ΔG | ΔG_H* = 0 eV | ΔG_OH* ≈ 1.6 eV |
| Optimal material | Pt (or MoS₂ edges) | IrO₂ (or NiFeOx in alkaline) |
| Key scaling limit | None (can achieve η→0 in principle) | OOH*–OH* gap = 3.2 eV → η_min ≈ 0.37 V |
| BEP relation | Not used (electrochemical) | Not used (electrochemical) |
| How to apply CatMAP | Add electrochemical steps; include potential U as variable | Same; use computational hydrogen electrode (CHE) |



---

# PART 7 — UNIVERSAL EXAM ANSWER TEMPLATES

> **How to use:** When the professor gives you a reaction, copy the relevant template and fill in the blanks. Every blank has a decision rule beneath it telling you exactly what to write.

---

## TEMPLATE A — "Given a reaction, set up the CatMAP microkinetic model"

### A.1 — State the Overall Reaction and Conditions

> "The overall reaction is:
> **[WRITE BALANCED EQUATION]**, ΔH° = **[+ or −]** kJ/mol (**[exothermic/endothermic]**).
> The reaction is carried out at T = **[___]** K and P = **[___]** bar over a **[metal/oxide]** catalyst."

**Decision rules:**
- ΔH° < 0 → exothermic (heat released, product favored at low T)
- ΔH° > 0 → endothermic (heat absorbed, product favored at high T)
- High P favors side with fewer moles of gas (Le Chatelier)

---

### A.2 — Write the Elementary Mechanism

> "The proposed Langmuir–Hinshelwood mechanism consists of **[N]** elementary steps:
>
> **Step 1:** [Reactant A](g) + * ⇌ [A]*  &nbsp;&nbsp;&nbsp;&nbsp;*(adsorption)*
> **Step 2:** [Reactant B](g) + 2* ⇌ 2[B]*  &nbsp;&nbsp;&nbsp;&nbsp;*(dissociative adsorption)*
> **Step k:** [X]* + [Y]* → **[TS_k]** → [Z]* + *  &nbsp;&nbsp;&nbsp;&nbsp;*(surface reaction — BEP applies)*
> **Step N:** [Product]* ⇌ [Product](g) + *  &nbsp;&nbsp;&nbsp;&nbsp;*(desorption)*
>
> Every step is written as reversible (⇌). The net reaction is enforced by thermodynamics via the free energy of the overall process."

**Decision rules for step types:**

| If the molecule... | Write it as... |
|-------------------|----------------|
| Is diatomic (H₂, N₂, O₂) | Dissociative: X₂ + 2* ⇌ 2X* |
| Has a strong triple bond (N₂) | Dissociative, high BEP barrier (α ≈ 0.9–1.0) |
| Is CO, CO₂, NO, H₂O | Molecular: X(g) + * ⇌ X* |
| Is H₂O on reactive metals | May also dissociate: H₂O* + * → OH* + H* |
| Is a product gas (H₂, NH₃, CH₃OH) | Desorption step |

**Number of elementary steps typical by reaction type:**

| Reaction | Typical # steps |
|----------|----------------|
| CO oxidation | 3 |
| HER | 2–3 |
| NH₃ synthesis | 6 |
| WGS | 7–9 |
| CO₂ hydrogenation to MeOH | 11 (formate pathway) |
| Fischer–Tropsch | 15+ |

---

### A.3 — Identify and Justify the Descriptors

> "The two descriptors chosen are:
>
> **Descriptor 1: E_f([X]*)**
> *Justification:* [X]* controls the [C/N/O/H]-chemistry of the reaction. All intermediates containing a [C/N/O/H]–metal bond scale linearly with E_f([X]*) via the Abild-Pedersen universal scaling relations [Ref: Abild-Pedersen et al., PRL 2007].
>
> **Descriptor 2: E_f([Y]*)**
> *Justification:* [Y]* controls the [O/N/H]-chemistry. Specifically, **[name the key step that depends on this descriptor]** requires knowledge of [Y]* binding energy.
>
> These two descriptors are sufficient because all N_int surface intermediates can be expressed as:
> E_f(X*_i) = aᵢ·E_f(desc₁) + bᵢ·E_f(desc₂) + cᵢ
> where cᵢ is fixed by the exact DFT value on a reference metal (e.g., Cu(111))."

**Decision rules for descriptor choice:**

| Reaction chemistry involves... | Choose descriptors... |
|-------------------------------|----------------------|
| C–O bond breaking/forming | CO*, O* |
| N–H bond forming | N*, H* |
| N–O bond breaking | N*, O* |
| C–H bond breaking (methane) | C*, H* |
| Only H chemistry | H* (single descriptor) |
| O-containing intermediates only | O* (or OH*) |
| Mixed C + O + H | CO*, O* (covers all three through scaling) |

---

### A.4 — Write Linear Scaling Relations

> "The formation energies of all surface intermediates are expressed through linear scaling:
>
> | Intermediate | a (desc₁ slope) | b (desc₂ slope) | Physical basis |
> |-------------|----------------|----------------|---------------|
> | [X]* | 1.00 | 0.00 | Descriptor itself |
> | [Y]* | 0.00 | 1.00 | Descriptor itself |
> | [Z]* | [a_Z] | [b_Z] | [Z]* binds through [C/O/N/H] |
> | ... | ... | ... | ... |
>
> The slopes satisfy:
> - a = (number of surface bonds via C) / (total C–surface bonds in parent species)
> - b = (number of surface bonds via O) / (total O–surface bonds in parent species)
>
> The intercepts c are fixed by the exact DFT energy on Cu(111) (or chosen reference metal)."

**Quick slope estimation guide:**

| Species | a (CO*) | b (O*) | Reasoning |
|---------|--------|-------|-----------|
| CO* | 1.00 | 0.00 | Reference |
| O* | 0.00 | 1.00 | Reference |
| H* | 0.22 | 0.00 | Weak correlation with CO* d-band |
| OH* | 0.00 | **0.50** | ½ of O* (one O–surface bond of two) |
| H₂O* | 0.00 | **0.30** | Weak O–surface bond |
| CO₂* | **0.80** | 0.00 | Weak C–surface interaction |
| HCOO* | **0.40** | **0.50** | Bidentate O-bonded formate |
| CH₃O* | **0.10** | **0.60** | O-bonded methoxy (1 bond, O-dominant) |
| CHO* | **0.50** | **0.20** | C-bonded formyl |
| N* | 0.00 | 0.00 | Independent (use as own descriptor) |
| NH* | **0.67**·E_f(N*) | 0.00 | 2/3 of N* bond character |
| NH₂* | **0.33**·E_f(N*) | 0.00 | 1/3 of N* bond character |

---

### A.5 — Identify and Justify Transition States with BEP

> "Transition states are parameterised via Brønsted–Evans–Polanyi (BEP) relations:
> E_a = α·ΔE_rxn + β
>
> where α is the BEP slope (0 = early/reactant-like TS; 1 = late/product-like TS).
>
> The transition states in this mechanism are:
>
> | Step | TS label | BEP slope α | Justification | Constraint type |
> |------|----------|-------------|---------------|----------------|
> | [k] | TS_k | [value] | [bond type + rationale] | initial_state / final_state |
>
> Steps with no activation barrier (barrierless): [list, e.g., H₂ dissociation, product desorption when exothermic]"

**BEP slope selection guide:**

| Bond type broken/formed | Typical α | Example |
|------------------------|----------|---------|
| Diatomic dissociation (N₂, O₂) | **0.9–1.0** | N₂ → 2N* |
| CO₂ activation (CO₂* + H*) | **0.60** | CO₂* + H* → HCOO* |
| Hydrogenation (X* + H* → XH*) | **0.50** | HCOO* + H* → H₂COO* |
| O–H bond formation | **0.50** | O* + H* → OH* |
| C–O bond breaking | **0.70–0.90** | CO* + * → C* + O* |
| C–O bond formation | **0.50–0.70** | CO* + OH* → COOH* |
| N–H bond formation | **0.50** | N* + H* → NH* |
| Recombinative desorption (H* + H*) | **0–0.30** | H* + H* → H₂ + 2* |

---

### A.6 — State All Approximations

> "The CatMAP microkinetic model employs the following approximations:
>
> 1. **Mean-field (Langmuir–Hinshelwood) kinetics:** All surface sites are treated as equivalent; adsorbate–adsorbate lateral interactions are neglected. The rate of step i is r_i = k_f,i·∏_j θ_j^ν_j − k_r,i·∏_j θ_j^ν'_j.
>
> 2. **Pseudo-steady-state (PSS) approximation:** The time derivatives of all surface coverages are set to zero: dθ_i/dt = 0 ∀i. This gives a system of nonlinear algebraic equations solved numerically.
>
> 3. **Linear scaling relations:** E_f(X*) = a·E_f(desc₁) + b·E_f(desc₂) + c. Valid because the d-band center governs all surface–adsorbate bond strengths, and adjacent adsorbates on transition metals show linear correlation. Breaks down for: strongly interacting adsorbates, alloys with unusual electronic structure, bifunctional sites.
>
> 4. **BEP relations:** E_a = α·ΔE_rxn + β. Linear correlation between activation barrier and reaction energy. Breaks down for: very exo/endothermic steps (curvature of Marcus parabola), non-adiabatic processes.
>
> 5. **Frozen adsorbate approximation:** Surface intermediates are treated as having zero vibrational entropy contribution. Free energy of surface species ≈ DFT energy only. Gas-phase species use full Shomate thermochemistry.
>
> 6. **Ideal gas approximation:** Gas-phase species follow PV = nRT. G(T,P) = G°(T) + RT·ln(P/P°).
>
> 7. **Thermodynamic consistency:** All elementary steps satisfy detailed balance: k_f/k_r = exp(−ΔG_step/k_BT). The equilibrium constant for each step is fixed by thermodynamics, independent of the BEP parameters.
>
> 8. **[If applicable] Dummy adsorption step:** If a descriptor species (e.g., CO*) does not appear naturally in the mechanism, a dummy reversible step is added at negligible partial pressure (P ≈ 10⁻²⁰ atm) to anchor the descriptor in the scaling matrix without affecting coverages or kinetics."

---

## TEMPLATE B — "Explain the Volcano Plot for [Reaction]"

### B.1 — Standard 5-Sentence Volcano Explanation

> "1. The volcano shape arises from the **Sabatier principle**: the optimal catalyst binds surface intermediates neither too strongly nor too weakly.
>
> 2. On the **strong-binding side** (left, E_f(desc) ≪ 0), **[name the MASI]** is excessively stabilised on the surface, occupying active sites and preventing further reaction. The degree of rate control (DRC) of **[MASI]** is approximately −1, confirming it as a surface inhibitor.
>
> 3. On the **weak-binding side** (right, E_f(desc) ≫ 0), **[name the endergonic step]** becomes thermodynamically unfavourable (ΔG > 0), suppressing the rate. The DRC of **[first adsorption/activation TS]** is approximately +1.
>
> 4. At the **volcano apex**, the binding energy is balanced: the activation barriers of all elementary steps are minimised simultaneously. Metal **[X]** sits nearest the apex at (E_f(desc₁), E_f(desc₂)) = (**[value]**, **[value]**) eV.
>
> 5. The **diagonal orientation** of the activity ridge (in 2D) reflects the correlated scaling of **[intermediate 1]** and **[intermediate 2]** with both descriptors; moving along the ridge keeps both intermediates at moderate binding energy, maintaining high activity."

---

### B.2 — "What limits the rate on [specific metal]?"

**Answer template (fill in blanks):**

> "On **[metal X]**, which sits on the **[strong/weak]-binding side** of the volcano at (E_f(CO*), E_f(O*)) = (**[value]**, **[value]**) eV:
>
> - The most abundant surface intermediate (MASI) is **[species]** with E_f = **[value]** eV, indicating **[deep/shallow]** thermodynamic stabilisation.
> - This leads to **[high/low]** steady-state coverage of **[species]**, blocking **[___]**% of active sites.
> - The degree of rate control is X_RC(**[species or TS]**) ≈ **[value]**, confirming it as the **[rate-limiting step / surface inhibitor]**.
> - The predicted log₁₀(TOF) ≈ **[value]** s⁻¹, which is **[N]** orders of magnitude **[below/above]** the optimal metal."

---

## TEMPLATE C — "Identify the Rate-Determining Step (RDS)"

> "The rate-determining step (RDS) is identified by:
>
> **Method 1 — Free Energy Diagram (qualitative):**
> The RDS is the elementary step with the **largest activation barrier** (highest transition state peak) in the free energy diagram at the operating conditions.
>
> **Method 2 — DRC Analysis (quantitative):**
> The RDS is the step i for which the degree of rate control X_RC,i = (∂ ln r / ∂ ln k_i)|_{K_eq, k_{j≠i}} ≈ +1.
>
> **For [reaction name] on [metal]:**
> - The largest free-energy barrier is the **[step name]** (Step [k]) with E_a ≈ **[value]** eV (apparent) or **[value]** eV (intrinsic).
> - DRC analysis confirms: X_RC(**[step k]**) ≈ +1 at the descriptor coordinates of **[metal]**.
> - A secondary contribution comes from **[step j]** with X_RC ≈ **[0.2–0.5]**, indicating it is **partially co-limiting**.
> - The sum rule ∑_i X_RC,i = 1 is satisfied: **[value_k]** + **[value_j]** ≈ 1.
>
> **Physical interpretation:**
> The RDS is rate-limiting because **[physical reason: e.g., 'the N≡N triple bond (945 kJ/mol) requires a very high activation energy to dissociate' / 'the HCOO*+H* → H₂COO* step involves forming a strained dioxymethylene intermediate']**."

---

## TEMPLATE D — "What are the descriptors and why are 2 sufficient?"

> "**Descriptor 1: E_f([X]*)** — chosen because [X]* controls the [C/N/O]-bond chemistry. All [C/N/O]-containing surface intermediates scale linearly with E_f([X]*) through the universal Abild-Pedersen relation.
>
> **Descriptor 2: E_f([Y]*)** — chosen because [Y]* controls the [O/H]-chemistry. Specifically, the energetics of **[key step]** depend primarily on E_f([Y]*).
>
> **Why only 2 descriptors are sufficient:**
> By the d-band centre theory (Hammer & Nørskov, 1995), a single electronic parameter — the d-band centre ε_d — governs the strength of all metal–adsorbate bonds on a given metal. Consequently, all adsorption energies scale linearly with each other. For reactions involving C and O chemistry, the d-band centre manifests as the CO* and O* binding energies. The full N_int-dimensional space of intermediate energies is therefore reduced to 2 dimensions via:
> E_f(X*_i) = aᵢ·E_f(CO*) + bᵢ·E_f(O*) + cᵢ
> The coefficients aᵢ and bᵢ are universal (independent of metal) to within ±0.2 eV, as validated by R² > 0.95 in linear regressions across 8+ transition metals.
>
> **Limitation:** The 2-descriptor framework breaks down when:
> - The reaction involves species with unusual electronic structure (e.g., spin-polarised N* on Fe)
> - The catalyst is a bimetallic alloy where the two metals independently control different sites
> - Adsorbate–adsorbate interactions are strong (high coverage regimes)"

---

## TEMPLATE E — "Draw/Describe the Free Energy Diagram (FED)"

> "The free energy diagram at T = [___] K shows the Gibbs free energy of each state along the reaction coordinate, referenced to **[gas-phase reactants] = 0 eV**.
>
> **Construction procedure:**
> 1. Set reference: G(reactants_gas) = 0
> 2. Add adsorption steps: G(X*) = G(ref) + E_f(X*) + corrections
> 3. Add surface intermediates in order along pathway
> 4. Add transition state peaks at G(TS_k) = G(reactant state) + E_a,k
> 5. End at G(products_gas) = −ΔG_rxn (thermodynamic endpoint)
>
> **For [metal] at T = [___] K:**
>
> | State | G (eV) | Notes |
> |-------|--------|-------|
> | [Reactants](g) | 0.000 | Reference |
> | [X]* + ... | [value] | Adsorption step |
> | TS1 | [value] | E_a = [value] eV from previous state |
> | [Intermediate 1]* | [value] | First surface intermediate |
> | TS2 (RDS) | **[value]** | **Highest point — RDS** |
> | [Intermediate 2]* | [value] | |
> | [Products](g) | [value] | ΔG_rxn = − [value] eV |
>
> **Key observation:** The FED reveals:
> - The RDS (step with largest ΔG‡ = ΔG_TS − ΔG_preceding_state)
> - The MASI (state with most negative G in the pathway)
> - Thermodynamic feasibility (final G < initial G for exergonic overall reaction)"

---

## TEMPLATE F — "CatMAP Setup Checklist (for .mkm file)"

When asked to describe CatMAP implementation for any reaction:

```
# CatMAP input file (.mkm) for [REACTION NAME]

# 1. REACTION EXPRESSIONS — elementary steps
rxn_expressions = [
    '[A](g) + * <-> [A]*',                         # Step 1: adsorption
    '[B2](g) + 2* <-> 2[B]*',                       # Step 2: dissociative adsorption
    '[A]* + [B]* <-> [TS1] <-> [AB]* + *',         # Step 3: surface rxn (BEP)
    '[AB]* <-> [AB](g) + *',                        # Step 4: desorption
]

# 2. SURFACE SPECIES — all surface intermediates
surface_species_names = ['A', 'B', 'AB', 'TS1']

# 3. DESCRIPTORS — the two binding energies
descriptor_names = ['[X]_s', '[Y]_s']   # e.g., 'CO_s', 'O_s'
descriptor_ranges = [[-1.5, 1.5], [-0.5, 2.0]]  # [min, max] in eV

# 4. SCALING RELATIONS — for all intermediates
scaling_constraint_dict = {
    '[A]_s': ['[X]_s', 1.0, 0.0, c_A],   # E_f(A*) = 1.0*E_f(X*) + 0*E_f(Y*) + c_A
    '[B]_s': ['[Y]_s', 0.0, 1.0, c_B],
    '[AB]_s': ['[X]_s', 0.5, '[Y]_s', 0.3, c_AB],
    '[TS1]': [initial_state, alpha_1],    # BEP from initial state
}

# 5. BEP PARAMETERS
brønsted_evans_polanyi_parameters = {
    '[TS1]': [alpha_1, beta_1],   # E_a = alpha * dE_rxn + beta
}

# 6. OPERATING CONDITIONS
temperature = [513]   # K
pressure_list = [0.2, 0.6, 1e-3, 1e-3]  # [P_A, P_B, P_C, P_D] in atm
decimal_precision = 100   # mpmath precision digits

# 7. SOLVER SETTINGS
max_rootfinding_iterations = 100
tolerance = 1e-50
```

---

## PART 8 — MASTER COMPARISON TABLE (All Reactions)

| Property | CO₂→MeOH | NH₃ Synthesis | CO Oxidation | NO Reduction | WGS | HER |
|----------|-----------|--------------|-------------|-------------|-----|-----|
| **Descriptors** | CO*, O* | N*, H* | CO*, O* | N*, O* | CO*, O* | H* |
| **# Descriptors** | 2 | 1–2 | 2 | 2 | 2 | **1** |
| **# Elem. steps** | 11 | 6 | 3 | 5 | 7–9 | 2–3 |
| **RDS** | HCOO*+H*→H₂COO* | N₂ dissociation | CO*+O*→CO₂ | NO dissociation | CO*+OH*→COOH* | Tafel or Volmer |
| **BEP (RDS) α** | 0.50 | 0.90–1.00 | 0.50–0.70 | 0.90 | 0.60 | N/A (electrochemical) |
| **MASI (strong)** | CH₃O* | N* | CO* | N* + O* | CO* | H* |
| **MASI (weak)** | CH₃OH* | H* | free surface | free surface | free surface | free surface |
| **Optimal metal** | Cu | Ru > Fe | Pt | Rh | Cu | Pt; MoS₂ edges |
| **Inactive (weak)** | Ag | Cu, Au | Au (bulk) | Cu, Au | Au | Ag, Au |
| **Inactive (strong)** | Rh, Ni | Mo, W | Fe, Ni | Fe | Fe, Co | W, Mo |
| **Volcano type** | 2D | 1D (or 2D) | 2D | 2D | 2D | **1D** |
| **Key BEP step** | 2 BEP steps | 1 (N₂ diss.) | 1 (CO*+O*) | 1 (NO diss.) | 1 (carboxyl) | 0 (electrochemical) |

---

## PART 9 — DECISION FLOWCHART: ANY REACTION

When the professor gives you **any** catalytic reaction, follow this flowchart:

```
GIVEN: A(g) + B(g) → C(g) + D(g)
         |
         ▼
STEP 1: What elements are involved?
    Contains C? → CO* is likely a descriptor
    Contains N? → N* is likely a descriptor  
    Contains O? → O* is likely a descriptor
    Only H? → H* single descriptor (HER-type)
         |
         ▼
STEP 2: What bonds are broken?
    X≡X triple bond (N₂, CO) → high BEP α (0.9–1.0), likely RDS
    X=X double bond (O₂, NO) → medium-high α (0.7–0.9)
    X–X single bond → medium α (0.5–0.7)
    X–H bond → α ≈ 0.5 (symmetric hydrogenation TS)
         |
         ▼  
STEP 3: What are the key intermediates?
    Draw all X* species → classify as C-bonded, O-bonded, N-bonded, mixed
    Assign scaling slopes using the table in STEP 5 of the 8-step procedure
         |
         ▼
STEP 4: Choose 2 descriptors
    Use the descriptor pair table (Part 1, Step 4)
    Rule: one descriptor per "atom type" that bonds to surface
         |
         ▼
STEP 5: Predict RDS qualitatively
    Strongest bond broken → highest α → likely RDS
    Most endergonic step in FED → likely RDS
         |
         ▼
STEP 6: Predict MASI qualitatively
    Most stable intermediate (most negative E_f) → likely MASI
    On strong-binding metals: first intermediate after RDS
    On weak-binding metals: last intermediate before RDS
         |
         ▼
STEP 7: Predict volcano shape
    Left side (strong binding): MASI = first key intermediate → blocks sites
    Right side (weak binding): First activation step becomes endergonic → no reaction
    Apex: metal with balanced E_f for both descriptors
         |
         ▼
STEP 8: Name the optimal metal
    Use the master comparison table or extrapolate from d-band trends:
    Moving left-to-right across a period: binding energy decreases
    Moving down a group: binding energy decreases
    Rule of thumb: 2nd row noble metals (Ru, Rh, Pd) often near optimal
```

---

## PART 10 — COMMON MISTAKES TO AVOID

| Mistake | Correct approach |
|---------|-----------------|
| Writing BEP for adsorption steps | BEP applies only to **activated** steps. Adsorption/desorption use van't Hoff: k = A·exp(−ΔG/k_BT) |
| Choosing too many descriptors | Maximum 2 for transition metals; choosing 3+ is overcomplete — use dimensionality reduction |
| Forgetting the dummy CO step | If CO* is a descriptor but doesn't appear in mechanism → add dummy step at P(CO) ≈ 10⁻²⁰ atm |
| Saying "scaling always has R² = 1" | Real scaling has scatter ±0.2 eV; claim R² > 0.95 as validation threshold |
| Confusing DRC with conversion | DRC measures kinetic sensitivity, not thermodynamic conversion. X_RC = +1 means doubling k_i doubles TOF; it says nothing about equilibrium |
| Ignoring MASI in rate expression | The PSS equations must include the site balance: ∑θᵢ + θ_* = 1. MASI reduces θ_* → reduces rate |
| Wrong BEP constraint type | If TS appears early in reaction coordinate → `initial_state`; if late → `final_state`. Wrong choice shifts entire activity volcano |
| Forgetting to verify the RDS changes across volcano | RDS is not the same on all metals. It changes from kinetic (TS-limited) at apex to thermodynamic (desorption-limited) at strong-binding extreme |

