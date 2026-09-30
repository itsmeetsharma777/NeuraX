# APP FLOW — Application & User Journeys

## 1. Overall application flow

```mermaid
flowchart TD
    START([Open SANKET]) --> ROLE{Choose interface}
    ROLE --> CIT[Citizen]
    ROLE --> RESP[Responder]
    ROLE --> ADMIN[Coordinator/Admin]

    CIT --> REPORT[Create Report]
    REPORT --> LOCATION[Capture / Select Location]
    LOCATION --> DETAILS[Enter Incident Details]
    DETAILS --> REVIEW[Review]
    REVIEW --> SUBMIT[Submit]
    SUBMIT --> TRACK[Track Incident]

    RESP --> LOGIN[Responder Login]
    LOGIN --> DASH[Dashboard]
    DASH --> MAP[Incident Map]
    DASH --> LIST[Incident Queue]
    LIST --> DETAIL[Incident Detail]
    MAP --> DETAIL
    DETAIL --> ASSIGN[Assign Team]
    ASSIGN --> UPDATE[Update Status]
    UPDATE --> CLOSE[Resolve / Close]

    ADMIN --> ALOGIN[Admin Login]
    ALOGIN --> ADASH[Operations Dashboard]
    ADASH --> TEAMS[Manage Teams]
    ADASH --> RES[Manage Resources]
    ADASH --> AUDIT[Audit Logs]
```

## 2. Citizen flow

```text
Landing
  ↓
Emergency / Report
  ↓
Disaster type
  ↓
Location
  ↓
People affected
  ↓
Immediate needs
  ↓
Contact consent
  ↓
Review
  ↓
Submit
  ↓
Reference ID
  ↓
Track status
```

## 3. Responder flow

```text
Login
 ↓
Dashboard
 ↓
Filter / Map
 ↓
Open incident
 ↓
Review evidence
 ↓
Assign team
 ↓
Acknowledge
 ↓
In progress
 ↓
Add action note
 ↓
Resolve
```

## 4. USSD simulator flow

```mermaid
stateDiagram-v2
    [*] --> MainMenu
    MainMenu --> SOS
    MainMenu --> Report
    MainMenu --> Status
    MainMenu --> Help

    Report --> Type
    Type --> Location
    Location --> People
    People --> Needs
    Needs --> Confirm
    Confirm --> Submitted
    Submitted --> MainMenu

    Status --> EnterID
    EnterID --> StatusResult
    StatusResult --> MainMenu
```

## 5. Incident state machine

```mermaid
stateDiagram-v2
    [*] --> DRAFT
    DRAFT --> SUBMITTED
    SUBMITTED --> VALIDATED
    SUBMITTED --> REJECTED
    VALIDATED --> PRIORITIZED
    PRIORITIZED --> ASSIGNED
    PRIORITIZED --> DUPLICATE
    ASSIGNED --> IN_PROGRESS
    IN_PROGRESS --> ESCALATED
    ESCALATED --> IN_PROGRESS
    IN_PROGRESS --> RESOLVED
    RESOLVED --> CLOSED
    CLOSED --> [*]
```

## 6. Navigation map

```text
PUBLIC
├── Home
├── Report Emergency
├── Track Report
├── Safety Information
└── USSD Simulator

RESPONDER
├── Dashboard
├── Live Map
├── Incidents
│   ├── New
│   ├── Assigned
│   ├── In Progress
│   └── Resolved
├── Teams
└── Profile

ADMIN
├── Operations
├── Incidents
├── Teams
├── Resources
├── Audit Logs
└── System Settings
```

## 7. Error flows

### Missing location

```text
Submit
 ↓
Location missing
 ↓
Explain why location helps
 ↓
Allow map selection
 ↓
Retry
```

### Duplicate report

```text
New report
 ↓
Similarity check
 ↓
Possible duplicate
 ↓
Show nearby matching incidents
 ↓
Citizen confirms
 ├── Same incident → attach information
 └── Different → create new incident
```

### Network failure

```text
Submit
 ↓
Network unavailable
 ↓
Save local draft
 ↓
Show pending state
 ↓
Retry automatically/manual
```
