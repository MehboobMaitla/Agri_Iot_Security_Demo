# Agricultural IoT Security Demo

A small Google Colab demo based on the paper "Cybersecurity and Privacy in AI-Enabled Agricultural IoT Ecosystems: A Systematic Review" (Algorithms 2026, 19, 827).

The paper is a systematic review, so this demo reproduces its method on toy data. It does not train a model.

## How to run
1. Open https://colab.research.google.com
2. File > Upload notebook > select `agri_iot_security_demo.ipynb`
3. Runtime > Run all

Dependencies: numpy, pandas, matplotlib, scikit-learn (all preinstalled on Colab).

## Sections

### 1. PRISMA flow
Checks the study selection arithmetic from Table 7 of the paper: 2535 records retrieved, 520 duplicates removed, 1195 excluded at title/abstract, 117 and 598 excluded at the two full-text stages, then +8 citation-tracked, -3 duplicates, -7 inaccessible, ending at 103 studies. An assertion confirms the final count and a bar chart shows the funnel.

### 2. Reported coverage
Plots the percentages reported in Sections 4.2 to 4.4 for threats (RQ1), LINDDUN privacy categories (RQ2), safeguards (RQ3) and architecture layers. Main points: DoS/DDoS (69.9%), tampering (52.4%) and spoofing (45.6%) dominate; the edge/fog layer is covered by only 27.2% of studies; Disclosure of Information (68.0%) dominates privacy coverage.

### 3. STRIDE coding and reliability
- A keyword equivalence dictionary maps text to the six STRIDE categories (a simplified version of the paper's retrospective coding).
- 20 synthetic abstracts are generated with known multi-label ground truth.
- Reviewer 1 is the keyword coder. Reviewer 2 is simulated by flipping about 10% of the labels.
- Per category, the notebook reports observed agreement and Cohen's kappa (binary present/absent), as in Table 8. Kappa is shown as "not estimable" when a category is constant in both series, which is why the paper reports observed agreement alongside it.

### 4. Ecological validity rater
A rule-based rater following Section 3.6 of the paper:
- **High**: real agricultural data or hardware in a genuine field, at least 2 agricultural constraints, and results reported under those conditions.
- **Moderate**: agricultural data or hardware in a lab, testbed or incomplete field setting. Ambiguous cases get the more conservative rating, as in the paper.
- **Low**: pure simulation, generic non-agricultural data, or analytical work only.

It is applied to 8 hand-written toy studies and the result is plotted.

## Key findings from the paper
- The edge layer and adversarial attacks on agricultural AI are under-studied.
- Privacy research focuses on confidentiality; 90.3% of studies reference no regulation.
- Only 7.8% of studies (8 of 103) have High ecological validity, so lab accuracy (for example 98% IDS accuracy on benchmarks) does not show real-farm performance.

## Notes
The abstracts and studies in sections 3 and 4 are synthetic and written for this demo. They are not the paper's dataset.

## Possible extensions
- Train an Isolation Forest on simulated soil-sensor data and inject tampered readings to test detection.
- Add a small adversarial perturbation to a crop-disease classifier to illustrate AI as an attack surface.
