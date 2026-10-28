# System Architecture

## Goal

NBO SaaS CRM is a service-business operating system with a generic core and modular brand overlays.

## Product composition

The product should be shaped like this:

- Shared CRM core
- Brand configuration layer
- Admin tools
- Public marketing/template layer
- Private internal tools outside the main product path

## Core layers

### 1. Domain layer
This layer owns the business logic and records for:

- customer
- contact
- job / work order
- estimate
- invoice
- payment
- schedule
- staff
- communication
- documents
- notes

### 2. App layer
This includes the main product screens and workflows:

- dashboard
- customer records
- jobs and service lifecycle
- money and billing
- scheduling
- team tools
- search and AI workflows
- admin settings

### 3. UI layer
Shared design rules and reusable UI components for:

- tables and lists
- forms and dialogs
- status badges
- schedule grids
- cards and detail layouts
- mobile and desktop layouts

### 4. Brand layer
Defines:

- company name and logo
- colors
- content and labels
- service categories
- workflow rules
- invoice templates
- custom forms
- localized copy

### 5. Data / storage layer
Supports:

- local-first persistence
- browser storage / offline capability
- document storage
- structured JSON / export
- import pipelines

## Brand overlays

### OTTO Plumbing overlay
- plumbing service operations
- job workflow and dispatch logic
- billing and team service patterns
- plumbing-specific naming and status labels

### Tucker Pool overlay
- pool service operations
- scheduling and customer history patterns
- pool maintenance and service categories
- bilingual service labels

## Design principles

- No duplication of shared product logic
- No client-specific logic in the core by default
- Minimal product surface for office/admin users
- Real data and real workflows over artificial dashboards
- Bilingual UI and content support
- Progressive disclosure rather than overloading every user

## Recommended repository boundaries

```
repo-root/
├── apps/
│   ├── web/
│   ├── admin/
│   └── mobile/
├── packages/
│   ├── core/
│   ├── types/
│   ├── ui/
│   └── branding/
├── brands/
│   ├── otto/
│   └── tucker/
├── docs/
├── scripts/
├── README.md
└── .gitignore
```

## Migration principle

The migration should not copy the old apps and rename them. It should extract the common features and preserve the unique business behavior through config-driven brand overlays.

