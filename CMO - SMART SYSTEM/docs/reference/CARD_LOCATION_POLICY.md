# CARD LOCATION POLICY - NO DUPLICATES

## Core Principle
**ONE CARD = ONE LOCATION + MANY TAGS**

Each individual card (Tier 5) should exist in exactly ONE location in the hierarchy. Cross-referencing happens through the tagging system, not by listing the same card in multiple places.

---

## Why This Matters

### Problem with Duplicates
If "Lidocaine patches" appears in:
- Pain Management Medications > Topical Analgesics
- Neurological Medications > Neuropathic Pain Medications

Then you have:
- ❌ Two separate cards to maintain
- ❌ Version control nightmare
- ❌ Confusing for clinicians (which one to prescribe?)
- ❌ Duplicate effort when updating

### Solution: Single Location + Tags
Lidocaine patches appears ONCE:
- ✅ **Primary location**: Pain Management Medications > Topical Analgesics > Lidocaine patches
- ✅ **Tags**: #Pain #NeuropathicPain #TopicalAnalgesic #LocalAnesthetic
- ✅ Searchable by any relevant tag
- ✅ One card to maintain

---

## Location Assignment Rules

### Rule 1: Primary Use Case Determines Location
Place the card where it's MOST COMMONLY used.

**Examples**:
- **Metoprolol**: Used for hypertension, heart failure, AND arrhythmias
  - **Primary location**: Cardiovascular Medications > Antihypertensives > Beta Blockers
  - **Tags**: #Hypertension #HeartFailure #Arrhythmia #BetaBlocker
  
- **Gabapentin**: Used for neuropathic pain AND seizures
  - **Primary location**: Pain Management > Neuropathic Pain Medications
  - **Tags**: #NeuropathicPain #Seizures #NerveAgent
  - **Rationale**: More commonly prescribed for pain than seizures

- **Duloxetine (Cymbalta)**: Antidepressant AND neuropathic pain
  - **Primary location**: Neurological/Psychiatric Medications > Antidepressants > SNRIs
  - **Tags**: #Depression #Anxiety #NeuropathicPain #SNRI
  - **Rationale**: Classified as antidepressant, pain is secondary indication

### Rule 2: Drug Class Hierarchy Wins
When a medication has multiple indications, place it with its pharmacological drug class.

**Examples**:
- **Amitriptyline**: Antidepressant (TCA) used for depression, neuropathic pain, migraine prevention
  - **Location**: Neurological/Psychiatric > Antidepressants > TCAs
  - **Tags**: #Depression #NeuropathicPain #MigrainePrevention #TCA

- **Topiramate**: Anti-seizure drug used for seizures, migraine prevention, weight loss
  - **Location**: Neurological/Psychiatric > Anti-Seizure Medications
  - **Tags**: #Seizures #MigrainePrevention #WeightLoss #Anticonvulsant

### Rule 3: Therapeutic Category for Combination Use
If a medication is used equally across categories, choose the most specific therapeutic category.

**Examples**:
- **Prednisone**: Used for inflammation in MANY systems (respiratory, rheumatologic, GI, dermatologic)
  - **Location**: Endocrine & Other > Corticosteroids > Oral Corticosteroids
  - **Tags**: #Corticosteroid #AntiInflammatory #Asthma #IBD #Rheumatoid #Autoimmune
  - **Rationale**: "Corticosteroid" is the unifying drug class

---

## Resolved Duplicate Examples

### Example 1: Lidocaine Patches
**Appears in original outline**:
- Pain Management > Topical Analgesics
- Pain Management > Neuropathic Pain Medications

**CORRECTED - Single Location**:
- **Location**: Pain Management Medications > Topical Analgesics > Lidocaine Patches
- **Tags**: #Pain #NeuropathicPain #TopicalAnalgesic #LocalAnesthetic #PainManagement

---

### Example 2: Metoprolol
**Could appear in**:
- Cardiovascular > Antihypertensives > Beta Blockers
- Cardiovascular > Heart Failure Medications
- Cardiovascular > Antiarrhythmics

**CORRECTED - Single Location**:
- **Location**: Cardiovascular Medications > Antihypertensives > Beta Blockers > Metoprolol
- **Tags**: #Hypertension #HeartFailure #Arrhythmia #AtrialFibrillation #BetaBlocker #Cardiology

---

### Example 3: Gabapentin
**Could appear in**:
- Neurological/Psychiatric > Anti-Seizure Medications
- Pain Management > Neuropathic Pain Medications

**CORRECTED - Single Location**:
- **Location**: Pain Management Medications > Neuropathic Pain Medications > Gabapentin
- **Tags**: #NeuropathicPain #Seizures #NerveAgent #PainManagement #Neurology
- **Rationale**: More commonly prescribed for neuropathic pain in primary care

---

### Example 4: Spironolactone
**Could appear in**:
- Cardiovascular > Antihypertensives > Diuretics
- Cardiovascular > Heart Failure Medications
- Endocrine > Hormone-Related

**CORRECTED - Single Location**:
- **Location**: Cardiovascular Medications > Antihypertensives > Diuretics > Spironolactone
- **Tags**: #Hypertension #HeartFailure #Diuretic #PotassiumSparing #MineralocorticoidReceptorAntagonist

---

### Example 5: Omeprazole (Prilosec)
**Could appear in**:
- GI Medications > Acid Suppression > PPIs
- GI Medications > GERD Treatment

**CORRECTED - Single Location**:
- **Location**: Gastrointestinal Medications > Acid Suppression > Proton Pump Inhibitors > Omeprazole
- **Tags**: #GERD #PPI #AcidSuppression #GI #Heartburn #PepticUlcer

---

## How Tags Enable Discovery

Even though cards exist in ONE location, users can find them through multiple pathways:

### Search by Condition:
```
Search: #Hypertension
Results include:
- Lisinopril (in Cardiovascular > ACE Inhibitors)
- Metoprolol (in Cardiovascular > Beta Blockers)
- Amlodipine (in Cardiovascular > CCBs)
- DASH Diet (in Nutrition > Dietary Patterns)
- Walking Program (in Movement > Aerobic Exercise)
```

### Search by Drug Class:
```
Search: #BetaBlocker
Results include:
- Metoprolol (Cardiovascular > Beta Blockers)
- Atenolol (Cardiovascular > Beta Blockers)
- Carvedilol (Cardiovascular > Beta Blockers)
```

### Search by Symptom/Use:
```
Search: #NeuropathicPain
Results include:
- Gabapentin (Pain Management)
- Pregabalin (Pain Management)
- Duloxetine (Neurological/Psychiatric > SNRIs)
- Amitriptyline (Neurological/Psychiatric > TCAs)
- Lidocaine patches (Pain Management > Topical)
```

---

## Implementation Checklist

When adding a new card to the library:

- [ ] **Identify primary use case** (most common indication)
- [ ] **Assign ONE location** in hierarchy (Tier 3 → Tier 4 → Tier 5)
- [ ] **Apply ALL relevant tags** (condition, drug class, system, use case)
- [ ] **Check for potential duplicates** (search existing cards)
- [ ] **Document rationale** if location choice is ambiguous
- [ ] **Cross-reference in notes** if card could fit multiple places

---

## Master Card Location References

For commonly multi-use medications, here's the definitive location guide:

| Medication | Primary Location | Common Secondary Uses |
|------------|------------------|----------------------|
| Metoprolol | Cardiovascular > Beta Blockers | HF, arrhythmias |
| Gabapentin | Pain Management > Neuropathic | Seizures |
| Duloxetine | Neuro/Psych > Antidepressants | Neuropathic pain |
| Amitriptyline | Neuro/Psych > Antidepressants | Pain, migraine |
| Topiramate | Neuro/Psych > Anti-Seizure | Migraine, weight |
| Prednisone | Endocrine > Corticosteroids | Many inflammatory |
| Spironolactone | Cardiovascular > Diuretics | HF, acne, PCOS |
| Trazodone | Neuro/Psych > Antidepressants | Insomnia |
| Hydroxychloroquine | Rheumatologic > DMARDs | Lupus, RA, malaria |
| Allopurinol | Endocrine > Gout Medications | Hyperuricemia |

---

## Exception: When Duplicates ARE Allowed

**ONLY** when the same medication has DISTINCTLY DIFFERENT dosing, indication, and monitoring for different uses:

### Example: Semaglutide
- **Ozempic** (Diabetes): Lower dose (0.5-2mg weekly)
  - Location: Diabetes Medications > GLP-1 Agonists > Semaglutide (Ozempic)
  - Tags: #Diabetes #GLP1 #WeightLoss #Injectable

- **Wegovy** (Weight Loss): Higher dose (2.4mg weekly)
  - Location: Could be separate card if obesity management becomes its own Tier 3
  - Tags: #Obesity #WeightLoss #GLP1 #Injectable

**Rationale**: Different brand names, different dosing protocols, different indications = potentially separate cards (or noted as different formulations within one card)

---

## Summary

✅ **ONE card per medication/intervention**
✅ **Primary location determined by most common use**
✅ **MANY tags for cross-referencing**
✅ **Search/filter finds cards regardless of location**
✅ **No duplicate maintenance burden**

This policy ensures the library is maintainable, scalable, and unambiguous.