# Migration Plan

## Mission

Create one canonical SaaS CRM foundation that preserves the operational value of OTTO and Tucker while removing duplication and reducing portfolio clutter.

## Source repos

### OTTO
- `ejnburrows-rgb/otto`
- Active migration source for advanced operational workflows and business logic

### Tucker Pool CRM
- `ejnburrows-rgb/tucker-pool-crm`
- Active migration source for bilingual service-business workflow patterns and customer management logic

## Migration phases

### Phase 1 — audit feature overlap
Identify the features that are shared across both systems:

- customer management
- job or work-order tracking
- payments/invoices
- lead intake
- scheduling
- notes and interactions
- file attachments
- search and dashboards
- bilingual UI

### Phase 2 — define canonical domain models
Create shared domain types such as:

- `Customer`
- `Contact`
- `Job`
- `Estimate`
- `Invoice`
- `Payment`
- `ScheduleEntry`
- `Employee`
- `Document`
- `Note`
- `FollowUp`

### Phase 3 — build core modules
Move the reusable logic into the canonical product:

- customer model and CRUD
- service job lifecycle
- billing and ledger
- scheduling and dispatch
- team records
- file management and attachments
- notes and communications
- search and filtering

### Phase 4 — build brand overlays
Create overlays for:

- `brands/otto`
- `brands/tucker`

These overlays include:

- branding and theme
- labels and terminology
- workflow differences
- service categories
- form defaults
- pricing rules

### Phase 5 — verify parity
Validate that the product still supports the key business flows previously found in OTTO and Tucker:

- create customer
- schedule job
- track payment
- create estimate and invoice
- add photos and notes
- bilingual switching
- admin configuration

### Phase 6 — archive legacy repos
Once the product is stable, archive the original system repos as reference material instead of leaving them as active product truth.

## Rules

- Preserve real functionality first.
- Do not delete active business data.
- Do not keep duplicate app logic in two places.
- Keep brand-specific logic in brand config rather than in the core.
- Only archive after migration parity is validated.

---

## Verified portfolio and safe execution update — 2026-10-28

GitHub metadata and source READMEs/entry points were inspected for the 19 repositories owned by `ejnburrows-rgb`. **No repository was archived, renamed, made private/public, or deleted as part of this audit.** The classification below is a preservation decision, not an assertion of deployment health.

| Repository | Classification and present action |
| --- | --- |
| [nbo-saas-crm](https://github.com/ejnburrows-rgb/nbo-saas-crm) | **Canonical CRM home.** Already exists; currently documentation foundation, not a working SaaS app. Reuse it. |
| [otto](https://github.com/ejnburrows-rgb/otto) | **Active operational CRM and migration source.** Keep running; preserve full working behavior and history. Do not archive after a paper-only migration. |
| [tucker-pool-crm](https://github.com/ejnburrows-rgb/tucker-pool-crm) | **Branded pool-service source, currently marketing-oriented code.** Keep; operational CRM capabilities claimed by README are not demonstrated by current main. |
| [client-project-starter](https://github.com/ejnburrows-rgb/client-project-starter) | **Existing NBO public marketing website.** Keep; reuse rather than create duplicate `nbo-marketing`. Confirm live dependencies before renaming. |
| [nbo-starter-template](https://github.com/ejnburrows-rgb/nbo-starter-template) | **Public starter scaffold.** Already exists; keep rather than recreate. |
| [otto-plumbing-site](https://github.com/ejnburrows-rgb/otto-plumbing-site) | **Separate operational business website.** Keep its public customer-intake and deployment path. |
| [cartilla-de-gretel](https://github.com/ejnburrows-rgb/cartilla-de-gretel) | **Separate active education product.** Protect; never archive merely because it is outside the CRM. |
| [lany-books-web](https://github.com/ejnburrows-rgb/lany-books-web) | **Separate Gretel/publisher storefront.** Protect; never archive solely for portfolio tidiness. |
| [VD-](https://github.com/ejnburrows-rgb/VD-) | **Separate cultural/education product.** Keep; actual business use must be checked before any archival suggestion. |
| [Locks](https://github.com/ejnburrows-rgb/Locks) | **Client/website work; README says pre-production.** Keep until owner confirms it is retired. |
| [dbarrera-y-mas](https://github.com/ejnburrows-rgb/dbarrera-y-mas) | **Client/site work.** Keep until owner confirms use. |
| [Command-Center-](https://github.com/ejnburrows-rgb/Command-Center-) | **Internal command center; presently PUBLIC despite README saying private.** Flag for owner-approved privacy review. Do not change access automatically. |
| [dev-firm-compass](https://github.com/ejnburrows-rgb/dev-firm-compass) | **Internal operations, already PRIVATE.** Keep private. |
| [db-backups](https://github.com/ejnburrows-rgb/db-backups) | **Backups, already PRIVATE.** Keep private. |
| [Remax](https://github.com/ejnburrows-rgb/Remax) | **Separate client deliverable, already PRIVATE.** Keep. |
| [PeteStore](https://github.com/ejnburrows-rgb/PeteStore) | **Separate sales product, already PRIVATE.** Keep. |
| [Onesixthgiants-](https://github.com/ejnburrows-rgb/Onesixthgiants-) | **Separate showcase, already PRIVATE.** Keep. |
| [butterfly-garden-adventure-51](https://github.com/ejnburrows-rgb/butterfly-garden-adventure-51) | **Gretel-related project, already PRIVATE.** Keep; review its connection to the active Cartilla before changing anything. |
| [agency-agents](https://github.com/ejnburrows-rgb/agency-agents) | **Potential archive candidate only.** Public fork. Archive only if the owner verifies no active dependencies. |

### Existing structure to reuse

- **Product:** `nbo-saas-crm`. Do not create `nbo-crm` or another canonical product repository.
- **Brand-specific behavior:** the proposed existing design `brands/otto` and `brands/tucker`. These are **planned** folders; not shipped code.
- **Marketing:** `client-project-starter` contains the current NBO site. No duplicate `nbo-marketing` repository is necessary without a separate business reason.
- **Template:** `nbo-starter-template` exists.
- **Internal:** leave `dev-firm-compass`, `db-backups`, and related client repositories private. `Command-Center-` requires a separate owner-approved visibility decision.

### Safe implementation sequence

1. **Freeze destructive cleanup:** do not archive OTTO, Tucker, Cartilla, LANY, websites, private clients or backups. No existing repository is verified disposable from this audit.
2. **Prove the real feature inventory:** record OTTO features and direct tests, trace Tucker's real current screens and any owner-provided missing CRM implementation. See the dated correction in `docs/feature-matrix.md`.
3. **Protect live operations:** the current OTTO app must continue running unchanged. No migration should overwrite it or alter its business records. Preserve export/backup and rollback paths.
4. **Design shared CRM rules first:** customers, contacts, jobs, money, schedule, staff, notes, files, bilingual labels and export; keep plumbing/pool-only rules separate. Security and client-data separation require verification before real multi-client use.
5. **Implement one small shared feature on a review branch:** demonstrate it with fake/demo records and a clickable preview, then test matching OTTO behavior before expansion. Do not invent Tucker operational features.
6. **Do not archive source repos until:** working feature parity, data safety, business approval, and a live cutover are independently verified. A complete planning document alone is not a migration.
7. **Request specific approval before any access change:** especially Command Center visibility, public CRM code and client-owned repositories.

### Audit limits

Inspected GitHub metadata, repository roots, READMEs, current Tucker source files, relevant OTTO control documents and Tucker's available branches/history. **No local builds, automated tests, live deployments, real login, customer workflows or secret configurations were tested.** Nothing in these documents certifies a working SaaS release.
