---
Link: https://blog.logrocket.com/level-up-typescript-record-types/
tags:
  - TypeScript
  - Map
  - FactoryPattern
---

`Record<Keys, Type>` constructs an object type whose property keys are `Keys` and whose property values are `Type`. This utility can be used to map the properties of a type to another type.”

## Implementing the TypeScript `Record` type

The power of TypeScript’s `Record` type is that we can use it to model dictionaries with a fixed number of keys. For example, we could use the the `Record` type to create a model for university courses:

type Course = "Computer Science" | "Mathematics" | "Literature"

interface CourseInfo {
    professor: string
    cfu: number
}

const courses: Record<Course, CourseInfo> = {
    "Computer Science": {
                professor: "Mary Jane",
                cfu: 12
    },
    "Mathematics": {
                professor: "John Doe",
                cfu: 12
    },
    "Literature": {
                professor: "Frank Purple",
                cfu: 12
    }
}

In this example, we defined a type named `Course` that will list the names of classes and a type named `CourseInfo` that will hold some general details about the courses. Then, we used a `Record` type to match each `Course` with its `CourseInfo`.

So far, so good — it all looks like quite a simple dictionary. The real strength of the `Record` type is that TypeScript will detect whether we missed a `Course`.

### Identifying missing properties

Let’s say we didn’t include an entry for `Literature`. We’d get the following error at compile time:

> “Property `Literature` is missing in type `{ "Computer Science": { professor: string; cfu: number; }; Mathematics: { professor: string; cfu: number; }; }` but required in type `Record<Course, CourseInfo>`”

In this example, TypeScript is clearly telling us that `Literature` is missing.

### Identifying undefined properties

TypeScript will also detect if we add entries for values that are not defined in `Course`. Let’s say we added another entry in `Course` for a `History` class. Since we didn’t include `History` as a `Course` type, we’d get the following compilation error:

> “Object literal may only specify known properties, and `"History"` does not exist in type `Record<Course, CourseInfo>`”

### Accessing `Record` data

We can access data related to each `Course` as we would with any other dictionary:

console.log(courses["Literature"])

The statement above prints the following output:

{ "teacher": "Frank Purple", "cfu": 12 }

Let’s proceed to take a look at some cases where the `Record` type is particularly useful.

## Use case 1: Enforcing exhaustive case handling

When writing modern applications, it’s often necessary to run different logic based on some discriminating value. A perfect example is [the factory design pattern](https://en.wikipedia.org/wiki/Factory_method_pattern), where we create instances of different objects based on some input. In this scenario, handling all cases is paramount.

The simplest (and somehow naive) solution would probably be to use a `switch` construct to handle all the cases:

type Discriminator = 1 | 2 | 3

function factory(d: Discriminator): string {
    switch(d) {
            case 1:
            return "1"
            case 2:
                return "2"
            case 3:
                return "3"
            default:
                return "0"
    }
}

If we add a new case to `Discriminator`, however, due to the `default` branch, TypeScript will not tell us we’ve failed to handle the new case in the `factory` function. Without the `default` branch, this would not happen; instead, TypeScript would detect that a new value had been added to `Discriminator`.

We can leverage the power of the `Record` type to fix this:

type Discriminator = 1 | 2 | 3

```ts
function factory(d: Discriminator): string {
    const factories: Record<Discriminator, () => string> = {
            1: () => "1",
            2: () => "2",
            3: () => "3"
    }
    return factories[d]()
}
```


console.log(factory(1))

The new `factory` function simply defines a `Record` matching a `Discriminator` with a tailored initialization function, inputting no arguments and returning a `string`. Then, `factory` just gets the right function, based on the `d: Discriminator`, and returns a `string` by calling the resulting function. If we now add more elements to `Discriminator`, the `Record` type will ensure that TypeScript detects missing cases in `factories`.

## Use case 2: Enforcing type checking in applications that use generics

Generics allow us to write code that is abstract over actual types. For example, `Record<K, V>` is a generic type. When we use it, we have to pick two actual types: one for the keys (`K`) and one for the values (`V`).

Generics are extremely useful in modern programming, as they enable us to [write highly reusable code](https://blog.logrocket.com/using-typescript-generics-create-reusable-components/). The code to make HTTP calls or query a database is normally generic over the type of the returned value. This is very nice, but it comes at a cost because it makes it difficult for us to know the actual properties of the returned value.

We can solve this by leveraging the `Record` type:

class Result<Properties = Record<string, any>> {
    constructor(
                public readonly properties: Record<
                        keyof Properties,
                        Properties[keyof Properties]
                >
    ) {}
}

`Result` is a bit complex. In this example, we declare it as a generic type where the type parameter, `Properties`, defaults to `Record<string, any>`.