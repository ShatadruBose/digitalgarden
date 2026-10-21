---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/argumentlet/","dgPassFrontmatter":true,"updated":"2026-10-13T18:02:06.176+05:30","dg-note-properties":{"tags":null,"aliases":null}}
---

# Argumentlet: Executable Function Arguments for Storage Efficiency

**Version:** Concept Paper v1.0  
**Status:** Experimental Programming Language Concept  
**Author:** Open Design Proposal

---

# Abstract

Argumentlet is a proposed programming language feature where a function argument can contain an executable statement instead of merely a computed value.

Unlike traditional function calls, where expressions are evaluated before the function executes, an Argumentlet is stored as executable code and evaluated only when (or if) needed.

This enables:

- Deferred execution
- Reduced temporary object creation
- Better storage efficiency
- Lazy evaluation
- Compile-time optimization opportunities

The concept is inspired by lambdas, thunks, macros, and expression trees but introduces a much lighter syntax designed specifically for function arguments.

---

# Motivation

Traditional languages work like this:

```python
print("Hello " + name)
```

Evaluation steps:

1. Load string.
2. Load variable.
3. Allocate temporary string.
4. Concatenate.
5. Pass result to print().
6. Temporary object destroyed.

The temporary concatenated string exists only for a moment.

Argumentlet attempts to eliminate this unnecessary temporary allocation.

---

# Proposed Syntax

Instead of passing the evaluated result:

```python
print("Hello " + name)
```

Pass the statement itself.

```python
print({"Hello " + name})
```

or

```python
print({statement})
```

Everything inside `{}` becomes an Argumentlet.

The function receives executable code instead of the final value.

---

# Basic Example

Traditional

```python
print(a + b)
```

Memory

```
a
b
↓

a+b

↓

print(result)
```

Argumentlet

```python
print({a+b})
```

Memory

```
a
b

↓

Store AST

↓

print executes AST
```

No temporary result needs to exist before entering the function.

---

# Internal Representation

Instead of

```
Value:
42
```

store

```
BinaryExpression
    +
   / \
  a   b
```

The function owns the expression.

---

# Example

```python
print({"Hello " + username})
```

Internally

```
PrintFunction

Argument:

Concatenate

Left:
"Hello "

Right:
username
```

---

# Delayed Evaluation

Traditional

```
calculate()

↓

result

↓

print(result)
```

Argumentlet

```
print(

calculate()

)

↓

calculate runs only when print asks for it
```

This is similar to lazy evaluation.

---

# Multiple Argumentlets

```python
log(
    {current_time()},
    {user.name},
    {calculate()}
)
```

Nothing executes until `log()` evaluates each Argumentlet.

---

# Storage Efficiency

Traditional

```
Expression

↓

Temporary value

↓

Function
```

Argumentlet

```
Expression

↓

Stored directly

↓

Executed inside function
```

The temporary value can often be skipped.

---

# Compiler Optimization

The compiler may

- Inline expressions
- Merge operations
- Eliminate dead expressions
- Delay evaluation
- Cache repeated expressions

Example

```python
print({
    expensiveCalculation()
})
```

If print never needs it,

the calculation never runs.

---

# Comparison

## Traditional

```python
print(square(x))
```

Execution

```
square()

↓

number

↓

print()
```

---

## Argumentlet

```python
print({square(x)})
```

Execution

```
Store AST

↓

print()

↓

square()

↓

output
```

---

# Nested Argumentlets

```python
print({

    sqrt(

        square(x)

    )

})
```

Entire syntax tree is stored.

Nothing executes immediately.

---

# Conditional Execution

```python
debug({
    expensiveCalculation()
})
```

If debugging is disabled

```
Argument discarded

No calculation occurs.
```

---

# Memory Benefits

Possible reductions:

- Temporary strings
- Temporary arrays
- Temporary objects
- Intermediate calculations
- Stack allocations
- Heap allocations

This is especially beneficial for

- Logging
- Debugging
- Formatting
- Assertions
- Error messages

---

# Relationship to Existing Technologies

| Technology | Similarity |
|------------|------------|
| Lambda | Stores executable code |
| Closure | Stores code and captured variables |
| Thunk | Deferred computation |
| Expression Tree | Stores syntax tree |
| Macro | Manipulates source code |
| Argumentlet | Executable function argument |

Argumentlet combines aspects of all of them while focusing on function arguments.

---

# Example API

```python
assert({
    x > 10
})
```

If assertions are disabled

```
Nothing executes.
```

Traditional Python

```
x > 10

↓

True

↓

assert(True)
```

Argumentlet

```
assert()

↓

Need expression?

↓

Evaluate

↓

Done
```

---

# Logging Example

Traditional

```python
log(
    "Position: " + str(position)
)
```

Temporary string created.

Argumentlet

```python
log({
    "Position: " + str(position)
})
```

If logging is disabled

Nothing is evaluated.

---

# Serialization

An Argumentlet may internally store:

```
Node Type

Operator

Operands

Captured Variables

Evaluation Rules

Metadata
```

This resembles an Abstract Syntax Tree (AST) rather than a computed value.

---

# Advantages

- Reduced temporary allocations
- Lazy evaluation
- Better storage efficiency
- Compiler optimization opportunities
- Faster logging
- Efficient debugging
- Deferred execution
- Cleaner API design
- Expression introspection
- Potential for parallel execution

---

# Limitations

- Requires compiler support
- More complex runtime implementation
- Captured variables must remain valid until evaluation
- Debugging may be more difficult because execution occurs later
- Some expressions may still require temporary objects during evaluation
- Side effects can become less predictable if execution is deferred

---

# Potential Applications

- Logging frameworks
- Assertions
- Debugging tools
- GUI bindings
- Database query builders
- Reactive programming
- Rule engines
- Template engines
- Game scripting
- Scientific computing

---

# Example Flow

Source

```python
print({
    "Hello " + username
})
```

Compiler

```
↓

Argument AST

↓

Store inside function call

↓

print()

↓

Evaluate AST

↓

Output

↓

Discard AST
```

---

# Future Extensions

Possible enhancements include:

- Named Argumentlets for reusable deferred expressions.
- Memoized Argumentlets that cache their first computed result.
- Compile-time evaluation of constant Argumentlets.
- Asynchronous Argumentlets for deferred concurrent execution.
- Inspectable Argumentlets that allow tools to analyze or transform expressions before execution.

---

# Conclusion

Argumentlet is a hypothetical language feature that treats function arguments as executable expression objects rather than immediately evaluated values. By storing an expression's abstract syntax tree (AST) instead of its computed result, it enables deferred execution, reduces unnecessary temporary allocations, and opens opportunities for compiler optimizations such as lazy evaluation and dead-code elimination. While it introduces additional compiler and runtime complexity, it could provide significant performance and flexibility benefits in domains like logging, debugging, reactive systems, and expression-based APIs. As a language design concept, Argumentlet represents an interesting blend of expression trees, thunks, and lambdas with a dedicated focus on efficient, executable function arguments.