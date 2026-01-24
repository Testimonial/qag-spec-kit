# Feature Specification: [FEATURE NAME]

**Feature Branch**: `[###-feature-name]`  
**Created**: [DATE]  
**Status**: Draft  
**Input**: User description: "$ARGUMENTS"

## User Scenarios & Testing *(mandatory)*

<!--
  IMPORTANT: User stories should be PRIORITIZED as user journeys ordered by importance.
  Each user story/journey must be INDEPENDENTLY TESTABLE - meaning if you implement just ONE of them,
  you should still have a viable MVP (Minimum Viable Product) that delivers value.
  
  Assign priorities (P1, P2, P3, etc.) to each story, where P1 is the most critical.
  Think of each story as a standalone slice of functionality that can be:
  - Developed independently
  - Tested independently
  - Deployed independently
  - Demonstrated to users independently
-->

### User Story 1 - [Brief Title] (Priority: P1)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently - e.g., "Can be fully tested by [specific action] and delivers [specific value]"]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]
2. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 2 - [Brief Title] (Priority: P2)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

### User Story 3 - [Brief Title] (Priority: P3)

[Describe this user journey in plain language]

**Why this priority**: [Explain the value and why it has this priority level]

**Independent Test**: [Describe how this can be tested independently]

**Acceptance Scenarios**:

1. **Given** [initial state], **When** [action], **Then** [expected outcome]

---

[Add more user stories as needed, each with an assigned priority]

### Edge Cases

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right edge cases.
-->

- What happens when [boundary condition]?
- How does system handle [error scenario]?

## Requirements *(mandatory)*

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right functional requirements.
-->

### Functional Requirements

<!--
  CRITICAL: Write requirements that score high on quality metrics.
  Each requirement MUST include these components for high scores:

  1. TRIGGER (when/if): WHEN user clicks, IF validation fails, GIVEN condition
  2. ACTOR (who): the system, the user, the admin
  3. ACTION (what): MUST validate, MUST calculate, MUST display
  4. OUTCOME (result): RETURN JSON, DISPLAY message, STORE data, EXIT with code
  5. OBSERVABLE (verify): status codes, formats, error messages, logs
  6. CONSTRAINT (limits): within 500ms, >= 0, ISO 8601 format, max 100 chars
  7. BOUNDARY (must not): MUST NOT proceed, MUST NOT store, MUST NOT allow

  ATOMIC RULE: One testable statement per FR. Split compound requirements.

  Good pattern: [TRIGGER] the [ACTOR] MUST [ACTION] [OBJECT] and [OUTCOME] [OBSERVABLE]. [CONSTRAINT]. [BOUNDARY].
-->

#### [Feature Group 1] (FR-001 series)

- **FR-001a**: WHEN a user submits the form, the system MUST validate the email format against RFC 5322 standard and RETURN a validation result object with `isValid` (boolean) and `errorMessage` (string) fields.

- **FR-001b**: The validation process MUST complete within 200ms per request.

- **FR-001c**: IF the email format is invalid, the system MUST DISPLAY an error message "Please enter a valid email address" and return HTTP status code 400.

- **FR-001d**: The system MUST NOT store or process invalid email addresses.

#### [Feature Group 2] (FR-002 series)

- **FR-002a**: WHEN a user successfully logs in, the system MUST create a session token and RETURN it in the response body as a JSON object containing `token` (string), `expiresAt` (ISO 8601 timestamp), and `userId` (integer).

- **FR-002b**: Session tokens MUST be valid for exactly 24 hours from creation time.

- **FR-002c**: The system MUST NOT generate session tokens for unverified user accounts.

#### [Feature Group 3] (FR-003 series)

- **FR-003a**: Users MUST be able to reset their password by providing their email address.

- **FR-003b**: WHEN a password reset is requested, the system MUST send a reset link to the provided email address within 30 seconds and LOG the event with timestamp, user ID, and IP address.

- **FR-003c**: Password reset links MUST expire after 1 hour.

- **FR-003d**: The system MUST NOT allow password reset for locked or deleted accounts.

<!--
  Example of atomic requirements for complex features:
  Instead of: "System MUST validate data, store it, and send confirmation"
  Split into:
    - FR-004a: System MUST validate data
    - FR-004b: System MUST store validated data
    - FR-004c: System MUST send confirmation
-->

*Example of marking unclear requirements:*

- **FR-005**: The system MUST authenticate users via [NEEDS CLARIFICATION: auth method not specified - email/password, SSO, OAuth2?]
- **FR-006**: User data MUST be retained for [NEEDS CLARIFICATION: retention period not specified - 90 days, 1 year, indefinitely?]

### Key Entities *(include if feature involves data)*

- **[Entity 1]**: [What it represents, key attributes without implementation]
- **[Entity 2]**: [What it represents, relationships to other entities]

## Success Criteria *(mandatory)*

<!--
  ACTION REQUIRED: Define measurable success criteria.
  These must be technology-agnostic and measurable.
-->

### Measurable Outcomes

- **SC-001**: [Measurable metric, e.g., "Users can complete account creation in under 2 minutes"]
- **SC-002**: [Measurable metric, e.g., "System handles 1000 concurrent users without degradation"]
- **SC-003**: [User satisfaction metric, e.g., "90% of users successfully complete primary task on first attempt"]
- **SC-004**: [Business metric, e.g., "Reduce support tickets related to [X] by 50%"]
