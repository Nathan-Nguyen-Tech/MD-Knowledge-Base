# Master Parameter Library v1.0

**Document Version:** 1.0
**Last Updated:** 2025-11-18
**Purpose:** Comprehensive inventory of all clinical parameters assessed in the Health Overview Dashboard baseline assessment and longitudinal monitoring

---

## Document Overview

This is the **Master Parameter Library** - the single source of truth for all parameters measured, calculated, or assessed in the Health Overview Dashboard system. Every parameter listed here contributes to the 8 organ system scores and ultimately the Overall Health Score (0-100).

### Parameter Organization

Parameters are organized by **measurement category** and **temporal class**:

**Temporal Classes:**
- **Dynamic:** Measured every visit (vitals, weight)
- **Semi-Dynamic:** Measured quarterly to annually (labs, functional tests)
- **Stable:** Measured annually to biennially (imaging, body composition)
- **Static:** Assessed once at baseline (historical data)

### Total Parameter Count by Category

| Category | Parameter Count | Temporal Class | Frequency |
|----------|----------------|----------------|-----------|
| **1. Vital Signs** | 15 | Dynamic | Every visit |
| **2. Biometrics** | 2 | Dynamic | Every visit |
| **3. Laboratory Tests** | 106 | Semi-Dynamic | Quarterly to Annual |
| **4. Urinalysis** | 13 | Semi-Dynamic | Annual / Symptomatic |
| **5. Body Composition (InBody H20N)** | 10 | Semi-Dynamic | Quarterly |
| **6. Functional Tests** | 29 | Semi-Dynamic | Annual |
| **7. Imaging Studies** | 128 | Stable | Annual to Biennial |
| **8. Physical Examination** | ~80 | Dynamic/Semi-Dynamic | Every visit / Annual |
| **9. Lifestyle Assessment** | 6 | Dynamic | Quarterly |
| **10. Medical History** | Variable | Static | Baseline |
| **11. Surgical History** | Variable | Static | Baseline |
| **12. Family History** | Variable | Static | Baseline |
| **13. Medications** | Variable | Static/Dynamic | Baseline + Updates |
| **14. Allergies** | Variable | Static | Baseline |
| **TOTAL DISCRETE PARAMETERS** | **~400-450** | Mixed | Mixed |

---

## CATEGORY 1: VITAL SIGNS (15 Parameters)

**Temporal Class:** Dynamic
**Measurement Frequency:** Every visit
**Equipment:** Automated BP monitor, pulse oximeter, thermometer, scale, height rod

| ID | Parameter Name | Unit | Normal Range (Adult) | System Mapping (Primary) | Normalization Method |
|----|----------------|------|----------------------|-------------------------|---------------------|
| VS_001 | Systolic Blood Pressure | mmHg | 90-120 | Cardiovascular-Function | Normal Bidirectional |
| VS_002 | Diastolic Blood Pressure | mmHg | 60-80 | Cardiovascular-Function | Normal Bidirectional |
| VS_003 | Mean Arterial Pressure (MAP) | mmHg | 70-100 | Cardiovascular-Function | Normal Bidirectional |
| VS_004 | Pulse Pressure | mmHg | 30-60 | Cardiovascular-Structure | Normal Bidirectional |
| VS_005 | Heart Rate (Resting) | bpm | 60-100 | Cardiovascular-Function | Normal Bidirectional |
| VS_006 | Respiratory Rate | breaths/min | 12-20 | Respiratory-Function | Normal Bidirectional |
| VS_007 | Oxygen Saturation (SpO2) | % | 95-100 | Respiratory-Function | Unidirectional (High) |
| VS_008 | Body Temperature | °C / °F | 36.1-37.2°C | Immune-Function | Normal Bidirectional |
| VS_009 | Body Weight | kg / lb | BMI-dependent | Metabolic-Structure | Context-dependent |
| VS_010 | Height | cm / in | N/A (static) | Musculoskeletal-Structure | N/A |
| VS_011 | Body Mass Index (BMI) | kg/m² | 18.5-24.9 | Metabolic-Risk | Normal Bidirectional |
| VS_012 | Waist Circumference | cm / in | M:<94, F:<80 | Metabolic-Risk | Unidirectional (Low) |
| VS_013 | Hip Circumference | cm / in | Context-dependent | Metabolic-Structure | Context-dependent |
| VS_014 | Waist-to-Hip Ratio | Ratio | M:<0.90, F:<0.85 | Metabolic-Risk | Unidirectional (Low) |
| VS_015 | Waist-to-Height Ratio | Ratio | <0.50 | Cardiovascular-Risk | Unidirectional (Low) |

### Calculated Parameters
- **MAP** = (SBP + 2×DBP) / 3
- **Pulse Pressure** = SBP - DBP
- **BMI** = Weight (kg) / Height (m)²
- **WHR** = Waist / Hip
- **WHtR** = Waist / Height

---

## CATEGORY 2: BIOMETRICS (2 Parameters)

**Temporal Class:** Dynamic
**Measurement Frequency:** Every visit

| ID | Parameter Name | Unit | Normal Range | System Mapping | Notes |
|----|----------------|------|--------------|----------------|-------|
| BIO_001 | Grip Strength (Dominant Hand) | kg | M:>26, F:>16 | Musculoskeletal-Function | Sarcopenia screening |
| BIO_002 | Grip Strength (Non-Dominant Hand) | kg | ~10% lower | Musculoskeletal-Function | Asymmetry assessment |

---

## CATEGORY 3: LABORATORY TESTS (106 Parameters)

**Temporal Class:** Semi-Dynamic
**Measurement Frequency:** Quarterly to Annual (disease-dependent)

### 3A. Complete Blood Count (CBC) - 18 Parameters

| ID | Parameter Name | Unit | Normal Range (Adult) | System Mapping |
|----|----------------|------|---------------------|----------------|
| LAB_001 | White Blood Cell Count (WBC) | ×10³/μL | 4.5-11.0 | Immune-Function |
| LAB_002 | Red Blood Cell Count (RBC) | ×10⁶/μL | M:4.5-5.9, F:4.1-5.1 | Cardiovascular-Structure |
| LAB_003 | Hemoglobin (Hgb) | g/dL | M:13.5-17.5, F:12.0-15.5 | Cardiovascular-Function |
| LAB_004 | Hematocrit (Hct) | % | M:38-50, F:36-44 | Cardiovascular-Function |
| LAB_005 | Mean Corpuscular Volume (MCV) | fL | 80-100 | Cardiovascular-Structure |
| LAB_006 | Mean Corpuscular Hemoglobin (MCH) | pg | 27-33 | Cardiovascular-Structure |
| LAB_007 | Mean Corpuscular Hemoglobin Conc (MCHC) | g/dL | 32-36 | Cardiovascular-Structure |
| LAB_008 | Red Cell Distribution Width (RDW) | % | 11.5-14.5 | Cardiovascular-Risk |
| LAB_009 | Platelet Count | ×10³/μL | 150-400 | Immune-Function |
| LAB_010 | Mean Platelet Volume (MPV) | fL | 7.5-11.5 | Immune-Function |
| LAB_011 | Neutrophils (Absolute) | ×10³/μL | 1.5-8.0 | Immune-Function |
| LAB_012 | Lymphocytes (Absolute) | ×10³/μL | 1.0-4.8 | Immune-Function |
| LAB_013 | Monocytes (Absolute) | ×10³/μL | 0.2-0.8 | Immune-Function |
| LAB_014 | Eosinophils (Absolute) | ×10³/μL | 0.0-0.4 | Immune-Function |
| LAB_015 | Basophils (Absolute) | ×10³/μL | 0.0-0.2 | Immune-Function |
| LAB_016 | Neutrophils (Percentage) | % | 40-70 | Immune-Function |
| LAB_017 | Lymphocytes (Percentage) | % | 20-40 | Immune-Function |
| LAB_018 | Neutrophil-to-Lymphocyte Ratio (NLR) | Ratio | 0.78-3.53 | Immune-Risk |

### 3B. Comprehensive Metabolic Panel (CMP) - 14 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_019 | Glucose (Fasting) | mg/dL | 70-100 | Metabolic-Function |
| LAB_020 | Sodium (Na+) | mEq/L | 136-145 | Metabolic-Function |
| LAB_021 | Potassium (K+) | mEq/L | 3.5-5.0 | Cardiovascular-Function / Renal-Function |
| LAB_022 | Chloride (Cl-) | mEq/L | 98-107 | Metabolic-Function |
| LAB_023 | Carbon Dioxide (CO2) | mEq/L | 23-30 | Respiratory-Function |
| LAB_024 | Blood Urea Nitrogen (BUN) | mg/dL | 7-20 | Renal-Function |
| LAB_025 | Creatinine (Serum) | mg/dL | M:0.7-1.3, F:0.6-1.1 | Renal-Function |
| LAB_026 | BUN/Creatinine Ratio | Ratio | 10-20 | Renal-Function |
| LAB_027 | Estimated GFR (eGFR) | mL/min/1.73m² | >60 | Renal-Function |
| LAB_028 | Calcium (Total) | mg/dL | 8.5-10.5 | Metabolic-Structure / Endocrine-Function |
| LAB_029 | Calcium (Ionized) | mg/dL | 4.6-5.3 | Metabolic-Function |
| LAB_030 | Total Protein | g/dL | 6.0-8.3 | Metabolic-Function |
| LAB_031 | Albumin | g/dL | 3.5-5.5 | Metabolic-Function |
| LAB_032 | Globulin | g/dL | 2.0-3.5 | Immune-Function |
| LAB_033 | Albumin/Globulin Ratio (A/G) | Ratio | 1.1-2.5 | Metabolic-Function |

### 3C. Liver Function Tests (LFTs) - 8 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_034 | Alanine Aminotransferase (ALT) | U/L | M:7-55, F:7-45 | Metabolic-Function |
| LAB_035 | Aspartate Aminotransferase (AST) | U/L | M:8-48, F:8-43 | Metabolic-Function |
| LAB_036 | AST/ALT Ratio | Ratio | <1.0 | Metabolic-Risk |
| LAB_037 | Alkaline Phosphatase (ALP) | U/L | 44-147 | Metabolic-Function |
| LAB_038 | Gamma-Glutamyl Transferase (GGT) | U/L | M:8-61, F:5-36 | Metabolic-Function |
| LAB_039 | Bilirubin (Total) | mg/dL | 0.1-1.2 | Metabolic-Function |
| LAB_040 | Bilirubin (Direct) | mg/dL | 0.0-0.3 | Metabolic-Function |
| LAB_041 | Bilirubin (Indirect) | mg/dL | 0.1-0.9 | Metabolic-Function |

### 3D. Lipid Panel - 10 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_042 | Total Cholesterol | mg/dL | <200 | Cardiovascular-Risk |
| LAB_043 | LDL Cholesterol (Calculated) | mg/dL | <100 | Cardiovascular-Risk |
| LAB_044 | LDL Cholesterol (Direct) | mg/dL | <100 | Cardiovascular-Risk |
| LAB_045 | HDL Cholesterol | mg/dL | M:>40, F:>50 | Cardiovascular-Risk |
| LAB_046 | VLDL Cholesterol | mg/dL | 2-30 | Cardiovascular-Risk |
| LAB_047 | Triglycerides | mg/dL | <150 | Cardiovascular-Risk / Metabolic-Risk |
| LAB_048 | Non-HDL Cholesterol | mg/dL | <130 | Cardiovascular-Risk |
| LAB_049 | Total Cholesterol/HDL Ratio | Ratio | <5.0 | Cardiovascular-Risk |
| LAB_050 | Triglyceride/HDL Ratio | Ratio | <2.0 | Metabolic-Risk |
| LAB_051 | LDL Particle Number (LDL-P) | nmol/L | <1000 | Cardiovascular-Risk |

### 3E. Diabetes/Glucose Metabolism - 6 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_052 | Hemoglobin A1C (HbA1c) | % | <5.7 | Metabolic-Function |
| LAB_053 | Fasting Insulin | μU/mL | 2.6-24.9 | Metabolic-Function |
| LAB_054 | HOMA-IR (Insulin Resistance) | Index | <2.0 | Metabolic-Risk |
| LAB_055 | C-Peptide | ng/mL | 0.9-7.1 | Metabolic-Function |
| LAB_056 | Fructosamine | μmol/L | 190-270 | Metabolic-Function |
| LAB_057 | 1,5-Anhydroglucitol (1,5-AG) | μg/mL | >10 | Metabolic-Function |

### 3F. Thyroid Function - 6 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_058 | Thyroid Stimulating Hormone (TSH) | μIU/mL | 0.4-4.0 | Endocrine-Function |
| LAB_059 | Free T4 (Thyroxine) | ng/dL | 0.8-1.8 | Endocrine-Function |
| LAB_060 | Free T3 (Triiodothyronine) | pg/mL | 2.3-4.2 | Endocrine-Function |
| LAB_061 | Total T4 | μg/dL | 5.0-12.0 | Endocrine-Function |
| LAB_062 | Total T3 | ng/dL | 80-200 | Endocrine-Function |
| LAB_063 | Reverse T3 (rT3) | ng/dL | 9.2-24.1 | Endocrine-Function |

### 3G. Sex Hormones - 10 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_064 | Testosterone (Total) - Male | ng/dL | 264-916 | Endocrine-Function |
| LAB_065 | Testosterone (Total) - Female | ng/dL | 15-70 | Endocrine-Function |
| LAB_066 | Testosterone (Free) | pg/mL | M:50-200, F:1-8 | Endocrine-Function |
| LAB_067 | Sex Hormone Binding Globulin (SHBG) | nmol/L | M:10-57, F:18-144 | Endocrine-Function |
| LAB_068 | Estradiol (E2) | pg/mL | M:10-40, F:varies by phase | Endocrine-Function |
| LAB_069 | Progesterone | ng/mL | F:varies by phase | Endocrine-Function |
| LAB_070 | Luteinizing Hormone (LH) | mIU/mL | Varies by sex/age | Endocrine-Function |
| LAB_071 | Follicle Stimulating Hormone (FSH) | mIU/mL | Varies by sex/age | Endocrine-Function |
| LAB_072 | DHEA-Sulfate (DHEA-S) | μg/dL | Varies by age/sex | Endocrine-Function |
| LAB_073 | Prolactin | ng/mL | M:4-15, F:4-30 | Endocrine-Function |

### 3H. Adrenal/Stress Hormones - 2 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_074 | Cortisol (AM) | μg/dL | 6.2-19.4 | Endocrine-Function |
| LAB_075 | Cortisol (PM) | μg/dL | 2.3-11.9 | Endocrine-Function |

### 3I. Inflammatory Markers - 4 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_076 | High-Sensitivity C-Reactive Protein (hs-CRP) | mg/L | <1.0 (low risk) | Immune-Risk / Cardiovascular-Risk |
| LAB_077 | Erythrocyte Sedimentation Rate (ESR) | mm/hr | M:<15, F:<20 | Immune-Risk |
| LAB_078 | Fibrinogen | mg/dL | 200-400 | Cardiovascular-Risk |
| LAB_079 | Homocysteine | μmol/L | <15 | Cardiovascular-Risk / Neurological-Risk |

### 3J. Cardiac Biomarkers - 5 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_080 | Troponin I (High-Sensitivity) | ng/L | <19 (M), <12 (F) | Cardiovascular-Risk |
| LAB_081 | Troponin T (High-Sensitivity) | ng/L | <14 | Cardiovascular-Risk |
| LAB_082 | B-Type Natriuretic Peptide (BNP) | pg/mL | <100 | Cardiovascular-Function |
| LAB_083 | NT-proBNP | pg/mL | <125 (age-dependent) | Cardiovascular-Function |
| LAB_084 | Creatine Kinase-MB (CK-MB) | ng/mL | <5.0 | Cardiovascular-Risk |

### 3K. Coagulation Studies - 4 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_085 | Prothrombin Time (PT) | seconds | 11-13.5 | Cardiovascular-Risk |
| LAB_086 | International Normalized Ratio (INR) | Ratio | 0.8-1.2 | Cardiovascular-Risk |
| LAB_087 | Activated Partial Thromboplastin Time (aPTT) | seconds | 25-35 | Cardiovascular-Risk |
| LAB_088 | D-Dimer | ng/mL | <500 | Cardiovascular-Risk |

### 3L. Vitamins & Micronutrients - 8 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_089 | Vitamin D (25-OH) | ng/mL | 30-100 | Musculoskeletal-Function / Immune-Function |
| LAB_090 | Vitamin B12 | pg/mL | 200-900 | Neurological-Function |
| LAB_091 | Folate (Serum) | ng/mL | >3.0 | Neurological-Function |
| LAB_092 | Vitamin A (Retinol) | μg/dL | 30-100 | Immune-Function |
| LAB_093 | Vitamin E (Tocopherol) | mg/dL | 5.5-17.0 | Cardiovascular-Risk |
| LAB_094 | Ferritin | ng/mL | M:24-336, F:11-307 | Cardiovascular-Function |
| LAB_095 | Iron (Serum) | μg/dL | M:65-175, F:50-170 | Cardiovascular-Function |
| LAB_096 | Total Iron Binding Capacity (TIBC) | μg/dL | 250-450 | Cardiovascular-Function |
| LAB_097 | Transferrin Saturation | % | 20-50 | Cardiovascular-Function |

### 3M. Other Metabolic Markers - 9 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| LAB_098 | Uric Acid | mg/dL | M:3.4-7.0, F:2.4-6.0 | Metabolic-Risk / Renal-Risk |
| LAB_099 | Magnesium | mEq/L | 1.7-2.2 | Cardiovascular-Function |
| LAB_100 | Phosphorus | mg/dL | 2.5-4.5 | Renal-Function / Endocrine-Function |
| LAB_101 | Lactate Dehydrogenase (LDH) | U/L | 122-222 | Metabolic-Function |
| LAB_102 | Creatine Kinase (CK) | U/L | M:52-336, F:38-176 | Musculoskeletal-Function |
| LAB_103 | Lipoprotein(a) [Lp(a)] | mg/dL | <30 | Cardiovascular-Risk |
| LAB_104 | Apolipoprotein A1 (ApoA1) | mg/dL | M:>120, F:>140 | Cardiovascular-Risk |
| LAB_105 | Apolipoprotein B (ApoB) | mg/dL | <100 | Cardiovascular-Risk |
| LAB_106 | ApoB/ApoA1 Ratio | Ratio | <0.9 | Cardiovascular-Risk |

---

## CATEGORY 4: URINALYSIS (13 Parameters)

**Temporal Class:** Semi-Dynamic
**Measurement Frequency:** Annual or symptomatic

| ID | Parameter Name | Values | Normal Range | System Mapping |
|----|----------------|--------|--------------|----------------|
| URI_001 | Urine Color | Yellow, Amber, Red, Brown, Clear | Pale to dark yellow | Renal-Structure |
| URI_002 | Urine Clarity | Clear, Cloudy, Turbid | Clear | Renal-Structure |
| URI_003 | Specific Gravity | Numeric | 1.005-1.030 | Renal-Function |
| URI_004 | pH | Numeric | 4.5-8.0 | Renal-Function |
| URI_005 | Protein | Negative, Trace, 1+, 2+, 3+, 4+ | Negative | Renal-Function |
| URI_006 | Glucose | Negative, Trace, 1+, 2+, 3+, 4+ | Negative | Metabolic-Risk |
| URI_007 | Ketones | Negative, Trace, Small, Moderate, Large | Negative | Metabolic-Risk |
| URI_008 | Blood | Negative, Trace, 1+, 2+, 3+ | Negative | Renal-Risk |
| URI_009 | Bilirubin | Negative, 1+, 2+, 3+ | Negative | Metabolic-Risk |
| URI_010 | Urobilinogen | mg/dL | 0.1-1.0 | Metabolic-Function |
| URI_011 | Nitrites | Positive / Negative | Negative | Renal-Risk / Immune-Risk |
| URI_012 | Leukocyte Esterase | Negative, Trace, Small, Moderate, Large | Negative | Renal-Risk / Immune-Risk |
| URI_013 | Microalbumin/Creatinine Ratio (Spot Urine) | mg/g | <30 | Renal-Function |

---

## CATEGORY 5: BODY COMPOSITION - InBody H20N (10 Parameters)

**Temporal Class:** Semi-Dynamic
**Measurement Frequency:** Quarterly
**Equipment:** InBody H20N Smart Body Composition Analyzer

### Core Measured Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| BC_001 | Total Body Weight | kg | BMI-dependent | Metabolic-Structure |
| BC_002 | Skeletal Muscle Mass | kg | M:33-39, F:22-28 (age-dependent) | Musculoskeletal-Function |
| BC_003 | Body Fat Mass | kg | Varies | Metabolic-Risk |
| BC_004 | Body Fat Percentage | % | M:14-17, F:21-24 (fitness range) | Metabolic-Risk |
| BC_005 | Body Mass Index (BMI) | kg/m² | 18.5-24.9 | Metabolic-Risk |
| BC_006 | Basal Metabolic Rate (BMR) | kcal/day | Age/sex-dependent | Metabolic-Function |
| BC_007 | InBody Score | 0-100 | 80-100 (good-excellent) | Metabolic-Structure |

### Derived Parameters

| ID | Parameter Name | Formula | Unit | System Mapping |
|----|----------------|---------|------|----------------|
| BC_008 | Lean Body Mass (LBM) | Weight - Body Fat Mass | kg | Musculoskeletal-Structure |
| BC_009 | Fat-Free Mass Index (FFMI) | LBM / Height² | kg/m² | Musculoskeletal-Function |
| BC_010 | Body Fat Mass Index (BFMI) | Body Fat Mass / Height² | kg/m² | Metabolic-Risk |

---

## CATEGORY 6: FUNCTIONAL TESTS (29 Parameters)

**Temporal Class:** Semi-Dynamic
**Measurement Frequency:** Annual or baseline

### 6A. Cardiovascular Fitness - 4 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| FUNC_001 | VO2 Max (Estimated) | mL/kg/min | M:>42, F:>35 (age-dependent) | Cardiovascular-Function |
| FUNC_002 | Resting Heart Rate (Morning) | bpm | 50-70 (athletic:40-60) | Cardiovascular-Function |
| FUNC_003 | Heart Rate Recovery (1 min post-exercise) | bpm drop | >12 bpm | Cardiovascular-Function |
| FUNC_004 | 6-Minute Walk Distance | meters | >400m (age/health-dependent) | Cardiovascular-Function / Respiratory-Function |

### 6B. Flexibility/Mobility - 3 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| FUNC_005 | Sit-and-Reach Test | cm | >0 (past toes) | Musculoskeletal-Function |
| FUNC_006 | Shoulder Flexibility (Back Scratch Test) | cm | <5 cm gap | Musculoskeletal-Function |
| FUNC_007 | Ankle Dorsiflexion Range of Motion | degrees | >10° (knee flexed) | Musculoskeletal-Function |

### 6C. Balance & Proprioception - 7 Parameters (Y-Balance Test)

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| FUNC_008 | Y-Balance: Right Anterior Reach | cm | >90% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_009 | Y-Balance: Right Posteromedial Reach | cm | >100% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_010 | Y-Balance: Right Posterolateral Reach | cm | >105% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_011 | Y-Balance: Left Anterior Reach | cm | >90% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_012 | Y-Balance: Left Posteromedial Reach | cm | >100% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_013 | Y-Balance: Left Posterolateral Reach | cm | >105% leg length | Neurological-Function / Musculoskeletal-Function |
| FUNC_014 | Y-Balance: Composite Score | % | >90% | Neurological-Function / Musculoskeletal-Function |

### 6D. Strength & Power - 5 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| FUNC_015 | 30-Second Chair Stand Test | repetitions | >12 (age 60-64) | Musculoskeletal-Function |
| FUNC_016 | Push-Up Test (to fatigue) | repetitions | M:>17, F:>12 (age 20-29) | Musculoskeletal-Function |
| FUNC_017 | Plank Hold Time | seconds | >60 sec | Musculoskeletal-Function |
| FUNC_018 | Vertical Jump Height | cm | Age-dependent | Musculoskeletal-Function |
| FUNC_019 | Standing Broad Jump Distance | cm | Age-dependent | Musculoskeletal-Function |

### 6E. Agility & Reaction - 2 Parameters

| ID | Parameter Name | Unit | Normal Range | System Mapping |
|----|----------------|------|--------------|----------------|
| FUNC_020 | Timed Up-and-Go (TUG) Test | seconds | <10 sec (healthy adult) | Neurological-Function / Musculoskeletal-Function |
| FUNC_021 | Reaction Time (Simple Visual) | milliseconds | 200-300 ms | Neurological-Function |

### 6F. Cognitive Function - 8 Parameters

| ID | Parameter Name | Measurement Tool | Scoring | System Mapping |
|----|----------------|------------------|---------|----------------|
| FUNC_022 | Global Cognition (MoCA) | Montreal Cognitive Assessment | 26-30 (normal) | Neurological-Function |
| FUNC_023 | Executive Function (Trail Making B) | Trail Making Test Part B | <75 sec (age 18-44) | Neurological-Function |
| FUNC_024 | Processing Speed (Trail Making A) | Trail Making Test Part A | <29 sec (age 18-44) | Neurological-Function |
| FUNC_025 | Working Memory (Digit Span Forward) | Digit Span Test | 7±2 digits | Neurological-Function |
| FUNC_026 | Working Memory (Digit Span Backward) | Digit Span Test | 5±2 digits | Neurological-Function |
| FUNC_027 | Verbal Fluency (Animal Naming) | 60-second fluency test | >17 animals | Neurological-Function |
| FUNC_028 | Attention/Vigilance (Continuous Performance) | CPT Test | >85% accuracy | Neurological-Function |
| FUNC_029 | Visual Memory (Brief Visuospatial Test) | BVMT-R | Age-adjusted | Neurological-Function |

---

## CATEGORY 7: IMAGING STUDIES (128 Parameters)

**Temporal Class:** Stable
**Measurement Frequency:** Annual to Biennial (or symptomatic)
**Note:** Detailed specifications available in [STANDARDIZED_IMAGING_TEMPLATES.md](STANDARDIZED_IMAGING_TEMPLATES.md)

### Parameter Count by Modality

| Modality | Parameter Count | Key Findings |
|----------|----------------|--------------|
| **7A. Carotid Ultrasound** | 11 | IMT, stenosis, plaque characteristics |
| **7B. Cardiac Echocardiogram** | 15 | LVEF, chamber sizes, valve function |
| **7C. Liver Ultrasound** | 12 | Hepatic steatosis, surface, vasculature |
| **7D. Renal Ultrasound** | 13 | Kidney size, echogenicity, hydronephrosis |
| **7E. Thyroid Ultrasound** | 13 | Nodules, TI-RADS scoring, volume |
| **7F. Chest X-Ray** | 10 | Cardiac silhouette, lung fields, effusions |
| **7G. Electrocardiogram (12-Lead)** | 15 | Rhythm, intervals, ST-T changes, LVH |
| **7H. CT Chest** | 12 | Pulmonary nodules, emphysema, calcification |
| **7I. CT Abdomen/Pelvis** | 14 | Organ masses, aneurysm, lymphadenopathy |
| **7J. MRI Brain** | 13 | White matter lesions, atrophy, infarcts |
| **TOTAL** | **128** | -- |

### Representative Imaging Parameters (Selected High-Impact)

| ID | Parameter Name | Modality | System Mapping | Clinical Significance |
|----|----------------|----------|----------------|----------------------|
| IMG_CAR_001 | Right CCA Intima-Media Thickness | Carotid US | Cardiovascular-Structure | Atherosclerosis screening |
| IMG_CAR_003 | Right ICA Stenosis Degree | Carotid US | Cardiovascular-Risk | Stroke risk |
| IMG_ECHO_001 | Left Ventricular Ejection Fraction | Cardiac Echo | Cardiovascular-Function | Heart failure screening |
| IMG_LIV_003 | Hepatic Steatosis Grade | Liver US | Metabolic-Risk | Fatty liver disease |
| IMG_REN_007 | Right Hydronephrosis | Renal US | Renal-Risk | Obstruction detection |
| IMG_THY_013 | ACR TI-RADS Score | Thyroid US | Endocrine-Risk | Thyroid cancer risk |
| IMG_EKG_005 | QT Interval (corrected) | EKG | Cardiovascular-Risk | Arrhythmia risk |
| IMG_CTC_004 | Lung-RADS Category | CT Chest | Respiratory-Risk | Lung cancer screening |
| IMG_CTA_009 | Aortic Aneurysm | CT Abdomen | Cardiovascular-Risk | Rupture risk |
| IMG_MRB_002 | Fazekas Scale (WMH severity) | MRI Brain | Neurological-Structure | Vascular dementia risk |

---

## CATEGORY 8: PHYSICAL EXAMINATION (~80 Parameters)

**Temporal Class:** Dynamic (general exam every visit) / Semi-Dynamic (detailed annual)
**Measurement Frequency:** Every visit for general; Annual for comprehensive

### Representative Physical Exam Findings (Selected)

**Note:** Full physical examination includes ~80 discrete findings across all organ systems. User provided Vietnamese-English list. Below are key structured parameters:

| ID | Body System | Finding | Values | System Mapping |
|----|-------------|---------|--------|----------------|
| PE_001 | General Appearance | Overall appearance | Well, Ill-appearing, Distress | All Systems |
| PE_002 | HEENT | Pupil Response | Normal, Sluggish, Fixed | Neurological-Function |
| PE_003 | HEENT | Thyroid Palpation | Normal, Enlarged, Nodule | Endocrine-Structure |
| PE_004 | Cardiovascular | Heart Sounds | Regular, Irregular, Murmur present | Cardiovascular-Function |
| PE_005 | Cardiovascular | Peripheral Pulses | Normal (2+), Diminished (1+), Absent | Cardiovascular-Function |
| PE_006 | Cardiovascular | Peripheral Edema | None, 1+, 2+, 3+, 4+ | Cardiovascular-Risk |
| PE_007 | Respiratory | Breath Sounds | Clear, Crackles, Wheezes, Rhonchi | Respiratory-Function |
| PE_008 | Abdominal | Liver Span (Percussion) | cm | Metabolic-Structure |
| PE_009 | Abdominal | Spleen Palpable | Yes / No | Immune-Structure |
| PE_010 | Abdominal | Ascites | Present / Absent | Metabolic-Risk |
| PE_011 | Musculoskeletal | Joint Swelling | Present / Absent (specify joints) | Musculoskeletal-Structure |
| PE_012 | Musculoskeletal | Joint Tenderness | Present / Absent (specify joints) | Musculoskeletal-Function |
| PE_013 | Neurological | Gait | Normal, Antalgic, Ataxic, Parkinsonian | Neurological-Function |
| PE_014 | Neurological | Romberg Test | Negative / Positive | Neurological-Function |
| PE_015 | Neurological | Deep Tendon Reflexes (Average) | 0 (absent), 1+ (diminished), 2+ (normal), 3+ (brisk), 4+ (hyperactive with clonus) | Neurological-Function |
| PE_016 | Skin | Skin Lesions | None / Present (describe type, location) | Immune-Risk |
| PE_017 | Skin | Jaundice | Present / Absent | Metabolic-Risk |
| PE_018 | Skin | Cyanosis | Present / Absent | Respiratory-Risk / Cardiovascular-Risk |

---

## CATEGORY 9: LIFESTYLE ASSESSMENT (6 Parameters)

**Temporal Class:** Dynamic
**Measurement Frequency:** Quarterly
**Note:** Detailed questionnaire pending separate development. See [LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md](LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md)

| ID | Parameter Name | Measurement Tool | Score Range | System Mapping |
|----|----------------|------------------|-------------|----------------|
| LIFE_001 | Nutrition Score | Lifestyle Questionnaire (Pillar 1) | 0-10 | Metabolic (primary), Cardiovascular, Immune |
| LIFE_002 | Movement Score | Lifestyle Questionnaire (Pillar 2) | 0-10 | Musculoskeletal (primary), Cardiovascular, Metabolic |
| LIFE_003 | Recovery Score | Lifestyle Questionnaire (Pillar 3) | 0-10 | Neurological (primary), Cardiovascular, Immune |
| LIFE_004 | Emotion Score | Lifestyle Questionnaire (Pillar 4) | 0-10 | Neurological (primary), Cardiovascular, Immune |
| LIFE_005 | Environment Score | Lifestyle Questionnaire (Pillar 5) | 0-10 | Respiratory (primary), Immune, Neurological |
| LIFE_006 | Lifestyle Composite Score | Average of 5 pillars | 0-10 | All Systems (30% of Overall Health) |

---

## CATEGORY 10: MEDICAL HISTORY (Variable - Structured Data)

**Temporal Class:** Static
**Measurement Frequency:** Baseline assessment (updated as new diagnoses occur)

### Structure

**Data Model:** Standardized Diagnosis Library organized by 8 organ systems
**Total Anticipated Diagnoses:** ~100-150 most common conditions + extensible "Other" category

### Key Diagnoses by System (Representative Sample)

**Neurological:**
- Migraine headaches
- Prior stroke/TIA
- Seizure disorder
- Peripheral neuropathy
- Dementia/cognitive impairment

**Cardiovascular:**
- Hypertension
- Coronary artery disease / Prior MI
- Atrial fibrillation
- Heart failure (HFrEF/HFpEF)
- Peripheral arterial disease

**Respiratory:**
- Asthma
- Chronic obstructive pulmonary disease (COPD)
- Obstructive sleep apnea
- Pulmonary hypertension

**Metabolic:**
- Type 1 diabetes mellitus
- Type 2 diabetes mellitus
- Prediabetes / Impaired fasting glucose
- Non-alcoholic fatty liver disease (NAFLD)
- Metabolic syndrome
- Obesity (BMI ≥30)
- Hyperlipidemia
- Hypothyroidism
- Hyperthyroidism

**Renal:**
- Chronic kidney disease (Stage 1-5)
- History of kidney stones
- Acute kidney injury (prior)

**Musculoskeletal:**
- Osteoarthritis
- Rheumatoid arthritis
- Osteoporosis / Osteopenia
- Chronic low back pain
- Prior fractures

**Immune:**
- Autoimmune diseases (specify)
- HIV infection
- Hepatitis B or C
- Recurrent infections

**Reproductive/Endocrine:**
- Polycystic ovary syndrome (PCOS)
- Benign prostatic hyperplasia (BPH)
- Erectile dysfunction
- Menopausal status (women)
- Hypogonadism (men)

### Data Fields per Diagnosis

Each diagnosis includes:
- **ICD-10 Code:** Standardized coding
- **System Assignment:** Primary + related systems
- **Date Diagnosed:** For duration tracking
- **Status:** Active / Resolved / In remission
- **Severity:** Mild / Moderate / Severe
- **Complications:** List of related complications
- **Score Impact:** Target adjustments, context rules triggered
- **Treatment:** Current management (medications, lifestyle, procedures)

### Handling Rare/Uncommon Diagnoses

**Approach (Pending User Decision):**
- Option A: Extensible library with "Other" category + manual classification
- Option B: Full ICD-10 database integration (~70,000 codes) with rule-based assignment
- Option C: Hierarchical coding (ICD-10 chapter/block level) for broader categorization
- Option D: Hybrid - Common items fully specified, uncommon use parent category rules

---

## CATEGORY 11: SURGICAL HISTORY (Variable - Structured Data)

**Temporal Class:** Static
**Measurement Frequency:** Baseline assessment (updated as new surgeries occur)

### Structure

**Data Model:** Standardized Procedure Library organized by organ system
**Total Anticipated Procedures:** ~50-100 most common surgeries + extensible "Other" category

### Key Procedures by System (Representative Sample)

**Neurological:**
- Craniotomy
- Spinal fusion
- Carpal tunnel release

**Cardiovascular:**
- Coronary artery bypass grafting (CABG)
- Percutaneous coronary intervention (PCI/stent)
- Pacemaker/ICD implantation
- Valve replacement/repair

**Respiratory:**
- Lung resection
- Tonsillectomy/adenoidectomy

**Metabolic:**
- Cholecystectomy (gallbladder removal)
- Bariatric surgery (gastric bypass, sleeve)
- Liver resection

**Renal:**
- Nephrectomy (partial/total)
- Kidney transplant

**Musculoskeletal:**
- Total hip replacement
- Total knee replacement
- Spinal laminectomy
- Rotator cuff repair
- ACL reconstruction

**Reproductive/Endocrine:**
- Hysterectomy
- Prostatectomy
- Thyroidectomy
- Oophorectomy

### Data Fields per Procedure

Each surgery includes:
- **CPT Code:** Standardized procedure coding
- **System Assignment:** Primary + related systems
- **Date Performed:** For recovery duration tracking
- **Indication:** Reason for surgery
- **Complications:** Post-operative complications if any
- **Score Impact:** Structural domain modifications, functional expectations
- **Current Status:** Fully recovered / Ongoing rehab / Chronic sequelae

---

## CATEGORY 12: FAMILY HISTORY (Variable - Structured Data)

**Temporal Class:** Static
**Measurement Frequency:** Baseline assessment

### Structure

**Data Model:** Standardized Family History Template covering ~20-30 key heritable conditions
**Risk Calculation:** Age of onset × Relation degree → Risk multiplier

### Key Heritable Conditions Tracked

**Cardiovascular:**
- Premature coronary artery disease (age <55 M, <65 F)
- Sudden cardiac death
- Familial hypercholesterolemia
- Hypertrophic cardiomyopathy
- Aortic aneurysm

**Metabolic:**
- Type 2 diabetes mellitus
- Obesity
- Thyroid disorders

**Neurological:**
- Stroke
- Alzheimer's dementia
- Parkinson's disease
- Epilepsy

**Oncologic:**
- Breast cancer
- Colon cancer
- Prostate cancer
- Lung cancer
- Ovarian cancer

**Immune/Autoimmune:**
- Rheumatoid arthritis
- Lupus
- Multiple sclerosis

**Renal:**
- Polycystic kidney disease
- Chronic kidney disease

**Psychiatric:**
- Major depression
- Bipolar disorder
- Schizophrenia

### Data Fields per Condition

Each family history entry includes:
- **Condition:** From standardized list
- **Relation:** First-degree (parent, sibling, child) / Second-degree (grandparent, aunt/uncle) / Third-degree
- **Age of Onset:** Affects risk weighting (premature vs age-appropriate)
- **Number Affected:** Multiple family members increase risk
- **Risk Multiplier:** Calculated score adjustment
- **Screening Recommendations:** Triggered by high-risk family history

---

## CATEGORY 13: MEDICATIONS (Variable - Structured Data)

**Temporal Class:** Static at baseline, Dynamic for updates
**Measurement Frequency:** Baseline + every visit update

### Structure

**Data Model:** Medication Context Rules Library covering ~50-100 common drugs
**Purpose:** Enable expected parameter changes and target adjustments

### Key Medication Classes with Context Rules

**Cardiovascular Medications:**
- **ACE Inhibitors / ARBs:** Expect higher K+, lower eGFR (small decrease acceptable)
- **Beta-Blockers:** Lower heart rate target, may mask hypoglycemia
- **Diuretics:** Expect lower K+, higher uric acid
- **Statins:** May elevate liver enzymes (mild acceptable), check CK if myalgias
- **Anticoagulants (Warfarin):** Monitor INR (target 2-3 for most indications)

**Diabetes Medications:**
- **Metformin:** May lower B12, contraindicated if eGFR <30
- **Insulin:** Expect lower glucose/HbA1c, risk of hypoglycemia
- **SGLT2 Inhibitors:** Expect lower eGFR (acute, non-progressive), genital infections
- **GLP-1 Agonists:** Weight loss expected

**Thyroid Medications:**
- **Levothyroxine:** Expect normalized TSH/T4

**Psychiatric Medications:**
- **SSRIs:** May affect sodium (hyponatremia risk in elderly)
- **Lithium:** Requires therapeutic monitoring, affects thyroid/kidney
- **Atypical Antipsychotics:** Weight gain, metabolic syndrome risk

**Immunosuppressants:**
- **Corticosteroids:** Hyperglycemia, osteoporosis, increased infection risk
- **Tacrolimus/Cyclosporine:** Renal function monitoring

**Supplements (Relevant):**
- **Vitamin D:** Expect normalized 25-OH Vitamin D levels
- **Iron:** Expect rising ferritin/hemoglobin
- **Fish Oil:** May affect lipids, bleeding risk

### Data Fields per Medication

Each medication includes:
- **Generic Name:** Standardized drug name
- **Drug Class:** Therapeutic category
- **Indication:** Why prescribed
- **Dose:** Current dosage
- **Start Date:** Duration of therapy
- **Context Rules:** Parameter adjustments expected
- **Monitoring Requirements:** Labs/parameters to track
- **Drug Interactions:** Flagged contraindications

---

## CATEGORY 14: ALLERGIES (Variable - Structured Data)

**Temporal Class:** Static
**Measurement Frequency:** Baseline assessment

### Structure

**Data Model:** Allergy/Adverse Reaction Library

### Allergy Categories

1. **Medication Allergies:**
   - **Allergen:** Drug name
   - **Reaction Type:** Anaphylaxis, Rash, GI upset, Other
   - **Severity:** Mild / Moderate / Severe / Life-threatening
   - **Date of Reaction:** For verification

2. **Environmental Allergies:**
   - Pollen, dust, mold, pet dander
   - **Clinical Impact:** Respiratory system scoring

3. **Food Allergies:**
   - Common allergens (peanuts, shellfish, dairy, etc.)
   - **Clinical Impact:** Immune system scoring, nutrition counseling

4. **Latex Allergy:**
   - **Clinical Impact:** Procedural precautions

---

## Parameter Classification Summary

### By Temporal Class

| Temporal Class | Parameter Count | Frequency |
|----------------|----------------|-----------|
| **Dynamic** | ~110 | Every visit |
| **Semi-Dynamic** | ~160 | Quarterly to Annual |
| **Stable** | ~130 | Annual to Biennial |
| **Static** | ~Variable | Baseline only |
| **TOTAL DISCRETE** | **~400-450** | Mixed |

### By System Domain Mapping (Primary Assignment)

| Organ System | Approximate Parameter Count |
|--------------|----------------------------|
| **Neurological** | ~50 parameters |
| **Cardiovascular** | ~80 parameters |
| **Respiratory** | ~35 parameters |
| **Metabolic** | ~110 parameters |
| **Renal** | ~30 parameters |
| **Musculoskeletal** | ~45 parameters |
| **Immune** | ~30 parameters |
| **Reproductive/Endocrine** | ~40 parameters |
| **Lifestyle (Cross-system)** | 6 parameters |

**Note:** Many parameters map to multiple systems with varying weights (per 24-cell matrix framework)

### By Validation Tier (Parameter Weight Management Strategy)

| Tier | Parameters | Validation Approach |
|------|-----------|---------------------|
| **Tier A** | ~40 | Full expert panel validation, detailed weights |
| **Tier B** | ~100 | Template-based + clinical review |
| **Tier C** | ~260 | Auto-template, batch audit |
| **TOTAL** | **~400** | Mixed validation |

---

## Implementation Roadmap

### MVP Phase (Launch) - Target: ~150 Parameters

**Priority Parameters for MVP:**
1. **Vital Signs:** All 15 (Dynamic)
2. **Core Labs:** CBC (18), CMP (14), Lipids (10), HbA1c, Thyroid (TSH, Free T4) = ~45 parameters
3. **Urinalysis:** Basic dipstick (10 parameters)
4. **Body Composition:** InBody H20N core (7 parameters)
5. **Functional Tests:** Grip strength, chair stand, TUG, flexibility (6 parameters)
6. **EKG:** 12-lead basic findings (10 parameters)
7. **Lifestyle:** 5 pillar scores + composite (6 parameters)
8. **Physical Exam:** General exam findings (15 parameters)
9. **Medical History:** Top 20 diagnoses structured
10. **Medications:** Top 20 drugs with context rules

**MVP Total:** ~150 parameters covering 70-80% of clinical utility

### Phase 2 (Expansion) - Target: ~300 Parameters

**Add:**
- Advanced labs (hormones, vitamins, inflammatory markers, cardiac biomarkers)
- Complete functional testing battery
- Ultrasound imaging (carotid, cardiac echo, liver, renal, thyroid)
- Expanded medical/surgical/family history libraries
- Body composition derived parameters

### Phase 3 (Comprehensive) - Target: ~450 Parameters

**Add:**
- Advanced imaging (CT chest, CT abdomen, MRI brain)
- Complete physical examination structured parameters
- All InBody derived metrics
- Rare lab tests (specialized endocrine, genetics)
- Comprehensive medication/allergy database

---

## Outstanding Design Decisions

### 1. Rare Diagnosis/Surgery/Medication Handling

**Question:** How to handle uncommon conditions not in standardized libraries?

**Options:**
- A. Extensible library + "Other" category with manual classification
- B. Full database integration (ICD-10, CPT, RxNorm)
- C. Hierarchical coding using parent categories
- D. Hybrid approach

**Status:** ⏳ PENDING USER DECISION

### 2. Lifestyle Questionnaire Development

**Question:** Final content, length, validated instruments vs custom?

**Status:** ⏳ PLACEHOLDER - Separate discussion needed

### 3. Physical Examination Structured Data

**Question:** Full structured template for all 80+ findings vs free-text with key findings?

**Status:** ⏳ PENDING - Need clinician input on documentation workflow

---

## Usage Notes

### For Clinical Team

1. **Baseline Assessment:** Every new patient receives comprehensive assessment across all relevant categories
2. **Longitudinal Monitoring:** Parameters repeated at frequencies specified by temporal class
3. **Alert System:** Critical/high-risk findings trigger immediate clinical review
4. **Context Rules:** Medical history, medications, pregnancy status automatically adjust targets
5. **Scoring Integration:** All parameters contribute to 24-cell matrix → 8 system scores → Overall Health Score

### For IT/Development Team

1. **Database Schema:** Each parameter requires unique ID, normalization specifications, system weights
2. **Data Entry UI:** Forms organized by category with appropriate input types (numeric, categorical, free-text)
3. **Validation Logic:** Range checks, alert thresholds, context-aware validations
4. **API Integration:** InBody app, EMR import, imaging PACS systems
5. **Reporting:** Parameter → Domain → System → Overall score calculation pipeline

---

## Document Status

**Version:** 1.0 - Initial Comprehensive Library
**Status:** ✅ COMPLETE - Core framework established
**Next Steps:**
1. Finalize rare diagnosis/medication handling approach
2. Develop detailed lifestyle questionnaire
3. Build complete normalization specifications for all 400+ parameters (separate document)
4. Create weight matrix templates for all parameter classes
5. Implement database schema and data entry interfaces

---

## References

1. User-provided parameter lists (Vitals, Labs, Functional Tests, Physical Exam) - Message 6
2. InBody H20N specifications research - Web search results
3. [STANDARDIZED_IMAGING_TEMPLATES.md](STANDARDIZED_IMAGING_TEMPLATES.md) - Imaging parameter details
4. [LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md](LIFESTYLE_QUESTIONNAIRE_PLACEHOLDER.md) - Lifestyle structure
5. [PARAMETER_WEIGHT_MANAGEMENT_STRATEGY.md](PARAMETER_WEIGHT_MANAGEMENT_STRATEGY.md) - Classification system
6. [PARAMETER_NORMALIZATION_v2.md](PARAMETER_NORMALIZATION_v2.md) - Scoring methods
7. [SYSTEM_DOMAIN_SCORING_v2.md](SYSTEM_DOMAIN_SCORING_v2.md) - Aggregation framework

---

**End of Master Parameter Library v1.0**
