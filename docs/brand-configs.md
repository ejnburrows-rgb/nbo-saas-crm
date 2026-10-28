# Brand Configs

## Overview

The product should be able to represent multiple service-business brands without branching the app into entirely separate products.

## Brand overlay responsibilities

### `brands/otto`
This config should set:

- business name: OTTO Plumbing
- service categories: plumbing, service calls, installation, diagnostics
- terms and labels: job, estimate, invoice, customer, service ticket
- color palette and visual identity
- workflow defaults relevant to plumbing operations
- bilingual labels in English/Spanish

### `brands/tucker`
This config should set:

- business name: Tucker Pool CRM
- service categories: pool maintenance, repairs, chemical services
- workflow defaults relevant to recurring service maintenance
- bilingual labels for pool-related operations
- pricing and recurring service patterns

## Configuration pattern

Each brand config should contain:

- `brand.json`
- `labels.en.json`
- `labels.es.json`
- `theme.css`
- `service-categories.json`
- `workflow-rules.json`

## Principle

Brand-specific rules should be data-driven and isolated from the shared product engine.

