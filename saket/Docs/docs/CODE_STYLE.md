# CODE STYLE

## 1. General rules

- Prefer TypeScript.
- Use strict typing.
- Keep functions small.
- Use descriptive names.
- Avoid unnecessary abstractions.
- Prefer composition.
- Keep business logic out of UI components.
- Validate at API boundaries.

## 2. Naming

```ts
// Components
IncidentCard.tsx

// Functions
calculatePriority()

// Variables
incidentStatus

// Constants
MAX_INCIDENT_DESCRIPTION_LENGTH

// Types
IncidentStatus
CreateIncidentInput
```

## 3. TypeScript

Prefer:

```ts
type IncidentStatus =
  | "SUBMITTED"
  | "VALIDATED"
  | "ASSIGNED"
  | "IN_PROGRESS"
  | "RESOLVED"
  | "CLOSED";
```

Avoid:

```ts
const status: any = input.status;
```

## 4. Functions

Prefer:

```ts
function canAssignIncident(
  role: UserRole,
  incidentStatus: IncidentStatus,
): boolean {
  return role === "COORDINATOR" &&
    incidentStatus === "PRIORITIZED";
}
```

Avoid giant functions containing validation, database access, notification and UI logic.

## 5. API handlers

Keep handlers thin:

```text
handler
  ↓
parse/validate
  ↓
service
  ↓
repository
  ↓
response
```

## 6. Error handling

Use stable error codes:

```text
VALIDATION_ERROR
UNAUTHORIZED
FORBIDDEN
NOT_FOUND
CONFLICT
RATE_LIMITED
INTERNAL_ERROR
```

Never expose stack traces to end users.

## 7. React

Prefer:
- Small components
- Custom hooks for reusable behavior
- Controlled forms where appropriate
- Server state separated from UI state
- Accessible semantic HTML

Avoid:
- Huge page components
- Deep prop drilling
- Duplicate API calls
- Business rules scattered across components

## 8. Comments

Comment **why**, not obvious **what**.

Good:

```ts
// Keep this idempotent because mobile clients may retry after a timeout.
```

Bad:

```ts
// Set status to submitted.
incident.status = "SUBMITTED";
```

## 9. Environment variables

Example:

```text
DATABASE_URL=
AUTH_SECRET=
MAP_TILE_URL=
SMS_PROVIDER_KEY=
```

Never commit `.env` files containing secrets.

## 10. Formatting

Use one automated formatter across the repository.

Recommended:
- Prettier
- ESLint
- TypeScript strict mode

## 11. Commit conventions

```text
feat: add citizen incident form
fix: validate latitude bounds
refactor: split notification adapter
test: add incident lifecycle tests
docs: update architecture
chore: update dependencies
```

## 12. Pull request quality

A PR should answer:

```text
What changed?
Why?
Which user flow changed?
How was it tested?
Are there security implications?
Are docs updated?
```
