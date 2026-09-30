# AGENTS.md — Development Agent Rules

## 1. Project mission

You are contributing to SANKET, a disaster-response coordination prototype. Prefer reliability, clarity, accessibility, security and explainability over unnecessary complexity.

## 2. Before changing code

1. Read the relevant documentation.
2. Identify the affected user flow.
3. Check existing types/components/services.
4. Avoid duplicating existing logic.
5. Consider security and failure states.

## 3. Architectural rules

Use:

```text
UI
 ↓
API / Controller
 ↓
Service
 ↓
Repository
 ↓
Database
```

Do not place business logic directly inside UI components.

## 4. AI/automation rules

If adding an AI feature:

- Do not let the model autonomously dispatch emergency services.
- Treat model output as advisory.
- Validate structured outputs.
- Store an explanation or reason code where appropriate.
- Add deterministic fallback behavior.
- Never fabricate live emergency information.

## 5. Data rules

- Collect only necessary personal data.
- Never log raw sensitive data unnecessarily.
- Use IDs instead of exposing internal database identifiers.
- Validate all client-controlled fields server-side.

## 6. UI rules

- Use existing design-system components.
- Keep forms short.
- Show clear errors.
- Provide loading states.
- Provide empty states.
- Never hide a critical status change behind animation.

## 7. Testing rules

Every feature should include:
- Happy-path test
- Validation test
- Authorization test if relevant
- Failure-state test

## 8. Git rules

Commit style:

```text
feat: add incident creation
fix: prevent duplicate assignment
test: cover priority rules
docs: update API flow
refactor: extract notification service
```

Keep commits focused.

## 9. Pull request checklist

```text
[ ] Feature works locally
[ ] Tests added/updated
[ ] No secrets committed
[ ] Docs updated
[ ] Accessibility considered
[ ] Error states handled
[ ] Security implications reviewed
```
