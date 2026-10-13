---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/order-of-arithmetic/","dgPassFrontmatter":true,"updated":"2026-10-13T17:52:13.203+05:30"}
---

# Order of Arithmetic (OOA)

**Version:** OOA 1.0  
**Mnemonic:** **VBBPOEDMSA**  
**Expanded Form:** **Vendiculum → Brackets → Braces → Parentheses → Of → Exponents → Division → Multiplication → Subtraction → Addition**.

---

# Abstract

The **Order of Arithmetic (OOA)** is a proposed arithmetic evaluation system that extends the traditional order of operations by introducing additional grouping symbols and by treating some operations as transformations before evaluation.

Unlike the conventional **PEMDAS/BODMAS/BIDMAS**, OOA explicitly defines how arithmetic expressions are simplified through a sequence of conversion rules.

The mnemonic is:

> **VBBPOEDMSA**

where Division and Subtraction are interpreted as transformations into Multiplication and Addition respectively.

---

# Purpose

OOA aims to:

- Create a deterministic evaluation order.
- Separate every grouping symbol into its own precedence.
- Express arithmetic using fewer primitive operations.
- Demonstrate arithmetic as a sequence of algebraic rewrites.

---

# The OOA Sequence

| Step | Name           | Description                                             |
| ---- | -------------- | ------------------------------------------------------- |
| 1    | Vendiculum     | Evaluate expressions under a vinculum (horizontal bar). |
| 2    | Brackets       | Evaluate `[ ]`.                                         |
| 3    | Braces         | Evaluate `{ }`.                                         |
| 4    | Parentheses    | Evaluate `( )`.                                         |
| 5    | Of             | Evaluate the "of" operator (usually multiplication).    |
| 6    | Exponents      | Powers and roots.                                       |
| 7    | Division       | Convert into multiplication by reciprocal.              |
| 8    | Multiplication | Multiply values.                                        |
| 9    | Subtraction    | Convert into addition of the additive inverse.          |
| 10   | Addition       | Perform all additions.                                  |

---

# Step 1 — Vendiculum

A **vendiculum** (commonly called a **vinculum**) is a horizontal bar placed over an expression.

Example

```
  5+3
-------
   2
```

Everything beneath the bar is evaluated first.

---

# Step 2 — Brackets

Evaluate square brackets.

Example

```
[8−3]
```

↓

```
5
```

---

# Step 3 — Braces

Evaluate curly braces.

Example

```
{7+4}
```

↓

```
11
```

---

# Step 4 — Parentheses

Evaluate ordinary parentheses.

Example

```
(6×3)
```

↓

```
18
```

---

# Step 5 — Of

The word **of** is interpreted as multiplication.

Example

```
25% of 80
```

↓

```
0.25 × 80
```

↓

```
20
```

---

# Step 6 — Exponents

Evaluate powers.

Example

```
2³
```

↓

```
8
```

---

# Step 7 — Division

OOA does not consider division to be a primitive final operation.

Instead,

```
a ÷ b
```

is rewritten as

```
a × (1/b)
```

Example

```
18 ÷ 6
```

↓

```
18 × (1/6)
```

↓

```
3
```

This follows the algebraic identity

```
a ÷ b = a × b⁻¹
```

---

# Step 8 — Multiplication

Perform multiplication after all division transformations.

Example

```
8 × 5
```

↓

```
40
```

---

# Step 9 — Subtraction

OOA rewrites subtraction as addition.

```
a − b
```

becomes

```
a + (−b)
```

Example

```
15−9
```

↓

```
15 + (−9)
```

↓

```
6
```

This follows the identity

```
a − b = a + (−b)
```

---

# Step 10 — Addition

Finally perform all additions.

Example

```
12 + 9 + 5
```

↓

```
26
```

---

# Why Convert Division?

Division is multiplication by an inverse.

Instead of two operators

```
×
÷
```

OOA reduces them to one.

Example

```
24 ÷ 8 × 5
```

becomes

```
24 × (1/8) × 5
```

↓

```
3 × 5
```

↓

```
15
```

---

# Why Convert Subtraction?

Subtraction is addition of a negative number.

Instead of

```
+
−
```

OOA represents arithmetic with only addition.

Example

```
10−2−3
```

↓

```
10 + (−2) + (−3)
```

↓

```
5
```

---

# Complete Example

Expression

```
20 − 8 ÷ 4 × (3 + 1)
```

### Parentheses

```
20 − 8 ÷ 4 × 4
```

### Division

```
20 − 8 × (1/4) × 4
```

### Multiplication

```
20 − 2 × 4
```

↓

```
20 − 8
```

### Subtraction

```
20 + (−8)
```

### Addition

```
12
```

---

# Comparison with PEMDAS

| PEMDAS | OOA |
|---------|-----|
| Parentheses | Vendiculum → Brackets → Braces → Parentheses |
| Exponents | Exponents |
| Multiplication & Division | Division → Multiplication |
| Addition & Subtraction | Subtraction → Addition |
| No explicit rewrite rules | Uses algebraic transformations |

---

# Advantages

- Explicit evaluation order.
- Algebraically consistent rewrite rules.
- Demonstrates that division and subtraction are derived operations.
- Can simplify symbolic manipulation.
- Useful as an educational model for understanding arithmetic identities.

---

# Limitations

- This is **not** a standard mathematical convention.
- Conventional mathematics treats multiplication/division with equal precedence and evaluates them left-to-right.
- Likewise, addition and subtraction have equal precedence and are evaluated left-to-right.
- Most calculators, programming languages, and mathematics textbooks use standard operator precedence rather than OOA.
- Anyone using OOA should clearly state the convention to avoid ambiguity.

---

# Applications

Possible uses include:

- Experimental arithmetic notation.
- Educational demonstrations of algebraic identities.
- Symbolic mathematics systems.
- Expression rewriting engines.
- Research into alternative evaluation models.
- Custom programming language design.

---

# Summary

The **Order of Arithmetic (OOA)** is an alternative arithmetic evaluation framework based on the mnemonic:

> **VBBPOEDMSA**

1. Vendiculum
2. Brackets
3. Braces
4. Parentheses
5. Of
6. Exponents
7. Division (rewrite as multiplication by reciprocal)
8. Multiplication
9. Subtraction (rewrite as addition of a negative)
10. Addition

OOA emphasizes the idea that **division and subtraction are derived operations**, reducing arithmetic to multiplication and addition through algebraic transformations. While mathematically consistent as a rewrite system, it differs from the universally adopted order of operations and should therefore be treated as a proposed notation rather than a replacement for standard arithmetic.