# Architecture overview

<!-- GENESIS:FILL — from interview sections C & D -->

## Diagram

```
{{ high-level component / data-flow diagram }}
```

## Boundaries & worlds

{{Separate languages/runtimes/images with hard boundaries between them, if any.}}

## Sync vs async

{{Which long operations are job-based + event-driven (queue + push) vs blocking.}}

## Single sources of truth

{{State that must have exactly one authority — name it.}}

## Contract-first rules

{{What must not be built before its contract/schema/spec exists.}}

## Provider independence

{{Which external dependencies sit behind adapters (swappable) vs deliberately fixed.}}
