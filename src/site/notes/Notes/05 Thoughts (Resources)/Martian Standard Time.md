---
{"dg-publish":true,"dg-home":null,"tags":null,"aliases":null,"permalink":"/notes/05-thoughts-resources/martian-standard-time/","dgPassFrontmatter":true,"updated":"2026-10-13T17:59:31.932+05:30"}
---

# 🔴 Martian Standard Time (MST)

## 1. Overview

**Martian Standard Time (MST)** is a proposed civil timekeeping system for Mars. It uses the **SI second as its fundamental physical time unit**, while defining larger Martian calendar and clock units around a fixed Martian day structure.

The system is defined by:

- **Epoch:** `1971-12-02T13:47:00Z`
- **1 Martian minute:** 67 SI seconds
- **1 Martian hour:** 53 Martian minutes
- **1 Martian day:** 25 Martian hours
- **1 Martian year:** 687 Martian days
- **Calendar:** 3 months of 229 Martian days each
- **Leap adjustment:** +244 SI seconds every 1,000 Martian days

---

# 2. Fundamental Time Unit

## SI Second

MST does not redefine the physical second.

The fundamental unit remains the **SI second**:

> **1 SI second = 1 SI second**

Therefore, MST can be related directly to terrestrial UTC and other SI-based timescales.

All Martian units are integer multiples of the SI second.

---

# 3. Martian Minute

A Martian minute is defined as:

> **1 Martian minute = 67 SI seconds**

Therefore:

```text
1 Martian minute = 67 s
```

A Martian minute is intentionally longer than a terrestrial minute:

```text
Terrestrial minute = 60 s
Martian minute     = 67 s
```

Difference:

```text
67 − 60 = 7 s
```

Thus, one Martian minute contains **7 more SI seconds** than a conventional terrestrial minute.

---

# 4. Martian Hour

A Martian hour contains exactly **53 Martian minutes**.

Therefore:

```text
1 Martian hour
= 53 × 67 SI seconds
= 3,551 SI seconds
```

So:

> **1 Martian hour = 53 Martian minutes = 3,551 SI seconds**

The internal structure is:

```text
53 Martian minutes/hour
67 SI seconds/Martian minute
```

Consequently:

```text
53 × 67 = 3,551
```

---

# 5. Martian Day

A Martian day contains exactly **25 Martian hours**.

Therefore:

```text
1 Martian day
= 25 × 3,551 SI seconds
= 88,775 SI seconds
```

Thus:

> **1 Martian day = 25 Martian hours = 88,775 SI seconds**

The complete hierarchy is:

```text
1 Martian day
    = 25 Martian hours
    = 25 × 53 Martian minutes
    = 1,325 Martian minutes
    = 88,775 SI seconds
```

Therefore:

```text
1 Martian day = 88,775 SI seconds
```

---

# 6. Complete Clock Hierarchy

The complete MST clock is:

```text
1 Martian minute = 67 SI seconds

1 Martian hour
= 53 Martian minutes
= 3,551 SI seconds

1 Martian day
= 25 Martian hours
= 1,325 Martian minutes
= 88,775 SI seconds
```

In multiplicative form:

```text
1 day
= 25 hours

1 hour
= 53 minutes

1 minute
= 67 seconds
```

Therefore:

```text
1 day
= 25 × 53 × 67 SI seconds
= 88,775 SI seconds
```

---

# 7. Martian Clock Notation

A civil MST timestamp can be represented using:

```text
DD:HH:MM:SS
```

where:

- `DD` = Martian day
- `HH` = Martian hour
- `MM` = Martian minute
- `SS` = SI seconds within the Martian minute

The permitted ranges are:

```text
Martian hour:
00–24

Martian minute:
00–52

SI second:
00–66
```

The clock therefore has:

```text
25 hours/day
53 minutes/hour
67 seconds/minute
```

The final valid clock value before the next Martian day is:

```text
24:52:66
```

The next SI second begins:

```text
00:00:00
```

of the following Martian day.

---

# 8. Number of SI Seconds per Martian Day

One MST day contains:

```text
88,775 SI seconds
```

For comparison, a conventional 86,400-second terrestrial day is shorter by:

```text
88,775 − 86,400
= 2,375 SI seconds
```

Therefore, the proposed MST civil day is:

```text
2,375 SI seconds
```

longer than a conventional 24-hour terrestrial day.

In hours:

```text
2,375 / 3,600
≈ 0.659722 terrestrial hours
```

or approximately:

```text
39 minutes 35 seconds
```

longer than a conventional terrestrial day.

---

# 9. Martian Year

The MST calendar defines a Martian year as:

> **687 Martian days**

The year contains exactly three calendar months.

Each month contains:

```text
229 Martian days
```

Therefore:

```text
3 × 229
= 687 Martian days
```

So:

> **1 Martian year = 687 Martian days**

---

# 10. Martian Year in MST Clock Units

Each Martian day contains:

```text
25 Martian hours
```

Therefore one Martian year contains:

```text
687 × 25
= 17,175 Martian hours
```

Each Martian hour contains:

```text
53 Martian minutes
```

Therefore:

```text
17,175 × 53
= 910,275 Martian minutes
```

Each Martian minute contains:

```text
67 SI seconds
```

Therefore the nominal SI duration of one MST year is:

```text
910,275 × 67
= 60,988,425 SI seconds
```

Thus:

> **1 nominal MST year = 60,988,425 SI seconds**

before applying the periodic leap adjustment.

---

# 11. Calendar Structure

The MST calendar contains exactly:

```text
3 months/year
229 days/month
687 days/year
```

The months are named after major Martian-associated bodies and mythology:

1. **Ares**
2. **Phobos**
3. **Deimos**

---

# 12. Month 1 — Ares

**Ares** is the first month of the MST calendar.

Its range is:

```text
Days 1–229
```

Therefore:

```text
Ares = 229 Martian days
```

The first day of every MST year begins:

```text
Ares 1
```

and the final day of Ares is:

```text
Ares 229
```

---

# 13. Month 2 — Phobos

**Phobos** is the second month.

Its range is:

```text
Days 230–458
```

Therefore:

```text
Phobos = 229 Martian days
```

The month begins immediately after Ares 229:

```text
Ares 229
→
Phobos 1
```

In absolute year-day numbering:

```text
Phobos 1 = Day 230
```

and:

```text
Phobos 229 = Day 458
```

---

# 14. Month 3 — Deimos

**Deimos** is the third and final month.

Its range is:

```text
Days 459–687
```

Therefore:

```text
Deimos = 229 Martian days
```

The final day of the MST year is:

```text
Deimos 229
```

which is:

```text
Year Day 687
```

The next day begins:

```text
Ares 1
```

of the next MST year.

---

# 15. Complete Calendar

| Month | Month Number | Day Range | Length |
|---|---:|---:|---:|
| Ares | 1 | 1–229 | 229 days |
| Phobos | 2 | 230–458 | 229 days |
| Deimos | 3 | 459–687 | 229 days |
| **Total** | **3** | **1–687** | **687 days** |

The calendar is therefore perfectly symmetrical:

```text
Ares   = 229 days
Phobos = 229 days
Deimos = 229 days
-------------------
Total  = 687 days
```

---

# 16. MST Epoch

The MST epoch is:

```text
1971-12-02T13:47:00Z
```

This instant establishes the origin of the MST timescale.

At the epoch:

```text
MST Year = 1
Month    = Ares
Day      = 1
```

and the civil clock begins at:

```text
00:00:00
```

Therefore the fundamental epoch relationship is:

```text
1971-12-02T13:47:00Z
=
MST Year 1, Ares 1, Day 1, 00:00:00
```

The epoch is an **instant in UTC**, while MST subsequently advances according to the defined Martian clock.

---

# 17. Day Counting

The calendar uses one-based day numbering within a year.

Therefore:

```text
Ares 1   = Year Day 1
Ares 229 = Year Day 229

Phobos 1   = Year Day 230
Phobos 229 = Year Day 458

Deimos 1   = Year Day 459
Deimos 229 = Year Day 687
```

After:

```text
Deimos 229, 24:52:66
```

the calendar advances to:

```text
Next Year, Ares 1, 00:00:00
```

---

# 18. Leap Adjustment

Because the fixed MST civil day is not perfectly identical to the physical Martian rotational day, MST contains a periodic correction mechanism.

The defined correction is:

> **+244 SI seconds every 1,000 Martian days**

This is a **positive leap adjustment**.

It adds 244 SI seconds to the accumulated MST timescale at each 1,000-Martian-day boundary.

---

# 19. Leap Adjustment Rule

The basic rule is:

```text
Every 1,000 Martian days:
    add 244 SI seconds
```

Therefore:

```text
1,000 days → +244 s
2,000 days → +244 s
3,000 days → +244 s
4,000 days → +244 s
...
```

The adjustment is cumulative.

For example:

```text
After 1,000 days:
+244 s

After 2,000 days:
+488 s

After 3,000 days:
+732 s

After 4,000 days:
+976 s
```

In general:

```text
Leap adjustment =
244 × floor(N / 1,000) SI seconds
```

where `N` is the number of elapsed Martian days from the epoch.

---

# 20. Leap Adjustment Equivalent

The correction rate is:

```text
244 / 1,000
= 0.244 SI seconds/Martian day
```

Therefore the long-term correction rate is:

> **+0.244 SI seconds per Martian day**

or:

```text
244 ms/day
```

on average.

The correction is not continuously distributed. Instead, the system applies the accumulated correction at the defined 1,000-day boundaries.

---

# 21. Leap Adjustment and the Martian Year

One MST year contains:

```text
687 days
```

The leap adjustment occurs every:

```text
1,000 days
```

Therefore leap boundaries do **not** coincide with every calendar year.

For example:

```text
Year 1:
Days 1–687

Year 2:
Days 688–1,374
```

The first 1,000-day adjustment occurs during the second MST year.

Specifically:

```text
1,000 − 687
= 313
```

Therefore the first leap boundary occurs on:

```text
MST Year 2, Day 313
```

Since:

```text
Ares     = Days 1–229
Phobos   = Days 230–458
```

Day 313 falls in:

```text
Phobos
```

Its month-relative day is:

```text
313 − 229
= 84
```

Therefore:

> **The first +244-second adjustment occurs during Year 2, Phobos 84.**

---

# 22. Subsequent Leap Boundaries

The calendar has 687 days per year, while leap corrections occur every 1,000 days.

The cumulative day positions are:

```text
1,000 days
2,000 days
3,000 days
4,000 days
5,000 days
...
```

Converting these to MST years:

```text
1,000 / 687 ≈ 1.456 years
2,000 / 687 ≈ 2.911 years
3,000 / 687 ≈ 4.367 years
4,000 / 687 ≈ 5.822 years
5,000 / 687 ≈ 7.278 years
```

Thus the leap schedule naturally moves through different positions in the calendar from year to year.

---

# 23. Long-Term Leap Accumulation

After `N` complete 1,000-day intervals, the total adjustment is:

```text
244N SI seconds
```

Examples:

```text
1,000 days  → +244 s
2,000 days  → +488 s
3,000 days  → +732 s
4,000 days  → +976 s
5,000 days  → +1,220 s
6,000 days  → +1,464 s
7,000 days  → +1,708 s
8,000 days  → +1,952 s
9,000 days  → +2,196 s
10,000 days → +2,440 s
```

The 10,000-day correction is therefore:

```text
2,440 SI seconds
```

which is:

```text
40 minutes 40 seconds
```

---

# 24. Relationship Between Calendar and Clock

The MST system has two distinct layers:

## Civil Calendar

```text
3 months
229 days/month
687 days/year
```

## Civil Clock

```text
25 hours/day
53 minutes/hour
67 SI seconds/minute
```

The calendar determines **which Martian date it is**, while the clock determines **the position within that Martian day**.

---

# 25. Complete MST Definition

The system can be expressed compactly as:

```text
MST Epoch:
1971-12-02T13:47:00Z

1 Martian minute:
67 SI seconds

1 Martian hour:
53 Martian minutes
= 3,551 SI seconds

1 Martian day:
25 Martian hours
= 1,325 Martian minutes
= 88,775 SI seconds

1 Martian year:
687 Martian days

Calendar:
3 months/year
229 days/month

Month 1:
Ares — Days 1–229

Month 2:
Phobos — Days 230–458

Month 3:
Deimos — Days 459–687

Leap adjustment:
+244 SI seconds every 1,000 Martian days
```

---

# 26. Mathematical Definition

Let:

```text
S = SI seconds
m = Martian minutes
h = Martian hours
d = Martian days
y = Martian years
```

Then:

```text
1 m = 67 S

1 h = 53m
    = 53 × 67 S
    = 3,551 S

1 d = 25h
    = 25 × 53 × 67 S
    = 88,775 S

1 y = 687d
    = 687 × 88,775 S
    = 60,988,425 S
```

The leap correction after `D` elapsed Martian days is:

```text
L(D) = 244 × floor(D / 1,000) S
```

The resulting adjusted MST elapsed time is therefore conceptually:

```text
MST elapsed time
=
D × 88,775 S
+
time-within-day
+
L(D)
```

where the exact placement convention for the leap insertion must be specified by the final MST implementation.

---

# 27. Year-to-Year Structure

Every normal MST year has exactly:

```text
687 days
```

and:

```text
17,175 Martian hours
```

and:

```text
910,275 Martian minutes
```

and:

```text
60,988,425 nominal SI seconds
```

before leap adjustments.

The calendar therefore remains structurally constant:

```text
Year
├── Ares
│   └── 229 days
├── Phobos
│   └── 229 days
└── Deimos
    └── 229 days
```

---

# 28. Calendar Rollover

At the end of the final day:

```text
Deimos 229, 24:52:66
```

the next SI second produces:

```text
Ares 1, 00:00:00
```

of the next MST year.

Thus:

```text
Deimos 229 → Ares 1
```

and:

```text
Year N → Year N+1
```

occur simultaneously.

---

# 29. Design Characteristics

MST has several deliberate characteristics.

### 29.1 SI-Compatible Foundation

The fundamental physical unit is unchanged:

```text
1 SI second
```

This allows MST to be implemented using ordinary atomic-clock-derived SI timing.

### 29.2 Integer-Based Clock

Every major unit is an integer multiple of the previous unit:

```text
67 SI seconds/minute
53 minutes/hour
25 hours/day
```

There are no fractional seconds in the basic unit definitions.

### 29.3 25-Hour Day

The Martian civil day contains:

```text
25 hours
```

rather than Earth's conventional 24-hour structure.

### 29.4 53-Minute Hour

Every Martian hour contains:

```text
53 Martian minutes
```

### 29.5 67-Second Minute

Every Martian minute contains:

```text
67 SI seconds
```

### 29.6 687-Day Calendar

The calendar contains:

```text
687 days/year
```

matching the intended Martian-year structure.

### 29.7 Three Equal Months

Every month has exactly:

```text
229 days
```

giving:

```text
229 + 229 + 229 = 687
```

### 29.8 Periodic Correction

The timescale includes:

```text
+244 SI seconds
```

at every:

```text
1,000 Martian days
```

to provide a long-term correction mechanism.

---

# 30. Official Month Table

```text
MONTH 1
Name: Ares
Length: 229 Martian days
Year days: 1–229

MONTH 2
Name: Phobos
Length: 229 Martian days
Year days: 230–458

MONTH 3
Name: Deimos
Length: 229 Martian days
Year days: 459–687
```

---

# 31. Official Unit Table

| Unit | Definition | SI Duration |
|---|---|---:|
| SI second | Fundamental unit | 1 s |
| Martian minute | 67 SI seconds | 67 s |
| Martian hour | 53 Martian minutes | 3,551 s |
| Martian day | 25 Martian hours | 88,775 s |
| Martian year | 687 Martian days | 60,988,425 s |

---

# 32. Official Calendar Table

| Calendar Unit | Definition |
|---|---:|
| Month | 229 Martian days |
| Year | 687 Martian days |
| Ares | Days 1–229 |
| Phobos | Days 230–458 |
| Deimos | Days 459–687 |

---

# 33. Official Leap Rule

```text
IF elapsed Martian days MOD 1,000 = 0
THEN apply +244 SI seconds.
```

Equivalently:

```text
Every 1,000 elapsed Martian days:
    MST += 244 SI seconds
```

The correction is cumulative and does not change the nominal calendar structure.

---

# 34. Reference Epoch

The complete initial condition is:

```text
UTC:
1971-12-02T13:47:00Z

MST:
Year 1
Ares
Day 1
00:00:00
```

This instant is the zero point from which the MST timescale is counted.

---

# 35. Compact Specification

```text
╔══════════════════════════════════════════╗
║       MARTIAN STANDARD TIME — MST        ║
╠══════════════════════════════════════════╣
║ Epoch                                    ║
║ 1971-12-02T13:47:00Z                     ║
║                                          ║
║ 1 Martian minute                         ║
║ 67 SI seconds                            ║
║                                          ║
║ 1 Martian hour                           ║
║ 53 Martian minutes                       ║
║ 3,551 SI seconds                         ║
║                                          ║
║ 1 Martian day                            ║
║ 25 Martian hours                         ║
║ 1,325 Martian minutes                    ║
║ 88,775 SI seconds                        ║
║                                          ║
║ 1 Martian year                           ║
║ 687 Martian days                         ║
║ 3 months                                 ║
║                                          ║
║ Month 1                                  ║
║ Ares — 229 days                          ║
║                                          ║
║ Month 2                                  ║
║ Phobos — 229 days                        ║
║                                          ║
║ Month 3                                  ║
║ Deimos — 229 days                        ║
║                                          ║
║ Leap adjustment                          ║
║ +244 SI seconds / 1,000 Martian days    ║
╚══════════════════════════════════════════╝
```

---

# 36. One-Line Definition

> **Martian Standard Time (MST) is a Mars-based civil timescale beginning at 1971-12-02T13:47:00Z, with 67 SI-second minutes, 53-minute hours, 25-hour days of 88,775 SI seconds, 687-day years divided into Ares, Phobos, and Deimos of 229 days each, and a +244 SI-second adjustment every 1,000 Martian days.**

---

# 37. Final Specification

```text
MARTIAN STANDARD TIME (MST)

Epoch:
1971-12-02T13:47:00Z

Fundamental unit:
SI second

Clock:
67 SI seconds/minute
53 Martian minutes/hour
25 Martian hours/day

Therefore:
1 Martian hour = 3,551 SI seconds
1 Martian day  = 88,775 SI seconds

Calendar:
687 Martian days/year
3 months/year
229 Martian days/month

Months:
Ares   = Days 1–229
Phobos = Days 230–458
Deimos = Days 459–687

Leap rule:
+244 SI seconds every 1,000 Martian days

First leap boundary:
Day 1,000 from the epoch
= Year 2, Phobos 84

Nominal year duration:
60,988,425 SI seconds

Core structure:
25 hours/day
53 minutes/hour
67 seconds/minute
3 months/year
229 days/month
687 days/year
+244 SI seconds/1,000 days
```
:::