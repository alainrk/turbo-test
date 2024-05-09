# turborepo-filter-bug

### Adding a new package without dependencies:

```bash
pnpm dlx turbo run build --filter="[dd3feded73313b7f232a84c3c18ea3b3ef8d5eb2...3c03c889e8334505854298f7b576bd9e8dcb8ac8]" --filter='!//' --dry-run=json | jq -c '.packages'
```

> Output: `["package-d"]`

Correct

### Adding a package with dependencies

```bash
pnpm dlx turbo run build --filter="[58300a6d252f4201dabac18f3616fbff8507d116...dd3feded73313b7f232a84c3c18ea3b3ef8d5eb2]" --filter='!//' --dry-run=json | jq -c '.packages'
```
> Output: `["package-a","package-b","package-c","package-d"]`

*Wrong* - Should be only `["package-c"]` (`package-d` didn't even exist)