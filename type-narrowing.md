# Type Narrowing in TypeScript

## Introduction

Type narrowing is the process of reducing a variable's possible types inside a particular part of a program. It helps TypeScript understand which operations are safe. Narrowing is especially useful when a value can have more than one type.

## Detailed Explanation

The `typeof` operator is commonly used with primitive values. After checking the type, TypeScript allows operations that belong to that type.

```ts
function formatValue(value: string | number): string {
  if (typeof value === "string") {
    return value.trim().toLowerCase();
  }

  return value.toFixed(2);
}
```

The `instanceof` operator checks whether an object was created by a particular class or constructor. It is useful when working with class instances and built-in objects.

```ts
class Dog {
  bark(): string {
    return "Woof";
  }
}

function makeSound(animal: Dog | Date): string {
  if (animal instanceof Dog) {
    return animal.bark();
  }

  return animal.toDateString();
}
```

The `in` operator checks whether a property exists on an object. TypeScript can use that check to distinguish object types.

```ts
type Admin = { name: string; permissions: string[] };
type Customer = { name: string; purchaseCount: number };

function describeUser(user: Admin | Customer): string {
  if ("permissions" in user) {
    return `Admin: ${user.permissions.length} permissions`;
  }

  return `Customer: ${user.purchaseCount} purchases`;
}
```

These checks make code safer without requiring unsafe type assertions.

## Conclusion

Type narrowing connects runtime checks with TypeScript's static type system. Using `typeof`, `instanceof`, and `in` helps developers handle union types clearly and avoid accessing properties or methods that may not exist.
