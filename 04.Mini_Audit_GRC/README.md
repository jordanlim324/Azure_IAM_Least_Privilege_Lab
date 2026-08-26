## Summary
The purpose of this document is to translate the IAM work into GRC language, demonstrating how the fictional company's IAM implementation can be evaluated against real-world security and governance standards such as ISO/IEC 27001 and NIST SP 800-53.

## The Problem
Shirabuki Corporation is conducting an internal audit to evaluate its IAM implementation against applicable security and governance frameworks.

## What Was Built
   - Risk Register
   - Control Mapping

## Decisions Made
   -  Decisions
      - I decided to use a Risk Score to quantify and prioritize the relative level of risk based on:
         - A) the likelihood of each risk occurring; and
         - B) the potential impact each risk could have on the corporation's environment.
      - Risk Score = Likelihood x Impact
         - Likelihood and impact are on a scale of 1-10, with higher values representing greater impact or likelihood.
         - The thresholds were established for this project to categorize calculated risk scores.
      - Likelihood, Impact, and Risk Scoring Tables:
<div align ="center">

Likelihood Scoring Table
| Score Range | Rating | General Interpretation |
| ----------: | ------ | ---------------------- |
|1–2 | Very Low | Unlikely to occur |
|3–4 | Low | Possible but relatively unlikely |
|5–6 | Moderate | Reasonably possible |
|7–8 | High | Likely to occur |
|9–10 | Very High | Highly likely / expected to occur |

</div align ="center">


<div align ="center">

Impact Scoring Table
| Score Range | Rating | General Interpretation |
| -----: | -------- | -------------- |
| 1–2 | Very Low | Minimal security or operational consequence |
| 3–4 | Low | Limited consequence |
| 5–6 | Moderate | Noticeable security or operational consequence |
| 7–8 | High | Significant security or operational consequence |
| 9–10 | Very High | Severe consequence / major organizational impact |

</div align ="center">

<div align ="center">

Risk Score Classification Table
| Score  |  Rating  | Interpretation |
| -----: | -------- | -------------- |
| 1–20   | Low      | Limited overall risk; generally lower priority |
| 21–40  | Moderate | Moderate overall risk; may require planned remediation |
| 41–60  | High     | Signifigant overall risk; remediation should be prioritized |
| 61–100 | Critical | Severe overall risk, remediation should receive high priority|

</div align = "center">


## Screenshots
