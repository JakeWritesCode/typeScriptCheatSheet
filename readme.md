# Typescript Cheat Sheet

A cheat sheet for typing in Typescript as I'm learning it.

## Basic / Primitive Types
- `boolean` 
- `string` 
- `number`
  - `int` and `float` are just number, JS doesn't know the difference.


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

## Optional Args
You can make an arg optional like this.

```typescript
function myFunction(myArg1?: string) {
    if (myArg1) {
        console.log("Argument exists.")
    }
}
```

## Arrays
Just add a square brackets m8.
```typescript
let arrayOfStuff: string[] = ["An", "array", "of", "strings"]
```

You can also do this if it floats your boat
```typescript
let arrayOfStuff: array<string> = ["An", "array", "of", "strings"]
```


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

