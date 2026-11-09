# Type Alias vs Interface in TypeScript

## Introduction

TypeScript provides both `type` aliases and `interface` declarations to describe the shape of data. They often look similar, but they have different capabilities. Choosing the right one makes code easier to understand and maintain.

## Detailed Explanation

An interface is mainly used to describe object structures. It can be extended by another interface with the `extends` keyword. Interfaces also support declaration merging, which means two declarations with the same name are combined.

```ts
interface User {
  id: number;
  name: string;
}

interface Admin extends User {
  permissions: string[];
}
```

A type alias can represent more than object shapes. It can define primitive aliases, union types, intersection types, tuples, and function types.

```ts
type Status = "active" | "inactive";

type Coordinates = [number, number];

type Account = {
  email: string;
} & {
  verified: boolean;
};
```

Both can describe objects and both can be extended in different ways. However, an interface cannot directly represent a union such as `"success" | "error"`, while a type alias can. Type aliases do not support declaration merging in the same way as interfaces.

## When Should We Choose Each One?

I usually choose an interface when defining the public shape of an object, class contract, or API model that may be extended. I choose a type alias when I need unions, intersections, tuples, or a combination of different types. Consistency within a project is also important.

## Conclusion

Neither option is always better. Interfaces are convenient for extendable object contracts, while type aliases are more flexible for building complex type expressions. Understanding their differences helps developers choose clear and maintainable types.
