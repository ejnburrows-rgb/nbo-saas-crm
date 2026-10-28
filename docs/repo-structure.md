# Repository Structure

## Recommended layout

```
.nbo-saas-crm/
├── README.md
├── .gitignore
├── apps/
│   ├── web/
│   │   ├── src/
│   │   └── public/
│   ├── admin/
│   │   └── src/
│   └── mobile/
│       └── src/
├── packages/
│   ├── core/
│   │   ├── crm/
│   │   ├── billing/
│   │   ├── scheduling/
│   │   ├── documents/
│   │   └── search/
│   ├── ui/
│   │   ├── components/
│   │   ├── layout/
│   │   └── themes/
│   ├── types/
│   │   └── domain/
│   ├── branding/
│   │   ├── themes/
│   │   ├── labels/
│   │   └── config/
│   └── shared/
│       ├── utils/
│       ├── validators/
│       └── hooks/
├── brands/
│   ├── otto/
│   │   ├── config/
│   │   ├── rules/
│   │   └── README.md
│   └── tucker/
│       ├── config/
│       ├── rules/
│       └── README.md
├── docs/
│   ├── architecture.md
│   ├── migration-plan.md
│   ├── feature-matrix.md
│   └── brand-configs.md
├── scripts/
│   └── setup/
└── LICENSE
```

## Responsibilities

### `apps/web`
The main app where users manage customers, jobs, money, schedule, and customer communication.

### `apps/admin`
The configuration and settings layer: company data, invoice rules, onboarding, users, and admin tasks.

### `packages/core`
This is the reusable product logic. It should not contain client-specific names or special-case behaviors unless they are clearly brand configs.

### `packages/branding`
This is where brand themes, labels, currencies, and operational rules are defined.

### `brands/otto`
Plumbing-specific config and special workflows.

### `brands/tucker`
Pool-service-specific config and workflows.

## Final rule

The core must stay generic and reusable. All specific business logic must live in brand config overlays, not in the central product code.

