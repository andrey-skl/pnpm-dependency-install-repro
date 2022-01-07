To reproduce the PNPM@6.25.0 issue:

1. run `pnpm install`

See the following output **with no "install" script run"**

```
➜  pnpm-playwright-demo git:(main) pnpm install
 WARN  `node_modules` is present. Lockfile only installation will make it out-of-date
Packages: +46
++++++++++++++++++++++++++++++++++++++++++++++
Progress: resolved 46, reused 46, downloaded 0, added 0, done
```

If you change

```
node-linker = hoisted
=> 
node-linker = isolated
```

You will see how "install" script has been ran:

```
➜  pnpm-playwright-demo git:(main) ✗ pnpm install
Lockfile is up-to-date, resolution step is skipped
Packages: +46
++++++++++++++++++++++++++++++++++++++++++++++
Packages are hard linked from the content-addressable store to the virtual store.
  Content-addressable store is at: /Users/skladchikov/.pnpm-store/v3
  Virtual store is at:             node_modules/.pnpm
node_modules/.pnpm/playwright@1.17.1/node_modules/playwright: Running install script, done in 29.8s
Progress: resolved 46, reused 46, downloaded 0, added 46, done
```
