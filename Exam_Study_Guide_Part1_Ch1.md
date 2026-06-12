# Exam Study Guide — Modeling & Simulation of Chemical Process Systems
## Source: Ismail Tosun, *Modelling in Transport Phenomena* (Elsevier, 2007)
### Chapters 1 · 2 · 5 · 6 · 7 + CatMAP (CO₂ Hydrogenation to Methanol)

---

# CHAPTER 1 — INTRODUCTION

## 1.1 Key Concepts

### The Inventory Rate Equation
The single most important equation in the entire book:

$$\underbrace{\dot{n}_{in}}_{\text{Rate in}} - \underbrace{\dot{n}_{out}}_{\text{Rate out}} + \underbrace{\dot{n}_{gen}}_{\text{Rate of generation}} = \underbrace{\dot{n}_{acc}}_{\text{Rate of accumulation}}$$

This applies to every conserved quantity: **mass, momentum, energy, chemical species**.

| Condition | Simplification |
|-----------|---------------|
| Steady-state | Accumulation = 0 |
| No generation | Generation = 0 |
| Steady-state + no generation | Rate in = Rate out |
| Steady-state + generation | Rate in + Rate gen = Rate out |

---

### Levels of Application

| Level | Theory | Experiment |
|-------|--------|-----------|
| Microscopic | Equations of Change (PDEs) | Constitutive Equations |
| Macroscopic | Design Equations (ODEs) | Process Correlations |

---

### Important Definitions

**Steady-State**: Dependent variable does not change with time at a fixed location:
$$\left(\frac{\partial \phi}{\partial t}\right)_{x,y,z} = 0$$

**Uniform**: Dependent variable does not change with position at a fixed instant:
$$\frac{\partial \phi}{\partial x} = \frac{\partial \phi}{\partial y} = \frac{\partial \phi}{\partial z} = 0$$

**Equilibrium**: Both steady-state AND uniform simultaneously.

**Flux**: 
$$\text{Flux} = \frac{\text{Flow rate of a quantity}}{\text{Area perpendicular to flow}}$$

Units: Momentum flux → Pa (N/m²), Energy flux → W/m², Mass flux → kg/m²·s, Molar flux → kmol/m²·s

---

### Rate of Generation Term

$$\text{Generation rate} = \begin{cases} \mathfrak{R} \cdot V & \text{if } \mathfrak{R} = \text{constant} \\ \int\!\!\int\!\!\int_V \mathfrak{R}\, dV & \text{if } \mathfrak{R} = \mathfrak{R}(\mathbf{r}) \end{cases}$$

### Rate of Accumulation Term

$$\text{Accumulation rate} = \frac{d}{dt}\!\int\!\!\int\!\!\int_V \rho\hat{\phi}\, dV = \frac{d(m\hat{\phi})}{dt}$$

---

## 1.2 Worked Problems

---

### Problem 1.1
**Statement:** A friend writes the inventory rate equation for money as:
> (Change in amount of dollars) = (Interest) − (Service charge) + (Dollars deposited) − (Checks written)

Identify the terms.

**Solution:**

Rearrange to match the standard form: IN − OUT + GENERATION = ACCUMULATION

| Term | Role |
|------|------|
| Dollars deposited | Rate of **input** |
| Checks written | Rate of **output** |
| Interest | Rate of **generation** (money created) |
| Service charge | Rate of **depletion** (negative generation) |
| Change in amount of dollars | Rate of **accumulation** |

So the equation should really read:
$$(\text{Dollars deposited}) - (\text{Checks written}) + (\text{Interest}) - (\text{Service charge}) = (\text{Change in dollars})$$

This matches Eq. (1.1-1) exactly: IN − OUT + GEN = ACC.

---

### Problem 1.2
**Statement:** Determine whether steady or unsteady-state conditions prevail:
(a) Height of water in a dam during heavy rain
(b) Weight of an athlete during a marathon
(c) Temperature of an ice cube as it melts

**Solution:**

Recall: Steady-state means the dependent variable does NOT change with time at any fixed location, i.e., ∂ϕ/∂t = 0.

**(a) Water height in a dam during heavy rain:**
Rain is continuously adding water. The inlet flow rate ≠ outlet flow rate (assuming the dam is filling). Therefore dh/dt ≠ 0.
**→ UNSTEADY-STATE**

**(b) Weight of an athlete during a marathon:**
The athlete burns calories/fat and loses water through sweat throughout the race, so body mass decreases with time.
**→ UNSTEADY-STATE**

**(c) Temperature of an ice cube as it melts:**
The ice undergoes a phase change. During melting at constant pressure, the temperature remains constant at 0°C (latent heat absorbed at constant T). *However*, once the phase change is complete, temperature rises. During the melting process itself, T is constant in time and space throughout the ice.
**→ STEADY-STATE** (during the phase-change process, T = 0°C = constant throughout)

> **Note:** Strictly, if we consider the gradient inside the ice as melting proceeds from the surface inward, it is transient. But at the level of macroscopic analysis (bulk temperature), the ice-water mixture stays at 0°C throughout melting → steady-state is often the intended answer.

---

### Problem 1.3
**Statement:** What is the form of the function ϕ(x, y) if ∂²ϕ/∂x∂y = 0?

**Answer given:** ϕ(x, y) = f(x) + h(y) + C

**Solution:**

Starting from:
$$\frac{\partial^2 \phi}{\partial x \partial y} = 0$$

Integrate once with respect to x:
$$\frac{\partial \phi}{\partial y} = g(y)$$

where g(y) is an arbitrary function of y only (the "constant" of integration w.r.t. x is allowed to be a function of y).

Integrate once with respect to y:
$$\phi = \int g(y)\, dy + f(x) = h(y) + f(x)$$

where f(x) is the "constant" of integration w.r.t. y (allowed to depend on x), and h(y) = ∫g(y)dy.

Adding an arbitrary constant C:

$$\boxed{\phi(x, y) = f(x) + h(y) + C}$$

**Physical meaning:** The mixed partial being zero means the function is separable — the x-dependence and y-dependence are completely independent (additive).

---

### Problem 1.4
**Statement:** Steam at 200°C flows through a pipe of 5 cm inside diameter, 6 cm outside diameter, and 30 m length. Steady rate of heat loss per unit length = 2 W/m. Find heat fluxes at inner and outer surfaces.

**Answer given:** 12.7 W/m² at inner surface; 10.6 W/m² at outer surface

**Solution:**

**Step 1: Total heat transfer rate**

Given: heat loss per unit length = 2 W/m, length L = 30 m
$$\dot{Q} = 2\,\text{W/m} \times 30\,\text{m} = 60\,\text{W}$$

**Step 2: Heat flux at inner surface**

The inner surface area:
$$A_{inner} = \pi D_i L = \pi (0.05)(30) = 4.712\,\text{m}^2$$

$$q_{inner} = \frac{\dot{Q}}{A_{inner}} = \frac{60}{4.712} = \boxed{12.73 \approx 12.7\,\text{W/m}^2}$$

**Step 3: Heat flux at outer surface**

The outer surface area:
$$A_{outer} = \pi D_o L = \pi (0.06)(30) = 5.655\,\text{m}^2$$

$$q_{outer} = \frac{\dot{Q}}{A_{outer}} = \frac{60}{5.655} = \boxed{10.61 \approx 10.6\,\text{W/m}^2}$$

**Key insight:** In cylindrical geometry with constant heat transfer rate, the flux changes with radius because area changes — even though no energy is generated in the pipe wall.

---

### Problem 1.5
**Statement:** Dust evolves at 0.3 kg/h in a foundry (20 m × 8 m × 4 m). Maximum allowable concentration = 20 mg/m³. Find required ventilation volumetric flow rate.

**Answer given:** 15,000 m³/h

**Solution:**

**System:** Air in the foundry room
**Assumptions:** Steady-state, perfect mixing → concentration is uniform throughout

At steady-state, the dust concentration must NOT exceed cₘₐₓ = 20 mg/m³ = 20 × 10⁻⁶ kg/m³.

**Mass balance on dust at steady-state:**

$$\dot{m}_{in} - \dot{m}_{out} + \dot{m}_{gen} = 0$$

The dust enters via generation only (no dust in ventilating air):
- $\dot{m}_{gen}$ = 0.3 kg/h (dust produced)
- $\dot{m}_{in}$ = 0 (clean air enters with no dust)
- $\dot{m}_{out}$ = $Q \cdot c_{dust}$ (dust leaves with exhaust air)

$$0 - Q \cdot c_{max} + 0.3 = 0$$

$$Q = \frac{\dot{m}_{gen}}{c_{max}} = \frac{0.3\,\text{kg/h}}{20 \times 10^{-6}\,\text{kg/m}^3} = \boxed{15{,}000\,\text{m}^3/\text{h}}$$

**Check:** Room volume = 20 × 8 × 4 = 640 m³. Air changes per hour = 15,000/640 ≈ 23 — reasonable for industrial ventilation.

---

### Problem 1.6
**Statement:** Incompressible Newtonian fluid flows in z-direction between two parallel plates separated by 2B. Velocity distribution (coordinate origin at centre):
$$v_z = \frac{|\Delta P| B^2}{2\mu L}\left[1 - \left(\frac{x}{B}\right)^2\right]$$

(a) For origin at bottom plate (0 to 2B), show:
$$v_z = \frac{|\Delta P| B^2}{2\mu L}\left[2\left(\frac{x}{B}\right) - \left(\frac{x}{B}\right)^2\right]$$

(b) Calculate Q from both expressions and compare.

**Answer given:** Q = 2|ΔP|B³W / (3μL) for both cases

**Solution:**

**(a) Coordinate transformation:**

Original system: x ranges from −B to +B (centre at 0).
New system: x' ranges from 0 to 2B (origin at bottom plate).

The transformation is: x = x' − B (the centre corresponds to x' = B)

Substitute into original expression:
$$v_z = \frac{|\Delta P| B^2}{2\mu L}\left[1 - \left(\frac{x'-B}{B}\right)^2\right]$$

Expand the bracket:
$$\left(\frac{x'-B}{B}\right)^2 = \left(\frac{x'}{B} - 1\right)^2 = \left(\frac{x'}{B}\right)^2 - 2\frac{x'}{B} + 1$$

Therefore:
$$1 - \left(\frac{x'}{B} - 1\right)^2 = 1 - \left(\frac{x'}{B}\right)^2 + 2\frac{x'}{B} - 1 = 2\left(\frac{x'}{B}\right) - \left(\frac{x'}{B}\right)^2$$

$$\boxed{v_z = \frac{|\Delta P| B^2}{2\mu L}\left[2\left(\frac{x'}{B}\right) - \left(\frac{x'}{B}\right)^2\right]} \quad \checkmark$$

**(b) Volumetric flow rate:**

**Using original (centred) distribution:**

$$Q = W\int_{-B}^{+B} v_z\, dx = W \cdot \frac{|\Delta P| B^2}{2\mu L}\int_{-B}^{+B}\left[1-\left(\frac{x}{B}\right)^2\right]dx$$

Let u = x/B, du = dx/B, limits −1 to +1:

$$Q = W \cdot \frac{|\Delta P| B^3}{2\mu L}\int_{-1}^{+1}(1-u^2)\,du = W \cdot \frac{|\Delta P| B^3}{2\mu L}\left[u - \frac{u^3}{3}\right]_{-1}^{+1}$$

$$= W \cdot \frac{|\Delta P| B^3}{2\mu L}\left[\left(1-\frac{1}{3}\right)-\left(-1+\frac{1}{3}\right)\right] = W \cdot \frac{|\Delta P| B^3}{2\mu L} \cdot \frac{4}{3}$$

$$\boxed{Q = \frac{2|\Delta P| B^3 W}{3\mu L}}$$

**Using bottom-origin distribution (dropping prime):**

$$Q = W\int_{0}^{2B} v_z\,dx = W\cdot\frac{|\Delta P| B^2}{2\mu L}\int_0^{2B}\left[2\frac{x}{B} - \left(\frac{x}{B}\right)^2\right]dx$$

Let u = x/B, limits 0 to 2:

$$Q = W\cdot\frac{|\Delta P| B^3}{2\mu L}\int_0^{2}(2u-u^2)\,du = W\cdot\frac{|\Delta P| B^3}{2\mu L}\left[u^2 - \frac{u^3}{3}\right]_0^2$$

$$= W\cdot\frac{|\Delta P| B^3}{2\mu L}\left[4 - \frac{8}{3}\right] = W\cdot\frac{|\Delta P| B^3}{2\mu L}\cdot\frac{4}{3} = \frac{2|\Delta P| B^3 W}{3\mu L} \quad \checkmark$$

**Conclusion:** Both coordinate systems give the same volumetric flow rate, as they must — physical results are coordinate-independent.

---

### Problem 1.7
**Statement:** Flow in z-direction through triangular duct bounded by y = H, y = √3 x, y = −√3 x. Velocity:
$$v_z = \frac{|\Delta P|}{4\mu L H}(y - H)(3x^2 - y^2)$$

Find volumetric flow rate Q.

**Answer given:** $Q = \dfrac{\sqrt{3}\,H^4 |\Delta P|}{180\,\mu L}$

**Solution:**

The cross-section is a triangle with:
- Top side: y = H (horizontal)
- Left side: y = √3 x → x = y/√3
- Right side: y = −√3 x → x = −y/√3

At a given y, x ranges from −y/√3 to +y/√3, and y ranges from 0 to H.

$$Q = \int_0^H\int_{-y/\sqrt{3}}^{+y/\sqrt{3}} v_z\,dx\,dy$$

$$Q = \frac{|\Delta P|}{4\mu L H}\int_0^H\int_{-y/\sqrt{3}}^{+y/\sqrt{3}} (y-H)(3x^2 - y^2)\,dx\,dy$$

**Inner integral over x:**

$$\int_{-y/\sqrt{3}}^{+y/\sqrt{3}}(3x^2 - y^2)\,dx = \left[x^3 - y^2 x\right]_{-y/\sqrt{3}}^{+y/\sqrt{3}}$$

At x = +y/√3: $(y/\sqrt{3})^3 - y^2(y/\sqrt{3}) = y^3/(3\sqrt{3}) - y^3/\sqrt{3} = y^3/(3\sqrt{3}) - 3y^3/(3\sqrt{3}) = -2y^3/(3\sqrt{3})$

At x = −y/√3: $-(y/\sqrt{3})^3 + y^2(y/\sqrt{3}) = +2y^3/(3\sqrt{3})$ (opposite sign)

Total inner integral:
$$= -\frac{2y^3}{3\sqrt{3}} - \frac{2y^3}{3\sqrt{3}} = -\frac{4y^3}{3\sqrt{3}} = -\frac{4\sqrt{3}\,y^3}{9}$$

**Outer integral over y:**

$$Q = \frac{|\Delta P|}{4\mu L H}\int_0^H (y-H)\left(-\frac{4\sqrt{3}\,y^3}{9}\right)dy = \frac{|\Delta P|}{4\mu L H}\cdot\left(-\frac{4\sqrt{3}}{9}\right)\int_0^H y^3(y-H)\,dy$$

$$\int_0^H y^3(y-H)\,dy = \int_0^H(y^4 - Hy^3)\,dy = \left[\frac{y^5}{5} - \frac{Hy^4}{4}\right]_0^H = \frac{H^5}{5} - \frac{H^5}{4} = H^5\left(\frac{1}{5}-\frac{1}{4}\right) = -\frac{H^5}{20}$$

Combining:

$$Q = \frac{|\Delta P|}{4\mu L H}\cdot\left(-\frac{4\sqrt{3}}{9}\right)\cdot\left(-\frac{H^5}{20}\right) = \frac{|\Delta P|}{4\mu L H}\cdot\frac{4\sqrt{3}\,H^5}{180}$$

$$= \frac{|\Delta P|\cdot\sqrt{3}\,H^4}{180\,\mu L}$$

$$\boxed{Q = \frac{\sqrt{3}\,H^4\,|\Delta P|}{180\,\mu L}} \quad \checkmark$$

---

### Problem 1.8
**Statement:** Radial flow of incompressible Newtonian fluid between two parallel circular disks of radius R₂, gap 2b. Velocity distribution:
$$v_r = \frac{b^2 |\Delta P|}{2\mu r \ln(R_2/R_1)}\left[1-\left(\frac{z}{b}\right)^2\right]$$

Find volumetric flow rate.

**Answer given:** $Q = \dfrac{4\pi b^3 |\Delta P|}{3\,\mu \ln(R_2/R_1)}$

**Wait — the book answer is** $Q = \dfrac{4}{3}\dfrac{\pi b^3 |\Delta P|}{\mu\ln(R_2/R_1)}$

**Solution:**

The flow is radial. For a cylinder of radius r, the cross-sectional area perpendicular to the radial flow is a cylindrical ring surface: for a thin strip dz at height z, the area element has circumference 2πr and height dz.

$$Q = \int_{-b}^{+b} v_r \cdot (2\pi r)\,dz$$

But wait — Q is the total volumetric flow rate through any cylindrical surface at radius r. Since the flow is radially outward (or inward), Q is independent of r at steady state:

$$Q = 2\pi r \int_{-b}^{+b} v_r\,dz = 2\pi r \int_{-b}^{+b} \frac{b^2|\Delta P|}{2\mu r \ln(R_2/R_1)}\left[1-\left(\frac{z}{b}\right)^2\right]dz$$

The r cancels:

$$Q = \frac{\pi b^2 |\Delta P|}{\mu \ln(R_2/R_1)}\int_{-b}^{+b}\left[1-\left(\frac{z}{b}\right)^2\right]dz$$

Let u = z/b, dz = b·du, limits −1 to +1:

$$Q = \frac{\pi b^3 |\Delta P|}{\mu \ln(R_2/R_1)}\int_{-1}^{+1}(1-u^2)\,du = \frac{\pi b^3 |\Delta P|}{\mu \ln(R_2/R_1)}\left[u - \frac{u^3}{3}\right]_{-1}^{+1}$$

$$= \frac{\pi b^3 |\Delta P|}{\mu \ln(R_2/R_1)}\cdot\frac{4}{3}$$

$$\boxed{Q = \frac{4\pi b^3 |\Delta P|}{3\,\mu \ln(R_2/R_1)}} \quad \checkmark$$

---

## 1.3 Key Formulas Summary — Chapter 1

| Quantity | Formula |
|---------|---------|
| Steady-state condition | ∂ϕ/∂t = 0 |
| Flux | Flow rate / Area |
| Rate of input/output (const. flux) | Flux × Area |
| Rate of input/output (variable flux) | ∫∫ Flux dA |
| Rate of generation (const. ℜ) | ℜ × Volume |
| Rate of generation (variable ℜ) | ∫∫∫ ℜ dV |
| Rate of accumulation | d(mϕ̂)/dt |
| Steady-state no generation | Rate in = Rate out |
| Steady-state with generation | Rate in + Rate gen = Rate out |
