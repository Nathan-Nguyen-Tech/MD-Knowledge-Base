# EVIDENCE SECTION SPECIFICATION

**Version:** 1.0
**Date:** 2025-12-07
**Purpose:** Define the structure and requirements for the EVIDENCE section in all SMART Cards

---

## WHY EVIDENCE MATTERS

Evidence-based medicine is the foundation of the SMART system. Every card recommendation must be:
1. **Grounded** in published research
2. **Graded** by quality of evidence
3. **Transparent** about limitations
4. **Trustworthy** for patients and clinicians

**The EVIDENCE section serves two audiences:**
- **Patients:** "Why should I trust this recommendation?"
- **Clinicians:** "What's the supporting literature?"

---

## EVIDENCE SECTION STRUCTURE

### For Condensed View (Patient-Facing Summary)

Displayed in WHY section as single line:
```
**Evidence:** Grade [A/B/C] - [One sentence plain-language summary]
```

Example:
```
**Evidence:** Grade A - Proven effective in major studies over 60 years, reduces diabetes complications by 32%.
```

---

### For Expanded View (Full Evidence Section)

```markdown
## EVIDENCE

### Summary
[2-3 sentence plain-language summary accessible to patients]

### Grade: [A/B/C]

### Grading Criteria Met
- [ ] [Specific criteria for this grade]

### Primary Sources

#### Guideline: [Name]
- **Organization:** [Issuing body]
- **Year:** [Publication year]
- **Recommendation:** [Exact recommendation language]
- **Strength:** [Strong/Moderate/Weak]
- **Link:** [URL if available]

#### Trial: [Study Name]
- **Citation:** [Full citation]
- **Design:** [RCT/Meta-analysis/Cohort/etc.]
- **Population:** [Who was studied]
- **N:** [Sample size]
- **Key Finding:** [Primary outcome result]
- **NNT/NNH:** [If applicable]
- **Limitations:** [Key limitations]

### Supporting Evidence
[Additional studies, real-world data]

### Evidence Gaps
[What we don't know, areas of uncertainty]

### Last Evidence Review
[Date this evidence was last reviewed/updated]
```

---

## EVIDENCE GRADING SYSTEM

### Grade A - Strong Evidence
**Criteria (must meet ALL):**
- [ ] Supported by ≥1 high-quality systematic review/meta-analysis of RCTs
- [ ] OR ≥2 large, well-designed RCTs with consistent results
- [ ] Endorsed by major guideline body (ADA, ACC/AHA, USPSTF, etc.)
- [ ] Consistent real-world effectiveness data
- [ ] Benefits clearly outweigh risks for target population

**Patient-Friendly Language:** "Strong scientific evidence supports this recommendation."

**What This Means:**
- Highest confidence in recommendation
- Multiple high-quality studies agree
- Major medical organizations endorse this

---

### Grade B - Moderate Evidence
**Criteria (must meet ≥3):**
- [ ] Supported by ≥1 well-designed RCT
- [ ] OR consistent findings from multiple observational studies
- [ ] Endorsed by guideline body with moderate strength
- [ ] Benefits likely outweigh risks
- [ ] Some limitations in study quality, consistency, or applicability

**Patient-Friendly Language:** "Good scientific evidence supports this recommendation."

**What This Means:**
- Reasonable confidence in recommendation
- Studies generally support this
- Some uncertainty remains

---

### Grade C - Limited Evidence
**Criteria:**
- [ ] Based on observational studies only
- [ ] OR expert consensus/clinical experience
- [ ] OR extrapolated from related populations
- [ ] Limited or conflicting data
- [ ] Benefits may outweigh risks (uncertain)

**Patient-Friendly Language:** "Limited scientific evidence, but clinical experience supports this recommendation."

**What This Means:**
- Lower confidence in recommendation
- May be reasonable to try
- Discuss with your care team

---

### Grade D - Evidence Against (Rare - card should not exist)
**Criteria:**
- Evidence shows harm outweighs benefit
- Major guidelines recommend against

**Action:** Do not create card. If exists, archive with explanation.

---

## SOURCE HIERARCHY

When citing evidence, prioritize in this order:

1. **Systematic Reviews/Meta-Analyses** (Cochrane, high-quality)
2. **Clinical Practice Guidelines** (major specialty societies)
3. **Large RCTs** (≥1000 patients, well-designed)
4. **Smaller RCTs** (adequately powered for primary outcome)
5. **Prospective Cohort Studies**
6. **Retrospective Studies**
7. **Case Series/Expert Opinion** (lowest priority)

---

## REQUIRED SOURCES BY CARD TYPE

### Medication Cards
**Required:**
- FDA approval basis (pivotal trials)
- Current clinical practice guideline recommendation
- ≥1 systematic review or meta-analysis (if available)

**Recommended:**
- Real-world effectiveness data
- Safety/pharmacovigilance data
- Comparative effectiveness vs alternatives

### Behavioral Cards (Nutrition, Movement, etc.)
**Required:**
- ≥1 guideline recommendation OR
- ≥2 RCTs supporting intervention OR
- Systematic review

**Recommended:**
- Mechanistic studies
- Long-term outcome data
- Implementation/feasibility studies

### Diagnostic Testing Cards
**Required:**
- Guideline recommendation for screening/testing interval
- Test performance characteristics (sensitivity, specificity)
- Evidence for clinical utility (does testing improve outcomes?)

### Procedure Cards
**Required:**
- Guideline recommendation
- Efficacy data (RCT or large cohort)
- Safety data (complication rates)

---

## EXAMPLE: METFORMIN EVIDENCE SECTION

### Condensed (in WHY section)
```
**Evidence:** Grade A - Proven effective in major studies over 60 years, reduces diabetes complications by 32%.
```

### Expanded (EVIDENCE section)

```markdown
## EVIDENCE

### Summary
Metformin is the most extensively studied diabetes medication with over 60 years of clinical use. Multiple large trials and every major diabetes guideline recommend it as first-line therapy. It reliably lowers blood sugar and uniquely among diabetes drugs, has proven cardiovascular benefits.

### Grade: A

### Grading Criteria Met
- [x] Supported by multiple systematic reviews/meta-analyses
- [x] Multiple large, well-designed RCTs with consistent results
- [x] Endorsed by all major guideline bodies (ADA, EASD, AACE)
- [x] Extensive real-world effectiveness data
- [x] Benefits clearly outweigh risks

### Primary Sources

#### Guideline: ADA Standards of Care in Diabetes
- **Organization:** American Diabetes Association
- **Year:** 2024
- **Recommendation:** "Metformin is the preferred initial pharmacologic agent for type 2 diabetes"
- **Strength:** Strong (Level A)
- **Link:** https://diabetesjournals.org/care/issue/47/Supplement_1

#### Guideline: ADA/EASD Consensus Report
- **Organization:** American Diabetes Association / European Association for the Study of Diabetes
- **Year:** 2022
- **Recommendation:** "Metformin remains first-line therapy for most patients with T2DM"
- **Strength:** Strong consensus
- **Link:** https://doi.org/10.2337/dci22-0034

#### Trial: UKPDS 34 (UK Prospective Diabetes Study)
- **Citation:** UK Prospective Diabetes Study Group. Lancet. 1998;352(9131):854-865.
- **Design:** Randomized controlled trial
- **Population:** Newly diagnosed T2DM, overweight patients
- **N:** 1,704 (metformin arm vs conventional)
- **Follow-up:** Median 10.7 years
- **Key Findings:**
  - 32% reduction in diabetes-related endpoints (p=0.002)
  - 42% reduction in diabetes-related death (p=0.017)
  - 36% reduction in all-cause mortality (p=0.011)
- **NNT:** 14 (to prevent one diabetes-related endpoint over 10 years)
- **Limitations:** Overweight subgroup only; open-label design

#### Meta-Analysis: Cochrane Review
- **Citation:** Hirst JA, et al. Cochrane Database Syst Rev. 2012.
- **Design:** Systematic review and meta-analysis
- **Studies Included:** 35 RCTs
- **Key Finding:** Metformin reduces HbA1c by ~1.0-1.5% vs placebo
- **Limitations:** Heterogeneity in comparator arms

### Supporting Evidence

**A1c Reduction:**
- Consistent 1.0-1.5% reduction across trials
- Effect maintained long-term

**Cardiovascular Outcomes:**
- UKPDS showed CV mortality benefit (maintained at 10-year follow-up)
- Observational data consistently supportive
- HOME trial: reduced macrovascular events with metformin + insulin

**Weight Effects:**
- Weight neutral to modest loss (-1-2 kg) across trials
- Does not cause hypoglycemia as monotherapy

**Safety Profile:**
- 60+ years post-marketing experience
- Lactic acidosis extremely rare (4.3 per 100,000 patient-years)
- GI side effects common but usually transient

### Evidence Gaps

- Limited RCT data in patients with eGFR 30-45 (though now guideline-approved)
- No large RCTs comparing to newer agents (SGLT2i, GLP-1) as first-line
- Optimal dosing for CV benefit not established
- Long-term outcome data in combination with newer agents evolving

### Last Evidence Review
December 2024
```

---

## UPDATING EVIDENCE

### When to Review
- New guideline publication
- Major trial results released
- Safety signal identified
- Annual scheduled review

### Version Tracking
Each evidence update should note:
- Date of review
- What changed
- Whether grade changed
- Reviewer initials

---

## PATIENT TRUST ELEMENTS

To build patient trust, the EVIDENCE section should:

1. **Be Honest About Uncertainty**
   - Include evidence gaps
   - Acknowledge limitations
   - Don't oversell

2. **Use Plain Language**
   - Summary in accessible terms
   - Explain what grades mean
   - Avoid jargon in patient-facing parts

3. **Show the Work**
   - Link to actual sources
   - Name specific studies
   - Be transparent about who recommends this

4. **Stay Current**
   - Show last review date
   - Update when evidence changes
   - Remove outdated citations

---

## IMPLEMENTATION

### In Card Template

**Condensed View:** Evidence summary in WHY section

**Expanded View:** Full EVIDENCE section between FOLLOW-UP and NOTES

### AI Metadata
```yaml
evidence:
  grade: A
  last_reviewed: 2024-12
  primary_guideline: ADA_2024
  key_trials: [UKPDS, HOME]
  cochrane_review: available
  evidence_gaps: [eGFR_30-45_limited, comparison_to_newer_agents]
```

---

**END OF DOCUMENT**
