# kasl

`kasl` is an umbrella crate that includes re-exports of `kasl-core` and backends (currently there is only Cranelift backend).

# About the KASL language

KASL is a programming language designed for audio processing.
The KASL language itself is implemented as a simple numerical calculation language with unique `input`, `output` and `state` variables, and can be used for audio processing with my [Knodiq DAW](https://github.com/hatya-mouse/knodiq), which is under development.

## How to Run the KASL Programs

Currently, there are no hosts that can run KASL program for audio processing.
However, you can run KASL code for genuine numerical calculation and there two ways to run it:

- [`kaslc`](https://github.com/hatya-mouse/kaslc) — A command-line tool to run KASL programs locally.
- [`kasl.hatya.dev`](https://kasl.hatya.dev) — Features **online KASL playground** where you can run KASL programs without installation.

## Examples

### Example 1 — Fibonacci

The following program calculates the fibonacci sequence by using `state` variable to store the last two numbers.
I recommend running this program on the online playground, since it can show the outputs for each iterations, while `kaslc` can only show the output from the last iteration.

```kasl
import std

state a = 0
state b = 1
output result = 0

func main() {
    result = a
    let next = a + b
    a = b
    b = next
}
```

### Example 2 — Audio Processing

Here's an example KASL code which calculates the value of the sine function. The program outputs an output variable called `out`.

```kasl
import std
import math/float

state x = 0.0
output y = 0.0

func main() {
    y = float.sin(x)
    x = x + 0.1
}
```
