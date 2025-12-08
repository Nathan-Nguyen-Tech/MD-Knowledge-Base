# DME + Monitoring: Two-Step Workflow Pattern

**Version:** 1.0
**Date:** 2024-11-26
**Purpose:** Define the standard workflow for home monitoring activities that require equipment acquisition

---

## THE PATTERN

When a patient needs to perform home monitoring, there are TWO distinct card types involved:

### Step 1: DME Card (Durable Medical Equipment)
- **Card Type:** DME (Type 5)
- **Purpose:** Acquire the necessary equipment
- **Lifecycle:** One-time (or periodic for replacement)
- **Example:** "Obtain Glucose Meter"

### Step 2: Diagnostic Testing Card (Home Monitoring)
- **Card Type:** Diagnostic Testing - Home Monitoring (Type 2)
- **Purpose:** Perform the actual monitoring action
- **Lifecycle:** Ongoing (daily, weekly, etc.)
- **Example:** "Check Blood Glucose"

---

## WHY TWO STEPS?

### Different Lifecycles
| Aspect | DME Card (Step 1) | Monitoring Card (Step 2) |
|--------|-------------------|-------------------------|
| Frequency | Once | Ongoing (daily/weekly) |
| Duration | Until acquired | Indefinite |
| Completion | When equipment obtained | Continuous |
| Barriers | Insurance, cost, ordering | Adherence, technique |

### Different Tracking Needs
- **DME Card**: Track whether patient HAS the device
- **Monitoring Card**: Track whether patient is USING it

### Different Failure Points
- **DME Card fails**: Can't get equipment (insurance denial, cost barrier)
- **Monitoring Card fails**: Has equipment but not using it (forgetting, technique issues)

### Different Support Needs
- **DME Card**: Insurance navigation, supplier coordination, equipment setup
- **Monitoring Card**: Technique training, reminder systems, data interpretation

---

## COMPLETE REFERENCE: DME + MONITORING PAIRS

### Diabetes Monitoring

| DME Card | Monitoring Card | Frequency |
|----------|-----------------|-----------|
| Obtain Glucose Meter | Check Blood Glucose | 1-4x daily |
| Obtain Continuous Glucose Monitor (CGM) | Review CGM Data | Daily |
| Obtain Insulin Pen/Pump | Administer Insulin | Per prescription |
| Obtain Lancets | N/A (consumable) | Resupply |
| Obtain Test Strips | N/A (consumable) | Resupply |

---

### Cardiovascular Monitoring

| DME Card | Monitoring Card | Frequency |
|----------|-----------------|-----------|
| Obtain Blood Pressure Cuff | Check Blood Pressure | 1-2x daily |
| Obtain Home Scale | Check Body Weight | Daily |
| Obtain Pulse Oximeter | Check Oxygen Saturation | As directed |
| Obtain Heart Rate Monitor | Check Heart Rate | As directed |
| Obtain AED (Automated External Defibrillator) | N/A (emergency use) | N/A |

---

### Respiratory Monitoring

| DME Card | Monitoring Card | Frequency |
|----------|-----------------|-----------|
| Obtain Peak Flow Meter | Check Peak Flow | 1-2x daily |
| Obtain Pulse Oximeter | Check Oxygen Saturation | As directed |
| Obtain Nebulizer | Administer Nebulizer Treatment | Per prescription |
| Obtain CPAP/BiPAP | Use CPAP Device | Nightly |
| Obtain Home Oxygen | Use Supplemental Oxygen | As prescribed |

---

### Temperature/Fever Monitoring

| DME Card | Monitoring Card | Frequency |
|----------|-----------------|-----------|
| Obtain Thermometer | Check Temperature | When symptomatic |

---

### Medication Administration

| DME Card | Monitoring Card/Action | Frequency |
|----------|------------------------|-----------|
| Obtain Pill Organizer | Organize Weekly Medications | Weekly |
| Obtain Medication Reminder Device | N/A (automated) | N/A |
| Obtain Sharps Container | Dispose of Sharps | As needed |

---

### Mobility & Fall Prevention

| DME Card | Associated Cards | Type |
|----------|------------------|------|
| Obtain Walker | Use Walker | Behavioral/Ongoing |
| Obtain Cane | Use Cane | Behavioral/Ongoing |
| Obtain Grab Bars | N/A (installed) | Environmental |
| Obtain Wheelchair | Use Wheelchair | Behavioral/Ongoing |

---

### Hearing & Vision

| DME Card | Associated Cards | Type |
|----------|------------------|------|
| Obtain Hearing Aids | Wear Hearing Aids | Behavioral/Daily |
| Obtain Glasses/Contacts | Wear Corrective Lenses | Behavioral/Daily |

---

### Wound Care

| DME Card | Monitoring Card | Frequency |
|----------|-----------------|-----------|
| Obtain Wound Care Supplies | Perform Wound Care | Per instructions |
| Obtain Compression Stockings | Wear Compression Stockings | Daily |

---

## WORKFLOW IN PRACTICE

### Scenario: New Diabetes Diagnosis

**Phase 1: Equipment Acquisition (DME Cards)**
```
Week 1:
├── [DME] Obtain Glucose Meter ✓ Completed
├── [DME] Obtain Lancets ✓ Completed
├── [DME] Obtain Test Strips ✓ Completed
└── [Referral] Diabetes Educator Visit ✓ Completed
```

**Phase 2: Ongoing Monitoring (Diagnostic Cards)**
```
Daily (ongoing):
├── [Diagnostic] Check Blood Glucose - Before breakfast
├── [Diagnostic] Check Blood Glucose - Before dinner
└── [Behavioral] Log Results in App
```

---

### Scenario: New Hypertension Diagnosis

**Phase 1: Equipment Acquisition (DME Cards)**
```
Week 1:
├── [DME] Obtain Blood Pressure Cuff ✓ Completed
└── [Micro-Learning] How to Measure BP Correctly ✓ Completed
```

**Phase 2: Ongoing Monitoring (Diagnostic Cards)**
```
Daily (ongoing):
├── [Diagnostic] Check Blood Pressure - Morning
├── [Diagnostic] Check Blood Pressure - Evening
└── [Behavioral] Log Results in App
```

---

## CARD TEMPLATE DIFFERENCES

### DME Card Template Elements

```
WHO: Patient obtains; Provider prescribes; DME supplier provides
WHAT: Specific equipment name, brand if relevant
HOW: How to order, insurance process, setup instructions
WHEN: One-time acquisition (or replacement schedule)
WHERE: DME supplier, pharmacy, online
MEASURE: Equipment obtained Y/N, functional status
TARGET: Patient has working equipment
SAFETY: Proper use training, maintenance requirements
FOLLOW-UP: Equipment check, supply reorder
```

### Monitoring Card Template Elements

```
WHO: Patient performs; Provider interprets results
WHAT: Specific measurement/test
HOW: Proper technique, positioning, timing
WHEN: Frequency (daily, weekly, etc.)
WHERE: Home (consistent location)
MEASURE: The vital sign/value being tracked
TARGET: Goal range (personalized)
SAFETY: When to call provider (critical values)
FOLLOW-UP: Data review, trend analysis, adjustment
```

---

## CONSUMABLES vs. EQUIPMENT

Some items are **consumables** (need regular resupply) rather than durable equipment:

### Consumables (Resupply Cards)
- Test strips
- Lancets
- Batteries
- Filters (CPAP)
- Wound dressing supplies
- Nebulizer medication

### Durable Equipment (One-Time + Replacement)
- Glucose meter
- Blood pressure cuff
- CPAP machine
- Nebulizer
- Pulse oximeter

**Note:** Consumable resupply may be a behavioral card ("Reorder Test Strips") or automated through pharmacy/supplier.

---

## INTEGRATION WITH DASHBOARD

### DME Status Tracking
- Equipment ordered? Y/N
- Equipment received? Y/N
- Equipment functional? Y/N
- Supplies adequate? Y/N

### Monitoring Adherence Tracking
- Measurements completed today? Y/N
- Values within target? Y/N
- Critical values flagged? Y/N
- Trends concerning? Y/N

---

## CARD DE-LOADING RULES

### DME Cards
**De-load when:**
- Equipment successfully obtained AND
- Patient trained on use AND
- Equipment verified functional

**Keep active if:**
- Insurance approval pending
- Equipment on backorder
- Awaiting training

### Monitoring Cards
**De-load when:**
- Condition resolved (rare) OR
- Monitoring no longer clinically needed OR
- Replaced by different monitoring method

**Typically remain active indefinitely for chronic conditions**

---

## SUMMARY

| Step | Card Type | Example | Lifecycle |
|------|-----------|---------|-----------|
| 1 | DME | Obtain Glucose Meter | One-time |
| 2 | Diagnostic Testing | Check Blood Glucose | Ongoing |

**Key Principle:** Separate acquisition from use - they have different barriers, tracking needs, and lifecycles.

---

**END OF DOCUMENT**
