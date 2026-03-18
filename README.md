# Care Plan Dashboard

A React + TypeScript care coordination dashboard for dialysis teams. The app models patient-centric recurring and ad-hoc tasks, tolerates partial backend failures, and supports optimistic task status updates with rollback.

## What makes this version stronger

- Shift handover summary that surfaces priority patients and role queues.
- Persistent filters so reviewers can refresh without losing context.
- Error boundary and guarded browser storage for safer runtime behavior.
- GitHub Actions CI plus GitHub Pages deployment workflow.
- Relative Vite asset paths so the app deploys cleanly from a GitHub repository page.

## Why Zustand

I used Zustand because this assignment needs a compact state layer that can:

- hold cross-cutting UI state such as filters, toasts, and dashboard loading;
- perform optimistic writes without heavy reducer boilerplate;
- stay easy to test at the store level.

React Query would also fit server synchronization well, but for this dashboard and its custom optimistic rollback rules, Zustand keeps the flow easier to reason about.

## Data Contracts

Defined in `src/types/contracts.ts`:

- `PatientDTO`: patient identity and summary details.
- `TaskDTO`: task metadata including `category`, `assignedRole`, `status`, and optional backend fields like `notes`, `assigneeName`, and `dueDate`.
- `CreateTaskInput` and `UpdateTaskInput`: write contracts for the mocked API.
- `DashboardFilters`, `ToastMessage`, and `DashboardStats`: UI-level contracts.

## Run Locally

```bash
npm install
npm run dev
```

## Deploy to GitHub Pages

1. Push this project to a GitHub repository.
2. In GitHub, open `Settings > Pages`.
3. Set the source to `GitHub Actions`.
4. Push to `main`.
5. After the workflow completes, GitHub will publish the site and give you a live URL.

The deployment workflow is already included in `.github/workflows/deploy.yml`.

## Test

```bash
npm run test
```
