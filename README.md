# Turborepo --filter issue replication

## How to reproduce

The following script will:

- Clean everything up (node_modules, previous runs outputs, etc.)
- Create a new package `package-c` out of a template
- Install the packages
- Runs the turbo build command with the filter option `--filter [HEAD]` so to filter out everything else is not the unstaged changes

```sh
npm run reproduce-issue
```

- Expected output: `["package-c"]`
- Actual output: `["package-a","package-b","package-c"]`
