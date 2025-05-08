# Differences Between Interfaces and Types in TypeScript

1. Declaration Merging

Interface: Supports declaration merging. You can define the same interface multiple times, and TypeScript will merge them into a single definition.

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = { name: "Alice", age: 25 }; // Merged interface
```

## 2. Extending

Interface: Can be extended using the extends keyword.

```typescript
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}
```

Type: Can be extended using intersection (&).

```typescript
type Animal = {
  name: string;
};

type Dog = Animal & {
  breed: string;
};
```

When to Use:

Use interfaces when defining object shapes or when you need declaration merging.
Use types for unions, intersections, or more complex type definitions.

# Example of using union and intersection types in TypeScript:

Union Type Example
A union type allows a value to be one of several types.

```typescript
type Status = "success" | "error" | "loading";

function printStatus(status: Status): void {
  console.log(`The current status is: ${status}`);
}

printStatus("success"); // Output: The current status is: success
printStatus("error"); // Output: The current status is: error
```

Intersection Type Example
An intersection type combines multiple types into one.

```typescript
type Person = {
  name: string;
  age: number;
};

type Employee = {
  employeeId: number;
  department: string;
};

type EmployeeDetails = Person & Employee;

const employee: EmployeeDetails = {
  name: "Alice",
  age: 30,
  employeeId: 12345,
  department: "Engineering",
};

console.log(employee);
// Output: { name: 'Alice', age: 30, employeeId: 12345, department: 'Engineering' }
```

Explanation:
Union Type:

The Status type allows a value to be "success", "error", or "loading".
Useful when a variable can have multiple possible types or values.
Intersection Type:

The EmployeeDetails type combines the properties of Person and Employee.
Useful when you need to merge multiple types into one.
These examples demonstrate how union and intersection types can be used to create flexible and reusable type definitions in TypeScript.
