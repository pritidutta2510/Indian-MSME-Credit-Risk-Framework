# Indian MSME Credit Risk Framework
## An Integrated Scorecard, Stress Testing, and Shadow Rating Project

**Author:** Priti Dutta  
**Tools:** Python, Google Colab, scorecardpy, scikit-learn, pandas  
**Dataset:** UCI Default of Credit Card Clients (30,000 borrowers)

---

## Project Overview

This project builds an end-to-end credit risk framework for a fictional 
Indian NBFC (Pradhan MSME Lending Institution) across three interconnected 
notebooks. Each notebook is a standalone deliverable that feeds into the next, 
demonstrating systems-level thinking across credit risk, model risk, and 
credit research functions.

---

## Notebooks

### 01_Scorecard
Builds a credit scorecard using Weight of Evidence (WoE), Information Value (IV), 
and logistic regression on 30,000 borrower records. Scores the portfolio and 
classifies borrowers into Low, Medium, and High Risk bands.

- AUC-ROC: 0.76
- Score separation: 80 points (Non-default: 420.7 | Default: 340.6)
- High Risk default rate: 47.10% | Low Risk: 7.88%

### 02_Stress_Testing
Engineers synthetic Indian MSME features (sector, region, GST compliance, 
macro indicators) onto the scored portfolio and runs three RBI-style macro 
stress scenarios using an IFRS 9-aligned PD x LGD x EAD framework.

| Scenario | GDP Growth | Repo Rate | Portfolio ECL Rate |
|----------|-----------|-----------|-------------------|
| Base | 6.5% | 6.5% | 8.00% |
| Moderate Stress | 4.0% | 7.5% | 11.21% |
| Severe Stress | 1.5% | 9.0% | 16.01% |

### 03_Shadow_Rating
Aggregates stress test results into a CRISIL-style shadow credit rating 
using a five-dimension weighted scorecard. Produces a formal rating rationale 
document with upward and downward rating sensitivities.

**Final Rating: BB — Moderate Risk (Weighted Score: 2.75/5.00)**

---

## Key findings

- Portfolio ECL doubles from base to severe stress, indicating meaningful 
  macro sensitivity
- High Risk segment PD approaches 94% under severe stress — primary source 
  of tail risk
- GST non-compliance concentrated in High Risk borrowers (60%) signals 
  informal operations as a leading default indicator
- BB rating constrained by asset quality and stress resilience; adequate 
  diversification prevents a lower rating

---

## Project Structure
Credit_Risk_Framework/
├── Data/
│   └── default of credit card clients.xls
├── notebooks/
│   ├── 01_Scorecard.ipynb
│   ├── 02_Stress_Testing.ipynb
│   └── 03_Shadow_Rating.ipynb
└── Outputs/
├── scored_portfolio.csv
├── stress_results.csv
├── enriched_portfolio.csv
└── shadow_rating_report.txt

---

## Limitations and Future Work
- Synthetic MSME features are illustrative; real deployment would require 
  RBI/SIDBI borrower-level data
- LGD assumed constant at 45%; a dynamic LGD model would strengthen Part 2
- Shadow rating framework would benefit from calibration against actual 
  CRISIL/ICRA rating outcomes
