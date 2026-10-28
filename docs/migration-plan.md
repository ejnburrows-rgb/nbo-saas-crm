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

