# Typescript (Cheatsheets)

## JS vs Typescript

JavaScript is a dynamically typed language. This means that data types of variables can change as we assign different values to them.

* JS provides Values
* Typescript provides types


## Install tsc


```javascript
//tsconfig.json

```


## types


* string - the type is a primitive JavaScript string. E.g. "hello".
* number - the type is a primitive JavaScript number. E.g. 10.
* boolean - the type is a primitive JavaScript boolean. E.g. true.
* any - the type is anything.
* any[] - the type is an array of any.
* void - no type, effectively undefined.
* () => any - the type is a function that returns any.
* [string, number] - tuple


## values and types

```javascript
// value
var animal;

// type 
interface Bear {}

// type and value
class Cat {} 
```


## Structural typing

```javascript
interface Colored {
    color: string;
}

class Box implements Colored {
 constructor(public color: string) {}
}

let b: Colored = new Box("red)
let c: Colored = {color: "red"}
```


### inheritance

```javascript
class Point {...}

class Point3D extends Point {...}

class Pixel extends Point implements Colored {...}

```

### Generics

```javascript
class Greeter<T> {
  greeting: T
  constructor(message: T) {
    this.greeting = message
  }
}

let greeter = new Greeter<string>('Hello, world')

```


## Index Signatures

```javascript
interface Data {
    [key: string] : boolean;
}

const d: Data = {}
d["mykey"] = true;
```

## Types

Optional

```javascript
interface User {
  name: string,
  age?: number
}
```

Read only

```javascript
interface User {
  readonly name: string
}

```


### Union

```javascript
type Name = string | string[]

type nullable = string | undefined

```

### Intersection


```javascript
interface ErrorHandling {
  success: boolean;
  error?: { message: string };
}

interface ArtworksData {
  artworks: { title: string }[];
}

interface ArtistsData {
  artists: { name: string }[];
}

// These interfaces are composed to have
// consistent error handling, and their own data.
type ArtworksResponse = ArtworksData & ErrorHandling;
type ArtistsResponse = ArtistsData & ErrorHandling;


const handleArtistsResponse = (response: ArtistsResponse) => {
  if (response.error) {
    console.error(response.error.message);
    return;
  }

  console.log(response.artists);
};
```

## Union vs inheritance

```javascript
// BAD pratice
interface Props extends OwnProps, InjectedProps, StoreProps {}
type OwnProps = {...}
type StoreProps = {...}

// GOOD pratice
type Props = OwnProps & InjectedProps & StoreProps
type OwnProps = {...}
type StoreProps = {...}
```



### Optionals

```javascript
// x has type string | undefined
const myfunc = (x?: string)
```


## Type Assertion

```javascript
const msg = message as SpecialMessageType
```

```javascript
let len: number = (input as string).length

```

## Partials 

```javascript
interface Todo {
  title: string;
  description: string;
}

function updateTodo(todo: Todo, fieldsToUpdate: Partial<Todo>) {
  return { ...todo, ...fieldsToUpdate };
}

const todo1 = {
  title: "organize desk",
  description: "clear clutter",
};

const todo2 = updateTodo(todo1, {
  description: "throw out trash",
});

```

## enums

Enums in TypeScript default to number but you can assign strings insteads

```javascript
enum Colors {
    RED = 'Red',
    BLUE = 'Blue',
    GREEN = 'Green'
}
```

## Troubleshoots

### window object required by vendor lib

```javascript
declare global {
  interface Window {
    MyVendorThing: MyVendorType;
  }
}
```

### import non ts file


#### image ".png"

```javascript
// declaration.d.ts
// anywhere in your project, NOT the same name as any of your .ts/tsx files
declare module "*.png";
```

```javascript
// importing in a tsx file
import * as logo from "./logo.png";
```


#### Json import 

supported since TS 2.9+

```javascript
//ensure tsconfig.json have following keys
{
  "compilerOptions": {
      "resolveJsonModule": true,
      "esModuleInterop": true  
  }
}
```

```javascript
// importing in a tsx file
import * as news from "./file.json";
```


