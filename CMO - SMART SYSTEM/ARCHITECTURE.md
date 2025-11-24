# SMART Card Library - Technical Architecture

## System Overview

The SMART Card Library is a comprehensive digital health platform that transforms traditional patient education into actionable, trackable, evidence-based interventions. This document outlines the technical architecture required to build and deploy the system.

## Architecture Principles

1. **Patient-Centric Design**: All interfaces optimized for patient engagement and adherence
2. **Evidence-Based**: Every recommendation backed by clinical guidelines (Grade A/B/C)
3. **AI-Augmented, Clinician-Approved**: AI suggests, humans decide
4. **Scalable & Modular**: Support for ~1,000 cards with room for growth
5. **Interoperable**: Integrate with existing EHR, lab, and pharmacy systems
6. **Privacy-First**: HIPAA-compliant data handling and storage
7. **Accessible**: Multi-platform (web, iOS, Android), multilingual, low-tech alternatives

## High-Level System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    PRESENTATION LAYER                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   Patient    │  │  Clinician   │  │    Admin     │     │
│  │     App      │  │  Dashboard   │  │   Portal     │     │
│  │ (iOS/Android)│  │   (Web)      │  │   (Web)      │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│         │                  │                  │             │
└─────────┼──────────────────┼──────────────────┼─────────────┘
          │                  │                  │
          ▼                  ▼                  ▼
┌─────────────────────────────────────────────────────────────┐
│                      API GATEWAY                             │
│              (Authentication & Rate Limiting)                │
└─────────────────────────────────────────────────────────────┘
          │                  │                  │
          ▼                  ▼                  ▼
┌─────────────────────────────────────────────────────────────┐
│                   APPLICATION LAYER                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │   Card     │  │    Deck    │  │    AI      │           │
│  │  Service   │  │  Service   │  │  Service   │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │  Patient   │  │ Monitoring │  │ Community  │           │
│  │  Service   │  │  Service   │  │  Service   │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │    NLP     │  │   Drug     │  │ Evidence   │           │
│  │  Parser    │  │ Interaction│  │  Service   │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
          │                  │                  │
          ▼                  ▼                  ▼
┌─────────────────────────────────────────────────────────────┐
│                      DATA LAYER                              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │   Card     │  │  Patient   │  │  Evidence  │           │
│  │ Database   │  │ Database   │  │ Database   │           │
│  │ (Postgres) │  │ (Postgres) │  │ (Postgres) │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │   Metrics  │  │   Cache    │  │   Files    │           │
│  │   Store    │  │   (Redis)  │  │    (S3)    │           │
│  │(TimeSeries)│  └────────────┘  └────────────┘           │
│  └────────────┘                                            │
│                                                             │
└─────────────────────────────────────────────────────────────┘
          │                  │                  │
          ▼                  ▼                  ▼
┌─────────────────────────────────────────────────────────────┐
│                  INTEGRATION LAYER                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │    EHR     │  │    Lab     │  │  Pharmacy  │           │
│  │   (FHIR)   │  │  Systems   │  │  Systems   │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│  │ Wearables  │  │  Guideline │  │   Drug     │           │
│  │   APIs     │  │ Databases  │  │ Databases  │           │
│  └────────────┘  └────────────┘  └────────────┘           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Core Data Models

### 1. Card Model

```typescript
interface SmartCard {
  // Identity
  card_id: string;                    // Unique identifier
  card_name: string;                  // Human-readable name
  version: string;                    // Version number (e.g., "2.1")

  // Hierarchy
  tier_1_category: 'Medical' | 'Behavioral';
  tier_2_card_type: CardType;         // Medication, Lab, Nutrition, etc.
  tier_3_file: string;                // e.g., "Cardiovascular_Medications"
  tier_4_subcategory: string;         // e.g., "ACE Inhibitors"
  tier_5_individual_card: string;     // e.g., "Lisinopril 10mg"

  // Content (following Universal Template)
  patient_facing: {
    what: string;                     // Simple action (6th-8th grade)
    why: string;                      // Patient's personal goal
    how: string[];                    // 3-5 simple steps
    when: string;                     // Frequency + timeline
    watch_for: string[];              // Top 2-3 red flags
  };

  clinical_details: {
    what: WhatSection;
    who: WhoSection;
    when: WhenSection;
    where: WhereSection;
    why: WhySection;
    how: HowSection;
    measure: MeasureSection;
    target: TargetSection;
    safety: SafetySection;
    follow_up: FollowUpSection;
    notes: NotesSection;
  };

  // Metadata
  tags: string[];                     // 5-10 tags for filtering
  evidence_grade: 'A' | 'B' | 'C';   // Evidence quality
  guidelines: string[];               // e.g., ["ACC/AHA 2024", "USPSTF Grade A"]

  // Scoring
  feasibility_score: number;          // 0-100 (AI-calculated base)
  community_rating: number;           // 0-5 stars
  adherence_rate: number;             // % completing >30 days
  target_achievement_rate: number;    // % meeting clinical goals

  // Versioning
  created_at: Date;
  updated_at: Date;
  last_reviewed: Date;
  next_review: Date;
  version_history: VersionChange[];

  // Type-Specific Data
  card_type_data: MedicationData | LabData | NutritionData | ExerciseData | ...;
}

// Card Type Enumeration
type CardType =
  | 'Medication'
  | 'Lab'
  | 'Imaging'
  | 'Procedure'
  | 'Referral'
  | 'Nutrition'
  | 'Movement'
  | 'Recovery'
  | 'MindBody'
  | 'MicroLearning';
```

### 2. Deck Model

```typescript
interface SmartDeck {
  // Identity
  deck_id: string;
  deck_name: string;                  // e.g., "Hypertension Management Deck"
  version: string;

  // Clinical Context
  clinical_goals: string[];           // Linked to Performance Medicine Framework
  target_population: string;          // Who should use this deck
  indication: string;                 // Specific diagnosis/condition

  // Card Composition
  cards: DeckCard[];                  // Ordered array of cards

  // Progressive Unlocking Logic
  unlock_sequence: UnlockRule[];      // Card 1 unlocks Card 2, etc.

  // Metadata
  evidence_grade: 'A' | 'B' | 'C';   // Lowest grade among all cards
  total_time_burden: number;          // Minutes per day
  overall_feasibility: number;        // Average of all cards

  // Expected Outcomes
  primary_outcome: Outcome;
  secondary_outcomes: Outcome[];
  timeline: string;                   // "4-8 weeks to target"

  // Success Metrics
  completion_rate: number;            // % patients finishing deck
  outcome_achievement_rate: number;   // % meeting targets
  patient_satisfaction: number;       // Average rating

  // Customization
  is_standard: boolean;               // Pre-built vs custom
  created_by: string;                 // Clinician ID if custom

  // Versioning
  created_at: Date;
  updated_at: Date;
}

interface DeckCard {
  card_id: string;
  position: number;                   // Order in deck (1-based)
  is_optional: boolean;               // Can patient skip?
  unlock_after: string | null;        // card_id that must complete first
  category: 'MicroLearning' | 'Action' | 'Monitoring' | 'FollowUp';
}

interface UnlockRule {
  card_id: string;
  requires_completion_of: string[];   // Array of prerequisite card_ids
  auto_unlock_after_days: number | null;  // Or time-based unlock
}
```

### 3. Patient Model

```typescript
interface Patient {
  // Identity
  patient_id: string;
  demographics: Demographics;

  // Health Data
  diagnoses: Diagnosis[];             // Active ICD-10 codes
  medications: CurrentMedication[];   // Current med list
  allergies: Allergy[];
  recent_labs: LabResult[];
  recent_vitals: VitalSign[];

  // Social Determinants of Health
  barriers: PatientBarrier[];         // Transportation, cost, etc.
  language: string;
  literacy_level: string;
  insurance_coverage: InsurancePlan;

  // Goals & Preferences
  personal_goals: string[];           // Patient's own words
  preferences: Preference[];          // Diet, exercise, etc.

  // Active Care Plan
  active_decks: ActiveDeck[];
  active_individual_cards: ActiveCard[];

  // Historical Data
  completed_cards: CompletedCard[];
  card_history: CardHistory[];

  // Scores
  overall_adherence_rate: number;     // % of cards adhered to
  confidence_scores: ConfidenceScore[];  // Per card
}

interface ActiveCard {
  card_id: string;
  assigned_date: Date;
  assigned_by: string;                // Clinician ID
  deck_id: string | null;             // If part of deck

  // Patient-Specific Customization
  personalized_target: any | null;    // Override default target
  personalized_frequency: string | null;
  custom_instructions: string | null;

  // Tracking
  adherence_logs: AdherenceLog[];
  measurement_logs: MeasurementLog[];
  barrier_reports: BarrierReport[];
  side_effect_reports: SideEffectReport[];

  // Status
  status: 'Active' | 'Paused' | 'Completed' | 'Discontinued';
  patient_confidence_score: number;   // 0-10 scale
  personalized_feasibility: number;   // Adjusted from base
}

interface ActiveDeck {
  deck_id: string;
  assigned_date: Date;
  assigned_by: string;

  // Progress
  cards_unlocked: string[];           // card_ids currently available
  cards_completed: string[];          // card_ids patient finished
  current_phase: number;              // Which phase of deck (1, 2, 3)

  // Status
  status: 'Active' | 'Paused' | 'Completed' | 'Discontinued';
  completion_percentage: number;
}

interface AdherenceLog {
  date: Date;
  completed: boolean;                 // Did patient do the action?
  notes: string | null;               // Patient's comments
  time_spent: number | null;          // Minutes
}

interface MeasurementLog {
  date: Date;
  measure_type: string;               // BP, weight, glucose, etc.
  value: any;                         // Structured data (numeric, range, etc.)
  within_target: boolean;
}
```

### 4. AI Recommendation Model

```typescript
interface AIRecommendation {
  recommendation_id: string;
  patient_id: string;
  generated_at: Date;

  // Input Analysis
  patient_profile: PatientProfile;    // Snapshot of patient data

  // Recommended Cards/Decks
  recommended_decks: RecommendedDeck[];
  recommended_individual_cards: RecommendedCard[];

  // Reasoning
  clinical_rationale: string;
  evidence_summary: string;

  // Clinician Decision
  reviewed_by: string | null;         // Clinician ID
  reviewed_at: Date | null;
  decision: 'Approved' | 'Modified' | 'Rejected' | 'Pending';
  clinician_modifications: Modification[] | null;
}

interface RecommendedCard {
  card_id: string;
  priority: number;                   // 1 = highest
  score: number;                      // Total weighted score (0-100)

  // Score Breakdown
  evidence_score: number;
  feasibility_score: number;
  time_to_benefit_score: number;
  burden_score: number;
  patient_priority_score: number;
  guideline_mandate_score: number;

  // Rationale
  rationale: string;                  // Why AI recommends this card

  // Warnings
  contraindications: Contraindication[];
  interactions: Interaction[];
  barriers: string[];
}

interface RecommendedDeck {
  deck_id: string;
  priority: number;
  score: number;
  rationale: string;

  // Synergy Analysis
  synergy_notes: string[];            // How cards work together
  conflict_warnings: string[];        // Potential issues

  // Burden Analysis
  total_time_burden: number;          // Minutes/day
  complexity_level: 'Simple' | 'Moderate' | 'Complex';
}
```

## Service Architectures

### 1. Card Service

**Responsibilities:**
- CRUD operations for card library
- Version management
- Tag management
- Search and filtering
- Card validation

**Key Endpoints:**
```
GET    /api/cards                      # List cards (with filters)
GET    /api/cards/:id                  # Get specific card
POST   /api/cards                      # Create new card (admin)
PUT    /api/cards/:id                  # Update card (admin)
DELETE /api/cards/:id                  # Archive card (admin)

GET    /api/cards/search               # Advanced search with tags
GET    /api/cards/:id/versions         # Version history
GET    /api/cards/:id/community        # Community feedback
```

### 2. Deck Service

**Responsibilities:**
- Deck assembly and management
- Progressive unlocking logic
- Deck templates (condition-based)
- Custom deck creation

**Key Endpoints:**
```
GET    /api/decks                      # List available decks
GET    /api/decks/:id                  # Get specific deck
POST   /api/decks                      # Create custom deck
PUT    /api/decks/:id                  # Update deck
GET    /api/decks/templates            # Pre-built condition decks

GET    /api/decks/:id/cards            # Cards in deck with unlock status
POST   /api/decks/:id/unlock           # Manually unlock next card
GET    /api/decks/:id/synergy          # Analyze card synergies
GET    /api/decks/:id/conflicts        # Check for conflicts
```

### 3. AI Service

**Responsibilities:**
- Patient profile analysis
- Card/deck recommendation
- Feasibility scoring
- Conflict checking
- NLP parsing of clinical notes

**Key Endpoints:**
```
POST   /api/ai/recommend               # Generate recommendations
POST   /api/ai/score-feasibility       # Calculate feasibility for patient
POST   /api/ai/check-conflicts         # Check for contraindications
POST   /api/ai/parse-note              # Parse clinical note to cards
GET    /api/ai/recommendations/:id     # Get recommendation details
```

**AI Algorithms:**

**1. Prioritization Scoring:**
```
Total Score = (Evidence × 0.30) + (Feasibility × 0.25) +
              (Time-to-Benefit × 0.15) + (Burden × 0.15) +
              (Patient Priority × 0.10) + (Guideline Mandate × 0.05)
```

**2. Feasibility Scoring:**
```
Base Score: 100%

Deductions:
- No insurance coverage: -25%
- High cost (>$100/month): -20%
- Requires equipment patient lacks: -15%
- Transportation barriers: -15%
- Time intensive (>30 min/day): -10%
- Complex instructions (>5 steps): -10%
- Language barriers: -15%
- Contraindication/allergy: -100%

Additions:
- Previously succeeded: +15%
- Patient requested: +20%
- Low burden (<10 min/day): +10%
- Free or covered: +10%
- Can do at home: +10%
- Strong social support: +10%
- High community rating (>4 stars): +5%
```

**3. Conflict Checking:**
```
Priority 1: Absolute contraindications → BLOCK
Priority 2: Drug-drug major interactions → WARN/BLOCK
Priority 3: Drug-condition contraindications → WARN
Priority 4: Card-card conflicts → FLAG
Priority 5: Moderate interactions → INFORM
```

### 4. Patient Service

**Responsibilities:**
- Patient profile management
- Active card/deck management
- Adherence tracking
- Barrier reporting

**Key Endpoints:**
```
GET    /api/patients/:id               # Get patient profile
PUT    /api/patients/:id               # Update patient profile

GET    /api/patients/:id/active-cards  # Current active cards
GET    /api/patients/:id/active-decks  # Current active decks
POST   /api/patients/:id/log-adherence # Log adherence for card
POST   /api/patients/:id/log-measurement # Log measurement (BP, glucose, etc.)
POST   /api/patients/:id/report-barrier # Report barrier
POST   /api/patients/:id/report-side-effect # Report side effect

GET    /api/patients/:id/progress      # Progress dashboard
GET    /api/patients/:id/history       # Card history
```

### 5. Monitoring Service

**Responsibilities:**
- Continuous patient monitoring
- Alert generation
- Progress tracking
- Analytics and reporting

**Key Endpoints:**
```
GET    /api/monitoring/alerts          # Get active alerts
GET    /api/monitoring/patients/:id/alerts # Patient-specific alerts
POST   /api/monitoring/alerts/:id/acknowledge # Acknowledge alert

GET    /api/monitoring/adherence       # Adherence dashboard
GET    /api/monitoring/outcomes        # Outcome metrics
GET    /api/monitoring/analytics       # System-wide analytics
```

**Alert Types:**
- Low adherence (<50% for any card)
- Not improving toward target
- Adverse event reported
- Card conflict detected
- Patient disengagement (no logs >7 days)

### 6. Community Service

**Responsibilities:**
- Patient reviews and ratings
- Comment moderation
- Community analytics
- Flagging system

**Key Endpoints:**
```
GET    /api/community/cards/:id/reviews # Get reviews for card
POST   /api/community/cards/:id/review  # Submit review
PUT    /api/community/reviews/:id       # Edit own review
DELETE /api/community/reviews/:id       # Delete own review

POST   /api/community/reviews/:id/flag  # Flag inappropriate review
GET    /api/community/reviews/pending   # Pending moderation (admin)
POST   /api/community/reviews/:id/approve # Approve review (admin)
POST   /api/community/reviews/:id/reject  # Reject review (admin)

GET    /api/community/analytics         # Community insights
```

### 7. NLP Parser Service

**Responsibilities:**
- Parse clinical notes into structured cards
- Extract actionable items
- Map to card templates
- Generate draft cards for review

**Workflow:**
```
1. Input: Clinical MDM note (free text)
2. Section Identification: Detect Assessment & Plan sections
3. Entity Extraction: Medications, labs, lifestyle interventions
4. Template Mapping: Match entities to card templates
5. Auto-Population: Fill card fields from knowledge bases
6. Output: Draft cards for clinician review
```

**Example:**
```
Input: "Start lisinopril 10mg daily for HTN"

Extraction:
- Drug: Lisinopril
- Dose: 10mg
- Route: Oral (implied)
- Frequency: Daily
- Indication: Hypertension

Template Match: MED_ACE_Lisinopril

Auto-Population:
- Fill mechanism of action from drug database
- Add contraindications
- Add evidence citations
- Add safety information
- Generate patient-facing language

Output: Draft Lisinopril 10mg card for clinician to review/publish
```

## Database Schema

### Cards Table
```sql
CREATE TABLE smart_cards (
    card_id UUID PRIMARY KEY,
    card_name TEXT NOT NULL,
    version TEXT NOT NULL,

    -- Hierarchy
    tier_1_category TEXT NOT NULL,
    tier_2_card_type TEXT NOT NULL,
    tier_3_file TEXT,
    tier_4_subcategory TEXT,
    tier_5_individual_card TEXT,

    -- Content
    patient_facing JSONB NOT NULL,
    clinical_details JSONB NOT NULL,
    card_type_data JSONB,

    -- Metadata
    tags TEXT[],
    evidence_grade CHAR(1) CHECK (evidence_grade IN ('A', 'B', 'C')),
    guidelines TEXT[],

    -- Scoring
    feasibility_score DECIMAL(5,2),
    community_rating DECIMAL(3,2),
    adherence_rate DECIMAL(5,2),
    target_achievement_rate DECIMAL(5,2),

    -- Versioning
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW(),
    last_reviewed DATE,
    next_review DATE,
    version_history JSONB,

    -- Soft delete
    archived_at TIMESTAMP
);

CREATE INDEX idx_cards_type ON smart_cards(tier_2_card_type);
CREATE INDEX idx_cards_tags ON smart_cards USING GIN(tags);
CREATE INDEX idx_cards_grade ON smart_cards(evidence_grade);
```

### Decks Table
```sql
CREATE TABLE smart_decks (
    deck_id UUID PRIMARY KEY,
    deck_name TEXT NOT NULL,
    version TEXT NOT NULL,

    -- Clinical Context
    clinical_goals TEXT[],
    target_population TEXT,
    indication TEXT,

    -- Metadata
    evidence_grade CHAR(1),
    total_time_burden INTEGER,
    overall_feasibility DECIMAL(5,2),

    -- Expected Outcomes
    primary_outcome JSONB,
    secondary_outcomes JSONB,
    timeline TEXT,

    -- Success Metrics
    completion_rate DECIMAL(5,2),
    outcome_achievement_rate DECIMAL(5,2),
    patient_satisfaction DECIMAL(3,2),

    -- Customization
    is_standard BOOLEAN DEFAULT FALSE,
    created_by UUID REFERENCES users(user_id),

    -- Versioning
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE deck_cards (
    deck_card_id UUID PRIMARY KEY,
    deck_id UUID REFERENCES smart_decks(deck_id) ON DELETE CASCADE,
    card_id UUID REFERENCES smart_cards(card_id),
    position INTEGER NOT NULL,
    is_optional BOOLEAN DEFAULT FALSE,
    unlock_after UUID REFERENCES smart_cards(card_id),
    category TEXT CHECK (category IN ('MicroLearning', 'Action', 'Monitoring', 'FollowUp')),

    UNIQUE(deck_id, position)
);
```

### Patients Table
```sql
CREATE TABLE patients (
    patient_id UUID PRIMARY KEY,
    external_id TEXT UNIQUE, -- EHR patient ID
    demographics JSONB,

    -- Health Data
    diagnoses JSONB,
    current_medications JSONB,
    allergies JSONB,
    recent_labs JSONB,
    recent_vitals JSONB,

    -- Social Determinants
    barriers JSONB,
    language TEXT,
    literacy_level TEXT,
    insurance_coverage JSONB,

    -- Goals & Preferences
    personal_goals TEXT[],
    preferences JSONB,

    -- Scores
    overall_adherence_rate DECIMAL(5,2),

    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE patient_active_cards (
    patient_card_id UUID PRIMARY KEY,
    patient_id UUID REFERENCES patients(patient_id) ON DELETE CASCADE,
    card_id UUID REFERENCES smart_cards(card_id),
    deck_id UUID REFERENCES smart_decks(deck_id),

    assigned_date TIMESTAMP DEFAULT NOW(),
    assigned_by UUID REFERENCES users(user_id),

    -- Customization
    personalized_target JSONB,
    personalized_frequency TEXT,
    custom_instructions TEXT,

    -- Status
    status TEXT CHECK (status IN ('Active', 'Paused', 'Completed', 'Discontinued')),
    patient_confidence_score INTEGER CHECK (patient_confidence_score BETWEEN 0 AND 10),
    personalized_feasibility DECIMAL(5,2),

    completed_at TIMESTAMP
);

CREATE TABLE patient_active_decks (
    patient_deck_id UUID PRIMARY KEY,
    patient_id UUID REFERENCES patients(patient_id) ON DELETE CASCADE,
    deck_id UUID REFERENCES smart_decks(deck_id),

    assigned_date TIMESTAMP DEFAULT NOW(),
    assigned_by UUID REFERENCES users(user_id),

    -- Progress
    cards_unlocked UUID[],
    cards_completed UUID[],
    current_phase INTEGER,

    -- Status
    status TEXT CHECK (status IN ('Active', 'Paused', 'Completed', 'Discontinued')),
    completion_percentage DECIMAL(5,2),

    completed_at TIMESTAMP
);
```

### Adherence Tracking
```sql
CREATE TABLE adherence_logs (
    log_id UUID PRIMARY KEY,
    patient_card_id UUID REFERENCES patient_active_cards(patient_card_id) ON DELETE CASCADE,
    log_date DATE NOT NULL,
    completed BOOLEAN NOT NULL,
    notes TEXT,
    time_spent INTEGER, -- minutes

    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE measurement_logs (
    log_id UUID PRIMARY KEY,
    patient_card_id UUID REFERENCES patient_active_cards(patient_card_id) ON DELETE CASCADE,
    log_date DATE NOT NULL,
    measure_type TEXT NOT NULL,
    value JSONB NOT NULL,
    within_target BOOLEAN,

    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE barrier_reports (
    report_id UUID PRIMARY KEY,
    patient_card_id UUID REFERENCES patient_active_cards(patient_card_id) ON DELETE CASCADE,
    reported_at TIMESTAMP DEFAULT NOW(),
    barrier_type TEXT,
    description TEXT,
    resolved BOOLEAN DEFAULT FALSE,
    resolution_notes TEXT,
    resolved_at TIMESTAMP
);

CREATE TABLE side_effect_reports (
    report_id UUID PRIMARY KEY,
    patient_card_id UUID REFERENCES patient_active_cards(patient_card_id) ON DELETE CASCADE,
    reported_at TIMESTAMP DEFAULT NOW(),
    severity TEXT CHECK (severity IN ('Mild', 'Moderate', 'Severe')),
    description TEXT,
    reviewed_by UUID REFERENCES users(user_id),
    reviewed_at TIMESTAMP,
    action_taken TEXT
);
```

### Community Feedback
```sql
CREATE TABLE card_reviews (
    review_id UUID PRIMARY KEY,
    card_id UUID REFERENCES smart_cards(card_id) ON DELETE CASCADE,
    patient_id UUID REFERENCES patients(patient_id),

    rating INTEGER CHECK (rating BETWEEN 1 AND 5),
    comment TEXT,
    tags TEXT[],

    -- Eligibility (must have completed card)
    patient_card_id UUID REFERENCES patient_active_cards(patient_card_id),

    -- Outcome
    met_target BOOLEAN,
    adherence_rate DECIMAL(5,2),

    -- Moderation
    status TEXT CHECK (status IN ('Pending', 'Approved', 'Rejected')) DEFAULT 'Pending',
    moderated_by UUID REFERENCES users(user_id),
    moderated_at TIMESTAMP,

    created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE review_flags (
    flag_id UUID PRIMARY KEY,
    review_id UUID REFERENCES card_reviews(review_id) ON DELETE CASCADE,
    flagged_by UUID REFERENCES patients(patient_id),
    reason TEXT,
    created_at TIMESTAMP DEFAULT NOW()
);
```

## Integration Architecture

### EHR Integration (FHIR)

**Data Flows:**
1. **Patient Demographics** → FHIR Patient resource
2. **Diagnoses** → FHIR Condition resource
3. **Medications** → FHIR MedicationStatement resource
4. **Labs** → FHIR Observation resource
5. **Vitals** → FHIR Observation resource
6. **Prescriptions** → FHIR MedicationRequest resource

**Example: Creating Card from FHIR Data**
```
EHR writes prescription → FHIR MedicationRequest created
→ SMART Card System receives webhook
→ AI Service maps to card template
→ Draft card created for clinician review
→ Clinician approves
→ Card published to patient
```

### Drug Interaction Databases

Integrate with:
- **Micromedex** or **Lexicomp** for drug-drug interactions
- **FDA Drug Labels** for contraindications
- **RxNorm** for drug standardization

### Guideline Databases

Integrate with:
- **USPSTF** (Preventive Services)
- **ACC/AHA** (Cardiology)
- **ADA** (Diabetes)
- **KDIGO** (Kidney)
- **NICE** (UK Guidelines)

Sync quarterly to update evidence grades and recommendations.

## Security & Privacy

### Authentication & Authorization

**Roles:**
- **Patient**: View own cards, log adherence, submit reviews
- **Clinician**: View patient data, prescribe cards/decks, approve AI recommendations
- **Admin**: Manage card library, moderate reviews, system configuration

**Authentication:**
- OAuth 2.0 + OpenID Connect
- Multi-factor authentication (MFA) for clinicians
- Biometric authentication for patient app (fingerprint/face)

### Data Protection

- **Encryption at rest**: AES-256 for all databases
- **Encryption in transit**: TLS 1.3 for all API calls
- **PHI/PII**: Separate storage with enhanced access controls
- **Audit logging**: All access to patient data logged
- **Data retention**: 7-year minimum for medical records
- **Right to deletion**: GDPR/CCPA compliant patient data deletion

### HIPAA Compliance

- Business Associate Agreements (BAAs) with all vendors
- Regular security audits and penetration testing
- Incident response plan
- Access controls and role-based permissions
- Encrypted backups with 30-day retention

## Deployment Architecture

### Cloud Infrastructure (AWS Example)

```
Production Environment:
- Application Servers: ECS Fargate (auto-scaling)
- Database: RDS PostgreSQL (Multi-AZ)
- Cache: ElastiCache Redis (cluster mode)
- File Storage: S3 (versioned, encrypted)
- CDN: CloudFront for static assets
- Load Balancer: ALB with SSL termination
- Monitoring: CloudWatch + DataDog
- Logging: CloudWatch Logs + ELK stack

Staging Environment:
- Smaller instance sizes
- Single-AZ database
- Separate VPC

Development Environment:
- Docker Compose for local development
- Seed data for testing
```

### CI/CD Pipeline

```
Developer commits → GitHub
  ↓
GitHub Actions triggered
  ↓
  1. Run tests (unit + integration)
  2. Lint code
  3. Security scan (Snyk)
  4. Build Docker images
  ↓
Push to ECR
  ↓
Deploy to Staging (automatic)
  ↓
Run E2E tests
  ↓
Manual approval
  ↓
Deploy to Production (blue/green)
  ↓
Health checks
  ↓
Route traffic to new version
```

## Performance & Scalability

### Target Metrics

- **API Response Time**: <200ms (p95)
- **Page Load Time**: <2s (p95)
- **Database Query Time**: <50ms (p95)
- **Concurrent Users**: 10,000+
- **Daily Active Users**: 100,000+
- **Uptime**: 99.9%

### Optimization Strategies

1. **Caching**:
   - Card library cached in Redis (1-hour TTL)
   - Patient active cards cached (5-min TTL)
   - Community ratings cached (15-min TTL)

2. **Database Indexing**:
   - B-tree indexes on foreign keys
   - GIN indexes on JSONB and array fields
   - Partial indexes for common queries

3. **CDN**:
   - Static assets (images, CSS, JS) served from CloudFront
   - Geographic distribution for low latency

4. **Async Processing**:
   - AI recommendations processed asynchronously (queue-based)
   - Email/SMS notifications via SQS
   - Analytics aggregation via scheduled jobs

5. **Database Partitioning**:
   - Adherence logs partitioned by date (monthly)
   - Measurement logs partitioned by date
   - Archives moved to cold storage after 2 years

## Monitoring & Observability

### Key Metrics

**Application Metrics:**
- Request rate, error rate, latency (p50, p95, p99)
- AI recommendation generation time
- Card prescription rate
- Deck completion rate

**Business Metrics:**
- Daily/Monthly Active Users (DAU/MAU)
- Patient adherence rate (overall and per card)
- Clinician adoption rate
- Cards prescribed per day
- Deck completion rate
- Target achievement rate

**Infrastructure Metrics:**
- CPU, memory, disk usage
- Database connections, query performance
- Cache hit rate
- API gateway throttling

### Alerting

**Critical Alerts** (PagerDuty):
- Service down
- Database unavailable
- API error rate >5%
- Serious patient safety event reported

**Warning Alerts** (Slack):
- High latency (>500ms p95)
- Low cache hit rate (<80%)
- Failed background jobs

### Logging

**Structured Logging (JSON)**:
```json
{
  "timestamp": "2025-01-16T10:30:00Z",
  "level": "INFO",
  "service": "ai-service",
  "action": "generate_recommendation",
  "patient_id": "abc123",
  "duration_ms": 245,
  "cards_recommended": 5,
  "clinician_id": "doc456"
}
```

**Log Retention:**
- Application logs: 30 days (hot), 1 year (cold)
- Audit logs: 7 years
- Error logs: 1 year

## Future Enhancements

### Phase 8: Advanced Features
- Predictive analytics (identify patients at risk of non-adherence)
- Voice interface for hands-free logging
- Smart watch integration (auto-sync vitals)
- Multilingual support (Spanish, Chinese, etc.)
- Personalized timing recommendations (AI suggests best time of day)
- Social features (patient support groups, accountability partners)

### Phase 9: Research & Innovation
- Clinical trial integration (recruit patients for relevant studies)
- Real-world evidence generation (aggregate anonymized outcomes)
- Machine learning models for outcome prediction
- Genomics integration (pharmacogenomics for medication selection)

## Technology Stack Recommendations

**Backend:**
- Language: TypeScript (Node.js) or Python
- Framework: NestJS (Node) or FastAPI (Python)
- Database: PostgreSQL 15+
- Cache: Redis 7+
- Queue: AWS SQS or RabbitMQ
- Search: Elasticsearch (for advanced card search)

**Frontend:**
- Web: React + TypeScript
- Mobile: React Native (iOS + Android)
- State Management: Redux Toolkit or Zustand
- UI Library: Material-UI or Tailwind CSS

**AI/ML:**
- NLP: spaCy or Hugging Face Transformers
- ML Framework: scikit-learn or PyTorch
- LLM: OpenAI GPT-4 or Claude for NLP parsing

**DevOps:**
- Infrastructure as Code: Terraform
- Containers: Docker
- Orchestration: ECS Fargate or Kubernetes
- CI/CD: GitHub Actions
- Monitoring: DataDog or New Relic

**Testing:**
- Unit: Jest (JS) or pytest (Python)
- Integration: Supertest or pytest-django
- E2E: Cypress or Playwright
- Load Testing: k6 or Locust

---

This architecture provides a solid foundation for building the SMART Card Library system at scale while maintaining flexibility for future enhancements.
