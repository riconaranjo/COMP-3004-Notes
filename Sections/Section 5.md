# Section 4: Implementation

## Sections Table of Contents

Section 1: [Introduction to Software Engineering](Section%201.md)<br>
Section 2: [Requirements Analysis](Section%202.md)<br>
Section 3: [High-Level System Design](Section%203.md)<br>
Section 4: [Detailed Object Design](Section%204.md)<br>
Section 5: [Implementation](Section%205.md)<br>
Section 6: [Testing](Section%206.md)<br>
Section 7: [Software Management](Section%207.md)<br>
Section 8: [Professional Ethics](Section%208.md)<br>

## Section 5 Table of Contents

Section 5.1: [Overview](#section-5.1-overview)<br>
Section 5.2: [Mapping to Collections](#section-5.2-mapping-to-collections)<br>
Section 5.3: [Mapping to Storage](#section-5.3-mapping-to-storage)<br>

# Section 5.1: Implemention

This section covers strategies for:
- mapping models to code
- mapping models to persistent storage

Before implementation you need:
- subsystem decomposition
- detailed object model

Result from implementation is source code.

## Model Transformation

**Model transformation** is when changes are applied to an existing object model.
- such as modifying classes / attributes / operations
- in order to:
  - _simplify_
  - _optimize_
  - _better meet requirements_
- e.g. _grouping related classes under same super class_

**Goal:**
- to improve aspect of model without compromising other properties

**Characteristics:**
- small number of classes / attributes / operations
  - small series of steps
- can occur in:
  - object design phase
  - implementation phase

**Mapping contracts to exceptions:**
- describe behaviour for when a contract is broken
  - where exception is thrown / handled

**Mapping class model to storage schema:**
- defining how a class model relates to a schema

### Refactoring

**Refactoring** is good for improving the design a system.
- improving readability / modifiability without changing behaviour
- small incremental steps + while testing

### Forward Engineering

`Also known as implementing the model`

**Forward engineering** is writing code based on model design.
- object design model should match
  - implementation errors will be introduced

**Characteristics:**
- applied to a set of model elements
- results in:
  - _class definition_
  - _database schema_
  - _etc_

### Reverse Engineering

**Reverse engineering** is inferring model from implementation / code.
- to recreate a model from a system that is already implemented

**Characteristics:**
- applied to a set of source code elements
- results in a set of model elements

### Transformation Principles

**Overall Approach:**
- to improve the design of the system
  - without introducing faults

**Principles:**
- each transformation must **address one criterion**
  - _one design goal_
- each transformation must **be local**
  - _changes to few classes / attributes / operations_
- each transformation must **be validated**
  - models and documents must be updated

`// changes to multiple subsystems is an architectural change [not transformation]`

### Optimizing the Object Model

**Optimizing access paths:**
- repeated association traversals
  - identify frequency operations with multiple association traversals
  - make these direct connections
    - this may introduce redundant associations but reduces bottlenecks
- replace _many_ multiplicity associations
  - with _one_ qualified association
  - _use key or indexing to associate objects_
- for attributes only used for get / set operations
  - move to calling class
  - _this may reduce the number of classes_

**Result:**
- some redundant associations
- fewer many-to-many associations
- fewer classes

**Collapsing objects:**
- replace objects with attributes
  - e.g. _container class for information_

**Delaying expensive computation:**
- only create expensive objects when needed
- cache results of expensive operations
  - values cached in private attributes
  - trade-off between space + time

**Suitable for:**
- frequent + expensive operations
  - with results that seldom change

## Mapping Contracts

Use exceptions to mark contract violations.
- it's easy to overdo this
- it's more work and may introduce / mask bugs

### Heuristics

- only check preconditions
  - not postconditions / invariants
  - usually redundant
- focus on system interfaces
  - i.e. public operations
- focus on long-life components
  - this code may be reused
- reuse code for checking constraints
  - share exception classes

# Section 5.2: Mapping to Collections
`// todo: fill this out - overview`

## Mapping Association
`// todo: fill this out`

### Unidirectional One-to-One Associations
`// todo: fill this out`

### Bidirectional One-to-One Associations
`// todo: fill this out`

### One-to-Many Associations
`// todo: fill this out`

### Many-to-Many Associations
`// todo: fill this out`

## Optimizing Associations
`// todo: fill this out`

## Qualified Associations
`// todo: fill this out`

### Association Classes
`// todo: fill this out`

# Section 5.3: Mapping to Collections
`// todo: fill this out - overview`

## Relational Database Concepts
`// todo: fill this out`

## Mapping Classes and Attributes
`// todo: fill this out`

## Mapping Associations
`// todo: fill this out`

## Mapping Inheritance Relationships
`// todo: fill this out`

### Vertical Mapping [modifiability]
- each class has its own table
  - e.g. one for super class + one for sub class
- each to modify / add attributes
- access time is slow due to many tables

### Horizontal Mapping [performance]
- duplicates superclass columns for each subclass
- any schema modifications are complex
- queries are faster
  - especially when dealing with deep inheritance

## Implementation Recap
`// todo: fill this out`