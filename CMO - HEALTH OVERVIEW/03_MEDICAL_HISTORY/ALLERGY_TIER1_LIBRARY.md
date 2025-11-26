# ALLERGY TIER 1 LIBRARY
## Standardized Allergy Documentation for Health Overview Dashboard

**Version:** 1.0
**Last Updated:** November 25, 2025
**Purpose:** Patient intake integration - linking simple allergy checkboxes to clinical safety protocols
**Integration:** Feeds into Health Overview Dashboard critical alerts and prescribing safety checks

---

## 📋 OVERVIEW

This library standardizes allergy documentation for the patient intake form and Health Overview Dashboard. Unlike diagnoses that affect scoring, **allergies primarily serve safety functions**:

1. **Prescribing Safety Alerts** - Prevent dangerous medication orders
2. **Procedure Safety** - Flag contrast dye, latex, anesthesia risks
3. **Dietary Restrictions** - Guide nutritional counseling
4. **Environmental Management** - Inform lifestyle recommendations

### Allergy Categories:
- **Drug Allergies** (18 items) - Medications and medication classes
- **Food Allergies** (8 items) - Common food allergens
- **Environmental Allergies** (5 items) - Latex, contrast dye, anesthesia
- **Total Tier 1 Allergies:** 31

### Severity Classification:
- **Level 1 (Mild):** Rash, itching, mild GI upset
- **Level 2 (Moderate):** Hives, wheezing, facial swelling
- **Level 3 (Severe):** Anaphylaxis, airway compromise, hospitalization required

---

## 🔴 TIER 1: DRUG ALLERGIES (18 Items)

### ALLERGY-001: Penicillin / Amoxicillin
**Allergy Category:** Drug - Antibiotic
**Patient-Friendly Label:** Penicillin or Amoxicillin allergy
**Intake Priority:** 1 (Always visible)
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you took this medication?** (Check all that apply)
   - Options: □ Rash/hives | □ Difficulty breathing | □ Swelling of face/throat | □ Severe diarrhea | □ Hospitalized | □ Don't remember/was told as a child

2. **When did this reaction occur?**
   - Options: As a child (before age 10) | 10-20 years ago | Less than 10 years ago | Recent (within 5 years)

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid all penicillins (penicillin VK, amoxicillin, ampicillin, piperacillin)
- **Cross-Reactivity Risk:** ~10% react to cephalosporins (cephalexin, ceftriaxone)
- **Safe Alternatives:** Macrolides (azithromycin), fluoroquinolones, doxycycline
- **Severity-Based Actions:**
  - Mild childhood rash → May safely tolerate penicillins (consider testing)
  - Anaphylaxis → ABSOLUTE contraindication, avoid cephalosporins

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis, airway swelling) → Hard stop on all beta-lactams
- 🟡 **MODERATE** (hives, wheezing) → Soft warning, allow override with justification
- ⚪ **MILD** (childhood rash) → Informational only

---

### ALLERGY-002: Sulfa Drugs (Sulfonamides)
**Allergy Category:** Drug - Antibiotic
**Patient-Friendly Label:** Sulfa drug allergy (antibiotics like Bactrim)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you took this medication?**
   - Options: □ Rash/hives | □ Difficulty breathing | □ Severe skin reaction (blistering) | □ Liver problems | □ Don't remember

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid sulfamethoxazole-trimethoprim (Bactrim), sulfasalazine
- **Cross-Reactivity:** Generally SAFE to use sulfonylureas (diabetes meds), thiazides (blood pressure), furosemide
- **Safe Alternatives:** Fluoroquinolones, nitrofurantoin (UTIs)

**EMR Alert Flags:**
- 🔴 **SEVERE** (Stevens-Johnson syndrome, blistering) → Hard stop
- 🟡 **MODERATE** (rash, hives) → Warning only

---

### ALLERGY-003: Cephalosporins
**Allergy Category:** Drug - Antibiotic
**Patient-Friendly Label:** Cephalosporin allergy (Keflex, Ceftin, Rocephin)
**Intake Priority:** 2 (Expandable "Other Common Allergies")
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you took this medication?**
   - Options: □ Rash | □ Anaphylaxis | □ GI upset only | □ Don't remember

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid all cephalosporins (cephalexin, cefdinir, ceftriaxone)
- **Cross-Reactivity:** ~1-3% with penicillins (historically overstated)
- **Safe Alternatives:** Macrolides, fluoroquinolones

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Hard stop
- 🟡 **MODERATE** → Warning

---

### ALLERGY-004: Macrolides (Azithromycin, Erythromycin)
**Allergy Category:** Drug - Antibiotic
**Patient-Friendly Label:** Macrolide allergy (Z-pack, erythromycin)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Nausea/vomiting | □ Rash | □ Anaphylaxis | □ Heart rhythm problems

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid azithromycin, clarithromycin, erythromycin
- **Safe Alternatives:** Doxycycline, fluoroquinolones
- **Note:** Nausea/vomiting is a common side effect, NOT a true allergy

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis, cardiac arrhythmia) → Hard stop
- ⚪ **MILD** (GI upset only) → Informational

---

### ALLERGY-005: Fluoroquinolones (Cipro, Levaquin)
**Allergy Category:** Drug - Antibiotic
**Patient-Friendly Label:** Fluoroquinolone allergy (Cipro, Levaquin)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Tendon pain/rupture | □ Rash | □ Confusion/hallucinations | □ Anaphylaxis

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid ciprofloxacin, levofloxacin, moxifloxacin
- **Safe Alternatives:** Beta-lactams, macrolides
- **Note:** Tendon rupture is an adverse effect, not allergy (still avoid)

**EMR Alert Flags:**
- 🔴 **SEVERE** (tendon rupture, CNS effects, anaphylaxis) → Hard stop
- 🟡 **MODERATE** (rash) → Warning

---

### ALLERGY-006: Aspirin
**Allergy Category:** Drug - NSAID
**Patient-Friendly Label:** Aspirin allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you took aspirin?**
   - Options: □ Rash/hives | □ Difficulty breathing/wheezing | □ Swelling | □ Stomach bleeding | □ Anaphylaxis

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid aspirin (all doses)
- **Cross-Reactivity:** High risk with all NSAIDs (ibuprofen, naproxen)
- **Safe Alternatives:** Acetaminophen (Tylenol), COX-2 inhibitors (celecoxib) - use cautiously
- **Cardiovascular Impact:** If aspirin needed for MI/stroke prevention, consider desensitization protocol

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis, respiratory compromise) → Hard stop on all NSAIDs
- 🟡 **MODERATE** (hives) → Warning on NSAIDs

---

### ALLERGY-007: Ibuprofen / NSAIDs
**Allergy Category:** Drug - NSAID
**Patient-Friendly Label:** Ibuprofen, Advil, Motrin, or NSAID allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Rash/hives | □ Difficulty breathing | □ Swelling | □ Stomach problems | □ Anaphylaxis

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid ibuprofen, naproxen, ketorolac, diclofenac
- **Cross-Reactivity:** Often cross-reactive with aspirin
- **Safe Alternatives:** Acetaminophen (Tylenol)

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Hard stop on all NSAIDs
- 🟡 **MODERATE** → Warning

---

### ALLERGY-008: Codeine
**Allergy Category:** Drug - Opioid
**Patient-Friendly Label:** Codeine allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Nausea/vomiting | □ Itching | □ Rash | □ Difficulty breathing | □ Severe reaction

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid codeine, tramadol (converted to similar metabolite)
- **Cross-Reactivity:** May tolerate morphine, hydrocodone, oxycodone (different metabolism)
- **Note:** Nausea/itching are common side effects, not true allergies
- **Safe Alternatives:** Non-opioid analgesics, or morphine/hydromorphone if true allergy

**EMR Alert Flags:**
- 🔴 **SEVERE** (respiratory depression, anaphylaxis) → Hard stop
- ⚪ **MILD** (nausea/itching only) → Informational

---

### ALLERGY-009: Morphine
**Allergy Category:** Drug - Opioid
**Patient-Friendly Label:** Morphine allergy
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Nausea/vomiting | □ Itching | □ Hives | □ Difficulty breathing | □ Anaphylaxis

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid morphine, hydromorphone (Dilaudid)
- **Safe Alternatives:** Fentanyl, oxycodone, hydrocodone (chemically distinct)

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Hard stop
- ⚪ **MILD** (nausea/itching) → Informational

---

### ALLERGY-010: Oxycodone / Hydrocodone
**Allergy Category:** Drug - Opioid
**Patient-Friendly Label:** Oxycodone or Hydrocodone allergy (Percocet, Vicodin)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Nausea | □ Rash | □ Difficulty breathing | □ Severe reaction

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid oxycodone, hydrocodone
- **Safe Alternatives:** Morphine, fentanyl, or non-opioid analgesics

**EMR Alert Flags:**
- 🔴 **SEVERE** → Hard stop
- ⚪ **MILD** → Informational

---

### ALLERGY-011: Local Anesthetics (Lidocaine, Novocaine)
**Allergy Category:** Drug - Anesthetic
**Patient-Friendly Label:** Novocaine or lidocaine allergy (numbing medication)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Rash at injection site | □ Rapid heartbeat/shaking | □ Difficulty breathing | □ Passed out | □ Severe reaction

2. **Where did this happen?**
   - Options: Dentist office | Hospital/surgery | Doctor's office | Emergency room

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid lidocaine or specific -caine agent
- **Cross-Reactivity:** Amides (lidocaine, bupivacaine) vs. Esters (procaine, benzocaine) - different classes
- **Important Note:** Most "allergies" are vasovagal reactions or epinephrine response (not true allergy)
- **Safe Alternatives:** Use alternative class (amide vs. ester) or preservative-free preparations

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Anesthesiology consult before procedures
- 🟡 **MODERATE** → Allergy testing recommended

---

### ALLERGY-012: Acetaminophen (Tylenol)
**Allergy Category:** Drug - Analgesic
**Patient-Friendly Label:** Tylenol (acetaminophen) allergy
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Rash | □ Difficulty breathing | □ Liver problems | □ Severe reaction

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid acetaminophen (Tylenol)
- **Safe Alternatives:** NSAIDs (if tolerated), opioids for severe pain
- **Note:** True allergy is rare; most reports are overdose-related liver injury

**EMR Alert Flags:**
- 🔴 **SEVERE** → Hard stop
- 🟡 **MODERATE** → Warning

---

### ALLERGY-013: Statins (Cholesterol Medications)
**Allergy Category:** Drug - Cardiovascular
**Patient-Friendly Label:** Statin allergy (cholesterol medications like Lipitor, Crestor)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Severe muscle pain/weakness | □ Liver problems | □ Rash | □ Memory problems

**Clinical Implications:**
- **Prescribing Restrictions:** Document which statin(s) tried
- **Note:** Muscle pain is common side effect (10-15%), NOT true allergy
- **Safe Alternatives:** Different statin (lower dose), ezetimibe, PCSK9 inhibitors
- **Cardiovascular Impact:** High-risk patients may need alternative lipid management

**EMR Alert Flags:**
- 🔴 **SEVERE** (rhabdomyolysis, severe liver injury) → Hard stop on statins
- 🟡 **MODERATE** (myalgias) → Consider alternative statin or non-statin therapy

---

### ALLERGY-014: ACE Inhibitors (Blood Pressure Medications)
**Allergy Category:** Drug - Cardiovascular
**Patient-Friendly Label:** ACE inhibitor allergy (blood pressure meds like Lisinopril)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Dry cough | □ Swelling of face/lips/tongue | □ Difficulty breathing | □ Rash

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid all ACE inhibitors (lisinopril, enalapril, ramipril)
- **Cross-Reactivity:** Do NOT use ARBs (losartan, valsartan) if angioedema occurred
- **Note:** Dry cough is side effect (10-15%), not allergy - but still switch medication
- **Safe Alternatives:** ARBs (if no angioedema), calcium channel blockers, beta-blockers

**EMR Alert Flags:**
- 🔴 **SEVERE** (angioedema - swelling of face/tongue) → Hard stop on ACE-I AND ARBs
- 🟡 **MODERATE** (cough only) → Switch to ARB

---

### ALLERGY-015: Beta-Blockers (Blood Pressure/Heart Medications)
**Allergy Category:** Drug - Cardiovascular
**Patient-Friendly Label:** Beta-blocker allergy (heart medications like Metoprolol, Atenolol)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Severe fatigue/weakness | □ Difficulty breathing/wheezing | □ Very slow heart rate | □ Rash

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid beta-blockers (metoprolol, atenolol, carvedilol)
- **Note:** Most reactions are side effects (fatigue, bradycardia), not true allergies
- **Safe Alternatives:** Calcium channel blockers, other antihypertensives

**EMR Alert Flags:**
- 🔴 **SEVERE** (bronchospasm in asthmatics, severe bradycardia) → Hard stop
- 🟡 **MODERATE** → Warning

---

### ALLERGY-016: Metformin (Diabetes Medication)
**Allergy Category:** Drug - Metabolic
**Patient-Friendly Label:** Metformin allergy (diabetes medication)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Nausea/diarrhea | □ Lactic acidosis | □ Rash | □ Difficulty breathing

**Clinical Implications:**
- **Prescribing Restrictions:** Avoid metformin
- **Note:** GI side effects (diarrhea) are very common, NOT true allergy
- **Safe Alternatives:** Other diabetes medications (sulfonylureas, GLP-1, SGLT2, insulin)

**EMR Alert Flags:**
- 🔴 **SEVERE** (lactic acidosis, anaphylaxis) → Hard stop
- ⚪ **MILD** (GI upset) → Informational

---

### ALLERGY-017: Corticosteroids (Prednisone, Dexamethasone)
**Allergy Category:** Drug - Steroid
**Patient-Friendly Label:** Steroid allergy (prednisone, cortisone)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Severe mood changes | □ High blood sugar | □ Rash | □ Anaphylaxis | □ Severe side effects

**Clinical Implications:**
- **Prescribing Restrictions:** Document which steroid and reaction type
- **Note:** Most reactions are side effects (hyperglycemia, mood changes), not allergies
- **Safe Alternatives:** Different steroid formulation, non-steroidal anti-inflammatory therapy
- **Important:** True steroid allergy is extremely rare

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis - very rare) → Hard stop
- ⚪ **MILD** (side effects) → Informational

---

### ALLERGY-018: Insulin
**Allergy Category:** Drug - Metabolic
**Patient-Friendly Label:** Insulin allergy
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened?**
   - Options: □ Rash/redness at injection site | □ Hives all over body | □ Difficulty breathing | □ Severe reaction

**Clinical Implications:**
- **Prescribing Restrictions:** Document type of insulin (rapid, long-acting, brand)
- **Cross-Reactivity:** May react to preservatives/additives, not insulin itself
- **Safe Alternatives:** Different insulin brand, desensitization protocol (if needed for diabetes control)
- **Diabetes Impact:** Critical to identify - insulin essential for Type 1 diabetes

**EMR Alert Flags:**
- 🔴 **SEVERE** (systemic anaphylaxis) → Endocrinology consult, desensitization
- 🟡 **MODERATE** (local reaction) → Try different insulin brand/formulation

---

## 🥜 TIER 1: FOOD ALLERGIES (8 Items)

### ALLERGY-019: Peanuts
**Allergy Category:** Food - Legume
**Patient-Friendly Label:** Peanut allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you eat peanuts?** (Check all that apply)
   - Options: □ Hives/rash | □ Swelling of lips/face | □ Difficulty breathing | □ Vomiting/diarrhea | □ Anaphylaxis/EpiPen needed | □ Hospitalized

2. **Do you carry an EpiPen?**
   - Options: Yes | No

**Clinical Implications:**
- **Dietary Restrictions:** Avoid peanuts and peanut-containing products
- **Cross-Reactivity:** ~5% react to tree nuts (not related botanically, but cross-contamination risk)
- **Nutritional Impact:** Recommend alternative protein sources
- **Emergency Preparedness:** EpiPen prescription if severe

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Flag for nutritional counseling
- **Critical Alert:** If anaphylaxis history, display red alert banner

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → EpiPen required, avoid all peanut exposure
- 🟡 **MODERATE** (hives, GI symptoms) → Strict avoidance, consider EpiPen

---

### ALLERGY-020: Tree Nuts
**Allergy Category:** Food - Tree Nut
**Patient-Friendly Label:** Tree nut allergy (almonds, walnuts, cashews, etc.)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which nuts cause problems?** (Check all that apply)
   - Options: □ All tree nuts | □ Almonds | □ Walnuts | □ Cashews | □ Pecans | □ Pistachios | □ Hazelnuts | □ Brazil nuts

2. **What happens when you eat these nuts?**
   - Options: □ Hives | □ Swelling | □ Difficulty breathing | □ Anaphylaxis/EpiPen needed

3. **Do you carry an EpiPen?**
   - Options: Yes | No

**Clinical Implications:**
- **Dietary Restrictions:** Avoid specific tree nuts or all tree nuts
- **Cross-Reactivity:** 30-40% react to multiple tree nuts
- **Safe Alternatives:** Peanuts (usually safe), seeds, other protein sources

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Nutritional counseling flag

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → EpiPen required
- 🟡 **MODERATE** → Strict avoidance

---

### ALLERGY-021: Shellfish
**Allergy Category:** Food - Seafood
**Patient-Friendly Label:** Shellfish allergy (shrimp, crab, lobster)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which types cause problems?** (Check all that apply)
   - Options: □ All shellfish | □ Shrimp | □ Crab | □ Lobster | □ Clams/oysters | □ Scallops

2. **What happens when you eat shellfish?**
   - Options: □ Hives | □ Swelling | □ Difficulty breathing | □ Vomiting/diarrhea | □ Anaphylaxis/EpiPen needed

3. **Do you carry an EpiPen?**
   - Options: Yes | No

**Clinical Implications:**
- **Dietary Restrictions:** Avoid shellfish (crustaceans and/or mollusks)
- **Cross-Reactivity:** High within shellfish category; generally safe to eat fish
- **Iodine Myth:** Shellfish allergy does NOT mean iodine/contrast dye allergy

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Nutritional counseling (omega-3 alternatives)

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → EpiPen required
- 🟡 **MODERATE** → Strict avoidance

---

### ALLERGY-022: Fish
**Allergy Category:** Food - Seafood
**Patient-Friendly Label:** Fish allergy (salmon, tuna, etc.)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **Which types cause problems?**
   - Options: □ All fish | □ Specific types (please specify in notes)

2. **What happens when you eat fish?**
   - Options: □ Hives | □ Swelling | □ Difficulty breathing | □ Anaphylaxis/EpiPen needed

**Clinical Implications:**
- **Dietary Restrictions:** Avoid fish
- **Cross-Reactivity:** Often react to multiple fish species
- **Safe Alternatives:** Generally safe to eat shellfish (different allergen)
- **Nutritional Impact:** Need alternative omega-3 sources (flaxseed, walnuts, supplements)

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Flag for omega-3 alternative counseling

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → EpiPen required
- 🟡 **MODERATE** → Strict avoidance

---

### ALLERGY-023: Milk / Dairy
**Allergy Category:** Food - Dairy
**Patient-Friendly Label:** Milk or dairy allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you consume dairy?**
   - Options: □ Hives/rash | □ Swelling | □ Difficulty breathing | □ Vomiting/diarrhea | □ Anaphylaxis | □ Stomach upset only (may be lactose intolerance, not allergy)

2. **Can you tolerate:** (Check all that apply)
   - Options: □ Baked goods with milk | □ Butter | □ Hard cheeses | □ Nothing with any dairy

**Clinical Implications:**
- **Dietary Restrictions:** Avoid milk, cheese, yogurt, ice cream
- **Lactose Intolerance vs. Allergy:** GI symptoms only = likely lactose intolerance (NOT allergy)
- **Nutritional Impact:** Calcium and vitamin D supplementation needed
- **Safe Alternatives:** Soy, almond, oat milk

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Flag for calcium/vitamin D counseling
- **Metabolic - Function:** Monitor vitamin D levels

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → True IgE allergy, strict avoidance
- 🟡 **MODERATE** (hives) → Strict avoidance
- ⚪ **MILD** (GI only) → Likely lactose intolerance, not true allergy

---

### ALLERGY-024: Eggs
**Allergy Category:** Food - Egg
**Patient-Friendly Label:** Egg allergy
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you eat eggs?**
   - Options: □ Hives/rash | □ Swelling | □ Difficulty breathing | □ Vomiting/diarrhea | □ Anaphylaxis

2. **Can you tolerate baked goods with eggs (like cakes, cookies)?**
   - Options: Yes | No | Haven't tried

**Clinical Implications:**
- **Dietary Restrictions:** Avoid eggs and egg-containing products
- **Vaccine Considerations:** Most influenza vaccines safe (low egg protein), but document
- **Baked Eggs:** Many with egg allergy tolerate baked eggs (proteins denatured)
- **Nutritional Impact:** Need alternative protein sources

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Nutritional counseling flag
- **Vaccine Planning:** Document for influenza vaccine decision

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Strict avoidance, vaccine consultation
- 🟡 **MODERATE** → Avoidance, may tolerate baked eggs

---

### ALLERGY-025: Wheat / Gluten
**Allergy Category:** Food - Grain
**Patient-Friendly Label:** Wheat or gluten allergy/sensitivity
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you eat wheat/gluten?**
   - Options: □ Hives/rash | □ Difficulty breathing | □ Severe GI symptoms | □ Bloating/diarrhea only | □ Anaphylaxis

2. **Have you been diagnosed with:** (Check if applicable)
   - Options: □ Celiac disease (autoimmune) | □ Wheat allergy | □ Non-celiac gluten sensitivity | □ Unsure/self-diagnosed

**Clinical Implications:**
- **Dietary Restrictions:** Avoid wheat, barley, rye (if celiac or gluten sensitivity)
- **Celiac Disease:** Autoimmune condition requiring strict lifelong gluten avoidance
- **Wheat Allergy:** IgE-mediated, may tolerate other grains
- **Gluten Sensitivity:** Non-celiac, symptom-based avoidance
- **Nutritional Impact:** Risk of B vitamin, iron, fiber deficiency

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Flag for nutritional counseling
- **Metabolic - Function:** Monitor B12, iron, folate
- **Immune - Risk:** If celiac, increase autoimmune disease monitoring

**EMR Alert Flags:**
- 🔴 **SEVERE** (celiac disease or anaphylaxis) → Strict gluten avoidance, nutritional monitoring
- 🟡 **MODERATE** (wheat allergy) → Wheat avoidance
- ⚪ **MILD** (sensitivity) → Patient preference, symptom management

---

### ALLERGY-026: Soy
**Allergy Category:** Food - Legume
**Patient-Friendly Label:** Soy allergy
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you eat soy?**
   - Options: □ Hives | □ Swelling | □ Difficulty breathing | □ GI symptoms | □ Anaphylaxis

**Clinical Implications:**
- **Dietary Restrictions:** Avoid soy, tofu, edamame, soy sauce, many processed foods
- **Nutritional Impact:** Soy is common protein alternative for vegetarians
- **Safe Alternatives:** Other legumes (usually safe), dairy, meat

**Dashboard Impact:**
- **Lifestyle - Nutrition Score:** Flag if vegetarian/vegan (limited protein sources)

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Strict avoidance
- 🟡 **MODERATE** → Avoidance

---

## 🩹 TIER 1: ENVIRONMENTAL / PROCEDURAL ALLERGIES (5 Items)

### ALLERGY-027: Latex
**Allergy Category:** Environmental - Latex
**Patient-Friendly Label:** Latex allergy (rubber gloves)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you're exposed to latex?**
   - Options: □ Skin rash/itching | □ Hives all over | □ Difficulty breathing | □ Anaphylaxis

2. **When does this happen?** (Check all that apply)
   - Options: □ Wearing rubber gloves | □ Medical/dental procedures | □ Balloons | □ Condoms | □ Other latex products

**Clinical Implications:**
- **Procedural Safety:** Use latex-free gloves, equipment for ALL medical/dental procedures
- **Cross-Reactivity (Food):** 30-50% react to banana, avocado, kiwi, chestnut ("latex-fruit syndrome")
- **Surgical Considerations:** All surgeries must use latex-free equipment
- **Emergency Preparedness:** Severe reactions require EpiPen

**Dashboard Impact:**
- **Critical Alert:** Red banner "LATEX ALLERGY - USE LATEX-FREE EQUIPMENT"
- **Lifestyle - Nutrition:** Flag potential banana/avocado cross-reactivity

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis, respiratory) → CRITICAL ALERT - All procedures latex-free
- 🟡 **MODERATE** (hives) → Latex-free precautions

---

### ALLERGY-028: Contrast Dye (Iodinated)
**Allergy Category:** Environmental - Contrast Media
**Patient-Friendly Label:** CT contrast dye allergy (iodine dye)
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you received contrast dye?**
   - Options: □ Hives/itching | □ Difficulty breathing | □ Severe reaction/anaphylaxis | □ Nausea only | □ Kidney problems

2. **When did this happen?**
   - Options: During CT scan | During heart catheterization | Other procedure | Don't remember

**Clinical Implications:**
- **Imaging Safety:** Pre-medicate with steroids + antihistamines before contrast CT
- **Alternative Imaging:** Use MRI (gadolinium) when possible
- **Severe Reactions:** May require non-contrast imaging only
- **Shellfish Myth:** Shellfish allergy does NOT predict contrast allergy (different allergens)

**Dashboard Impact:**
- **Critical Alert:** Yellow banner "CONTRAST DYE ALLERGY - PRE-MEDICATE OR USE ALTERNATIVE"
- **Renal - Function:** Monitor kidney function if contrast needed

**EMR Alert Flags:**
- 🔴 **SEVERE** (anaphylaxis) → Avoid if possible, use alternative imaging
- 🟡 **MODERATE** (hives) → Pre-medication protocol required

---

### ALLERGY-029: Gadolinium (MRI Contrast)
**Allergy Category:** Environmental - Contrast Media
**Patient-Friendly Label:** MRI contrast allergy (gadolinium)
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened when you received gadolinium?**
   - Options: □ Hives | □ Difficulty breathing | □ Severe reaction | □ Nausea

**Clinical Implications:**
- **Imaging Safety:** Use non-contrast MRI when possible
- **Cross-Reactivity:** No cross-reactivity with iodinated contrast (different agents)
- **Alternative Imaging:** CT with iodinated contrast (if tolerated), ultrasound

**Dashboard Impact:**
- **Critical Alert:** Yellow banner for MRI procedures

**EMR Alert Flags:**
- 🔴 **SEVERE** → Avoid gadolinium MRI
- 🟡 **MODERATE** → Use with pre-medication

---

### ALLERGY-030: Anesthesia (General)
**Allergy Category:** Environmental - Anesthetic
**Patient-Friendly Label:** Reaction to general anesthesia
**Intake Priority:** 1
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happened during or after anesthesia?**
   - Options: □ Severe nausea/vomiting | □ High fever/muscle rigidity | □ Difficulty breathing | □ Family history of malignant hyperthermia | □ Don't remember

2. **Which procedure was this?**
   - Options: Surgery | Colonoscopy | Dental procedure | Other

**Clinical Implications:**
- **Surgical Safety:** Anesthesiology consultation required before ALL procedures
- **Malignant Hyperthermia:** Life-threatening genetic condition (high fever, muscle rigidity)
- **PONV (Post-Operative Nausea):** Very common, NOT a true allergy
- **Alternative Agents:** Anesthesiologist will select alternative medications

**Dashboard Impact:**
- **Critical Alert:** Red banner "ANESTHESIA REACTION - ANESTHESIOLOGY CONSULT REQUIRED"

**EMR Alert Flags:**
- 🔴 **SEVERE** (malignant hyperthermia, anaphylaxis) → CRITICAL - Anesthesiology consult mandatory
- 🟡 **MODERATE** (other reactions) → Document for anesthesia team
- ⚪ **MILD** (PONV only) → Informational, pre-treat with anti-emetics

---

### ALLERGY-031: Adhesive / Tape
**Allergy Category:** Environmental - Adhesive
**Patient-Friendly Label:** Adhesive or medical tape allergy
**Intake Priority:** 2
**Smart Expansion:** Yes

**Expansion Questions:**
1. **What happens when you use medical tape or bandages?**
   - Options: □ Rash where tape was applied | □ Blisters | □ Severe skin reaction | □ Itching only

**Clinical Implications:**
- **Procedural Safety:** Use hypoallergenic tape, silicone-based adhesives
- **Wound Care:** Special dressings for surgical wounds
- **Minor Issue:** Usually not life-threatening, but important for comfort and wound healing

**Dashboard Impact:**
- **Musculoskeletal - Structure:** Flag if planning orthopedic procedures

**EMR Alert Flags:**
- 🟡 **MODERATE** → Use hypoallergenic tape/dressings
- ⚪ **MILD** → Informational

---

## 📊 TIER 2: OTHER ALLERGIES (Free-Text Entry)

**Purpose:** Capture rare or unlisted allergies

**Patient-Facing Instruction:**
"Do you have any OTHER allergies not listed above? Please describe:"

**Fields to Capture:**
- Allergen name (free text)
- Reaction type (free text)
- Severity (dropdown: Mild | Moderate | Severe)

**Clinical Review Required:** Yes - Clinical staff must review and categorize

---

## 🔧 TECHNICAL IMPLEMENTATION NOTES

### 1. Allergy vs. Intolerance vs. Side Effect

**Critical Distinction:**
- **True Allergy (IgE-mediated):** Hives, swelling, anaphylaxis, respiratory symptoms
- **Intolerance:** GI symptoms (nausea, diarrhea), headache, fatigue
- **Side Effect:** Expected pharmacologic effect (e.g., NSAID stomach upset)

**Intake Form Guidance:**
- Label reactions accurately in EMR
- "Allergy" should be reserved for true immune reactions
- Use "Intolerance" for non-immune reactions
- Document side effects separately

### 2. Severity Classification for Auto-Alerts

| Severity | Criteria | EMR Alert Type | Clinical Action |
|----------|----------|----------------|-----------------|
| **SEVERE** | Anaphylaxis, airway compromise, hospitalization, organ damage | 🔴 Hard stop | Prescriber must document override reason |
| **MODERATE** | Hives, wheezing, facial swelling, severe GI | 🟡 Soft warning | Warning displayed, easy to proceed |
| **MILD** | Rash, itching, nausea, common side effects | ⚪ Informational | Background note only |

### 3. Cross-Reactivity Auto-Flags

**System Should Auto-Flag:**
- Penicillin allergy → Warn about cephalosporins
- Aspirin allergy → Warn about ALL NSAIDs
- ACE inhibitor angioedema → HARD STOP on ARBs
- Latex allergy → Suggest asking about banana/avocado
- Sulfa antibiotic → Clarify does NOT include sulfonylureas/thiazides

### 4. Integration with Health Overview Dashboard

**Dashboard Display Locations:**

1. **Critical Alerts Panel (Level 1 - Always Visible):**
   - Severe drug allergies (anaphylaxis history)
   - Latex allergy (procedural risk)
   - Anesthesia reaction
   - Contrast dye allergy

2. **Lifestyle - Nutrition Pillar:**
   - Food allergies affecting nutritional status
   - Trigger nutritional counseling recommendations

3. **System-Specific Risk Scores:**
   - Celiac disease → Immune-Risk score modifier
   - Dairy allergy → Metabolic-Function (vitamin D concern)

### 5. EpiPen Prescription Triggers

**Auto-Recommend EpiPen if:**
- ANY history of anaphylaxis (food, drug, insect sting)
- Moderate food allergy to peanuts, tree nuts, shellfish, fish
- Severe drug allergy requiring frequent exposure (e.g., antibiotics)

**Dashboard Action:**
- Yellow alert: "Patient may benefit from EpiPen prescription - discuss with provider"

---

## 📋 INTAKE FORM DISPLAY LOGIC

### Priority 1 Allergies (Always Visible - 16 Items)

**Drug Allergies:**
- Penicillin / Amoxicillin
- Sulfa drugs
- Aspirin
- Ibuprofen / NSAIDs
- Codeine
- ACE inhibitors
- Local anesthetics

**Food Allergies:**
- Peanuts
- Tree nuts
- Shellfish
- Fish
- Milk / Dairy
- Eggs
- Wheat / Gluten

**Environmental:**
- Latex
- Contrast dye
- Anesthesia

### Priority 2 Allergies (Expandable Section - 15 Items)

**Click "Other Common Drug Allergies" to expand:**
- Cephalosporins
- Macrolides
- Fluoroquinolones
- Morphine
- Oxycodone/Hydrocodone
- Acetaminophen
- Statins
- Beta-blockers
- Metformin
- Corticosteroids
- Insulin

**Click "Other Common Allergies" to expand:**
- Soy
- Gadolinium (MRI contrast)
- Adhesive/tape

### Free-Text Section (Always Visible)

**"Other Allergies Not Listed"**
- Free-text box for rare/unlisted allergies
- Requires clinical review

---

## 🎯 COMPLETION SUMMARY

**Total Tier 1 Allergies:** 31
**Drug Allergies:** 18
**Food Allergies:** 8
**Environmental/Procedural:** 5

**Integration Points:**
- ✅ EMR prescribing safety alerts (hard stops and warnings)
- ✅ Procedural safety flags (latex, contrast, anesthesia)
- ✅ Nutritional counseling triggers (food allergies)
- ✅ Dashboard critical alerts panel
- ✅ EpiPen prescription recommendations

**Key Features:**
- Patient-friendly labels for low health literacy
- Smart expansion questions to capture severity and specifics
- Cross-reactivity auto-warnings
- Distinction between true allergy, intolerance, and side effects
- Severity-based EMR alert system (🔴🟡⚪)

---

**Document Status:** ✅ Complete
**Version:** 1.0
**Last Updated:** November 25, 2025
**Next Steps:** Integrate with patient-facing intake form mockup (Task 5)

---

*This Allergy Tier 1 Library ensures comprehensive allergy documentation while maintaining patient safety through structured smart expansion questions and automated clinical decision support.*
