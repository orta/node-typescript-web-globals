A version of [@types/web](https://www.npmjs.com/package/@types/web) which has the types separated from the declaration of globals based on [this diff](https://github.com/microsoft/TypeScript-DOM-lib-generator/pull/new/split_types_2) with a bit of manual hand-holding by me.

Old:

```ts
var EventTarget: {
    prototype: EventTarget;
    new(): EventTarget;
};
```

Now:
```ts
interface EventTargetConstructor {
    prototype: EventTarget;
    new(): EventTarget;
}

var EventTarget: EventTargetConstructor
```

This library can be used like:

```sh
pnpm add @orta/lib-dom-globals@npm:@types/web --save-dev
npm install @orta/lib-dom-globals@npm:@types/web --save-dev
yarn add @orta/lib-dom-globals@npm:@types/web --dev
```


Which will give other libraries the ability to do:

```
/// <reference lib="dom.types" />
```

Which resolves to [`./types.d.ts`](./types.d.ts) - which only contains the global type and no runtime declarations.