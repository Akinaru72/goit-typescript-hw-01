# goit-typescript-hw-01

To complete this homework, you need to create a repository **goit-typescript-hw-01** and set up a project using **Vite**.

In the `src` folder, create two folders: `basic` and `generics`.  
In these folders, you will create `.ts` files for each task.

## Basic Types

The goal of this task block is to reinforce your skills in working with TypeScript's basic types.

## Task 1

Complete this task in the file `src/basic/1.ts`.

Here is the following JavaScript code:

```js
const age = 50;
const username = "Max";
const toggle = true;
const empty = null;
const callback = (a) => {
  return 100 + a;
};
```

Convert this code to TypeScript by specifying the appropriate types for all variables.

## Task 2

Complete this task in the file `src/basic/2.ts`.

You have the following JavaScript array:

```js
let person = ["Max", 21];
```

How can you rewrite this code in TypeScript using the concept of tuples to ensure that the first element is always a string and the second is a number?

## Task 3

Complete this task in the file `src/basic/3.ts`.

Create a variable that can hold either a string or a number (union type).  
Also, declare a variable that can hold only one of two possible string values: `'enable'` or `'disable'` (literal type).

## Task 4

Complete this task in the file `src/basic/4.ts`.

You have the following JavaScript functions:

```js
function showMessage(message) {
  console.log(message);
}

function calc(num1, num2) {
  return num1 + num2;
}

function customError() {
  throw new Error("Error");
}
```

How would you specify types for the arguments and return values for these functions?

## Task 5

Complete this task in the file `src/basic/5.ts`.

Type the function `isWeekend`, which takes a day of the week from the `enum DayOfWeek` and returns a `boolean` indicating whether it is a weekend or a weekday.

```ts
enum DayOfWeek {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday,
}

const isWeekend = (day) => {};
```

## Task 6

Complete this task in the file `src/basic/6.ts`.

Create an interface `User` to type objects that contain the following properties.  
Note that the `address` property is optional.

```js
const mango = {
  name: "Mango",
  age: 30,
  email: "john@example.com",
  address: {
    city: "New York",
    country: "USA",
  },
};

const poly = {
  name: "Mango",
  age: 30,
  email: "john@example.com",
};
```

## Task 7

Complete this task in the file `src/basic/7.ts`.

You have two objects:

```js
const page1 = {
  title: "The awesome page",
  likes: 100,
  accounts: ["Max", "Anton", "Nikita"],
  status: "open",
  details: {
    createAt: new Date("2021-01-01"),
    updateAt: new Date("2021-05-01"),
  },
};

const page2 = {
  title: "Python or Js",
  likes: 5,
  accounts: ["Alex"],
  status: "close",
};
```

Create a new data type that fits both of these objects.

---

## Generic Types

The goal of this section is to help you understand and apply generics in TypeScript.  
You will work with functions that return promises, use the built-in `Pick` type, merge objects using generics, and also solve type-related problems in classes.

## Task 1

Complete this task in the file `src/generics/1.ts`.

Type the asynchronous function `fetchData`, which takes a resource URL and returns an object with data.  
Use generics to type the returned data.

```ts
import axios from "axios";

async function fetchData(url) {
  try {
    const response = await axios.get(url);
    return response.data;
  } catch (error) {
    throw new Error(`Error fetching from ${url}: ${error}`);
  }
}
```

## Task 2

Complete this task in the file `src/generics/2.ts`.

You have a type `AllType`. There is a function `compare` that takes two objects.  
These objects contain fields of type `AllType`.

Your task is to use `Pick` and generics to indicate that the fields of these parameters belong to the `AllType` type.  
The `compare` function should return a value of type `AllType`.

```ts
type AllType = {
  name: string;
  position: number;
  color: string;
  weight: number;
};

function compare(top, bottom): AllType {
  return {
    name: top.name,
    color: top.color,
    position: bottom.position,
    weight: bottom.weight,
  };
}
```

# Task 3

Complete this task in the file `src/generics/3.ts`.

You have a function `merge` that combines two objects.  
Use generics to indicate that these objects can be of any type.

```ts
function merge(objA, objB) {
  return Object.assign(objA, objB);
}
```

## Task 4

Complete this task in the file `src/generics/4.ts`.

You have a user registration form. Sometimes you need to prefill the form with user data to update their profile.  
However, you do not always need to fill in all fields. For example, a user may update only their email and password, leaving the first name and surname unchanged.

Using the `Partial` utility and generics, fix the type of the function parameter to avoid type errors.

```ts
type User = {
  name: string;
  surname: string;
  email: string;
  password: string;
};

function createOrUpdateUser(initialValues: User) {
  // Update user
}

createOrUpdateUser({
  email: "user@mail.com",
  password: "password123",
});
```

## Task 5

Complete this task in the file `src/generics/5.ts`.

You have an enum `UserRole` that is used to classify users in your application.  
You want to create an object `RoleDescription` that maps each user role to its description.

```ts
export enum UserRole {
  admin = "admin",
  editor = "editor",
  guest = "guest",
}

// Replace the following code with a version using Record
const RoleDescription = {
  admin: "Admin User",
  editor: "Editor User",
  guest: "Guest User",
};
```

## Task 6

Complete this task in the file `src/generics/6.ts`.

You have a type `Form` that contains information about a form, including the `errors` field.  
You want to create a new type `Params` that includes all fields from `Form` except `errors`.

```ts
type Errors = {
  email?: string[];
  firstName?: string[];
  lastName?: string[];
  phone?: string[];
};

type Form = {
  email: string | null;
  firstName: string | null;
  lastName: string | null;
  phone: string | null;
  errors: Errors;
};

// Implement Params so that the 'errors' field from Form is excluded
type Params = Form;
```
