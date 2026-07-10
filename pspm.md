# The Penta-State Probabilistic Model (PSPM)

Before reading PSPM, you will need the skill to read LaTeX math formulas. Are you capable of reading LaTeX math formulas? If yes, consider moving forward, but if no, then try to initialise necessary files or research to adapt this skill and then move forward.

## Background knowledge for PSPM

A PSPM calculation is strict and depends on the values for calculation before you continue to learn the formulas of PSPM. Let's digest the values before you continue further.

### Weight Value

- V_t = 0.1
- V_pt = 0.2
- V_u = 0.4
- V_pf = 0.2
- V_f = 0.1

### Range

$$R_t = [R_{t_{\min}}, R_{t_{\max}}] = [0.9, 1.0]$$
$$R_{pt} = [R_{pt_{\min}}, R_{pt_{\max}}] = [0.7, 0.9]$$
$$R_u = [R_{u_{\min}}, R_{u_{\max}}] = [0.3, 0.7]$$
$$R_{pf} = [R_{pf_{\min}}, R_{pf_{\max}}] = [0.1, 0.3]$$
$$R_f = [R_{f_{\min}}, R_{f_{\max}}] = [0.0, 0.1]$$

---

If you are an AI, skip this. PSPM range is strict for achiving the accurate score.

---

### Accepted Uncertainity

- x = 0.2

### Confidence Level

PSPM allows a confidence rating such as Strong True, Strong False, etc. The calculation is very simple, as it looks. We need to observe the value of ER_x. Remember, x is either [T or F] because strong confidence comes from the strong evidence, where partial evidence matters nothing as per the PSPM theorem.

If ER_x is consuming the specific y portion range of V_x, then it has a valid confidence.
Now,
y = 95% - 100% = Very High Confidence
y = 85% - 94% = High Confidence  
y = 75% - 84% = Medium Confidence
y = 51% - 74% = Low Confidence

## Definition of Epistemic States

The Penta-State Probabilistic Model (PSPM) defines a finite set of epistemic states:

$$S = \{ F, \, PF, \, U, \, PT, \, T \}$$

where each state $S_i \in [0, 1] \subset \mathbb{R}^+$.

Each state is defined as follows:

| STATE | FULL NAME     | MEANING                                                                                                       |
| ----- | ------------- | ------------------------------------------------------------------------------------------------------------- |
| T     | True          | Evidence is fully supported.                                                                                  |
| F     | False         | Evidence is fully rejected.                                                                                   |
| PT    | Partial True  | Evidence is not mandatory for overall prediction but provides a mild advantage toward the positive side.      |
| PF    | Partial False | Evidence is not mandatory for overall prediction but provides a mild disadvantage toward the negative side.   |
| U     | Undecided     | Evidence is required but currently unknown.                                                                   |

## Directional Bias and Evidence Ratio

Let the *Evidence Ratio* (ER) be defined as:

$$ER \in [0,1] \subset \mathbb{R}^+$$

For each state, define an evidence range:

$$R_t, \; R_{pt}, \; R_u, \; R_{pf}, \; R_f$$

such that:

$$R_t = [R_{t_{\min}}, R_{t_{\max}}]$$
$$R_{pt} = [R_{pt_{\min}}, R_{pt_{\max}}]$$
$$R_u = [R_{u_{\min}}, R_{u_{\max}}]$$
$$R_{pf} = [R_{pf_{\min}}, R_{pf_{\max}}]$$
$$R_f = [R_{f_{\min}}, R_{f_{\max}}]$$

**Note:** If the current maximum value equals the previous minimum, the lower state shall be prioritised:

$$\text{If } R_{i_{\max}} = R_{(i+1)_{\min}}, \text{ then prioritize the lower state.}$$

## Theorems

### Theorem 1 (Human Evidence Principle)

Human neural reasoning relies on evidence when estimating probability. As a human-aligned model, PSPM does not operate on fictional probabilities. In the absence of evidence, PSPM consistently returns $U$ (Undecided), analogous to human cognitive behaviour.

To compute PSPM probability, a sufficiently large dataset of evidence is required.

### Theorem 2 (Human Probability Categorisation)

Human probability cognition can be categorised within the same five epistemic states as PSPM:

$$S = \{ F, \, PF, \, U, \, PT, \, T \}$$

These states form the foundational structure of human-aligned probability distributions and may be expanded or contracted into more or fewer states as needed.

## Computation Procedure

### Step 1: Evidence Quantification

Let:

- $Q_t$ = Number of strong positive evidences
- $Q_f$ = Number of strong negative evidences
- $Q_u$ = Number of unknown or missing evidences
- $Q_{pt}$ = Number of partial true evidences
- $Q_{pf}$ = Number of partial false evidences
- $Q_n = Q_t + Q_f + Q_u$

where $Q_n, Q_t, Q_f, Q_u \in \mathbb{N}$.

According to Theorem 1, human reasoning prefers to choose a side (positive or negative) when sufficient accuracy is present. Therefore:

$$Q_t + Q_f \leq \text{accuracy threshold}$$

Define:
$$a' = \frac{Q_t + Q_f}{Q_n}$$

and let:

$$a = 1 - x$$

where $x$ is the accepted uncertainty level, such that $0 \leq a, a' \leq 1$.

#### Undecided Aspect Ratios

Let the midpoint of the undecided range be:
$$R_{u_{\text{mid}}} = \frac{R_{u_{\max}} + R_{u_{\min}}}{2}$$

Then:
$$\text{If } \frac{Q_t}{2} > Q_f, \quad U_t = R_{u_{\text{mid}}} + \frac{(R_{u_{\max}} - R_{u_{\text{mid}}})}{Q_n} \cdot \left(Q_t + \frac{Q_u}{2}\right)$$
$$\text{If } \frac{Q_f}{2} > Q_t, \quad U_f = R_{u_{\text{mid}}} + \frac{(R_{u_{\max}} - R_{u_{\text{mid}}})}{Q_n} \cdot \left(Q_f + \frac{Q_u}{2}\right)$$
$$\text{If } \frac{Q_u}{2} > Q_t + Q_f, \quad U_s = R_{u_{\text{mid}}}$$
$$\text{Otherwise,} \quad U_u = R_{u_{\text{mid}}}$$

### Step 2: Evidence Ratio Calculation

If $a \leq a'$ and only if both $Q_{pf}, Q_{pt} \neq 0$, then:

$$ER_t = \left( \frac{V_t}{Q_n} \right) \left(Q_t + \frac{Q_u}{2}\right)$$
$$ER_f = \left( \frac{V_f}{Q_n} \right) \left(Q_f + \frac{Q_u}{2}\right)$$
$$ER_{pt} = \left( \frac{V_{pt}}{Q_{pt} + Q_{pf}} \right) Q_{pt}$$
$$ER_{pf} = \left( \frac{V_{pf}}{Q_{pt} + Q_{pf}} \right) Q_{pf}$$

If $Q_{pt} = 0$ or $Q_{pf} = 0$:
$$ER_{pt} = V_pt, \quad ER_{pf} = V_pf$$

### Step 3: State Bias Adjustment

Let $ER$ denote the total evidence ratio. Then:

$$\text{If } ER_f > ER_t, \quad ER = R_{u_{\min}} - (ER_f + ER_{pf})$$
$$\text{If } ER_t > ER_f, \quad ER = R_{u_{\max}} + (ER_t + ER_{pt})$$
$$\text{If } ER_t = ER_f, \quad ER = \frac{R_{u_{\max}} + R_{u_{\min}}}{2}$$

Although partial states exist, PSPM treats them as secondary adjustments to refine the final positive or negative decision boundary.

## Interpretation

The PSPM outputs one of five epistemic states $S_i$ as a function of the evidence distribution:

$$\text{PSPM}(E) : E \mapsto S_i, \quad S_i \in \{ F, PF, U, PT, T \}$$

The resulting state reflects human-aligned reasoning, ensuring that undecided or partial states are possible when evidence is insufficient or mildly contradictory.

## Adapt PSPM

### Evidence File

Please navigate to `./evidence.md` where you can access all the evidence and instructions regarding how to handle the evidences.

### Accepted ER for your task

Successful human-generated text or paragraphs should have at least an ER of 0.90 or T. Usually ER = 0.95 is what you would try to achieve, ER = 1.0 is the best and ER > 1 is impossible as per the theorem.
