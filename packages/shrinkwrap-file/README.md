# @pnpm/shrinkwrap-file

> Read/write shrinkwrap.yaml files

Reads and writes the wanted (`shrinkwrap.yaml`) and current (`node_modules/.shrinkwrap.yaml`) shrinkwrap files of pnpm.
Shrinkwrap files are the state files of the `node_modules` installed via pnpm. They are like
the `package-lock.json` of npm or the `yarn.lock` of Yarn.

## Install

```
npm i @pnpm/shrinkwrap
```

## API

### `readWanted(pkgPath, opts) => Promise<Shrinkwrap>`

Alias: `read`

Reads the `shrinkwrap.yaml` file from the root of the package.

#### Arguments

* `pkgPath` - *Path* - the path to the project
* `opts.ignoreIncompatible` - *Boolean* - `false` by default. If `true`, throws an error
if the shrinkwrap file format is not compatible with the current library.

### `readCurrent(pkgPath, opts) => Promise<Shrinkwrap>`

Alias: `readPrivate`

Reads the shrinkwrap file from `node_modules/.shrinkwrap.yaml`.

### `existsWanted(pkgPath) => Promise<Boolean>`

Returns `true` if a `shrinkwrap.yaml` exists in the root of the package.

### `write(pkgPath, wantedShrinkwrap, currentShrinkwrap) => Promise<void>`

Writes the wanted/current shrinkwrap files. When they are empty, removes them.

### `writeWantedOnly(pkgPath, wantedShrinkwrap) => Promise<void>`

Writes the wanted shrinkwrap file only. Sometimes it is needed just to update the wanted shrinkwrap
without touching `node_modules`.

### `writeCurrentOnly(pkgPath, currentShrinkwrap) => Promise<void>`

Writes the current shrinkwrap file only. Fails if there is no `node_modules` directory in the `pkgPath`.

## License

[MIT](LICENSE)
