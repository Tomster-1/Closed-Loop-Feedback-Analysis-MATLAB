# Closed-Loop-Feedback-Analysis-Practical-2-MATLAB

MATLAB implementation of **ENG3018 Practical 2**, analysing a negative unity feedback control system using classical control techniques.  
The script performs transfer-function construction, stability analysis, time-domain simulation, and frequency-domain phase interpretation using standard Control System Toolbox functions.

---

## Overview

This repository contains a **single, linear MATLAB script** implementing Tasks (a)–(g) from ENG3018 Practical 2 exactly as specified in the practical sheet.

The system consists of a plant  
G(s) = 10(s + 4) / [ s(s² + 4s + 5) ]  
and a controller  
K(s) = (s + 1) / (s + 3),  

connected in a **negative unity feedback loop**.

The code is structured as an academic submission rather than a modular software library, prioritising transparency, traceability, and analytical clarity.

---

## System Construction

- Open-loop transfer function  
  L(s) = K(s)G(s)

- Closed-loop transfer function  
  T(s) = y / r = L(s) / (1 + L(s))

- Sensitivity function  
  S(s) = 1 / (1 + L(s))

Both toolbox-based construction (`series`, `feedback`) and **explicit polynomial convolution** (`conv`) are used, as required.

---

## Analysis Performed

---

### Closed-Loop Properties

- Closed-loop transfer function derived using `feedback`
- Manual reconstruction of the closed-loop denominator using polynomial addition
- Extraction of poles and zeros of T(s)
- DC gain evaluation of the closed-loop system

---

### Sensitivity Function

- Construction of the sensitivity function S(s)
- Pole and zero analysis of S(s)
- Interpretation of disturbance rejection characteristics

---

### Time-Domain Responses

- Unit step response of T(s) plotted over 0–10 s
- Axes and limits chosen to match the practical specification
- Sinusoidal response for  
  r(t) = sin(ωt), with ω = 1.7 rad/s
- Direct comparison of input and output using `lsim`

---

### Frequency-Domain Phase Interpretation

- Evaluation of T(jω) at ω = 1.7 rad/s
- Extraction of magnitude and phase
- Conversion of phase lag into an equivalent time delay  
  t_d = −φ / ω
- Interpretation of the sinusoidal steady-state response as  
  y(t) ≈ |T(jω)| sin(ω(t − t_d))

---

## Output and Reporting

A **large PRINT BLOCK** at the end of the script provides a clean summary of all required results, including:

- Open-loop and closed-loop transfer functions in polynomial form
- Poles and zeros of T(s) and S(s)
- DC gain of the closed-loop system
- Phase, magnitude, and time-delay estimates
- Characteristic equation verification using both:
  - Closed-loop denominator
  - `poly(poles(T))`

This mirrors the format expected in a written coursework submission.

---

## Plot Outputs

The script automatically generates:

- Unit step response of the closed-loop system
- Sinusoidal input/output comparison plot
- Clearly labelled figures corresponding to the practical questions

All plots are produced programmatically and require no manual interaction.

---

## Context

This repository is maintained as an **academic reference and portfolio artefact**.  
It demonstrates closed-loop control analysis, feedback theory, and careful numerical reporting using MATLAB’s Control System Toolbox, rather than serving as a general-purpose control design package.
