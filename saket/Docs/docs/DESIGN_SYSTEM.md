# DESIGN SYSTEM

## 1. Design goals

SANKET should feel:

- Trustworthy
- Calm
- Clear
- Operational
- Accessible
- Government/public-service oriented without pretending to be an official government service

## 2. Visual hierarchy

```text
CRITICAL
  ↓
Primary action
  ↓
Current status
  ↓
Important supporting information
  ↓
Secondary information
```

## 3. Color semantics

Use semantic tokens rather than hard-coded colors:

```text
--color-primary
--color-background
--color-surface
--color-text
--color-muted
--color-success
--color-warning
--color-danger
--color-info
--color-border
```

Do not rely on color alone to communicate severity.

Example:

```text
HIGH
[icon] [label] [reason]
```

rather than only a red dot.

## 4. Typography

Recommended hierarchy:

```text
Display → page title
H1 → main section
H2 → subsection
Body → normal content
Caption → metadata
Mono → incident IDs / technical values
```

## 5. Core components

### Button

Variants:
- Primary
- Secondary
- Destructive
- Ghost

### Incident card

```text
┌───────────────────────────────┐
│ HIGH   FLOOD        5 min ago │
│ SKT-2026-004821               │
│ 4 people affected             │
│ Medical + evacuation          │
│                              │
│ [Open incident]              │
└───────────────────────────────┘
```

### Status badge

```text
SUBMITTED
VALIDATED
ASSIGNED
IN PROGRESS
RESOLVED
CLOSED
```

### Timeline

```text
● Submitted
│
● Validated
│
● Team assigned
│
● Responder acknowledged
│
● Resolved
```

## 6. Dashboard layout

```text
┌─────────────────────────────────────────────┐
│ Header                                      │
├──────────────┬──────────────────────────────┤
│ Sidebar      │ KPI cards                    │
│              ├──────────────────────────────┤
│              │ Map                          │
│              │                              │
│              ├──────────────────────────────┤
│              │ Incident queue               │
└──────────────┴──────────────────────────────┘
```

## 7. Citizen report UX

Use progressive disclosure:

```text
Step 1 — What happened?
Step 2 — Where?
Step 3 — Who needs help?
Step 4 — What is needed?
Step 5 — Review
Step 6 — Submitted
```

## 8. Accessibility

Target:
- Semantic HTML
- Keyboard support
- Visible focus
- Minimum readable text sizes
- Form labels
- Inline errors
- Screen-reader announcements for important status changes
- Reduced-motion support

## 9. Responsive behavior

```text
Desktop:
Sidebar + map + queue

Tablet:
Collapsible sidebar + map + queue

Mobile:
Bottom navigation
Map/list toggle
Single-column incident details
Large emergency action
```

## 10. Content guidelines

Use direct language:

Good:
> “Report received. Reference: SKT-2026-004821.”

Avoid:
> “Your request has been successfully processed through our advanced intelligent emergency ecosystem.”

Never imply a simulated service is a live emergency service.
