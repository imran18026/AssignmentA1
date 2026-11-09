# Type Alias vs Interface

## Introduction

TypeScript gives us two ways to describe the shape of data: one is `type` aliases and another is `interface`. For simple objects they look almost the same, but a small difference. The difference becomes clear once we look at what each one can and cannot do.

## What They Have in Common

Both can describe an object and both can be extended.

```ts
type UserType = { name: string; age: number }

interface UserInterface {
    name: string
    age: number
}

```

## Differences

**1. Type aliases can name any type.** A `type` can describe unions, tuples and primitives. An `interface` can only describe object shapes.

```ts
type Status = "active" | "inactive"
type Point = [number, number]

```

**2. Extending works differently.** Interfaces use `extends`, while type aliases use the intersection operator `&`.

```ts
interface Animal { name: string }
interface Dog extends Animal { breed: string }

type Bird = { name: string } & { canFly: boolean }
```

## When to Choose Which

Use an `interface` when you describe objects or class contracts, especially in libraries where others may want to extend them. Use a `type` when you need unions, tuples, function types or other combinations an interface cannot express.

## Conclusion

Both tools are useful and often interchangeable for objects. A simple rule: reach for `interface` for object shapes and `type` for everything else. Being consistent across a project matters more than which one you pick.
