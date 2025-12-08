# Surgical History Tier 1 Library v1.0

**Document Version:** 1.0
**Last Updated:** 2025-11-25
**Purpose:** Standardized surgical history library linking procedures to health implications, monitoring needs, and dashboard score adjustments

---

## Document Overview

This document defines **40 Tier 1 surgical procedures** that are:
- Common enough to warrant intake form inclusion
- Have ongoing health implications
- Affect scoring, monitoring, or treatment decisions
- Patient-recognizable procedures

Each surgical entry includes:

1. **Patient-Friendly Label** - How procedure appears on intake form
2. **Linked Medical Diagnoses** - Related Tier 1 diagnoses this suggests/implies
3. **Clinical Implications** - What this tells us about patient's health
4. **Score Modifiers** - Impact on health dashboard scores
5. **Monitoring Needs** - Ongoing surveillance or management
6. **Smart Expansion Questions** - Brief follow-ups when procedure checked (if applicable)

---

## Intake Priority System

**Priority 1 (20 surgeries):** Always visible - major procedures with significant health implications
**Priority 2 (15 surgeries):** Under "Other common surgeries" expandable section
**Priority 3 (Unlimited):** Free-text "Other surgery: [____]" field

**Skip Option:** "No major surgeries" checkbox allows patients to bypass section

---

# SYSTEM 1: CARDIOVASCULAR SURGERIES (8 Procedures)

---

## SURG-001: Heart Bypass Surgery (CABG)

**Patient-Friendly Label:** Heart bypass surgery

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **When did you have this surgery?**
   - Options: Less than 1 year ago | 1-5 years ago | 5-10 years ago | More than 10 years ago
   - Clinical significance: Recent surgery = more monitoring

**Linked Tier 1 Diagnoses:**
- CARDIO-002: Coronary Artery Disease (always present)
- CARDIO-003: Prior MI (often, but not always)
- CARDIO-001: Hypertension (usually comorbid)

**Clinical Implications:**
- Confirms significant coronary artery disease
- Indicates prior high cardiovascular risk
- Patient should be on guideline-directed medical therapy (GDMT):
  - Aspirin
  - Statin (high-intensity)
  - Beta-blocker
  - ACE inhibitor or ARB

**Score Modifiers:**
- Cardiovascular-Structure: **-15 points** (permanent atherosclerosis despite revascularization)
- Cardiovascular-Risk: **-12 points** (ongoing CAD risk)

**Monitoring Needs:**
- Annual cardiology follow-up
- Lipid panel every 3-6 months until LDL <70
- Stress testing or imaging as directed by cardiology
- Medication adherence critical

**Special Considerations:**
- Some grafts may fail over time (especially saphenous vein grafts)
- Recurrent symptoms warrant urgent evaluation

---

## SURG-002: Heart Stent Placement (PCI)

**Patient-Friendly Label:** Heart stent placement

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How many times have you had stents placed?**
   - Options: Once | Twice | 3 or more times
   - Multiple procedures = more severe/progressive disease

2. **When was your most recent stent?**
   - Options: Less than 1 year ago | 1-5 years ago | More than 5 years ago
   - Recent stent = dual antiplatelet therapy (DAPT) required

**Linked Tier 1 Diagnoses:**
- CARDIO-002: Coronary Artery Disease
- CARDIO-003: Prior MI (if stent for STEMI/NSTEMI)

**Clinical Implications:**
- Confirms coronary artery disease
- If recent (<1 year): Should be on dual antiplatelet therapy (aspirin + P2Y12 inhibitor like Plavix)
- Multiple stents suggest progressive or diffuse CAD

**Score Modifiers:**
- Cardiovascular-Structure: **-12 points**
- Cardiovascular-Risk: **-10 points**
- If 3+ stent procedures: **-15 points** to Risk (suggests progressive disease)

**Monitoring Needs:**
- Annual cardiology follow-up
- Medication adherence critical (premature DAPT discontinuation = stent thrombosis risk)
- Lipid management aggressive (LDL <70)

**Special Considerations:**
- DAPT duration varies (usually 12 months for drug-eluting stents)
- Aspirin usually lifelong

---

## SURG-003: Heart Valve Replacement or Repair

**Patient-Friendly Label:** Heart valve surgery (replacement or repair)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which valve was replaced or repaired?**
   - Options: Aortic valve | Mitral valve | Multiple valves | Not sure
   - Aortic vs. mitral have different natural histories

2. **What type of valve?**
   - Options: Mechanical valve | Tissue/biological valve | Repair (no replacement) | Not sure
   - CRITICAL: Mechanical valve requires lifelong anticoagulation

**Linked Tier 1 Diagnoses:**
- CARDIO-008: Valvular Heart Disease

**Clinical Implications:**
- **If mechanical valve:** MUST be on warfarin (Coumadin) lifelong with INR monitoring
  - This is CRITICAL - flag immediately if not on anticoagulation
- **If tissue valve:** Aspirin typically, but no warfarin
- **If repair only:** Monitoring for recurrence

**Score Modifiers:**
- Cardiovascular-Structure: **-10 points** (if repair) / **-8 points** (if replacement - actually improves structure)
- Cardiovascular-Function: **+5 to +10 points** (surgery often improves function)
- Cardiovascular-Risk: **-10 points** (if mechanical - anticoagulation bleeding risk)

**Monitoring Needs:**
- **Mechanical valve:**
  - Monthly INR checks (target INR 2.5-3.5)
  - Endocarditis prophylaxis for dental procedures
  - Annual echocardiogram
- **Tissue valve:**
  - Annual echocardiogram (degeneration risk over time)
  - Endocarditis prophylaxis
  - May need replacement in 10-20 years

**Special Considerations:**
- Mechanical valves last longer but require anticoagulation
- Tissue valves avoid anticoagulation but degenerate faster (worse in younger patients)
- Pregnancy is complex with mechanical valves

---

## SURG-004: Pacemaker or Defibrillator (ICD) Implantation

**Patient-Friendly Label:** Pacemaker or defibrillator implant

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which type do you have?**
   - Options: Pacemaker only | Defibrillator (ICD) | Both (ICD includes pacing) | Not sure
   - ICD indicates higher arrhythmia/sudden death risk

**Linked Tier 1 Diagnoses:**
- CARDIO-024: Heart Block (if pacemaker)
- CARDIO-004: Heart Failure (if ICD for primary prevention)
- CARDIO-009: Cardiomyopathy (common indication for ICD)
- CARDIO-005: Atrial Fibrillation (sometimes)

**Clinical Implications:**
- **Pacemaker:** Usually for bradycardia/heart block
  - Relatively low-risk condition
- **ICD:** For life-threatening arrhythmia risk
  - Suggests significant cardiac disease (low EF, prior sudden death, high-risk condition)

**Score Modifiers:**
- **Pacemaker:** Minimal impact (device compensates)
  - Cardiovascular-Function: **+5 points** (actually helps)
  - Cardiovascular-Risk: **-5 points** (underlying disease risk)
- **ICD:** Indicates serious underlying disease
  - Cardiovascular-Risk: **-15 points**
  - Cardiovascular-Function: **-10 points** (low EF usually)

**Monitoring Needs:**
- Device checks every 3-6 months
- Battery life monitoring (replacement needed every 5-10 years)
- MRI restrictions (most modern devices are MRI-conditional)

---

## SURG-005: Aortic Aneurysm Repair

**Patient-Friendly Label:** Aortic aneurysm repair (open surgery or stent)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What type of repair?**
   - Options: Open surgery | Endovascular stent (EVAR/TEVAR) | Not sure
   - Different follow-up needs

**Linked Tier 1 Diagnoses:**
- CARDIO-012: Aortic Aneurysm

**Clinical Implications:**
- Indicates severe vascular disease
- High cardiovascular risk
- Need for lifelong surveillance

**Score Modifiers:**
- Cardiovascular-Structure: **-18 points** (permanent structural defect despite repair)
- Cardiovascular-Risk: **-20 points** (high mortality if rupture; other aneurysms possible)

**Monitoring Needs:**
- **Post-EVAR:** CT angiography every 6-12 months (endoleak surveillance)
- **Post-open repair:** Imaging annually
- Monitor for other aneurysms (thoracic, popliteal, femoral)
- Aggressive blood pressure control essential

---

## SURG-006: Carotid Artery Surgery (Endarterectomy or Stent)

**Patient-Friendly Label:** Neck artery surgery (carotid artery)

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- NEURO-001: Stroke (or high stroke risk)
- CARDIO-002: Coronary artery disease (often coexist)

**Clinical Implications:**
- Indicates significant carotid stenosis (usually >70%)
- Often part of systemic atherosclerosis (check coronary and peripheral arteries)

**Score Modifiers:**
- Neurological-Risk: **-10 points** (post-procedure, better than pre-procedure)
- Cardiovascular-Risk: **-12 points** (indicates widespread atherosclerosis)

**Monitoring Needs:**
- Carotid duplex ultrasound annually
- Aggressive lipid management (LDL <70)
- Antiplatelet therapy lifelong

---

## SURG-007: Peripheral Artery Bypass (Leg Arteries)

**Patient-Friendly Label:** Leg artery bypass surgery

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- CARDIO-007: Peripheral Artery Disease

**Clinical Implications:**
- Severe PAD (often critical limb ischemia)
- Systemic atherosclerosis
- High cardiovascular event risk

**Score Modifiers:**
- Cardiovascular-Function: **-10 points**
- Cardiovascular-Risk: **-18 points** (very high MI/stroke risk)
- Musculoskeletal-Function: **-8 points** (claudication may persist)

**Monitoring Needs:**
- Vascular surgery follow-up
- Ankle-brachial index (ABI) monitoring
- Bypass graft surveillance
- Foot care critical (ulcer/amputation risk)

---

## SURG-008: AV Fistula or Dialysis Access Creation

**Patient-Friendly Label:** Dialysis access surgery (AV fistula or graft)

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- RENAL-003: End-Stage Renal Disease (ESRD)
- RENAL-002: Dialysis

**Clinical Implications:**
- Confirms end-stage kidney disease
- Patient is on or about to start dialysis

**Score Modifiers:**
- Already captured in dialysis/ESRD diagnosis
- No additional modifier

**Monitoring Needs:**
- Fistula surveillance (check thrill/bruit)
- Fistula maturation (takes 2-3 months)
- Watch for infection, stenosis, thrombosis

---

# SYSTEM 2: ORTHOPEDIC SURGERIES (8 Procedures)

---

## SURG-009: Hip Replacement (Total Hip Arthroplasty)

**Patient-Friendly Label:** Hip replacement

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which hip?**
   - Options: Left | Right | Both hips
   - Bilateral suggests more severe arthritis

**Linked Tier 1 Diagnoses:**
- MUSCULO-001: Osteoarthritis (most common indication)

**Clinical Implications:**
- Severe hip arthritis (pre-surgery)
- Should improve function significantly post-surgery

**Score Modifiers:**
- Musculoskeletal-Structure: **+10 points** (improves structure - replaced damaged joint)
- Musculoskeletal-Function: **+15 points** (improves function significantly)
- Net effect: Surgery improves scores (assuming successful)

**Monitoring Needs:**
- Annual X-ray first few years, then as needed
- Watch for loosening, infection, dislocation
- Fall precautions (dislocation risk)

**Special Considerations:**
- Hip precautions for first 6-12 weeks (avoid certain positions)
- Implant may last 15-20 years; revision may be needed

---

## SURG-010: Knee Replacement (Total Knee Arthroplasty)

**Patient-Friendly Label:** Knee replacement

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which knee?**
   - Options: Left | Right | Both knees

**Linked Tier 1 Diagnoses:**
- MUSCULO-001: Osteoarthritis

**Clinical Implications:**
- Same as hip replacement (severe arthritis)

**Score Modifiers:**
- Musculoskeletal-Structure: **+10 points**
- Musculoskeletal-Function: **+12 points**

**Monitoring Needs:**
- Similar to hip replacement
- Physical therapy critical for optimal outcomes

---

## SURG-011: Spinal Fusion or Back Surgery

**Patient-Friendly Label:** Spinal fusion or major back surgery

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which part of your spine?**
   - Options: Neck (cervical) | Upper back (thoracic) | Lower back (lumbar) | Multiple levels

**Linked Tier 1 Diagnoses:**
- MUSCULO-004: Chronic Back Pain
- MUSCULO-013: Spinal Stenosis

**Clinical Implications:**
- Severe spinal pathology (stenosis, spondylolisthesis, disc disease)
- Outcomes variable (some improve, some persistent pain)

**Score Modifiers:**
- Musculoskeletal-Function: **-5 points** (fusion limits mobility)
- Neurological-Function: **+5 points** (if nerve decompression successful)
- Net: Variable outcome

**Monitoring Needs:**
- Watch for adjacent segment disease (arthritis at levels above/below fusion)
- Chronic pain management often needed
- Physical therapy

---

## SURG-012: Shoulder Surgery (Rotator Cuff Repair)

**Patient-Friendly Label:** Shoulder surgery (rotator cuff or other)

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- MUSCULO-006: Rotator Cuff Tear

**Clinical Implications:**
- May have residual shoulder dysfunction

**Score Modifiers:**
- Musculoskeletal-Function: **-5 points** (variable outcomes)

---

## SURG-013: Knee Arthroscopy / Meniscus or Ligament Repair

**Patient-Friendly Label:** Knee surgery (arthroscopy, meniscus, or ligament repair)

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- MUSCULO-007: Meniscal Tear
- MUSCULO-008: ACL Tear

**Clinical Implications:**
- May predispose to early knee arthritis

**Score Modifiers:**
- Musculoskeletal-Function: **-3 points** (minor residual)
- Musculoskeletal-Risk: **-4 points** (future OA risk)

---

## SURG-014: Carpal Tunnel Release

**Patient-Friendly Label:** Carpal tunnel surgery

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- MUSCULO-009: Carpal Tunnel Syndrome

**Clinical Implications:**
- Usually curative

**Score Modifiers:**
- Minimal (successful surgery resolves issue)

---

## SURG-015: Foot or Ankle Surgery

**Patient-Friendly Label:** Foot or ankle surgery

**Intake Priority:** 2
**Smart Expansion:** No

**Clinical Implications:**
- Variable (bunion, fracture, arthritis, etc.)

**Score Modifiers:**
- Musculoskeletal-Function: **-3 points** (minor impact)

---

## SURG-016: Amputation

**Patient-Friendly Label:** Amputation (leg, foot, toe, finger)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What was amputated?**
   - Options: Toe(s) | Part of foot | Below-knee leg | Above-knee leg | Finger(s) | Arm/hand

**Linked Tier 1 Diagnoses:**
- CARDIO-007: Peripheral Artery Disease (if leg/foot)
- METAB-001: Diabetes with complications (if leg/foot)
- Trauma (if hand/arm)

**Clinical Implications:**
- **Lower extremity amputation:**
  - Usually from PAD or diabetic foot complications
  - Indicates severe vascular disease
  - High mortality risk (50% 5-year mortality post-amputation)
- **Upper extremity:** Usually trauma

**Score Modifiers:**
- Cardiovascular-Risk: **-20 points** (if vascular cause)
- Musculoskeletal-Function: **-15 to -30 points** (depending on level)

**Monitoring Needs:**
- Contralateral limb surveillance (prevent second amputation)
- Prosthetic fitting and training
- Aggressive cardiovascular risk reduction

---

# SYSTEM 3: ABDOMINAL SURGERIES (8 Procedures)

---

## SURG-017: Bariatric / Weight Loss Surgery

**Patient-Friendly Label:** Weight loss surgery (gastric bypass, sleeve, or lap-band)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What type of weight loss surgery?**
   - Options: Gastric bypass (Roux-en-Y) | Gastric sleeve | Lap-band | Other/not sure

**Linked Tier 1 Diagnoses:**
- METAB-005: Obesity (pre-surgery)
- METAB-001: Type 2 Diabetes (often goes into remission post-surgery)
- METAB-004: Metabolic Syndrome

**Clinical Implications:**
- **Major metabolic benefits:**
  - Often resolves or improves Type 2 diabetes
  - Improves hypertension, sleep apnea, joint pain
  - Significant weight loss (typically 50-70% excess weight)
- **Lifelong monitoring required:**
  - Nutritional deficiencies common (iron, B12, calcium, vitamin D)
  - Dumping syndrome (especially bypass)
  - Need for supplements

**Score Modifiers:**
- Metabolic-Function: **+20 points** (major improvement if successful)
- Metabolic-Risk: **-10 points** → **+5 points** (dramatically reduces future risk)
- Cardiovascular-Risk: **-8 points** → **-2 points** (big improvement)
- Net: VERY POSITIVE impact if sustained weight loss

**Monitoring Needs:**
- Annual vitamin B12, iron studies, vitamin D, calcium
- Bone density monitoring (increased fracture risk)
- Weight regain surveillance
- Lifelong bariatric vitamin supplementation

**Special Considerations:**
- Pregnancy requires careful management
- Alcohol absorption altered (bypass especially)
- May need revision surgery if weight regain

---

## SURG-018: Gallbladder Removal (Cholecystectomy)

**Patient-Friendly Label:** Gallbladder removal

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- METAB-028: Gallstones (indication)

**Clinical Implications:**
- Very common surgery
- Minimal long-term implications for most patients
- Some develop post-cholecystectomy diarrhea

**Score Modifiers:**
- None (gallbladder not essential)

**Special Considerations:**
- Recommend low-fat diet if diarrhea issues
- No ongoing monitoring needed

---

## SURG-019: Appendix Removal (Appendectomy)

**Patient-Friendly Label:** Appendix removal

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- None (acute appendicitis)

**Clinical Implications:**
- No long-term health implications

**Score Modifiers:**
- None

---

## SURG-020: Hernia Repair

**Patient-Friendly Label:** Hernia repair (inguinal, umbilical, or hiatal)

**Intake Priority:** 1
**Smart Expansion:** No

**Clinical Implications:**
- Common procedure
- May recur

**Score Modifiers:**
- None

---

## SURG-021: Colon or Bowel Resection

**Patient-Friendly Label:** Colon or intestine surgery (part removed)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Why was this surgery done?**
   - Options: Cancer | Diverticulitis | Inflammatory bowel disease (Crohn's or colitis) | Other

2. **Do you have an ostomy (colostomy or ileostomy)?**
   - Options: Yes, permanent | Yes, but reversed | No

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (if colon cancer)
- METAB-027: Inflammatory Bowel Disease

**Clinical Implications:**
- **If cancer:** Surveillance colonoscopy critical
- **If IBD:** Ongoing disease management
- **If ostomy:** Significant quality of life impact, special care needs

**Score Modifiers:**
- Immune-Risk: Variable based on indication
- Metabolic-Function: **-8 points** (if ostomy or short bowel)

**Monitoring Needs:**
- Colonoscopy surveillance (if cancer or polyps)
- Nutritional monitoring (especially if significant bowel resected)

---

## SURG-022: Liver Resection

**Patient-Friendly Label:** Liver surgery (part of liver removed)

**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Why was this done?**
   - Options: Liver cancer | Metastatic cancer | Benign tumor | Other

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer
- METAB-009: Cirrhosis (if that was underlying)

**Clinical Implications:**
- Liver has good regenerative capacity
- May have residual liver dysfunction depending on extent

**Score Modifiers:**
- Metabolic-Function: **-10 to -20 points** (depends on remaining liver function)
- Immune-Risk: **-15 points** (if cancer)

**Monitoring Needs:**
- Liver function tests
- Imaging surveillance (if cancer)

---

## SURG-023: Pancreas Surgery (Whipple or Other)

**Patient-Friendly Label:** Pancreas surgery

**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What was the reason?**
   - Options: Pancreatic cancer | Pancreatitis | Other

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (often pancreatic cancer - poor prognosis)
- METAB-025: Chronic Pancreatitis

**Clinical Implications:**
- Major surgery with significant morbidity
- Often results in:
  - Diabetes (if enough pancreas removed)
  - Malabsorption (need pancreatic enzymes)

**Score Modifiers:**
- Metabolic-Function: **-20 points**
- Immune-Risk: **-25 points** (if cancer)

**Monitoring Needs:**
- Pancreatic enzyme replacement
- Diabetes management
- Nutritional status

---

## SURG-024: Splenectomy (Spleen Removal)

**Patient-Friendly Label:** Spleen removal

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- Variable (trauma, ITP, lymphoma, etc.)

**Clinical Implications:**
- **Lifelong infection risk** (especially encapsulated bacteria)
- Need for vaccinations

**Score Modifiers:**
- Immune-Risk: **-10 points** (infection susceptibility)

**Monitoring Needs:**
- **CRITICAL:** Vaccinations required
  - Pneumococcal (Prevnar 20 or Pneumovax)
  - Meningococcal
  - Haemophilus influenzae type b (Hib)
- Annual influenza vaccine
- Consider antibiotic prophylaxis for some patients
- Patient education: Fever = urgent evaluation

---

# SYSTEM 4: CANCER SURGERIES (6 Procedures)

---

## SURG-025: Mastectomy (Breast Removal)

**Patient-Friendly Label:** Mastectomy (breast removal for cancer or prevention)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Type of mastectomy:**
   - Options: Lumpectomy (partial) | Single mastectomy | Double mastectomy

2. **Was it for cancer or prevention?**
   - Options: Cancer treatment | Preventive (due to high risk/genetic mutation) | Not sure

3. **Did you have reconstruction?**
   - Options: Yes | No | Planning to

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (Breast)
- FHX-006: Strong family history (if preventive)

**Clinical Implications:**
- **If cancer:** Surveillance and systemic therapy important
- **If preventive:** Significantly reduces breast cancer risk
- Reconstruction has its own complications/monitoring needs

**Score Modifiers:**
- Immune-Risk: **-12 points** (if cancer history) / **+5 points** (if preventive - reduces risk)

**Monitoring Needs:**
- **If cancer history:**
  - Annual mammography (remaining tissue if lumpectomy)
  - Surveillance imaging
  - Endocrine therapy monitoring (if hormone-receptor positive)
- **If reconstruction:**
  - Monitor implants (can rupture, need replacement)

---

## SURG-026: Prostatectomy (Prostate Removal)

**Patient-Friendly Label:** Prostate removal (for cancer)

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (Prostate)

**Clinical Implications:**
- Prostate cancer treatment
- Common side effects:
  - Erectile dysfunction (common)
  - Urinary incontinence (often improves with time)

**Score Modifiers:**
- Immune-Risk: **-10 points** (cancer history, but prostate cancer often indolent)
- Reproductive-Function: **-10 points**
- Renal-Function: **-5 points** (urinary issues)

**Monitoring Needs:**
- PSA monitoring (should be undetectable post-prostatectomy; rise = recurrence)
- Pelvic floor physical therapy for incontinence

---

## SURG-027: Thyroidectomy (Thyroid Removal)

**Patient-Friendly Label:** Thyroid removal (partial or total)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How much of your thyroid was removed?**
   - Options: Half (partial) | Entire thyroid (total) | Not sure

2. **What was the reason?**
   - Options: Cancer | Goiter/large thyroid | Overactive thyroid | Not sure

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (if thyroid cancer)
- METAB-007: Hyperthyroidism (if that was indication)

**Clinical Implications:**
- **If total thyroidectomy:** Requires lifelong thyroid hormone replacement
- **If cancer:** Generally good prognosis (most thyroid cancers are indolent)

**Score Modifiers:**
- Endocrine-Function: **-10 points** (requires hormone replacement)
- Immune-Risk: **-6 points** (if cancer - but thyroid cancer usually low-risk)

**Monitoring Needs:**
- **Total thyroidectomy:**
  - Lifelong levothyroxine
  - TSH monitoring every 6-12 months
- **If cancer:**
  - Thyroglobulin monitoring (tumor marker)
  - Radioactive iodine may be needed

---

## SURG-028: Lung Surgery / Lobectomy

**Patient-Friendly Label:** Lung surgery (lobe or part of lung removed)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Why was this done?**
   - Options: Lung cancer | Other cancer | Infection | Other

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (Lung) - if that was cause

**Clinical Implications:**
- Reduced lung capacity
- If cancer: Prognosis depends on stage

**Score Modifiers:**
- Respiratory-Function: **-15 points**
- Respiratory-Structure: **-12 points**
- Immune-Risk: **-20 points** (if cancer)

**Monitoring Needs:**
- Pulmonary function tests
- CT surveillance (if cancer)

---

## SURG-029: Kidney Removal (Nephrectomy)

**Patient-Friendly Label:** Kidney removal (partial or complete)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How much kidney was removed?**
   - Options: Part of one kidney | Entire kidney (one side) | Both kidneys (on dialysis)

2. **What was the reason?**
   - Options: Kidney cancer | Donation (gave kidney to someone) | Other

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (if kidney cancer)
- RENAL-001: CKD (if function impaired)

**Clinical Implications:**
- **One kidney removed:**
  - Can live normal life with one kidney
  - Remaining kidney compensates (GFR ~70-80% of normal)
  - Need to protect remaining kidney
- **Kidney donation:**
  - Generally healthy individuals
  - Long-term outcomes excellent

**Score Modifiers:**
- Renal-Function: **-15 points** (reduced reserve)
- Immune-Risk: **-12 points** (if cancer)

**Monitoring Needs:**
- Annual kidney function (creatinine, GFR)
- Blood pressure control critical
- Avoid nephrotoxins (NSAIDs, contrast when possible)

---

## SURG-030: Brain Surgery

**Patient-Friendly Label:** Brain surgery

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What was the reason?**
   - Options: Brain tumor | Aneurysm | Bleed/stroke | Epilepsy | Other

**Linked Tier 1 Diagnoses:**
- IMMUNE-001: Cancer (if brain tumor)
- NEURO-001: Stroke (if hemorrhage)
- NEURO-006: Epilepsy

**Clinical Implications:**
- Variable depending on indication and extent
- May have residual neurological deficits

**Score Modifiers:**
- Neurological-Structure: **-15 to -25 points**
- Neurological-Function: Variable
- Immune-Risk: **-20 points** (if malignant tumor)

**Monitoring Needs:**
- MRI surveillance (if tumor)
- Seizure monitoring (anti-epileptic drugs often needed)

---

# SYSTEM 5: TRANSPLANT SURGERIES (4 Procedures)

---

## SURG-031: Kidney Transplant

**Patient-Friendly Label:** Kidney transplant

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **When did you receive the transplant?**
   - Options: Less than 1 year ago | 1-5 years ago | More than 5 years ago

2. **Where did the kidney come from?**
   - Options: Living donor | Deceased donor | Not sure

**Linked Tier 1 Diagnoses:**
- RENAL-003: ESRD (pre-transplant)

**Clinical Implications:**
- **MAJOR improvement** in quality of life vs. dialysis
- Requires lifelong immunosuppression
- Transplant may eventually fail (chronic rejection)

**Score Modifiers:**
- Renal-Function: **+40 points** (huge improvement from ESRD)
- Immune-Function: **-10 points** (immunosuppression)
- Immune-Risk: **-8 points** (infection, malignancy risk)
- Net: MAJOR POSITIVE impact

**Monitoring Needs:**
- Creatinine monitoring (frequent early, then every 3 months)
- Immunosuppression drug levels
- BK virus, CMV monitoring
- Avoid live vaccines
- Cancer screening (skin cancer, PTLD)

---

## SURG-032: Liver Transplant

**Patient-Friendly Label:** Liver transplant

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- METAB-009: Cirrhosis (pre-transplant)

**Clinical Implications:**
- Life-saving for end-stage liver disease
- Requires immunosuppression

**Score Modifiers:**
- Metabolic-Function: **+40 points** (huge improvement)
- Immune-Function: **-10 points**

**Monitoring Needs:**
- Similar to kidney transplant
- Liver function tests
- Rejection surveillance

---

## SURG-033: Heart Transplant

**Patient-Friendly Label:** Heart transplant

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- CARDIO-004: Heart Failure (end-stage)
- CARDIO-009: Cardiomyopathy

**Clinical Implications:**
- Life-saving for end-stage heart failure
- Excellent quality of life post-transplant (if no complications)

**Score Modifiers:**
- Cardiovascular-Function: **+50 points** (dramatic improvement)
- Immune-Function: **-10 points**

**Monitoring Needs:**
- Frequent endomyocardial biopsies (rejection surveillance)
- Immunosuppression monitoring
- Cardiac catheterization annually (transplant vasculopathy)

---

## SURG-034: Lung Transplant

**Patient-Friendly Label:** Lung transplant

**Intake Priority:** 1
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- RESP-002: COPD (end-stage)
- RESP-005: Pulmonary Fibrosis

**Clinical Implications:**
- For end-stage lung disease
- Complex post-operative course

**Score Modifiers:**
- Respiratory-Function: **+40 points**
- Immune-Function: **-10 points**

**Monitoring Needs:**
- Pulmonary function tests frequently
- Bronchoscopy for rejection surveillance

---

# SYSTEM 6: WOMEN'S HEALTH SURGERIES (3 Procedures)

---

## SURG-035: Hysterectomy (Uterus Removal)

**Patient-Friendly Label:** Hysterectomy (uterus removal)

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What was removed?**
   - Options: Uterus only | Uterus + ovaries | Uterus + ovaries + cervix (total) | Not sure

**Linked Tier 1 Diagnoses:**
- REPRO-007: Uterine Fibroids (common indication)
- IMMUNE-001: Cancer (if uterine or ovarian cancer)

**Clinical Implications:**
- **If ovaries also removed (especially before menopause):**
  - Surgical menopause (sudden, severe symptoms)
  - Increased cardiovascular and bone health risks
  - May need hormone replacement therapy

**Score Modifiers:**
- Reproductive-Function: N/A (no longer relevant)
- Endocrine-Function: **-8 points** (if ovaries removed pre-menopause)
- Cardiovascular-Risk: **-5 points** (if ovaries removed)

**Monitoring Needs:**
- If ovaries removed:
  - Consider hormone replacement therapy (HRT)
  - Bone density monitoring
  - Cardiovascular risk factor management

---

## SURG-036: Cesarean Section (C-Section)

**Patient-Friendly Label:** C-section delivery

**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **How many C-sections have you had?**
   - Options: 1 | 2 | 3 or more

**Linked Tier 1 Diagnoses:**
- None (obstetric indication)

**Clinical Implications:**
- **Multiple C-sections:**
  - Scar tissue increases with each surgery
  - Placenta complications in future pregnancies (placenta previa, accreta)
  - Usually limit to 3-4 C-sections

**Score Modifiers:**
- Reproductive-Risk: **-5 points** (if 3+ C-sections - future pregnancy complications)

**Special Considerations:**
- VBAC (vaginal birth after cesarean) may be option for some
- Future pregnancies require close monitoring

---

## SURG-037: Breast Reconstruction

**Patient-Friendly Label:** Breast reconstruction (after mastectomy)

**Intake Priority:** 2
**Smart Expansion:** No

**Linked Tier 1 Diagnoses:**
- Linked to SURG-025 (Mastectomy)

**Clinical Implications:**
- Implants need monitoring (rupture risk)
- May need revisions/replacements

**Score Modifiers:**
- None (cosmetic restoration)

**Monitoring Needs:**
- MRI surveillance if silicone implants (check for rupture)

---

# SYSTEM 7: OTHER COMMON SURGERIES (3 Procedures)

---

## SURG-038: Cataract Surgery

**Patient-Friendly Label:** Cataract surgery

**Intake Priority:** 2
**Smart Expansion:** No

**Clinical Implications:**
- Very common, low-risk
- Improves vision

**Score Modifiers:**
- None (positive outcome)

---

## SURG-039: Tonsillectomy / Adenoidectomy

**Patient-Friendly Label:** Tonsils/adenoids removed

**Intake Priority:** 2
**Smart Expansion:** No

**Clinical Implications:**
- Common childhood procedure
- No long-term implications

**Score Modifiers:**
- None

---

## SURG-040: Sinus Surgery

**Patient-Friendly Label:** Sinus surgery

**Intake Priority:** 2
**Smart Expansion:** No

**Clinical Implications:**
- For chronic sinusitis
- May improve quality of life

**Score Modifiers:**
- None

---

# INTAKE PRIORITY SUMMARY

## PRIORITY 1 (Always Visible - 20 Surgeries)

**Cardiovascular:**
- Heart bypass surgery
- Heart stent placement
- Heart valve surgery
- Pacemaker/defibrillator
- Aortic aneurysm repair
- Dialysis access (AV fistula)

**Orthopedic:**
- Hip replacement
- Knee replacement
- Spinal fusion/back surgery
- Amputation

**Abdominal:**
- Bariatric/weight loss surgery
- Gallbladder removal
- Appendix removal
- Hernia repair
- Colon/bowel resection

**Cancer:**
- Mastectomy
- Prostatectomy
- Thyroidectomy
- Lung surgery
- Kidney removal

**Transplant:**
- Kidney transplant
- Liver transplant
- Heart transplant
- Lung transplant

**Women's Health:**
- Hysterectomy
- C-section

**TOTAL: 29 surgeries Priority 1**

## PRIORITY 2 (Expandable Section - 11 Surgeries)

- Carotid artery surgery
- Peripheral artery bypass
- Shoulder surgery
- Knee arthroscopy
- Carpal tunnel release
- Liver resection
- Pancreas surgery
- Splenectomy
- Breast reconstruction
- Cataract surgery
- Sinus surgery

---

**Document Status:** ✅ COMPLETE - 40 Tier 1 Surgical Procedures
**Next Priority:** Allergy Library

---

**End of Document - Surgical History Tier 1 Library v1.0**
