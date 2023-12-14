# Typescript Cheat Sheet

A cheat sheet for typing in Typescript as I'm learning it.

## Basic / Primitive Types
- `boolean` 
- `string` 
- `number`
  - `int` and `float` are just number, JS doesn't know the difference.

## Other basicish types:
- Literals: `"tomatos"`
- Enums: `"tomatos" | "eggs" | "bacon"`


<br>

## How to type stuff
Pretty much the same as python here.

In a function:
```typescript
function myFunction(arg1: number, arg2: boolean, arg3: string) {
    return
}
```

As a variable:
```typescript
let myVariable: string = "Hey variable!"
```

<br>

## Optional Args
You can make an arg optional like this.

```typescript
function myFunction(myArg1?: string) {
    if (myArg1) {
        console.log("Argument exists.")
    }
}
```

<br>

## Function Return Typing
```typescript
function myFunction(): string {
    return "A string"
}
```

<br>


## Arrays
Just add a square brackets m8.
```typescript
let arrayOfStuff: string[] = ["An", "array", "of", "strings"]
```

You can also do this if it floats your boat
```typescript
let arrayOfStuff: array<string> = ["An", "array", "of", "strings"]
```

<br>


## Typing Objects
After much deliberation I've decided that a JS objects is most like 
a python class. Though it also feels a bit dictionaryish.

Not that this matters. Here's how to type one.
```typescript
function myFunc(obj: {thing1: string, thing2: string}) {
    console.log("Hello!");
}

const myObj: {thing1: string, thing2: string} = new Object({thing1: "test", thing2: "test"})
```

<br>

## Interfaces
Interfaces are my favourite new thing. They're basically the same as structs in Go or 
dataclasses in python (which nobody really uses). 

You know when you write something like this in Python?
```python
def my_function(car: dict):
    """I'm passing a dict called car. What does it have in it? Nobody knows."""
```

Well what you do is create an interface which is an object but with defined parameters. You can
then just use this object as a type wherever.

```typescript
interface car {
  wheelDiameter: number,
  numberOfSeats: number,
  make: string,
  model: string,
}

function myFunction(car: car) {
    console.log(`Car has ${car.numberOfSeats} seats.`)
}
```

Interesting side note here. If you define the interface as having a thing then it must have that thing
from the get go. Here's an example.
```typescript
type AddTwoNumbersArgs = {
    first: number;
    second: number;
};

export const addTwoNumbers = (params: AddTwoNumbersArgs) => {
    return params.first + params.second;
};
```

This seems to make sense. But means you can't build the interface up typed as you go. 
This won't work:

```typescript

function getTwoNumbersToAddTogether(): AddTwoNumbersArgs {
  // This won't work, you need to define those params from the get go.
  let args: AddTwoNumbersArgs = {}
  args.first = 1
  args.second = 2

  // You could define them with dummy values to start with, but this feels unsafe
  // to me. What if you forget to overwrite?
  args: AddTwoNumbersArgs = {
    first: 0,
    second: 0
  }
  args.first = 1
  args.second = 2
  
  // Possibly the better thing to do here is to create an untyped object then unpack it at the end?
  args = {}
  args.first = 1
  args.second = 2
  args: AddTwoNumbersArgs = {...args}
}

```
