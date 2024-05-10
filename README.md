# Turborepo --filter issue replication

## How to reproduce

The following script will:

- Clean everything up (node_modules, previous runs outputs, etc.)
- Create a new workspace `package-c` out of a template
- Install the npm packages
- Runs the turbo build command with the filter option `--filter [HEAD]` so to filter between the unstaged changes and HEAD

```sh
pnpm run reproduce-issue
```

- Expected output: `["package-c"]`
- Actual output: `["package-a","package-b","package-c"]`

### Notes:

- It doesn't work with the canary release either, i.e. running `pnpm dlx turbo@canary run build --filter=\"[HEAD]\" --filter='!//' --dry-run=json | jq -c '.packages'`
- The package manager used is pnpm@9.0.6
