# Turborepo --filter issue replication

### Adding a new package without dependencies:

```bash
pnpm dlx turbo run build --filter="[__FIRST_COMMIT__...__SECOND_COMMIT__]" --filter='!//' --dry-run=json | jq -c '.packages'
```

> Output: `["package-c"]`

Correct

### Adding a package with dependencies

```bash
pnpm dlx turbo run build --filter="[__FIRST_COMMIT__...__SECOND_COMMIT__]" --filter='!//' --dry-run=json | jq -c '.packages'
```

> Output: `["package-a","package-b","package-c"]`

_Wrong_ - Should be only `["package-c"]`
