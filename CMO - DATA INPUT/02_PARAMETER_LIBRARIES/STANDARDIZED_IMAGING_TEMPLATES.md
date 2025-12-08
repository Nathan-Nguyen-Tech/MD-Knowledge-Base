# Standardized Imaging Finding Templates

**Document Version:** 1.0
**Last Updated:** 2025-11-18
**Purpose:** Define standardized data extraction templates for all imaging modalities to enable consistent parameter capture regardless of internal or third-party source

---

## Overview

This document provides structured templates for extracting standardized findings from imaging reports. These templates are designed to:

1. **Work universally** - whether images performed internally or by third-party facilities
2. **Extract consistent data** - same parameters captured regardless of reporting format
3. **Enable scoring** - findings mapped to structure/function/risk domains
4. **Support longitudinal tracking** - standardized nomenclature for serial comparison

Each template includes:
- Standardized parameter list
- Normal reference ranges
- Abnormal finding classifications
- Severity grading where applicable
- System domain mapping for scoring integration

---

## Template 1: Carotid Ultrasound

### Purpose
Screen for atherosclerotic disease and stroke risk

### Standard Protocol
Bilateral common carotid arteries (CCA), internal carotid arteries (ICA), external carotid arteries (ECA), vertebral arteries

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_CAR_001 | Right CCA Intima-Media Thickness | Numeric | mm | Cardiovascular-Structure |
| IMG_CAR_002 | Left CCA Intima-Media Thickness | Numeric | mm | Cardiovascular-Structure |
| IMG_CAR_003 | Right ICA Stenosis Degree | 0%, <50%, 50-69%, 70-99%, Occluded | % | Cardiovascular-Risk |
| IMG_CAR_004 | Left ICA Stenosis Degree | 0%, <50%, 50-69%, 70-99%, Occluded | % | Cardiovascular-Risk |
| IMG_CAR_005 | Right CCA Plaque Present | Yes / No | Boolean | Cardiovascular-Structure |
| IMG_CAR_006 | Left CCA Plaque Present | Yes / No | Boolean | Cardiovascular-Structure |
| IMG_CAR_007 | Right ICA Plaque Present | Yes / No | Boolean | Cardiovascular-Structure |
| IMG_CAR_008 | Left ICA Plaque Present | Yes / No | Boolean | Cardiovascular-Structure |
| IMG_CAR_009 | Plaque Characteristics | None, Calcified, Soft, Mixed, Ulcerated | Categorical | Cardiovascular-Risk |
| IMG_CAR_010 | Right Vertebral Artery Flow | Normal, Reduced, Reversed, Absent | Categorical | Neurological-Risk |
| IMG_CAR_011 | Left Vertebral Artery Flow | Normal, Reduced, Reversed, Absent | Categorical | Neurological-Risk |

### Reference Ranges

**Carotid IMT:**
- Normal: <0.9 mm
- Increased: 0.9-1.3 mm
- Plaque defined as: >1.3 mm or focal thickening >50% of surrounding IMT

**Stenosis Grading:**
- Normal: 0%
- Mild: <50%
- Moderate: 50-69%
- Severe: 70-99%
- Occluded: 100%

### Scoring Impact

- **Critical Alert:** ≥70% stenosis either side (urgent vascular referral)
- **High Risk:** 50-69% stenosis, ulcerated plaque
- **Moderate Risk:** Plaque present, IMT >1.3mm

---

## Template 2: Cardiac Echocardiogram (Transthoracic)

### Purpose
Assess cardiac structure, function, and hemodynamics

### Standard Protocol
2D, M-Mode, Doppler evaluation of all chambers and valves

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_ECHO_001 | Left Ventricular Ejection Fraction (LVEF) | Numeric (35-75) | % | Cardiovascular-Function |
| IMG_ECHO_002 | LV End-Diastolic Dimension | Numeric | mm | Cardiovascular-Structure |
| IMG_ECHO_003 | LV End-Systolic Dimension | Numeric | mm | Cardiovascular-Structure |
| IMG_ECHO_004 | Interventricular Septum Thickness | Numeric | mm | Cardiovascular-Structure |
| IMG_ECHO_005 | LV Posterior Wall Thickness | Numeric | mm | Cardiovascular-Structure |
| IMG_ECHO_006 | Left Atrial Volume Index | Numeric | mL/m² | Cardiovascular-Structure |
| IMG_ECHO_007 | Right Ventricular Function | Normal, Mild dysfunction, Moderate, Severe | Categorical | Cardiovascular-Function |
| IMG_ECHO_008 | Diastolic Function Grade | Normal, Grade I, Grade II, Grade III | Categorical | Cardiovascular-Function |
| IMG_ECHO_009 | Mitral Valve Status | Normal, Regurgitation (trace/mild/moderate/severe), Stenosis | Categorical | Cardiovascular-Structure |
| IMG_ECHO_010 | Aortic Valve Status | Normal, Regurgitation (trace/mild/moderate/severe), Stenosis | Categorical | Cardiovascular-Structure |
| IMG_ECHO_011 | Tricuspid Valve Status | Normal, Regurgitation (trace/mild/moderate/severe), Stenosis | Categorical | Cardiovascular-Structure |
| IMG_ECHO_012 | Pulmonic Valve Status | Normal, Regurgitation, Stenosis | Categorical | Cardiovascular-Structure |
| IMG_ECHO_013 | Estimated PA Systolic Pressure | Numeric | mmHg | Cardiovascular-Risk / Respiratory-Risk |
| IMG_ECHO_014 | Pericardial Effusion | None, Small, Moderate, Large, Tamponade | Categorical | Cardiovascular-Risk |
| IMG_ECHO_015 | Regional Wall Motion Abnormalities | None / Present (specify segments) | Categorical | Cardiovascular-Function |

### Reference Ranges

**LVEF:**
- Normal: ≥55%
- Mild dysfunction: 45-54%
- Moderate: 30-44%
- Severe: <30%

**LV Wall Thickness:**
- Normal: ≤11 mm
- Mild hypertrophy: 12-13 mm
- Moderate: 14-15 mm
- Severe: ≥16 mm

**Left Atrial Volume Index:**
- Normal: ≤34 mL/m²
- Mild enlargement: 35-41 mL/m²
- Moderate: 42-48 mL/m²
- Severe: >48 mL/m²

### Scoring Impact

- **Critical Alert:** LVEF <30%, severe valve disease, cardiac tamponade
- **High Risk:** LVEF 30-40%, moderate-severe valve disease, PA pressure >50 mmHg
- **Moderate Risk:** Diastolic dysfunction, mild valve disease, LVH

---

## Template 3: Liver Ultrasound

### Purpose
Screen for fatty liver disease, cirrhosis, masses

### Standard Protocol
Right upper quadrant evaluation of liver parenchyma, vasculature, biliary tree

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_LIV_001 | Liver Size (Craniocaudal) | Numeric | cm | Metabolic-Structure |
| IMG_LIV_002 | Liver Echogenicity | Normal, Mildly increased, Moderately increased, Markedly increased | Categorical | Metabolic-Structure |
| IMG_LIV_003 | Hepatic Steatosis Grade | None, Grade 1 (mild), Grade 2 (moderate), Grade 3 (severe) | Categorical | Metabolic-Risk |
| IMG_LIV_004 | Liver Surface | Smooth, Nodular | Categorical | Metabolic-Structure |
| IMG_LIV_005 | Liver Parenchyma Texture | Homogeneous, Coarse, Heterogeneous | Categorical | Metabolic-Structure |
| IMG_LIV_006 | Portal Vein Diameter | Numeric | mm | Metabolic-Risk |
| IMG_LIV_007 | Portal Vein Flow Direction | Hepatopetal (normal), Hepatofugal (reversed), Absent | Categorical | Metabolic-Risk |
| IMG_LIV_008 | Splenomegaly | No, Yes (measure length) | Boolean / cm | Immune-Structure |
| IMG_LIV_009 | Ascites | None, Small, Moderate, Large | Categorical | Metabolic-Risk |
| IMG_LIV_010 | Focal Liver Lesion | None / Present (size, characteristics) | Boolean / cm | Metabolic-Risk |
| IMG_LIV_011 | Gallbladder Status | Normal, Stones, Polyps, Wall thickening, Sludge | Categorical | Metabolic-Structure |
| IMG_LIV_012 | Bile Duct Dilation | No, Yes (measure diameter) | Boolean / mm | Metabolic-Structure |

### Reference Ranges

**Liver Size:**
- Normal: <15.5 cm craniocaudal

**Hepatic Steatosis Grading (by echogenicity):**
- Grade 1 (Mild): Slight diffuse increase, normal diaphragm/vessel borders
- Grade 2 (Moderate): Moderate increase, impaired diaphragm/vessel borders
- Grade 3 (Severe): Marked increase, poor beam penetration

**Portal Vein:**
- Normal diameter: <13 mm
- Portal hypertension: ≥13 mm

### Scoring Impact

- **Critical Alert:** Liver mass requiring immediate workup, large ascites, portal vein thrombosis
- **High Risk:** Grade 3 steatosis, cirrhotic changes (nodular surface + splenomegaly)
- **Moderate Risk:** Grade 2 steatosis, gallstones, mild splenomegaly

---

## Template 4: Renal Ultrasound

### Purpose
Assess kidney structure, size, hydronephrosis, stones, masses

### Standard Protocol
Bilateral kidney evaluation with Doppler of renal arteries

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_REN_001 | Right Kidney Length | Numeric | cm | Renal-Structure |
| IMG_REN_002 | Left Kidney Length | Numeric | cm | Renal-Structure |
| IMG_REN_003 | Right Kidney Cortical Thickness | Numeric | mm | Renal-Structure |
| IMG_REN_004 | Left Kidney Cortical Thickness | Numeric | mm | Renal-Structure |
| IMG_REN_005 | Right Kidney Echogenicity | Normal, Increased | Categorical | Renal-Structure |
| IMG_REN_006 | Left Kidney Echogenicity | Normal, Increased | Categorical | Renal-Structure |
| IMG_REN_007 | Right Hydronephrosis | None, Mild, Moderate, Severe | Categorical | Renal-Risk |
| IMG_REN_008 | Left Hydronephrosis | None, Mild, Moderate, Severe | Categorical | Renal-Risk |
| IMG_REN_009 | Right Kidney Stone | None / Present (size, location) | Boolean / mm | Renal-Risk |
| IMG_REN_010 | Left Kidney Stone | None / Present (size, location) | Boolean / mm | Renal-Risk |
| IMG_REN_011 | Right Renal Artery Resistive Index | Numeric (0.50-0.75) | Ratio | Renal-Function |
| IMG_REN_012 | Left Renal Artery Resistive Index | Numeric (0.50-0.75) | Ratio | Renal-Function |
| IMG_REN_013 | Renal Mass | None / Present (side, size, characteristics) | Boolean / cm | Renal-Risk |

### Reference Ranges

**Kidney Length:**
- Normal: 9-13 cm (average 10-12 cm)
- Small kidneys: <9 cm (chronic kidney disease)

**Cortical Thickness:**
- Normal: >7 mm
- Thinned: <7 mm (suggests chronic disease)

**Resistive Index (RI):**
- Normal: 0.50-0.70
- Elevated: >0.70 (suggests intrarenal disease or obstruction)

### Scoring Impact

- **Critical Alert:** Severe hydronephrosis, renal mass >4cm, bilateral small kidneys
- **High Risk:** Moderate hydronephrosis, large stones (>5mm), RI >0.75
- **Moderate Risk:** Increased echogenicity, cortical thinning, small stones

---

## Template 5: Thyroid Ultrasound

### Purpose
Evaluate thyroid size, nodules, echogenicity

### Standard Protocol
Both lobes and isthmus in transverse and longitudinal planes

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_THY_001 | Right Lobe Volume | Numeric | mL | Endocrine-Structure |
| IMG_THY_002 | Left Lobe Volume | Numeric | mL | Endocrine-Structure |
| IMG_THY_003 | Isthmus Thickness | Numeric | mm | Endocrine-Structure |
| IMG_THY_004 | Thyroid Echogenicity | Normal, Diffusely decreased, Heterogeneous | Categorical | Endocrine-Structure |
| IMG_THY_005 | Thyroid Nodule Present | None / Yes (number) | Boolean | Endocrine-Risk |
| IMG_THY_006 | Largest Nodule Size | Numeric | mm | Endocrine-Risk |
| IMG_THY_007 | Nodule Characteristics | Solid, Cystic, Mixed, Spongiform | Categorical | Endocrine-Risk |
| IMG_THY_008 | Nodule Echogenicity | Hyperechoic, Isoechoic, Hypoechoic, Markedly hypoechoic | Categorical | Endocrine-Risk |
| IMG_THY_009 | Nodule Margins | Well-defined, Ill-defined, Irregular | Categorical | Endocrine-Risk |
| IMG_THY_010 | Microcalcifications | Absent, Present | Boolean | Endocrine-Risk |
| IMG_THY_011 | Nodule Vascularity | None, Peripheral, Central, Mixed | Categorical | Endocrine-Risk |
| IMG_THY_012 | Lymphadenopathy | None / Present (size, location) | Boolean / mm | Endocrine-Risk |
| IMG_THY_013 | ACR TI-RADS Score | 1, 2, 3, 4, 5 | Categorical | Endocrine-Risk |

### Reference Ranges

**Thyroid Volume:**
- Men: <18 mL
- Women: <16 mL

**ACR TI-RADS Risk Stratification:**
- TR1: Benign (0% malignancy risk)
- TR2: Not suspicious (0%)
- TR3: Mildly suspicious (5%)
- TR4: Moderately suspicious (5-20%)
- TR5: Highly suspicious (>20%)

### Scoring Impact

- **Critical Alert:** TI-RADS 5, suspicious lymphadenopathy
- **High Risk:** TI-RADS 4, nodule >2cm with suspicious features
- **Moderate Risk:** TI-RADS 3, multiple nodules, diffuse heterogeneity

---

## Template 6: Chest X-Ray (Posterior-Anterior & Lateral)

### Purpose
Screen for cardiopulmonary abnormalities

### Standard Protocol
PA and lateral views, inspiratory films

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_CXR_001 | Cardiac Silhouette Size | Normal, Borderline, Enlarged | Categorical | Cardiovascular-Structure |
| IMG_CXR_002 | Cardiothoracic Ratio | Numeric (0.40-0.55) | Ratio | Cardiovascular-Structure |
| IMG_CXR_003 | Pulmonary Vasculature | Normal, Increased (congestion), Decreased | Categorical | Cardiovascular-Risk / Respiratory-Risk |
| IMG_CXR_004 | Lung Fields | Clear, Infiltrate, Nodule, Mass, Fibrosis | Categorical | Respiratory-Structure |
| IMG_CXR_005 | Pleural Effusion | None, Small, Moderate, Large | Categorical | Respiratory-Risk |
| IMG_CXR_006 | Pneumothorax | None / Present (size) | Boolean / % | Respiratory-Risk |
| IMG_CXR_007 | Mediastinal Contour | Normal, Widened, Mass | Categorical | Respiratory-Risk |
| IMG_CXR_008 | Aortic Contour | Normal, Tortuous, Dilated, Calcified | Categorical | Cardiovascular-Structure |
| IMG_CXR_009 | Bony Thorax | Normal, Degenerative changes, Fracture, Lytic lesion | Categorical | Musculoskeletal-Structure |
| IMG_CXR_010 | Diaphragm | Normal, Elevated (right/left), Flattened | Categorical | Respiratory-Structure |

### Reference Ranges

**Cardiothoracic Ratio:**
- Normal: <0.50 (cardiac width / thoracic width)
- Borderline: 0.50-0.55
- Cardiomegaly: >0.55

### Scoring Impact

- **Critical Alert:** Large pneumothorax, massive effusion, mediastinal mass, acute infiltrate
- **High Risk:** Cardiomegaly (CTR >0.55), pulmonary edema, pulmonary nodule/mass
- **Moderate Risk:** Small effusion, degenerative changes

---

## Template 7: Electrocardiogram (12-Lead EKG)

### Purpose
Screen for arrhythmias, ischemia, conduction abnormalities, structural disease

### Standard Protocol
Standard 12-lead at rest (25 mm/sec, 10 mm/mV)

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_EKG_001 | Heart Rate | Numeric (40-100) | bpm | Cardiovascular-Function |
| IMG_EKG_002 | Rhythm | Sinus, Atrial fibrillation, Atrial flutter, Other | Categorical | Cardiovascular-Function |
| IMG_EKG_003 | PR Interval | Numeric (120-200) | ms | Cardiovascular-Function |
| IMG_EKG_004 | QRS Duration | Numeric (80-120) | ms | Cardiovascular-Structure |
| IMG_EKG_005 | QT Interval (corrected) | Numeric (350-460) | ms | Cardiovascular-Risk |
| IMG_EKG_006 | QRS Axis | Normal (-30 to +90°), LAD, RAD, Extreme | Categorical | Cardiovascular-Structure |
| IMG_EKG_007 | ST Segment Changes | None, Elevation, Depression | Categorical | Cardiovascular-Risk |
| IMG_EKG_008 | T Wave Abnormalities | None, Inverted, Flattened, Peaked | Categorical | Cardiovascular-Risk |
| IMG_EKG_009 | Q Waves | None / Pathologic (location) | Boolean | Cardiovascular-Structure |
| IMG_EKG_010 | Left Ventricular Hypertrophy | None, Possible, Present | Categorical | Cardiovascular-Structure |
| IMG_EKG_011 | Right Ventricular Hypertrophy | None, Possible, Present | Categorical | Cardiovascular-Structure |
| IMG_EKG_012 | Bundle Branch Block | None, RBBB, LBBB, Incomplete | Categorical | Cardiovascular-Function |
| IMG_EKG_013 | AV Block | None, 1st degree, 2nd degree (Mobitz I/II), 3rd degree | Categorical | Cardiovascular-Risk |
| IMG_EKG_014 | Atrial Enlargement | None, Left, Right, Biatrial | Categorical | Cardiovascular-Structure |
| IMG_EKG_015 | Premature Complexes | None, PACs, PVCs, Frequent PVCs | Categorical | Cardiovascular-Risk |

### Reference Ranges

**PR Interval:**
- Normal: 120-200 ms
- Short: <120 ms (pre-excitation syndrome)
- Prolonged: >200 ms (1st degree AV block)

**QRS Duration:**
- Normal: 80-120 ms
- Prolonged: >120 ms (bundle branch block, ventricular conduction delay)

**QTc (Corrected QT):**
- Normal: 350-450 ms (men), 350-460 ms (women)
- Borderline: 450-470 ms (men), 460-480 ms (women)
- Prolonged: >470 ms (men), >480 ms (women) - arrhythmia risk

### Scoring Impact

- **Critical Alert:** ST elevation (STEMI), 3rd degree AV block, sustained VT, QTc >500ms
- **High Risk:** Atrial fibrillation, pathologic Q waves, 2nd degree AV block, LVH with strain
- **Moderate Risk:** Frequent PVCs, 1st degree AV block, nonspecific ST-T changes

---

## Template 8: CT Chest (Non-Contrast)

### Purpose
Detailed lung parenchyma evaluation, mediastinal assessment

### Standard Protocol
Thin-slice axial images, coronal/sagittal reconstructions

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_CTC_001 | Pulmonary Nodule | None / Present (number, size) | Boolean / mm | Respiratory-Risk |
| IMG_CTC_002 | Largest Nodule Size | Numeric | mm | Respiratory-Risk |
| IMG_CTC_003 | Nodule Characteristics | Solid, Ground-glass, Part-solid, Calcified | Categorical | Respiratory-Risk |
| IMG_CTC_004 | Lung-RADS Category | 0, 1, 2, 3, 4A, 4B, 4X | Categorical | Respiratory-Risk |
| IMG_CTC_005 | Emphysema | None, Trace, Mild, Moderate, Severe | Categorical | Respiratory-Structure |
| IMG_CTC_006 | Interstitial Changes | None, Reticular, Ground-glass, Honeycombing | Categorical | Respiratory-Structure |
| IMG_CTC_007 | Bronchiectasis | None / Present (location) | Boolean | Respiratory-Structure |
| IMG_CTC_008 | Pleural Thickening | None / Present | Boolean | Respiratory-Structure |
| IMG_CTC_009 | Lymphadenopathy | None / Present (station, size) | Boolean / mm | Immune-Risk / Respiratory-Risk |
| IMG_CTC_010 | Coronary Artery Calcification | None, Mild, Moderate, Severe | Categorical | Cardiovascular-Risk |
| IMG_CTC_011 | Aortic Diameter (ascending) | Numeric | mm | Cardiovascular-Structure |
| IMG_CTC_012 | Aortic Calcification | None, Mild, Moderate, Severe | Categorical | Cardiovascular-Risk |

### Reference Ranges

**Lung-RADS (Lung Cancer Screening):**
- Category 1: Negative (0% malignancy risk)
- Category 2: Benign (<1%)
- Category 3: Probably benign (1-2%)
- Category 4A: Suspicious (5-15%)
- Category 4B: Very suspicious (>15%)
- Category 4X: Additional findings warranting clinical evaluation

**Aortic Diameter (Ascending):**
- Normal: <37 mm (men), <34 mm (women)
- Mild dilation: 37-40 mm
- Moderate: 40-45 mm
- Severe: >45 mm (aneurysm)

### Scoring Impact

- **Critical Alert:** Lung-RADS 4B/4X, aortic aneurysm >5cm
- **High Risk:** Lung-RADS 4A, moderate-severe emphysema, significant lymphadenopathy
- **Moderate Risk:** Lung-RADS 3, mild emphysema, coronary calcification

---

## Template 9: CT Abdomen/Pelvis (With or Without Contrast)

### Purpose
Evaluate abdominal organs, vasculature, masses, inflammation

### Standard Protocol
Axial images with coronal/sagittal reconstructions, oral/IV contrast per protocol

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_CTA_001 | Liver Size | Normal, Enlarged, Small | Categorical | Metabolic-Structure |
| IMG_CTA_002 | Liver Attenuation | Normal, Decreased (fatty), Heterogeneous | Categorical | Metabolic-Structure |
| IMG_CTA_003 | Liver Mass | None / Present (size, characteristics) | Boolean / cm | Metabolic-Risk |
| IMG_CTA_004 | Spleen Size | Normal, Enlarged (measure) | Categorical / cm | Immune-Structure |
| IMG_CTA_005 | Pancreas | Normal, Atrophy, Calcifications, Mass | Categorical | Metabolic-Risk |
| IMG_CTA_006 | Kidneys Size/Enhancement | Normal, Small, Mass, Cyst | Categorical | Renal-Structure |
| IMG_CTA_007 | Adrenal Nodule | None / Present (size, density) | Boolean / mm | Endocrine-Risk |
| IMG_CTA_008 | Abdominal Aorta Diameter | Numeric | mm | Cardiovascular-Structure |
| IMG_CTA_009 | Aortic Aneurysm | None / Present (size) | Boolean / cm | Cardiovascular-Risk |
| IMG_CTA_010 | Lymphadenopathy | None / Present (location, size) | Boolean / mm | Immune-Risk |
| IMG_CTA_011 | Ascites | None, Small, Moderate, Large | Categorical | Metabolic-Risk |
| IMG_CTA_012 | Bowel Wall Thickening | None / Present (location) | Boolean | Metabolic-Risk |
| IMG_CTA_013 | Free Air | None / Present | Boolean | Metabolic-Risk |
| IMG_CTA_014 | Bone Lesions | None / Present (sclerotic/lytic) | Boolean | Musculoskeletal-Risk |

### Reference Ranges

**Abdominal Aorta:**
- Normal: <30 mm
- Ectatic: 30-40 mm
- Aneurysm: >30 mm (>50% normal diameter) or >40 mm absolute

### Scoring Impact

- **Critical Alert:** AAA >5.5cm, free air, large bowel obstruction, organ rupture
- **High Risk:** AAA 4-5.5cm, solid organ mass, moderate ascites
- **Moderate Risk:** Small AAA (3-4cm), adrenal nodule, hepatic cysts

---

## Template 10: MRI Brain (With or Without Contrast)

### Purpose
Evaluate brain parenchyma, vasculature, structural abnormalities

### Standard Protocol
T1, T2, FLAIR sequences minimum

### Standardized Parameters

| Parameter ID | Finding | Values/Range | Unit | System Assignment |
|--------------|---------|--------------|------|-------------------|
| IMG_MRB_001 | White Matter Hyperintensities | None, Mild, Moderate, Severe | Categorical | Neurological-Structure |
| IMG_MRB_002 | Fazekas Scale (WMH severity) | 0, 1, 2, 3 | Categorical | Neurological-Structure |
| IMG_MRB_003 | Cerebral Atrophy | None, Mild, Moderate, Severe | Categorical | Neurological-Structure |
| IMG_MRB_004 | Hippocampal Atrophy | None, Mild, Moderate, Severe | Categorical | Neurological-Structure |
| IMG_MRB_005 | Lacunar Infarcts | None / Present (number, location) | Boolean | Neurological-Risk |
| IMG_MRB_006 | Acute Infarct | None / Present (location, size) | Boolean / cm | Neurological-Risk |
| IMG_MRB_007 | Chronic Infarct | None / Present (location, size) | Boolean / cm | Neurological-Structure |
| IMG_MRB_008 | Microhemorrhages | None / Present (number) | Boolean | Neurological-Risk |
| IMG_MRB_009 | Intracranial Mass | None / Present (location, size) | Boolean / cm | Neurological-Risk |
| IMG_MRB_010 | Hydrocephalus | None, Mild, Moderate, Severe | Categorical | Neurological-Risk |
| IMG_MRB_011 | Midline Shift | None / Present (mm) | Boolean / mm | Neurological-Risk |
| IMG_MRB_012 | Vascular Stenosis | None / Present (location, degree) | Boolean / % | Neurological-Risk |
| IMG_MRB_013 | Aneurysm | None / Present (location, size) | Boolean / mm | Neurological-Risk |

### Reference Ranges

**Fazekas Scale (White Matter Hyperintensity):**
- Grade 0: None
- Grade 1: Punctate foci
- Grade 2: Beginning confluent lesions
- Grade 3: Large confluent areas

**Age-Expected WMH:**
- <50 years: Fazekas 0-1 expected
- 50-70 years: Fazekas 1-2 expected
- >70 years: Fazekas 2 expected

### Scoring Impact

- **Critical Alert:** Acute infarct, mass with midline shift, unruptured aneurysm >7mm
- **High Risk:** Multiple lacunar infarcts, severe atrophy (age-inappropriate), microhemorrhages
- **Moderate Risk:** Fazekas 2-3 WMH, mild-moderate atrophy

---

## Data Extraction Workflow

### For Third-Party Reports

1. **Receive imaging report** (PDF, text, or dictation)
2. **Parse report** using template matching (manual or NLP-assisted)
3. **Extract standardized findings** matching parameter IDs
4. **Map values** to categorical scales or numeric ranges
5. **Flag missing data** if key parameters not reported
6. **Manual review** for quality assurance

### For Internal Imaging

1. **Perform imaging** per standardized protocol
2. **Generate report** using structured templates
3. **Auto-populate** parameters from reporting system
4. **Direct integration** to Health Overview Dashboard database

### Quality Assurance

- **Completeness check:** All template parameters addressed (or marked "not assessed")
- **Consistency check:** Findings align with severity classifications
- **Alert validation:** Critical/high-risk findings flagged for clinical review
- **Longitudinal comparison:** Prior studies linked for trend analysis

---

## Integration with Scoring System

### System Domain Mapping

Each imaging parameter maps to 1-3 system domains:

**Example: Carotid IMT (IMG_CAR_001)**
- Primary: Cardiovascular-Structure (80% weight)
- Secondary: Cardiovascular-Risk (60% weight)
- Tertiary: Neurological-Risk (30% weight)

### Normalization Approach

**Binary Findings (Present/Absent):**
- Absent = 85 points (baseline)
- Present = Severity-dependent penalty
  - Mild: 70-80 points
  - Moderate: 50-65 points
  - Severe: 20-45 points

**Categorical Findings (Ordinal):**
- Use ordinal scoring with target at "Normal" category
- Penalties increase with worsening category

**Numeric Findings:**
- Apply standard normalization methods (bidirectional/unidirectional)
- Use evidence-based targets and standard deviations

---

## Parameter Classification

**Temporal Class:** Stable (annual to biennial repeat)

**Validation Tier:**
- **Tier A (Full validation):** EKG findings, cardiac echo LVEF, carotid stenosis
- **Tier B (Template + review):** Ultrasound measurements, CT nodules
- **Tier C (Template only):** Descriptive findings, minor abnormalities

**Clinical Priority:**
- **Critical:** Findings requiring urgent intervention
- **High:** Findings requiring specialist referral/close monitoring
- **Moderate:** Findings requiring routine follow-up

---

## Future Enhancements

1. **Natural Language Processing (NLP):** Auto-extract findings from free-text reports
2. **Image Analysis AI:** Direct extraction from DICOM images for quantitative parameters
3. **Longitudinal Trend Tracking:** Automated comparison to prior studies with change detection
4. **Clinical Decision Support:** Automated recommendations based on findings (e.g., "Carotid stenosis >70% detected → Urgent vascular surgery referral")

---

## Summary: Total Imaging Parameters

| Modality | Parameter Count | Critical Alerts | High Risk | Moderate Risk |
|----------|----------------|-----------------|-----------|---------------|
| Carotid Ultrasound | 11 | 1 | 2 | 2 |
| Cardiac Echo | 15 | 3 | 3 | 3 |
| Liver Ultrasound | 12 | 2 | 2 | 3 |
| Renal Ultrasound | 13 | 3 | 3 | 3 |
| Thyroid Ultrasound | 13 | 2 | 2 | 3 |
| Chest X-Ray | 10 | 3 | 3 | 2 |
| EKG (12-Lead) | 15 | 4 | 4 | 3 |
| CT Chest | 12 | 2 | 3 | 3 |
| CT Abdomen/Pelvis | 14 | 4 | 3 | 3 |
| MRI Brain | 13 | 3 | 3 | 2 |
| **TOTAL** | **128 parameters** | **27 critical** | **28 high** | **27 moderate** |

---

**Document Status:** ✅ COMPLETE
**Next Steps:** Integrate into Master Parameter Library with full normalization specifications and system domain weights
