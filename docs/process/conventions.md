# Conventions

Keep only what applies to this project's stack; fill the stack-specific parts
during/after the interview.

## Naming & structure

- Small, single-responsibility files. No god classes.
- Domains don't import each other directly; shared contracts live in one place.
- {{stack-specific naming rules}}

## API shape (if applicable)

- Consistent success/error envelopes.
- Errors are typed and logged with context; never swallow them silently.
- {{realtime event naming, if any}}

## Authorization

- **Deny by default.** Grant explicitly.

## Validation & config

- Validate input at boundaries. Configuration via env; never commit secrets.

## Testing

- {{what must be tested and at what level — fill per stack}}

## Commits & branches

- Convention: {{COMMIT_CONVENTION}} _(default: Conventional Commits)_.
- Branch naming: {{branch convention}}.
- **Commit only when the user asks.**
