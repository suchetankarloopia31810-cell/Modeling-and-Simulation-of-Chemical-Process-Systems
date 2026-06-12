# CHAPTER 5 — RATE OF GENERATION IN MOMENTUM, ENERGY AND MASS TRANSPORT

> Chapter 5 has **no problems section** — it is entirely theory and worked examples.  
> All five examples are reproduced here with full solutions because they are **examinable**.

---

## 5.1 Rate of Generation in Momentum Transport

### 5.1.1 Gravitational Force Contribution
When a body of mass M is subject to gravity, Newton's 2nd law gives:

$$\text{Rate of momentum generation} = Mg$$

Per unit volume:
$$\boxed{\mathfrak{R}_{grav} = \rho g}$$

### 5.1.2 Pressure Force Contribution
For steady flow of an incompressible fluid through a pipe of cross-sectional area A and length L:

$$\mathfrak{R}_{press} = \frac{|\Delta P|}{L}$$

This is the pressure gradient driving the flow.

### 5.1.3 Modified Pressure
The combined effect of pressure + gravity is captured in the **modified pressure** P̄:

$$\boxed{\bar{P} = P + \rho g h}$$

where h is the elevation measured **opposite** to the direction of gravity. Any variation in P̄ indicates flow; under static conditions P̄ = constant throughout the fluid.

**Key advantage:** The pressure drop ΔP̄ is **independent of pipe orientation** — the same formula applies whether the pipe is horizontal, inclined, or vertical (Table 5.1 in the book).

| Pipe orientation | ΔP (actual) | ΔP̄ (modified) |
|-----------------|-------------|---------------|
| Horizontal | (ρ_m − ρ)gH | same |
| Inclined at θ | (ρ_m − ρ)gH + ρgL sinθ | same |
| Vertical | (ρ_m − ρ)gH + ρgL | same |

---

## 5.2 Rate of Generation in Energy Transport

Energy can be "generated" (degraded from higher to lower quality forms) by:
- Viscous dissipation (mechanical → thermal)
- Electrical resistance heating (electrical → thermal)  
- Chemical reactions
- Absorption of radiation
- Nuclear reactions

The generation rate per unit volume ℜ may be:
- Constant (uniform)
- Temperature-dependent: ℜ = a + bT  or  ℜ = ℜ₀ e^{aT}

---

## 5.3 Rate of Generation in Mass Transport

### 5.3.1 Stoichiometry
For a reaction written as:
$$\sum_{i=1}^{s} \alpha_i A_i = 0$$

The **stoichiometric coefficient** α_i is **positive for products, negative for reactants**.

**Element balance** to find stoichiometric coefficients:
$$\sum_{i=1}^{s} \alpha_i \beta_{ji} = 0 \quad \text{for each element } j$$

where β_{ji} = number of atoms of element j in species i.

---

### 5.3.2 Law of Combining Proportions

$$\frac{n_i - n_{io}}{\alpha_i} = \varepsilon \quad \text{(molar extent of reaction)}$$

Rearranging:
$$\boxed{n_i = n_{io} + \alpha_i \varepsilon}$$

**Fractional conversion** of species i:
$$X_i = \frac{n_{io} - n_i}{n_{io}}$$

Relationship between ε and X:
$$\varepsilon = \frac{n_{io}}{(-\alpha_i)} X_i$$

**Limiting reactant**: species with the **smallest** value of n_{io}/(−α_i). The reaction goes to completion when ε reaches this value.

**Intensive extent** (per unit volume):
$$\xi = \varepsilon/V \implies c_i = c_{io} + \alpha_i \xi$$

**Total moles at any time:**
$$n_T = n_{To} + \alpha\,\varepsilon, \quad \alpha = \sum_i \alpha_i$$

---

### 5.3.3 Rate of Reaction

$$r = \frac{1}{V}\frac{d\varepsilon}{dt} > 0 \text{ always}$$

Rate of generation of species i per unit volume:
$$\mathfrak{R}_i = \alpha_i r$$

For multiple reactions j:
$$\mathfrak{R}_i = \sum_j \alpha_{ij} r_j$$

**Arrhenius rate constant:**
$$k(T) = A\,e^{-E/RT}$$

**Power-law rate expression:**
$$r = k(T)\prod_i c_i^{\gamma_i}$$

The **reaction order** n = Σγ_i.

---

## 5.4 Worked Examples (Exam-Level)

---

### Example 5.1 (Balancing a Reaction)
**Balance:** α₁N₂ + α₂H₂ + α₃NH₃ = 0

**Solution:**
- E₁ = N (j=1), E₂ = H (j=2)
- β matrix: N₂ has 2 N, 0 H; H₂ has 0 N, 2 H; NH₃ has 1 N, 3 H

Element N: 2α₁ + 0·α₂ + 1·α₃ = 0 → α₁ = −α₃/2

Element H: 0·α₁ + 2α₂ + 3α₃ = 0 → α₂ = −3α₃/2

Choose α₃ = +2 (NH₃ is product):
$$\alpha_1 = -1,\quad \alpha_2 = -3,\quad \alpha_3 = +2$$

$$\boxed{N_2 + 3H_2 \rightarrow 2NH_3}$$

---

### Example 5.2 (Limiting Reactant & Conversions)
**System:** 1 mol A₁, 2 mol A₂, 7 mol A₃  
**Reaction:** A₁ + A₂ + 3/2 A₃ → A₄ + 3A₅

**Find:** limiting reactant; conversions at completion.

**Solution:**

| Species | n_{io} | −α_i | n_{io}/(−α_i) |
|---------|--------|------|---------------|
| A₁ | 1 | 1 | **1.0** ← smallest = limiting |
| A₂ | 2 | 1 | 2.0 |
| A₃ | 7 | 3/2 | 4.67 |

At completion: ε = 1 (limited by A₁)

Moles remaining:
- n₁ = 1 − 1(1) = 0
- n₂ = 2 − 1(1) = 1 mol
- n₃ = 7 − (3/2)(1) = 5.5 mol
- n₄ = 0 + 1(1) = 1 mol
- n₅ = 0 + 3(1) = 3 mol

Fractional conversions:
$$X_1 = \frac{1-0}{1} = 1.0 \quad X_2 = \frac{2-1}{2} = 0.50 \quad X_3 = \frac{7-5.5}{7} = 0.214$$

---

### Example 5.3 (Mole Fractions at Given Extent)
**System:** 3 mol A₁, 4 mol A₂; Reaction: 2A₁ + 3A₂ → A₃ + 2A₄; ε = 1.1

**Solution:**

Using n_i = n_{io} + α_i ε:
- n₁ = 3 − 2(1.1) = 0.8 mol
- n₂ = 4 − 3(1.1) = 0.7 mol
- n₃ = 0 + 1(1.1) = 1.1 mol
- n₄ = 0 + 2(1.1) = 2.2 mol

Total: n_T = 0.8 + 0.7 + 1.1 + 2.2 = 4.8 mol

Mole fractions:
$$x_1 = 0.167, \quad x_2 = 0.146, \quad x_3 = 0.229, \quad x_4 = 0.458$$

**Limiting reactant:** n_{io}/(−α_i): A₁ → 3/2 = 1.5, A₂ → 4/3 = 1.33 → **A₂ is limiting**

Conversion of A₂: $X_{A_2} = (4 - 0.7)/4 = 0.825$

---

### Example 5.4 (Simultaneous Reactions)
**Two reactions in batch reactor:**
1. C₂H₆ → C₂H₄ + H₂ (ε₁)
2. C₂H₆ + H₂ → 2CH₄ (ε₂)

**Feed:** 85% C₂H₆, 15% inerts (basis: 1 mol mixture)  
**Products observed:** 25 mol% C₂H₄, 5 mol% CH₄

**Solution:**

Species moles using Eq. (5.3-21): $n_i = n_{io} + \sum_j \alpha_{ij}\varepsilon_j$

| Species | n_{io} | Rxn 1 | Rxn 2 | n_i |
|---------|--------|-------|-------|-----|
| C₂H₆ | 0.85 | −1 | −1 | 0.85 − ε₁ − ε₂ |
| C₂H₄ | 0 | +1 | 0 | ε₁ |
| H₂ | 0 | +1 | −1 | ε₁ − ε₂ |
| CH₄ | 0 | 0 | +2 | 2ε₂ |
| Inerts | 0.15 | 0 | 0 | 0.15 |

α₁ = Σα_i(rxn 1) = −1+1+1 = +1; so n_T = 1 + ε₁

From x(C₂H₄) = 0.25:
$$\frac{\varepsilon_1}{1+\varepsilon_1} = 0.25 \implies \varepsilon_1 = 0.333$$

From x(CH₄) = 0.05:
$$\frac{2\varepsilon_2}{1+\varepsilon_1} = 0.05 \implies \varepsilon_2 = \frac{0.05(1.333)}{2} = 0.033$$

Composition:

| Species | Moles | Mole % |
|---------|-------|--------|
| C₂H₆ | 0.85 − 0.333 − 0.033 = 0.484 | **36.3%** |
| C₂H₄ | 0.333 | **25.0%** |
| H₂ | 0.333 − 0.033 = 0.300 | **22.5%** |
| CH₄ | 0.066 | **5.0%** |
| Inerts | 0.150 | **11.2%** |
| **Total** | **1.333** | **100%** |

---

### Example 5.5 (Reaction Rate Expressions)
**Reaction:** 3A → B + C

Express r in terms of d[A]/dt, d[B]/dt, d[C]/dt.

**Solution:**

Using r = (1/α_i)(1/V)(dn_i/dt) with α_A = −3, α_B = +1, α_C = +1:

$$r = \frac{1}{-3}\cdot\frac{1}{V}\frac{dn_A}{dt} = \frac{1}{+1}\cdot\frac{1}{V}\frac{dn_B}{dt} = \frac{1}{+1}\cdot\frac{1}{V}\frac{dn_C}{dt}$$

For constant volume (V = const.), n_i = c_i V:

$$\boxed{r = -\frac{1}{3}\frac{dc_A}{dt} = \frac{dc_B}{dt} = \frac{dc_C}{dt}}$$

**Important:** The rate of change of concentration equals the reaction rate only when volume is constant. The rate r itself is always positive (it is defined as the rate of advancement of the reaction).

---

## 5.5 Key Formulas Summary — Chapter 5

| Concept | Formula |
|---------|---------|
| Momentum generation (gravity) | ℜ = ρg |
| Momentum generation (pressure) | ℜ = \|ΔP\|/L |
| Modified pressure | P̄ = P + ρgh |
| Moles of species i | n_i = n_{io} + α_i ε |
| Molar concentration of i | c_i = c_{io} + α_i ξ |
| Total moles | n_T = n_{To} + αε |
| Fractional conversion | X_i = (n_{io} − n_i)/n_{io} |
| Extent and conversion | ε = n_{io} X_i/(−α_i) |
| Generation rate of i | ℜ_i = α_i r |
| Rate constant | k = A e^{−E/RT} |
| Reaction rate (power law) | r = k ∏ c_i^{γ_i} |
| Reaction order | n = Σγ_i |

---

## 5.6 Critical Exam Points for Chapter 5

1. **Modified pressure eliminates the need to track pipe orientation** — only ΔP̄ matters for flow problems.

2. **Stoichiometric coefficients are signed**: products positive, reactants negative. The reaction rate r is always positive.

3. **Limiting reactant** = species with smallest n_{io}/(−α_i).

4. **Molar extent ε is extensive** (in mol); intensive extent ξ = ε/V (in mol/m³). For a CSTR, ξ relates to conversion: ξ = c_{io} X_i/(−α_i).

5. **Arrhenius relationship:** ln(k) vs. 1/T gives a straight line with slope −E/R. The activation energy E quantifies temperature sensitivity.

6. **Multiple reactions:** each has its own extent ε_j. The total change in moles of species i is Σ_j α_{ij} ε_j.
