---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/equal-area-circle-partitions-and-their-connection-to-the-yin-yang-symbol/","dgPassFrontmatter":true,"updated":"2026-10-13T18:00:50.991+05:30"}
---

# Equal-Area Circle Partitions and Their Connection to the Yin–Yang Symbol

## Abstract

A circle is commonly divided into three equal areas by drawing three sectors of 120° each. While mathematically correct, this approach relies entirely on rotational symmetry and produces simple wedges.

A more unusual construction divides the circle into three equal areas using **nested semicircles** based on **trisecting the diameter**. The resulting regions resemble the flowing curves found in the **Yin–Yang (Taijitu)** symbol. Although the construction is not the traditional method used to create a Yin–Yang, both share important geometric ideas: circles inside circles, complementary curved boundaries, and balance through symmetry.

---

# 1. The Classical Method

The standard way to divide a circle into three equal areas is:

- Draw an equilateral triangle inside the circle.
- Connect the center to each vertex.
- This creates three sectors of 120°.
- Since each sector covers one-third of the full angle (360°), each has one-third of the total area.

This method is simple but produces only straight radial boundaries.

---

# 2. A More Interesting Construction

Instead of dividing by angle:

1. Draw the circle.
2. Trisect its diameter.
3. Construct:
   - the original semicircle,
   - a semicircle with diameter 2/3,
   - a semicircle with diameter 1/3.

These nested semicircles create curved regions.

---

# 3. Area Calculation

Suppose the original circle has radius **r**.

The upper semicircle has area

$$
\frac{\pi r^2}{2}
$$

---

## Large inner semicircle

Its radius is

$$
\frac{2r}{3}
$$

Area

$$
\frac{\pi}{2}\left(\frac{2r}{3}\right)^2
=
\frac{\pi}{2}\cdot\frac{4r^2}{9}
$$

Remaining area

$$
\frac{\pi}{2}\cdot\frac{5r^2}{9}
$$

---

## Small inner semicircle

Its radius is

$$
\frac{r}{3}
$$

Area

$$
\frac{\pi}{2}\cdot\frac{r^2}{9}
$$

Area between the two semicircles

$$
\frac{\pi}{2}\cdot\frac{3r^2}{9}
$$

---

## Smallest region

The innermost semicircle itself has area

$$
\frac{\pi}{2}\cdot\frac{1r^2}{9}
$$

Define

$$
z=\frac{\pi r^2}{18}
$$

The three upper regions therefore have areas

- z
- 3z
- 5z

These satisfy

$$
z+3z+5z=9z
$$

which equals the area of the upper semicircle.

---

# 4. The Rotation Trick

Now rotate these three regions by **180°** into the lower half of the circle.

Each region is paired with its opposite copy.

Areas become

- z + 5z = 6z
- 3z + 3z = 6z
- 5z + z = 6z

Therefore all three final regions have identical area

$$
6z
=
\frac{\pi r^2}{3}
$$

which is exactly one-third of the whole circle.

---

# 5. Why This Is Beautiful

Unlike ordinary sector division,

- no straight radial boundaries are used,
- every boundary is circular,
- every region flows smoothly,
- the construction is based entirely on nested circles.

This makes the partition visually elegant and mathematically surprising.

---

# 6. Relationship to the Yin–Yang Symbol

The famous Yin–Yang (Taijitu) symbol is constructed using circular arcs.

Its main characteristics include

- one circle
- S-shaped boundary
- two complementary regions
- rotational symmetry
- nested circles
- continuous curvature

The equal-area partition above shares many of these properties.

---

## Similarities

### Circular boundaries

Neither construction relies on straight lines.

Everything is built from arcs of circles.

---

### Nested circles

Both use circles inside circles rather than polygons.

---

### Rotational symmetry

The construction becomes balanced after a 180° rotation.

The Taijitu also has 180° rotational symmetry.

---

### Complementary regions

The Yin–Yang consists of two complementary halves.

This construction forms three complementary equal-area regions.

---

### Flowing geometry

Instead of sharp corners, boundaries curve naturally.

This gives both figures an organic appearance.

---

# 7. Important Difference

The construction **is not** the traditional geometric construction of the Yin–Yang.

The Taijitu has its own historical and geometric design involving:

- an S-shaped divider,
- two equal lobes,
- two small opposite circles,
- philosophical symbolism of Yin and Yang.

The equal-area partition is a modern mathematical construction focused purely on geometry.

Its resemblance is visual rather than historical.

---

# 8. Mathematical Significance

This construction demonstrates several beautiful ideas.

## Area can be controlled by radius

Since

$$
A=\pi r^2,
$$

changing the radius changes area quadratically.

---

## Equal areas need not have equal shapes

The three regions look completely different.

Yet all have identical area.

---

## Symmetry can preserve area

Rotating and pairing regions creates balance without changing total area.

---

## Curves can replace straight boundaries

Equal partitions are possible using only circular arcs.

---

# 9. Possible Extensions

The same philosophy suggests many research questions.

- Divide a circle into four equal curved regions.
- Divide into five or more equal curved regions.
- Use quarter-circles instead of semicircles.
- Generalize to spheres in three dimensions.
- Explore artistic tilings based on nested circles.

---

# 10. Conclusion

The nested-semicircle construction offers an elegant alternative to the standard sector-based division of a circle into three equal areas. By trisecting the diameter, constructing semicircles, and pairing complementary regions through a 180° rotation, the circle is partitioned into three regions of identical area despite their very different shapes.

Although it is **not** the traditional construction of the Yin–Yang symbol, it shares many visual and geometric principles with the Taijitu: circular arcs, rotational symmetry, nested circles, flowing boundaries, and a sense of balanced composition. This makes it an appealing example of how mathematical geometry can produce forms that echo iconic artistic and philosophical designs.