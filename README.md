# Closed-Loop-Feedback-Analysis-Practical-2-MATLAB

MATLAB implementation of **ENG3018 Practical 2**, analysing a negative unity feedback control system using classical control techniques.  
The script performs transfer-function construction, stability analysis, time-domain simulation, and frequency-domain phase interpretation using standard Control System Toolbox functions.

---

## Overview

This repository contains a **single, linear MATLAB script** implementing Tasks (a)–(g) from ENG3018 Practical 2 exactly as specified in the practical sheet.

The system consists of a plant:

```math
G(s)=\frac{10(s+4)}{s(s^2+4s+5)}
```

and a controller:

```math
K(s)=\frac{s+1}{s+3}
```

connected in a **negative unity feedback loop**.

The code is structured as an academic submission rather than a modular software library, prioritising transparency, traceability, and analytical clarity.

---

## System Construction

- Open-loop transfer function:

```math
L(s)=K(s)G(s)
```

- Closed-loop transfer function:

```math
T(s)=\frac{y(s)}{r(s)}=\frac{L(s)}{1+L(s)}
```

- Sensitivity function:

```math
S(s)=\frac{1}{1+L(s)}
```

Both toolbox-based construction (`series`, `feedback`) and **explicit polynomial convolution** (`conv`) are used, as required.

---

## Analysis Performed

### Closed-Loop Properties

- Closed-loop transfer function $T(s)$ derived using `feedback`
- Manual reconstruction of the closed-loop denominator using polynomial addition
- Extraction of poles and zeros of $T(s)$
- DC gain evaluation of the closed-loop system $T(0)$

### Sensitivity Function

- Construction of the sensitivity function $S(s)$
- Pole and zero analysis of $S(s)$
- Interpretation of disturbance rejection characteristics via $S(s)$

### Time-Domain Responses

- Unit step response of $T(s)$ plotted over $0\,\text{s}$ to $10\,\text{s}$
- Axes and limits chosen to match the practical specification
- Sinusoidal response for:

```math
r(t)=\sin(\omega t),\quad \omega=1.7\ \text{rad/s}
```

- Direct comparison of input $r(t)$ and output $y(t)$ using `lsim`

### Frequency-Domain Phase Interpretation

- Evaluation of $T(j\omega)$ at $\omega=1.7\ \text{rad/s}$
- Extraction of magnitude $\lvert T(j\omega)\rvert$ and phase $\angle T(j\omega)$
- Conversion of phase lag into an equivalent time delay:

```math
t_d=-\frac{\phi}{\omega}
```

- Interpretation of the sinusoidal steady-state response as:

```math
y(t)\approx \lvert T(j\omega)\rvert\,\sin\big(\omega(t-t_d)\big)
```

---

## Output and Reporting

A **large PRINT BLOCK** at the end of the script provides a clean summary of all required results, including:

- Open-loop and closed-loop transfer functions ($L(s)$ and $T(s)$) in polynomial form
- Poles and zeros of $T(s)$ and $S(s)$
- DC gain of the closed-loop system $T(0)$
- Phase, magnitude, and time-delay estimates at $\omega=1.7\ \text{rad/s}$
- Characteristic equation verification using both:
  - Closed-loop denominator polynomial
  - `poly(poles(T))`

This mirrors the format expected in a written coursework submission.

---

## Plot Outputs

The script automatically generates:

- Unit step response of the closed-loop system $T(s)$
- Sinusoidal input/output comparison plot for $r(t)=\sin(\omega t)$
- Clearly labelled figures corresponding to the practical questions

All plots are produced programmatically and require no manual interaction.

---

## Context

This repository is maintained as an **academic reference and portfolio artefact**.  
It demonstrates closed-loop control analysis, feedback theory, and careful numerical reporting using MATLAB’s Control System Toolbox, rather than serving as a general-purpose control design package.
