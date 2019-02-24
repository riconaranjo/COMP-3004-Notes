# Section 2: Requirement Analysis

# Section 2.1: Overview

## Purpose

Requirement analysis is the first of the 5 phases of the **software development lifecycle**.

1. requirements analysis
2. high-level system
3. detailed object design
4. implementation
5. testing

The **role of development team**, in the requirement analysis is to **understand the problem**, and to **model the application domain**.
- **results in:**
  - functional requirements
  - functional model
  - the non-functional requirements
  - the dynamic model
  - the analysis object model

## Breakdown

### Requirement Elicitation

- first gather a detailed + complete set of requirements
  - from clients information
  - _use-cases + scenarios_
  - should create a **system specification**
    - that can be understood by client
    - from user's point of view
    - including functions + non-functional requirements

### Requirement Analysis

- create high-level model
  - given the requirements
  - focus on **system / object behaviour**
  - from user's point of view
  - non-technical
  - _state machine / sequence activity diagrams_

## Requirement Elicitation

**Elicitation:** getting information from the client, for the development team.<br>
**Requirements:** what the client wants the system to do (i.e. features / tasks), and design constraints.

### Types of Requirements
**Functional:** what the system does (not how)
- features
- tasks
- interactions between system and external environment

**Non-functional:** the user-visible constraints on the system
- non-functional aspects of the system...
- specific + testable

### Non-Functional Requirements (NFR)
Main categories:
- usability
  - ease of use (colour scheme)
  - online help (documentation)
- reliability
  - load performance
  - dependability (fault-tolerance + security)
- performance
  - response time + throughput
  - availablity
- supportability
  - maintainability
  - portability

## Requirement Specification

**Requirement specification:** is a system definition that the client understands, that serves as a contract between the client and the development team.
- they are **complete / consistent / unambiguous**
- includes functional requirements
  - embodied in the functional model
- non-functional requirements

## Traceability

**Every requirement tracked** through development lifecycle (use-cases -> system functions -> test cases)
- all **dependencies documented**
- facilitates maintenance of project
  - change impact easier to assess
- achieved with numbering requirements and cross-referencing

## Requirement Validation

**Requirement specification** must be validated by the client and development team for:
completeness
- consistency
- clarity
- correctness
- realism
- verifiability
- traceability

## Dorc Slayer Case Study

**Functional requirements:**
- FR-01: player can save the game
- FR-02: player can restore saved game
- FR-03: player can control character
  - FR-03-01: move the character
  - FR-03-02: wield weapon
  - FR-03-03: hit another character
  - FR-03-04: eat food ration from inventory
  - FR-03-05: view inventory

**Non-functional requirements:**
- NF-01 UI shows character health _(usability)_
- NF-02 game should be recoverable after crash _(reliability)_
- NF-03 configurable graphics _(performance)_
- NF-04 show be extensible to other graphics libraries_(supportability)_
- ...

## Requirements Elicitation Activities

**Identifying:**
- actors
- scenarios
- use-cases (+ refining)
- actor / use-case relationships
- initial analysis objects
- non-functional requirements

### Identifying Actors

**An actor** is an entity that **interacts** with the system; they are **role abstraction**.
- e.g. people / users
  - that need **access to the system**
  - that **execute** the main **functionality** of the system
- e.g. external systems
  - for input / output data
  - (high-level functional systems, not implementation details)
    - _OS / libraries are not external systems_

Actors are useful for **defining the system boundaries**.

### Identifying Scenarios

**A scenario** is a _**component**_ of a **use-case** that describes the system as **user interactions**; they describe a **single feature** from the **point of view** of a user.

Scenarios help figure out the main system functionality.
- allows for clients + users to understand:
  - application domain
  - system

Scenarios can be used to create test plans.

To identify a scenario, you can use:
- interviews with clients / users
- application domain + procedure manuals
- UI mock-ups

The goal is to **identify**:
- **tasks** performed by actors
- **information** created / accessed / modified by actors
- **interactions** between actors + system

### Identifying Use-Cases

**A use-case** is a **set of scenarios** that describes user / system interactions, **initiated by an actor**; it distinguishes user steps / system steps.

Use-cases are used to **facilitate client / developer communication**, and to **establish system scope**.

They can be identified by using generalized high-level scenarios and asking clients / users about:
- alternatives
- feature details
- constraints

#### High-Level Use-Case Diagram

![high-level-use-case](../img/high-level-use-case.png)

`// high-level use-case diagrams contained in a box`

#### Detailed Use-Case Diagram

![detailed-use-case](../img/detailed-use-case.png)

Then use detailed use-cases.

Use-cases are represented with:
- **table-based text descriptions**
  - unique use-case name
  - actors
  - event flow
    - responses should be indented
    - other use-cases referenced using **extends** / **includes** / **inherits**
  - entry conditions
  - exit conditions
  - quality requirements
  - traceability
- **UML use-case diagrams**
  - there is no order specified
    - it would be shown in the text description
  - there should be no mapping to menu navigation
    - button presses are not states

#### Table-Based Description

![table-description](../img/table-description.png)

### Identifying Relationships

**Relationships:**
- between actors and use-cases:
  - **communication**
    - initiation / participation
    - permissions
- between use-cases:
  - extend
  - include
  - inherit

Use-case relationships are represented using:
- case diagrams (arrows + labels)
- case table-based text description
  - using **extends** / **includes** / **inherits** (bold font)

**Extend** relationship is when one use-case **extends the functionality** of another.
- used only for **exceptional** event flow (i.e. `Exceptions`)
  - e.g. **`ResponseTimeout`** extends **`Register`**
- origin case is not aware about extending case
  - extending case must have specific entry condition

`// arrows can be dotted or not`

![extends-use-case](../img/extends-use-case.png)

**Include** relationship is used to remove **redundant functionality** and break down the system complexity.
- e.g. **`ViewProfile`** for animals and users
- origin use-case triggers included use-case
- included case is not aware of origin use-case

`// arrows can be dotted or not`

![includes-use-case](../img/includes-use-case.png)

**Inheritance** relationships indicates **use-case sub-types**.
- this is not the same as **includes**

![inheritance](../img/inheritance.png)

### Identifying Initial Analysis Objects
**Initial analysis objects** are the main **participating objects** present in the system (i.e. objects in the use cases).

### Identifying Non-Functional Requirements

`// todo: fill this out`

# Section 2.3: Analysis

High-level object categories:
- entity
- control
- boundary

**Object model** construction:
- associations (inheritance / aggregation)
- directionality / multiplicity
- UML class diagrams

**Dynamic model** construction (based on functional requirements):
- UML sequence diagrams
- state machine diagrams
- activity diagram

## Analysis Phase

The **analysis phase** is highly **iterative / incremental**, and is not necessarily for the client.
- the **focus** is on:
  - structuring / formalizing the requirements
  - defining / describing the application domain
  - from the user's point of view

`// todo: fill this out`