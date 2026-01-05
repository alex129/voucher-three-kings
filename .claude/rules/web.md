---
path: apps/web
---

# Web Application

Next.js 15 frontend for the Fluxput field support platform.

## Tech Stack

- **Framework**: Next.js 15 (App Router) + React 19
- **UI**: Tailwind CSS 4 + shadcn/ui
- **Data**: TanStack Query
- **Auth**: Better Auth (HTTP-only cookies)
- **Forms**: React Hook Form + Zod
- **Testing**: Vitest + React Testing Library + Storybook
- **i18n**: next-intl

## Critical Rules

1. **i18n**: NEVER hardcode text → `useTranslations()` from next-intl
2. **WCAG 2.2**: ALL components must be accessible (Level AA)
3. **TDD**: Test first (RED → GREEN → REFACTOR)
4. **Descriptive Naming**: Clear, self-documenting names (no `data`, `info`, `temp`)
5. **Shared Package**: Import from `@packages/shared` main entry only
6. **Auth**: Always `credentials: 'include'` for auth endpoints
7. **Quality Checks**: ALWAYS run `pnpm ts-check` and `pnpm biome check` before finishing any task

## Project Structure

```
src/
├── app/[locale]/         # i18n routes (pages here)
├── components/ui/        # shadcn/ui only
├── features/{name}/      # Feature modules at ROOT
│   ├── components/       # Component + .stories + .test
│   ├── hooks/
│   └── api/
├── i18n/                 # i18n config
├── messages/{locale}/    # Translations by feature
└── lib/                  # Utils, API client
```

## Naming

| Type | Pattern | Example |
|------|---------|---------|
| Components | PascalCase | `LoginForm.tsx` |
| Hooks | useCamelCase | `useAuth.ts` |
| API | kebab-case.api | `auth.api.ts` |
| Tests | Name.test | `LoginForm.test.tsx` |
| Stories | Name.stories | `LoginForm.stories.tsx` |

## Commands

```bash
pnpm dev          # Dev server
pnpm build        # Production build
pnpm test         # Run tests
pnpm storybook    # Storybook dev
pnpm ts-check     # Type check
pnpm biome check  # Lint and format check
```

## Pre-completion Checklist

Before finishing any task, ALWAYS run:
```bash
pnpm ts-check              # Verify no TypeScript errors
pnpm biome check apps/web  # Verify no lint errors
```

## Agents

For detailed guidance, use the specialized agents:

- **nextjs-architecture-expert**: Architecture decisions, Server/Client Components, data fetching, routing
- **frontend-practices**: i18n, WCAG 2.2, TDD workflow, code conventions, code reviews
