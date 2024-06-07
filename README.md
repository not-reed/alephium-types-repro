# QuickStart

tested on Bun v1.1.12

```sh
bun install
bun dev
```

## Issue 1

Open App.vue and receive this typescript error

```md
Could not find a declaration file for module 
 . /alephium-types-repro/node_modules/@alephium/web3/dist/alephium-web3.min.js implicitly has an 
 type.

There are types at /alephium-types-repro/node_modules/@alephium/web3/dist/src/index.d.ts', but this result could not be resolved when respecting package.json "exports". The @alephium/web3' library may need to update its package.json or typings.
```

## Issue 2

`asdasdf` is calculated as a valid address ![alt text](https://github.com/not-reed/alephium-types-repro/blob/main/public/asdasdf.png?raw=true)

