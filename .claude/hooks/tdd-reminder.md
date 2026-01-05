# TDD Reminder Hook

This hook executes before writing implementation code to ensure TDD workflow is followed.

## Trigger
- Before using Write or Edit tools on implementation files (non-test files)

## Action

When about to write implementation code, CHECK:

1. **Does a test file exist for this code?**
   - Component: `__tests__/components/ComponentName.test.tsx`
   - Hook: `__tests__/hooks/useHookName.test.tsx`
   - API: `__tests__/lib/api/moduleName.test.ts`
   - Util: `__tests__/utils/utilName.test.ts`

2. **Has the test been written FIRST and is it FAILING?**
   - Tests must be written before implementation
   - Run `pnpm test` to verify test fails (🔴 RED)

3. **Are you writing minimal code to pass the test?**
   - Only add code needed for current test
   - Don't add features without tests

## Workflow Enforcement

**BEFORE writing implementation:**

```
❌ STOP if:
- No test file exists
- Test hasn't been written yet
- Test is not failing (RED)
- Writing code beyond what test requires

✅ PROCEED only if:
- Test file exists with failing test
- Test clearly defines expected behavior
- Writing minimal code to pass specific test
```

## Example

**Bad Flow (❌):**
```
User: "Create a LoginForm component"
Assistant: [Writes LoginForm.tsx directly] ❌ WRONG
```

**Good Flow (✅):**
```
User: "Create a LoginForm component"
Assistant:
  1. "I'll follow TDD. First, let me create the test file"
  2. Creates __tests__/components/LoginForm.test.tsx
  3. Writes failing test for first behavior
  4. Runs test → Confirms it fails (🔴 RED)
  5. Creates minimal LoginForm.tsx to pass test
  6. Runs test → Confirms it passes (🟢 GREEN)
  7. Repeats for next behavior
```

## Response Template

When user requests implementation without test:

> "Following TDD workflow. I'll create the test first to define expected behavior, then implement the minimal code to pass it."

Then proceed with RED-GREEN-REFACTOR cycle.

## Override

User can override with explicit instruction:
- "skip tdd for now"
- "write without tests" (not recommended)

Otherwise, TDD is MANDATORY.
