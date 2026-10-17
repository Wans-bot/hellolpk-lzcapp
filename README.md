# Lazycat Vue App

## First Deploy
```bash
lzc-cli project deploy
lzc-cli project info
```

By default, project commands use `lzc-build.dev.yml` when it exists.
Each command prints the active `Build config`.
Use `--release` if you want to operate on `lzc-build.yml`.

Open the app first.
If the frontend dev server is not running yet, the app page will show the expected port and next step.

## Frontend Dev Loop
```bash
npm run dev
```

Then refresh the app page.

## Logs
```bash
lzc-cli project log -f
```
