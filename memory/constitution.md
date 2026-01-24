# Spec Kit Quality Constitution

## Core Principles

### I. Requirements Quality (NON-NEGOTIABLE)

All functional requirements MUST achieve minimum quality scores across scientifically-proven metrics to ensure implementability and testability.

**Mandatory Components**:

Every functional requirement MUST include all 7 components:

1. **TRIGGER** (when/if): Condition that initiates the requirement
   - Examples: `WHEN user clicks`, `IF validation fails`, `GIVEN authenticated session`

2. **ACTOR** (who): Entity performing the action
   - Examples: `the system`, `the user`, `the admin`, `the service`

3. **ACTION** (what): Action using strong modal verbs (MUST/SHALL/SHOULD)
   - Examples: `MUST validate`, `MUST calculate`, `MUST display`, `MUST store`

4. **OUTCOME** (result): Observable result of the action
   - Examples: `RETURN JSON`, `DISPLAY message`, `STORE data`, `EXIT with code`

5. **OBSERVABLE** (verify): Elements that can be tested/verified
   - Examples: status codes, response formats, error messages, log entries

6. **CONSTRAINT** (limits): Quantifiable constraints
   - Examples: `within 500ms`, `>= 0`, `ISO 8601 format`, `max 1000 records`

7. **BOUNDARY** (must not): Explicit boundaries and prohibited behaviors
   - Examples: `MUST NOT proceed if`, `MUST NOT store invalid`, `MUST NOT expose`

**Quality Gates**:

- **Overall Score**: Minimum 0.70 (Good)
- **Semantic Score**: Minimum 0.60 (outcome_presence, trigger_presence)
- **Testability Score**: Minimum 0.60 (constraint_density, negative_space_coverage)
- **Behavioral Score**: Minimum 0.50 (observability_score, transition_completeness)

**Atomicity Rule**:

- One testable statement per functional requirement
- If a requirement contains "AND", split into separate atomic requirements
- Each requirement must be independently testable
- Group related atomic requirements using series notation (FR-001a, FR-001b, etc.)

**Pattern Template**:

```
[TRIGGER] the [ACTOR] MUST [ACTION] [OBJECT] and [OUTCOME] [OBSERVABLE]. [CONSTRAINT]. [BOUNDARY].
```

**Example**:

✅ HIGH QUALITY (score: 0.85):
```
FR-001a: WHEN a user submits a registration form, the system MUST validate
the email format against RFC 5322 standard and RETURN a JSON response with
`isValid` (boolean) and `errorMessage` (string) fields within 200ms.
The system MUST NOT store invalid email addresses.
```

❌ LOW QUALITY (score: 0.35):
```
FR-001: System must validate email addresses.
```

**Validation Enforcement**:

- All specs MUST be validated using `specify metrics-scan` before proceeding to planning
- Specs scoring below 0.70 overall MUST be revised
- Specs with semantic, testability, or behavioral scores below 0.50 MUST be rejected
- Run `specify metrics-scan --spec <path>` to validate quality

### II. Specification Structure

All specifications MUST follow the standard template structure:

- **Mandatory sections**: User Scenarios & Testing, Requirements, Success Criteria
- **Optional sections**: Only include when relevant (remove if not applicable)
- **Technology-agnostic**: No frameworks, languages, APIs, or implementation details
- **Stakeholder-focused**: Written for business stakeholders, not developers

### III. Testability First

Every requirement and success criterion must be independently testable:

- Each functional requirement maps to specific test cases
- Success criteria must be measurable without implementation details
- Acceptance scenarios must use Given-When-Then format
- Edge cases must be explicitly identified

### IV. Clarity and Completeness

Requirements must be unambiguous and complete:

- Maximum 3 `[NEEDS CLARIFICATION]` markers per spec
- Informed assumptions documented in Assumptions section
- Edge cases identified and handled
- Dependencies and constraints explicitly stated

### V. Iterative Refinement

Specifications evolve through structured phases:

1. **Specify** (`/speckit.specify`): Create initial spec with quality validation
2. **Clarify** (`/speckit.clarify`): Resolve remaining questions (max 3)
3. **Analyze** (`/speckit.analyze`): Cross-artifact consistency check
4. **Plan** (`/speckit.plan`): Technical implementation plan
5. **Tasks** (`/speckit.tasks`): Actionable task breakdown
6. **Implement** (`/speckit.implement`): Execute tasks

### VI. Quality Automation

Quality checks are automated and deterministic:

- Deterministic metrics run on every spec change
- 31 scientifically-proven metrics across 6 categories:
  - Readability (25%): Flesch Reading Ease, Grade Level, Fog Index
  - Structure (35%): Atomicity, Completeness, Modal Verb Distribution
  - Cognitive (25%): Sentence Length, Concept Density, Complexity
  - Semantic (5%): Actor, Action, Object, Outcome, Trigger presence
  - Testability (5%): Constraint Density, Negative Space Coverage
  - Behavioral (5%): Observability, Transition Completeness
- Automated reports identify specific improvement areas
- CI/CD integration with configurable thresholds

## Research Foundation

All quality metrics are validated against peer-reviewed research:

- **Visual Narrator** (Lucassen et al. 2017, 421 citations): Semantic role extraction
- **Semantic Role Labeling** (Gildea & Jurafsky 2002, 2,891 citations): Actor-action-object patterns
- **Statechart Generation** (Harel et al. 2005): Behavioral simulatability
- **PIE Testability Model** (Voas & Miller 1995): Observability scoring
- **IEEE 830-1998, ISO 29148:2018**: Requirements engineering standards
- **Cognitive Load Theory** (Sweller 1988, Miller 1956): Working memory limits

Research shows 40% fewer implementation defects with high-quality requirements.

## Governance

**Constitution Enforcement**:

- This constitution supersedes all other practices
- All specifications must comply before proceeding to planning
- Quality gates are automated and non-negotiable
- Amendments require documentation, approval, and migration plan

**Validation Commands**:

```bash
# Validate single spec
specify metrics-scan --spec specs/001-feature/spec.md

# Validate all specs
specify metrics-scan --all

# CI/CD quality gate
specify metrics-scan --all --threshold 0.70 --fail-below-threshold
```

**Non-Negotiable Standards**:

- Requirements below 0.70 overall score: MUST REVISE
- Missing triggers or outcomes: MUST ADD
- Compound requirements: MUST SPLIT
- Vague constraints: MUST QUANTIFY
- Missing boundaries: MUST SPECIFY

**Version**: 1.0.0 | **Ratified**: 2026-01-24 | **Last Amended**: 2026-01-24
