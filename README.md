# tsx

Node.js runtime that can instantaneously load TypeScript & ESM, powered by [esbuild](https://esbuild.github.io/).

### Features
- Transforms TypeScript & ESM → to CJS or ESM (depending on [package type](https://nodejs.org/api/packages.html#type))
- Supports TS extensions `.cjs` & `.mjs` (`.cts` & `.mts`)
- TypeScript REPL
- Supports Node.js v12.20+
- Handles `node:` import prefixes
- Hides experimental feature warnings

## Install
```sh
npm install --save-dev tsx
```

### Install globally
Install it globally to use it anywhere, outside of your npm project, without [npx](https://docs.npmjs.com/cli/v8/commands/npx).
```sh
npm install --global tsx
```

## Usage

> Note: Commands are prefixed with [`npx`](https://docs.npmjs.com/cli/v8/commands/npx) to execute the `tsx` binary, but it's not necessary if globally installed or when using it in the `script` object in `package.json`

### Run TypeScript / ESM / CJS module

```sh
npx tsx ./file.ts
```

### Watch mode
Run file and automatically re-run on changes.

All imported files are watched except from the following directories:
`node_modules`, `bower_components`, `vendor`, `dist`, and `.*` (hidden directories).

Press <kbd>Return</kbd> to manually re-run.

```sh
npx tsx watch ./file.ts
```

### Cache
Modules transformations are cached in the system cache directory ([`TMPDIR`](https://en.wikipedia.org/wiki/TMPDIR)). Transforms are cached by content hash so duplicate dependencies are not re-transformed.

Set the `--no-cache` flag to disable the cache:

```sh
npx tsx --no-cache ./file.ts
```

## Dependencies

- [@esbuild-kit/esm-loader](https://github.com/esbuild-kit/esm-loader) - Node.js Loader to transform TypeScript to ESM.

- [@esbuild-kit/cjs-loader](https://github.com/esbuild-kit/cjs-loader) - Node.js `requie()` hook to transform TypeScript & ESM to CommonJS.
