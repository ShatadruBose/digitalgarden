---
{"dg-publish":true,"dg-home":null,"tags":["thoughts"],"permalink":"/notes/05-thoughts-resources/a-geometric-representation-of-games-in-micro-mezo-macro-space/","dgPassFrontmatter":true,"updated":"2026-07-16T16:04:13.393+05:30"}
---

# A Geometric Representation of Games in Micro–Mezo–Macro Space

## Abstract

Traditional game genres are often too coarse to describe what a game actually tests. Terms like “strategy,” “shooter,” or “sandbox” are useful, but they do not fully capture the balance of execution, information, planning, creativity, and other player-facing demands that define gameplay. This paper proposes a multidimensional representation of games in which each game is modeled as a geometric region in a three-axis gameplay space: Micro, Mezo, and Macro. The model is extended with summary statistics, mode-level decomposition, and auxiliary metadata such as SVG geometry, convex hull, and density functions. In addition, a complete feature vector is introduced to represent non-geometric game properties such as creativity, knowledge, logic, reflexes, cooperation, story, progression, and spatial reasoning. The result is a compact but expressive framework for classifying, comparing, and analyzing games as structured systems rather than as fixed genre labels.

---

## 1. Introduction

A game is rarely a single thing. Many games contain multiple modes, playstyles, and subgames. For example, a game may include survival play, creative construction, player-versus-player combat, speedrunning, roleplay, or cooperative progression. Each of these modes may emphasize different forms of skill and different types of decision-making.

A single genre label cannot fully describe this variation. A better representation is to treat a game as a structured object with:

1. A **center** in gameplay space.
2. A **shape** showing how widely the game varies.
3. A **set of modes** that define the game's internal structure.
4. A **feature vector** describing the game’s deeper demands and characteristics.
5. **Geometry data** that preserves the exact region.

This paper formalizes that idea.

---

## 2. The Micro–Mezo–Macro Model

The first axis system is the Micro–Mezo–Macro framework.

### 2.1 Micro
Micro represents execution-heavy gameplay.

It includes:
- Aim
- Reflexes
- Timing
- Precision
- Movement
- Mechanical consistency
- Input speed

A game high in Micro rewards the ability to perform difficult actions accurately and quickly.

### 2.2 Mezo
Mezo represents information-heavy and uncertainty-heavy gameplay.

It includes:
- Reading opponents
- Bluffing
- Predicting behavior
- Hidden information
- Probability management
- Mind games
- Adaptation to changing conditions

A game high in Mezo rewards understanding people, randomness, or incomplete information.

### 2.3 Macro
Macro represents system-heavy gameplay.

It includes:
- Planning
- Optimization
- Resource management
- Long-term strategy
- Build order
- Route selection
- Economy
- Win-condition management

A game high in Macro rewards finding and executing strong overall solutions.

---

## 3. Core Representation

A game can be represented by the following structure:

```text
Game = [
    [
        Radius,
        CentreOfGravity,
        TotalModes,
        Density,
        Perimeter,
        Area,
        [Micro, Mezo, Macro],
        [Creativity, Knowledge, Logic, Memory, Strategy, Tactics, ProblemSolving, PatternRecognition,
         Skill, Reflexes, Precision, Speed, Timing, Coordination,
         Luck, Exploration, ResourceManagement, RiskManagement, Optimization, Persistence, Adaptability, Simulation,
         Competition, Cooperation, Communication, Negotiation, Leadership, SocialDeduction,
         Story, Roleplay, Immersion, Worldbuilding,
         Customization, Construction, Design,
         Collection, Progression, Economy, Grinding, ExplorationDepth,
         SpatialReasoning, Navigation, Mapping, PuzzleSolving]
    ],

    [
        Mode1,
        Mode2,
        Mode3,
        ...
    ],

    [
        Extra
    ]
]
```

This model has three major layers:

- **Summary layer**: global statistics for the game.
- **Mode layer**: each distinct mode or playstyle.
- **Extra layer**: geometry and technical metadata.

---

## 4. Summary Layer

The summary layer contains the main statistics of the entire game.

### 4.1 Radius
Radius measures how far the game spreads across the Micro–Mezo–Macro space.

A small radius means the game is focused.
A large radius means the game has many different playable forms.

### 4.2 Centre of Gravity
Centre of gravity is the average position of the game in Micro–Mezo–Macro space.

It answers the question:

> “On average, what kind of skill does this game test most strongly?”

### 4.3 Total Modes
Total modes counts the number of distinguishable game modes, submodes, or major playstyles.

### 4.4 Density
Density measures how concentrated the game is inside its region.

A dense game has most of its gameplay clustered around a narrow core.
A sparse game has gameplay spread broadly across a larger region.

### 4.5 Perimeter
Perimeter measures the boundary complexity of the game region.

A simple, compact game has a low perimeter.
A fragmented or irregular game has a high perimeter.

### 4.6 Area
Area measures how much of the Micro–Mezo–Macro space the game occupies.

A large area means the game supports many distinct forms of play.
A small area means the game is tightly specialized.

### 4.7 [Micro, Mezo, Macro]
This is the center point or typical point of the game.

It may be interpreted as:
- the average mode,
- the dominant mode,
- or the center of gameplay mass.

---

## 5. Feature Vector

The feature vector is separate from Micro–Mezo–Macro.  
Micro–Mezo–Macro tells us **what kind of challenge** the game presents.  
The feature vector tells us **what kinds of qualities the game contains or rewards**.

A completed feature set can be written as follows:

```text
[Creativity, Knowledge, Logic, Memory, Strategy, Tactics, ProblemSolving, PatternRecognition,
 Skill, Reflexes, Precision, Speed, Timing, Coordination,
 Luck, Exploration, ResourceManagement, RiskManagement, Optimization, Persistence, Adaptability, Simulation,
 Competition, Cooperation, Communication, Negotiation, Leadership, SocialDeduction,
 Story, Roleplay, Immersion, Worldbuilding,
 Customization, Construction, Design,
 Collection, Progression, Economy, Grinding, ExplorationDepth,
 SpatialReasoning, Navigation, Mapping, PuzzleSolving]
```

These features can be grouped into categories.

### 5.1 Cognitive
- Creativity
- Knowledge
- Logic
- Memory
- Strategy
- Tactics
- ProblemSolving
- PatternRecognition

### 5.2 Mechanical
- Skill
- Reflexes
- Precision
- Speed
- Timing
- Coordination

### 5.3 Environmental
- Luck
- Exploration
- ResourceManagement
- RiskManagement
- Optimization
- Persistence
- Adaptability
- Simulation

### 5.4 Social
- Competition
- Cooperation
- Communication
- Negotiation
- Leadership
- SocialDeduction

### 5.5 Narrative
- Story
- Roleplay
- Immersion
- Worldbuilding

### 5.6 Creative
- Customization
- Construction
- Design

### 5.7 Progression
- Collection
- Progression
- Economy
- Grinding
- ExplorationDepth

### 5.8 Spatial
- SpatialReasoning
- Navigation
- Mapping
- PuzzleSolving

This feature vector gives the model expressive power beyond the 3Ms.  
For example, two games may have similar Micro–Mezo–Macro values but very different levels of creativity, story, or social deduction.

---

## 6. Mode Layer

A game is not usually one point. It is a collection of modes.

Each mode can be described by its own summary and feature profile.

```text
Mode = [
    [Micro, Mezo, Macro],
    [Creativity, Knowledge, Logic, Memory, Strategy, Tactics, ProblemSolving, PatternRecognition,
     Skill, Reflexes, Precision, Speed, Timing, Coordination,
     Luck, Exploration, ResourceManagement, RiskManagement, Optimization, Persistence, Adaptability, Simulation,
     Competition, Cooperation, Communication, Negotiation, Leadership, SocialDeduction,
     Story, Roleplay, Immersion, Worldbuilding,
     Customization, Construction, Design,
     Collection, Progression, Economy, Grinding, ExplorationDepth,
     SpatialReasoning, Navigation, Mapping, PuzzleSolving]
]
```

A game then becomes:

```text
Game = [
    Summary,
    Modes[],
    Extra
]
```

Where `Modes[]` is a list of all meaningful modes.

### Why modes matter
The same game can behave very differently depending on mode.

Examples:
- Survival mode in a sandbox game may be Macro-heavy.
- PvP mode may be Micro-heavy.
- Roleplay mode may be Mezo-heavy.
- Creative building may be Creativity-heavy and Macro-heavy.

So the game itself is best treated as a collection of mode objects rather than a single fixed point.

---

## 7. Extra Layer

The extra layer stores the exact geometry and technical descriptors of the game region.

This may include:

```text
Extra = [
    SVG,
    ConvexHull,
    DensityFunction,
    BoundaryPoints,
    Mesh,
    RegionSegments,
    ModeGraph,
    Metadata
]
```

### 7.1 SVG
SVG stores the visual geometric shape of the game region.

### 7.2 Convex Hull
The convex hull gives the smallest convex shape containing all the game’s points.

### 7.3 Density Function
The density function gives the relative importance or frequency of each point in the region.

### 7.4 Boundary Points
Boundary points define the outline of the playable region.

### 7.5 Mode Graph
The mode graph can show how modes are related to each other.

This extra layer prevents information loss.  
Without it, two different games could share the same summary statistics and still be structurally different.

---

## 8. Why a Single Radius Is Not Enough

A single radius cannot uniquely describe a game region.

Two games can have the same radius and still be very different:
- one may be circular,
- another may be long and thin,
- another may be fragmented,
- another may have several separate clusters.

That is why radius must be combined with:
- center of gravity,
- area,
- perimeter,
- density,
- convex hull,
- and exact geometry.

The game is not just a number.  
It is a shape.

---

## 9. Interpretation of the Model

This model allows several levels of interpretation.

### 9.1 Point
A single play session, role, or activity.

### 9.2 Mode
A distinct game type such as survival, creative, ranked PvP, or speedrun.

### 9.3 Game
The full set of all major modes and playstyles.

### 9.4 Platform
A broader container that includes many different games or game-like experiences.

This means a platform like a sandbox ecosystem can occupy a much larger and more varied region than a focused game.

---

## 10. Practical Uses

This framework can be used for:

- game design
- player preference matching
- mode comparison
- competitive analysis
- recommendation systems
- game database indexing
- research into gameplay structure
- procedural mode classification

It is especially useful when genre labels fail to capture what the game actually asks from the player.

---

## 11. Example Application

A focused execution game may look like this:

```text
Game = [
    [
        Radius = 5,
        CentreOfGravity = [95, 0, 5],
        TotalModes = 1,
        Density = High,
        Perimeter = Low,
        Area = Small,
        [Micro, Mezo, Macro] = [95, 0, 5],
        [Creativity, Knowledge, Logic, Memory, Strategy, Tactics, ProblemSolving, PatternRecognition,
         Skill, Reflexes, Precision, Speed, Timing, Coordination,
         Luck, Exploration, ResourceManagement, RiskManagement, Optimization, Persistence, Adaptability, Simulation,
         Competition, Cooperation, Communication, Negotiation, Leadership, SocialDeduction,
         Story, Roleplay, Immersion, Worldbuilding,
         Customization, Construction, Design,
         Collection, Progression, Economy, Grinding, ExplorationDepth,
         SpatialReasoning, Navigation, Mapping, PuzzleSolving] = [...]
    ],

    [
        Mode1
    ],

    [
        SVG, ConvexHull, DensityFunction, Metadata
    ]
]
```

A broad sandbox game may look like this:

```text
Game = [
    [
        Radius = 80,
        CentreOfGravity = [30, 15, 55],
        TotalModes = 12,
        Density = Medium,
        Perimeter = High,
        Area = Large,
        [Micro, Mezo, Macro] = [30, 15, 55],
        [Creativity, Knowledge, Logic, Memory, Strategy, Tactics, ProblemSolving, PatternRecognition,
         Skill, Reflexes, Precision, Speed, Timing, Coordination,
         Luck, Exploration, ResourceManagement, RiskManagement, Optimization, Persistence, Adaptability, Simulation,
         Competition, Cooperation, Communication, Negotiation, Leadership, SocialDeduction,
         Story, Roleplay, Immersion, Worldbuilding,
         Customization, Construction, Design,
         Collection, Progression, Economy, Grinding, ExplorationDepth,
         SpatialReasoning, Navigation, Mapping, PuzzleSolving] = [...]
    ],

    [
        SurvivalMode,
        CreativeMode,
        HardcoreMode,
        PvPMode,
        SpeedrunMode,
        RedstoneMode,
        RoleplayMode,
        ModdedMode,
        CoOpMode,
        BuildingMode,
        ExplorationMode,
        ChallengeMode
    ],

    [
        SVG, ConvexHull, DensityFunction, Metadata
    ]
]
```

---

## 12. Conclusion

The proposed framework improves game classification by moving from fixed genres to a geometric and feature-based representation. The Micro–Mezo–Macro axes describe the type of challenge. The feature vector describes the kinds of abilities and experiences involved. The mode layer captures variation inside the game. The extra layer preserves exact geometry and advanced metadata.

This produces a model that is:
- flexible,
- extensible,
- mathematically meaningful,
- and much more accurate than genre labels alone.

In short:

**A game is not just a label.  
A game is a region, a center, a set of modes, and a structured feature space.**
