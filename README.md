# NBO SaaS CRM

Default SaaS CRM foundation for service businesses, designed to support multiple brands and operational workflows without duplicating the entire product.

## Vision

NBO SaaS CRM is the reusable operational core behind businesses like OTTO Plumbing and Tucker Pool CRM. The system is intentionally generic at the core and configurable at the brand layer.

Rather than shipping a single one-off app for one company, the product is structured as:

- a shared CRM engine for service businesses
- a configurable brand layer for OTTO, Tucker, and future clients
- a public marketing/template layer separate from the core backend product
- private internal tools kept out of the public portfolio

## Product model

This system is built for businesses that need:

- customer and contact management
- job and work-order tracking
- invoices and payment tracking
- scheduling and dispatch
- employee records and team coordination
- communication history and notes
- file uploads, photos, and plans
- bilingual support and flexible forms
- brand-specific workflow configuration

## Core principles

1. Generic at the core
- Shared CRM logic should not be built around one business vertical.

2. Configurable by brand
- Company name, service types, workflows, labels, and forms should be configurable.

3. Bilingual by default
- English and Spanish support should be a product requirement.

4. Local-first operational capability
- Core workflows should work without network dependence where possible.

5. Public/private separation
- Product code stays clear; internal systems remain private.

## Architecture summary

- `apps/web`: customer-facing app shell and dashboards
- `apps/admin`: business admin and configuration screens
- `packages/core`: shared product logic, schemas, and service layer
- `packages/ui`: design-system and shared components
- `packages/types`: domain types and validation schemas
- `packages/branding`: brand themes, labels, and service configs
- `brands/otto`: plumbing-specific config and workflow overrides
- `brands/tucker`: pool-service config and workflow overrides
- `docs/`: architecture, migration, product rules, roadmap

## User-facing domains

The product supports core business operations across:

- Customers
- Contacts
- Jobs / work orders
- Invoices
- Estimates
- Payments
- Schedule / dispatch
- Files / photos / plans
- Team / staff records
- Follow-ups / communications
- Search and AI assistance

## Current migration context

This repo is intentionally the canonical product home for the business platform being consolidated from:

- `ejnburrows-rgb/otto`
- `ejnburrows-rgb/tucker-pool-crm`

The migration goal is to preserve the real functionality while reducing duplication and creating a clean, reusable SaaS foundation.

## Repo strategy

### Main product
- `nbo-saas-crm`

### Brand overlays
- `brands/otto`
- `brands/tucker`

### Public portfolio repos
- `nbo-marketing`
- `nbo-starter-template`

### Internal/private repos
- `Command-Center-`
- `dev-firm-compass`
- `db-backups`

## Roadmap

### Phase 1
- finalize the shared CRM model
- identify common features from OTTO and Tucker
- define brand config system

### Phase 2
- create reusable domain models for customer, job, invoice, schedule, and team
- build shared UI rules and workflows

### Phase 3
- add OTTO and Tucker brand overlays
- validate both workflows against the original product behavior

### Phase 4
- create public-facing marketing and starter repos
- archive or de-prioritize one-off projects

## Notes

This repo is the canonical source of truth for the unified CRM strategy. It is not meant to be a one-client app; it is meant to become the reusable service-business operating system behind branded deployments.

## Next steps

1. Document the shared feature set from OTTO and Tucker
2. Build the generic CRM schema and modules
3. Add OTTO and Tucker brand config
4. Keep public repos limited and intentional
5. Archive old side-projects that no longer matter

