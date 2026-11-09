# any, unknown and never

## Introduction

TypeScript's types form a hierarchy. At the top are types that can hold every value, and at the bottom is a type that holds no value at all. Three special types live at these edges: `any`, `unknown` and `never`. Knowing how they work helps us write safer code.

## any: Turning Off Type Checking

`any` accepts every value, and TypeScript stops checking anything you do with it. This means mistakes slip through to runtime.

```ts
let data: any = "hello"
data.toFixed(2)

```

## unknown: The Safe Top Type

`unknown` also accepts every value, but TypeScript will not let you use it until you check its type. This forces us to narrow the value first.

```ts
let input: unknown = "hello"


if (typeof input === "string") {
    console.log(input.toUpperCase())
}

```

## never: The Bottom Type

`never` represents a value that can never happen. A function that always throws returns `never`. It is also useful for checking that every case in a union is handled.

```ts
const fail = (message: string): never => {
    throw new Error(message)
}

```

## Why unknown Is Preferred Over any

Both `any` and `unknown` can hold anything, but only `unknown` keeps type safety. With `any`, errors are hidden until the program runs. With `unknown`, the compiler makes us prove what the value is before using it. That is why `unknown` is the better choice for data from APIs, user input or `JSON.parse`.

## Conclusion

`unknown` and `any` sit at the top of the hierarchy, while `never` sits at the bottom. Use `unknown` when a type is truly unknown, use `never` for impossible cases, and avoid `any` whenever possible.
