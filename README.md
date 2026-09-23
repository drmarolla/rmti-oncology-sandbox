# RMTI Sandbox — Oncology & Public Health Surveillance

**An interactive reference implementation of the Risk Mechanism Theory Index (RMTI) for hepatocellular carcinoma (HCC) surveillance and other public-health surveillance settings.**
By Dr. Cesar Marolla

<!-- DOI badge: after your first Zenodo release, replace XXXXXXX with your concept DOI number and delete the comment markers around the line below.
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)
-->

### ▶ Open the live sandbox: [https://drmarolla.github.io/rmti-oncology-sandbox/](https://drmarolla.github.io/rmti-oncology-sandbox/)

> **Research prototype for education and research only.** This sandbox is a teaching companion and a methodological reference. It is **not** a medical device, has **not** been clinically validated, is **not** for patient-care decisions, and does **not** provide medical advice, diagnosis or treatment recommendations. Clinical decisions remain the responsibility of qualified healthcare professionals. Please read [DISCLAIMER.md](DISCLAIMER.md).

## Built-in transparency

The sandbox tells its users plainly what it is and is not:

- **On opening**, a "Before you use this tool" dialog explains the limits, and users must click *I understand — continue* to proceed. A red banner at the top ("Research prototype…") keeps the notice one click away at all times.
- **Wording of results:** the messages shown next to a score are labelled *framework readings* and are phrased as things a clinical team *may wish to consider*. They are not recommendations for any patient.
- **A notice sits under every result** and the footer repeats the limits.
- The two demonstration profiles are named *Illustrative case A / B* and are hypothetical.

## What it is

RMTI scores risk on one bounded 0–1 scale: likelihood, exposure and vulnerability raise the score, and resilience brings it down. This sandbox applies the same equations used in the author's disaster-science work to surveillance settings, where:

- **Likelihood** comes from a published risk score (for example aMAP or THRI for HCC),
- **Vulnerability** comes from hepatic reserve (for example ALBI grade),
- **Resilience** describes how adequately surveillance is delivered, and
- **Consequence** is mapped to stage bands (BCLC).

The clinical instruments named above belong to their original authors. This project does not validate or replace them.

## What you can do

- **Public Health / Oncology Surveillance tab:** load one of the worked examples (Untreated HBV, Active viral cirrhosis, Alcohol cirrhosis, Cured-HCV cirrhosis, Suppressed-HBV, NAFLD cirrhosis, High-burden MASLD, plus two hypothetical illustrative cases), move the sliders, and compare the score *now* against a planned improvement in surveillance delivery.
- **Custom / Your Field tab:** type the name of your own field and case (for example another cancer, an epidemic early-warning system, a screening programme or a hospital service line), optionally relabel the five inputs, and save cases as chips for the current browser session.
- Read the score, its tier, the relative expected-loss index, the per-capita view and the size of the risk reduction from the planned improvement.

## The model

The sandbox implements the RMTI scoring equations. All inputs are on a 0–1 scale unless noted.

| Quantity | Equation |
|---|---|
| Inherent risk | `IR = L · E · V` |
| Residual risk score | `R = IR · (1 − ρ)` (bounded 0–1) |
| Expected annual loss (relative index) | `EAL = L · C · (1 − ρ)` |
| Log-normalized exposure helper | `E_log(N) = [log10(N) − log10(N_min)] / [log10(N_max) − log10(N_min)]`, clamped to 0–1 |

`L` = likelihood, `E` = exposure, `V` = vulnerability, `ρ` = resilience, `C` = consequence. Resilience enters as `(1 − ρ)`, never as `ρ`, so more coping capacity always lowers the score. The consequence level (1–5) maps to `C = 0.10, 0.30, 0.50, 0.75, 1.00`.

**Fixed tier bands** (set in advance and not adjustable in the tool):

| Tier | R |
|---|---|
| Low | < 0.05 |
| Moderate | 0.05 – 0.15 |
| High | 0.15 – 0.35 |
| Severe | 0.35 – 0.60 |
| Critical | ≥ 0.60 |

Rounding follows the half-up convention so that browser results match the Python reference implementation of the model.

## Privacy

The sandbox is a single self-contained HTML file. All calculations run in your browser. There are no accounts, no analytics and no server that receives what you type. Saved cases exist only in the open browser tab and disappear when you reload or close it. The page does load its web fonts from Google Fonts, so your browser contacts that service to display them; nothing you enter is sent.

**Please do not type patient names or any identifying details** into the field, case or label boxes.

## Run it yourself

Download `index.html` and open it in any modern browser, or host it for free on GitHub Pages, Netlify or Vercel. On GitHub Pages: *Settings → Pages → Deploy from a branch → `main` / root*.

## Cite this software

Use GitHub's **Cite this repository** button (right-hand sidebar; it reads `CITATION.cff`). Released versions are archived on Zenodo, and the DOI is shown in this repository once it has been assigned.

Please also cite the RMTI publication on which the method rests:

> Marolla, C. (2025). Enhancing urban resilience to California wildfires: A systemic risk mechanism design and theory framework for a comprehensive risk assessment. *International Journal of Management and Data Analytics, 5*(1), 60–77. https://doi.org/10.5281/zenodo.14948760

## Related work

- Marolla, C. (2026). Application of RMTI to HCC surveillance. *In preparation.*
- Marolla, C. *Risk by Design: Integrating Disaster, Environment, and Health in the Urban Century.* CRC Press / Taylor & Francis. *In preparation.*
- The disaster-science version of the sandbox is a separate tool with its own scope and notices: [https://drmarolla.github.io/rmti-disaster-science-sandbox/](https://drmarolla.github.io/rmti-disaster-science-sandbox/).

## License

The software is released under the [MIT License](LICENSE). The MIT License covers the code. The RMTI method, rubrics and tier structure are the author's published work and should be cited when used.
