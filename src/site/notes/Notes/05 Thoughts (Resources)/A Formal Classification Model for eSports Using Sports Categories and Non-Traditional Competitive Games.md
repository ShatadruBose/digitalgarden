---
{"dg-publish":true,"dg-home":null,"tags":["thoughts"],"permalink":"/notes/05-thoughts-resources/a-formal-classification-model-for-e-sports-using-sports-categories-and-non-traditional-competitive-games/","dgPassFrontmatter":true,"updated":"2026-07-16T15:55:59.360+05:30"}
---

# A Formal Classification Model for eSports Using Sports Categories and Non-Traditional Competitive Games

## Core Formula

$$
z = \sum_{i=1}^{n} s_i + \theta
$$

## Abstract

This paper proposes a mathematical classification framework for eSports. The framework divides the eSports ecosystem into two primary domains:

1. Sports-based competitive games.
2. Non-traditional competitive games.

The total eSports domain is represented by:

$$
z = \sum_{i=1}^{n} s_i + \theta
$$

where:

- $z$ = Total eSports domain
- $s_i$ = Individual sports-game categories
- $n$ = Number of sports-game categories
- $\theta$ = Non-traditional competitive game categories

This model provides a simple, scalable, and logically structured method for organizing competitive gaming.

---

# 1. Introduction

The term "eSports" covers a wide range of competitive digital activities. Some games are direct simulations of real-world sports, while others are entirely digital competitions without a physical sports counterpart.

Examples:

| Type | Examples |
|--------|--------|
| Sports eSports | FC, eFootball, NBA 2K, F1, Cricket Games |
| Non-Traditional eSports | Chess.com, Valorant, Counter-Strike, Dota 2, League of Legends |

To formally classify these categories, the eSports Formula is proposed.

---

# 2. Mathematical Definition

The complete eSports ecosystem is defined as:

$$
z = \sum_{i=1}^{n} s_i + \theta
$$

This means:

$$
\text{eSports}
=
\text{Sports eSports}
+
\text{Non-Traditional eSports}
$$

---

# 3. Sports eSports Component

Sports eSports are represented by:

$$
\sum_{i=1}^{n} s_i
$$

where each $s_i$ represents a sports category.

Examples:

$$
s_1 = \text{Football}
$$

$$
s_2 = \text{Cricket}
$$

$$
s_3 = \text{Basketball}
$$

$$
s_4 = \text{Tennis}
$$

$$
s_5 = \text{Racing}
$$

$$
s_6 = \text{Hockey}
$$

$$
s_7 = \text{Baseball}
$$

Thus:

$$
\sum_{i=1}^{n} s_i
=
s_1+s_2+s_3+\cdots+s_n
$$

Sports eSports include any competitive game directly derived from a recognized physical sport.

---

# 4. Theta Component

The symbol:

$$
\theta
$$

represents all non-traditional competitive games.

These games are competitive but are not simulations of physical sports.

Examples:

- Chess
- FPS
- MOBA
- RTS
- Fighting Games
- Battle Royale
- Tactical Shooters
- Digital Card Games

Examples of titles:

- Chess.com
- Valorant
- Counter-Strike
- Dota 2
- League of Legends
- StarCraft II
- Street Fighter
- Tekken

Therefore:

$$
\theta
=
\text{All Non-Traditional Competitive Games}
$$

---

# 5. Expanded Formula

The formula may be expanded as:

$$
z
=
s_1+s_2+s_3+s_4+\cdots+s_n+\theta
$$

This explicitly includes every sports category together with all non-traditional competitive categories.

---

# 6. Hierarchical Representation

```text
eSports (z)
├── Sports eSports (Σsᵢ)
│   ├── Football
│   ├── Cricket
│   ├── Basketball
│   ├── Tennis
│   ├── Racing
│   ├── Hockey
│   └── Other Sports
│
└── θ (Theta)
    ├── Chess
    ├── FPS
    ├── MOBA
    ├── RTS
    ├── Fighting Games
    ├── Battle Royale
    └── Other Competitive Games
```

---

# 7. Properties

## Property 1: Completeness

Every competitive game belongs either to:

$$
\sum s_i
$$

or

$$
\theta
$$

Therefore every competitive title can be classified.

---

## Property 2: Scalability

New sports categories create new values of $s_i$.

New non-traditional categories are added inside $\theta$.

The core formula remains unchanged.

---

## Property 3: Simplicity

Only two major branches are required:

- Sports eSports
- Non-Traditional eSports

This makes the classification easy to understand and maintain.

---

## Property 4: Extensibility

Future categories may be added without modifying the structure of the model.

---

# 8. Examples

## Example A

FC

Classification:

$$
FC \in s_1
$$

where $s_1$ represents Football.

---

## Example B

F1

Classification:

$$
F1 \in s_5
$$

where $s_5$ represents Racing.

---

## Example C

Chess.com

Classification:

$$
Chess.com \in \theta
$$

---

## Example D

Valorant

Classification:

$$
Valorant \in \theta
$$

---

## Example E

Dota 2

Classification:

$$
Dota2 \in \theta
$$

---

# 9. The eSports Theorem

The eSports Theorem states:

> Every competitive digital game belongs either to a sports-game category $s_i$ or to the non-traditional category $\theta$.

Formally:

$$
z
=
\sum_{i=1}^{n} s_i
+
\theta
$$

---

# 10. Conclusion

The proposed eSports Formula establishes a mathematical structure for classifying competitive digital games.

The model separates:

- Sports-based competitive games.
- Non-traditional competitive games.

into a single unified framework.

The defining equation is:

$$
\boxed{
z
=
\sum_{i=1}^{n} s_i
+
\theta
}
$$

This equation provides a concise, scalable, and comprehensive representation of the entire eSports ecosystem.
