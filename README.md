A project which has the [split types/vars branch](https://github.com/orta/orta-types-web-globals/blob/master/README.md) of TS DOM lib generator which integrates with the Node JS types. [See this thread](https://github.com/microsoft/TypeScript/issues/43972#issuecomment-986887338)

Changes to [node's types](node_modules/@types/node/globals.d.ts):

```diff
// For me in here:
+ /// <reference path="../../@typescript/lib-dom/types.d.ts" />

// Real world:
+ /// <reference lib="dom/types" />


+ declare var AbortController: AbortControllerConstructor
- declare var AbortController: {
-     prototype: AbortController;
-     new(): AbortController;
- };

+ declare var AbortSignal: AbortSignalConstructor
- declare var AbortSignal: {
-     prototype: AbortSignal;
-     new(): AbortSignal;
-     // TODO: Add abort() static
- };
```

The: 
```
/// <reference path="../../@typescript/lib-dom/types.d.ts" />
```

Would be something like `/// <reference lib="dom.type" />`.

The tricky part is that this is not backwards compatible, e.g. clients on 4.5 don't have `dom.type` in their lib and so that would fail. Unsure on what to do there yet.
