# Feature Matrix

## Shared features across OTTO and Tucker

| Feature | OTTO | Tucker Pool CRM | Shared in core? |
| --- | --- | --- | --- |
| Customer management | Yes | Yes | Yes |
| Contact records | Yes | Yes | Yes |
| Job / work order tracking | Yes | Yes | Yes |
| Invoices and billing | Yes | Yes | Yes |
| Payments and ledger | Yes | Yes | Yes |
| Scheduling / dispatch | Yes | Yes | Yes |
| Photo / file intake | Yes | Yes | Yes |
| Bilingual UX | Yes | Yes | Yes |
| Notes and follow-ups | Yes | Yes | Yes |
| Dashboard reporting | Yes | Yes | Yes |
| Search / lookup | Yes | Yes | Yes |
| Data export/import | Yes | Yes | Yes |
| HR / staff data | Potentially | Possibly | Yes |
| Admin settings | Yes | Yes | Yes |

## Brand-specific features

### OTTO-specific
- plumbing work order context
- service category language for plumbing operations
- plumbing billing conventions
- field operations workflow patterns

### Tucker-specific
- pool service categories
- maintenance schedules and recurring service logic
- pool customer relationship flows
- bilingual pool-service context

## Core product recommendation

The default SaaS CRM should support both brands through configuration overlays. Features unique to each business remain in the brand layer rather than the central architecture.

---

## Verified source audit — 2026-10-28

**IMPORTANT: The feature table above is a target-state planning table, NOT a verified inventory of working features in both repositories. In particular, each Tucker "Yes" above is unverified as an implemented CRM feature on `main`. Do not use that table to certify migration parity.**

Evidence reviewed:
- [OTTO README](https://github.com/ejnburrows-rgb/otto/blob/main/README.md), [OTTO current control rules](https://github.com/ejnburrows-rgb/otto/blob/main/docs/REPO-CONTROL.md), tests and repository layout.
- [Tucker current entry point](https://github.com/ejnburrows-rgb/tucker-pool-crm/blob/main/src/App.tsx), [simulated login](https://github.com/ejnburrows-rgb/tucker-pool-crm/blob/main/src/components/LoginPage.tsx), [pool-services sections](https://github.com/ejnburrows-rgb/tucker-pool-crm/tree/main/src/sections), package and repository trees.
- Tucker's `main`, `fix/viktor-bug-fixes` and available repository history, including the initial commit.

| Capability | OTTO source evidence | Tucker current `main` evidence | Migration decision |
| --- | --- | --- | --- |
| Customers, contacts, jobs, estimates, invoices and payment tracking | Documented as implemented; direct end-to-end tests not rerun for this audit | **Missing as verified working CRM screens**; current `App.tsx` renders a marketing site | Build shared models from verified OTTO behavior; do not claim Tucker parity |
| Scheduling, dispatch and field workflow | Documented in OTTO README/control rules; tests exist | Marketing text describes scheduling; operational scheduling UI not found | Carry OTTO patterns into shared core; pool-specific scheduling rules require real source evidence |
| HR, payroll, crew hours, policy acknowledgments | Documented OTTO capability | **Missing as verified implementation** | Preserve from OTTO; do not silently drop |
| Files, photos, PDF/plan intake, OCR and backups | Documented OTTO capability | Images exist for marketing; customer-record attachment workflow not verified | Preserve actual OTTO workflow; do not mistake marketing assets for file intake |
| Bilingual interface | Documented OTTO capability | Some bilingual marketing claims; full bilingual CRM parity not verified | Require hands-on English/Spanish testing |
| Offline-first persistent business records | OTTO documents IndexedDB as active and localStorage as existing mirror | Current Tucker UI does not demonstrate persistent CRM records | Preserve working OTTO persistence; require explicit data-safety design before migration |
| Pool services and brand-specific presentation | OTTO is plumbing-specific | Pool service categories, imagery, marketing layout and login-style presentation exist | Reuse Tucker's **actual** available brand assets and service vocabulary, subject to owner approval |
| Authentication and user access | OTTO's current local profile selection is not internet-grade multi-tenant authentication | Tucker login calls `onLogin` after a delay, without password verification | **Do not reuse either as secure SaaS tenant authentication** |
| SaaS multi-tenant isolation | Not verified | Not verified | **Missing**: design and test before any real customer data is hosted |

**Security hold:** [Tucker's Supabase client helper](https://github.com/ejnburrows-rgb/tucker-pool-crm/blob/main/src/lib/supabase/server.ts) references `VITE_SUPABASE_SERVICE_ROLE_KEY`. A service-role secret must never be exposed through a browser-bundled `VITE_` variable. No actual key value was inspected or published in this audit. Treat configuration and exposed-key rotation as separate security checks if this variable was ever populated.

**Migration acceptance gate:** for each business feature, identify actual source files, record creation/edit/deletion behavior, persistence and access behavior, photos/documents, English/Spanish, offline handling, and a user-clickable test. Leave a feature **missing/not verified** until demonstrated. No customer data should be copied during structural work.
