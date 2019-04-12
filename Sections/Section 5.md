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
- e.g. _grouping related classes under same super-class_

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

- **only check preconditions**
  - not postconditions / invariants
  - usually redundant
- **focus on system interfaces**
  - i.e. public operations
- **focus on long-life components**
  - this code may be reused
- **reuse code for checking constraints**
  - share exception classes

# Section 5.2: Mapping to Collections

**Associations in UML** are represented as links between objections.
- unidirectional / bidirectional

**Associations in code** are represented as references to other objects.
- only unidirectional

## Mapping Associations

### Programming Constructs

Associations implemented as:
- **single references:**
  - one object stores reference to other object
- **collections:**
  - one object stores multiple references to other objects of same type
- unidirectional associations

### Unidirectional One-to-One Associations

- Mapped as a reference from **source** object to **destination** object

### Bidirectional One-to-One Associations

- Mapped as a reference from **source** object to **destination** object
- Mapped as a reference from **destination** object to **source** object

### One-to-Many Associations

- Mapped as a source object with a **collection** of references to destination object _(with `*` multiplier / range)_

### Many-to-Many Associations

- Mapped as a **source** object with a **collection** of references to **destination** object
- Mapped as a **destination** object with a **collection** of references to **source** object
  - _(with `*` multiplier / range)_

## Optimizing Associations

Using any **"many"** associations can cause issues
- slow to access
- consistency difficult to maintain

This can be improved by using:
- qualified associations [using keys]
- association classes

## Qualified Associations

These reduce multiplicity on a "many" side of an association
- can be used with one-to-many + many-to-many
- mapped as:
  - additional [unique] _qualifier_ attribute on destination object
  - a keyed collection [map] on source object
    - **key:** qualifier attribute
    - **value:** destination object

### Association Classes

**Association classes** are used to hold attributes and operations specific to an association
- implemented as a seperate object
  - with binary associations
    - each mapped to a set of reference attributes

# Section 5.3: Mapping to Storage

**Persistent objects** need to be **mapped** to structures in the **data management system**.
- data management system selected in the system design
- data structures may be:
  - _flat files_
  - _relational / OO databases_
- by transforming model to storage schema
  - for flat files + relation databases

- **rows:** data records
- **columns:** attributes
- **cell:** value of a record attribute

## Relational Database Concepts

### Schema

- data description
- the set of attributes stored for each object
  - _aka data meta-model_

### Primary Key

- set of attributes used to **uniquely** identify a record

### Foreign Key

- attribute that references primary key in another table
  - links data records between tables

## Mapping Classes and Attributes

| code      | database |
| --------- | -------- |
| class     | table    |
| attribute | column   |
| instance  | row      |

**Names** between object model and schema **should match**.
- to provide traceability and reduce confusion

**Mapping attribute types:**
- some constraints may have to be added
  - e.g. _string length due to database implementation_

**Primary key:**
- chosen from a set of class attributes
  - causes problems
    - if values change
    - if application domain changes
- adding a **unique identifier** is more robust
  - e.g. _student ID_

## Mapping Associations

### Buried association

- used to implement:
  - **one-to-one associations**
    - use **foreign key of destination** in source object
      - vice versa in for bidirectionality
  - **one-to-many associations**
    - use **foreign key of source** in destination objects

### Association Table

- used for many-to-many associations
  - creating a new two column table with linking both class foreign key
  - each row is one association
- increases number of tables and the time required to traverse associations
  - can be used for one-to-one associations

## Mapping Inheritance Relationships

### Vertical Mapping [modifiability]

- two tables per object:
  - one super-class attributes
  - one for sub-class attributes
    - super-class table has column for actual sub-class
- easy to modify / add attributes
- access time is **slow** due to **many tables**
  - just for one object

### Horizontal Mapping [performance]

- duplicates **superclass columns for each subclass**
  - since each subclass has same column
- any schema modifications are complex
  - since multiple tables affected
- queries are **faster**
  - especially when dealing with deep inheritance

## Implementation Recap

Strategies for mapping models to code:
- avoid _"many"_ associations
  - use qualified associations instead
  - or association classes
    - to hold attributes specific to an operation

Strategies for mapping models to persistent storage:
- associations to collections
  - vertical / horizontal mapping
- contracts mapped to exceptions
- object models mapped to storage
  - **buried associations:** foreign key in destination / source
  - **association tables:** seperate table with foreign keys