# EXCA
> Extended EMCAScript

Basically just stage-0+ babel plugins and a custom resolver for modules right now.

## Usage (from this folder)
> `npm run exca run help`

## Features

### Binary Operator Overloading

```js
'exca overloads enable'

class Vec2D {
  point = [0, 0]

  constructor(x, y) {
    this.point = [x, y]
  }

  get x() { return this.point[0] }
  get y() { return this.point[1] }
  
  set x(val) { this.point[0] = val }
  set y(val) { this.point[1] = val }

  [Symbol.for("+")](right) {
    return new this.constructor(this.x + right.x, this.y + right.y)
  }
}

let pos = new Vec2D(3, 5)
let vel = new Vec2D(2, 3)

// no += yet.
pos = pos + vel
// Vec2D(5, 8)
```

## Todo:
- checking and resolving import maps for every import (where possible)
- babel macros
- wasm importing and maybe some default compiled language that can be imported