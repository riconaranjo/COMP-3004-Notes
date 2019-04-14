# Sections Summary

Summaries of each section covered in this course.

# Section 1: Introduction to Software Engineering

Software engineering is about creating a solution to a problem.

## Software Development Phase

- **Requirements analysis**
  - requirements elicitation
  - analysis
  - _results in requirement analysis document_
- **Design**
  - high-level system design
  - detailed object design
  - _results in system design document_
- **Implementation**
- **Testing**
  - unit testing + integration testing
  - system testing
- **Deployment and maintenance**

## Software Development Products

**Work Product:** unit of work (e.g. diagrams / source code / etc)
- **functional model:** _system behaviour_ from user's point of view
- **dynamic model:** _internal system behaviour_ from user's point of view
- **object model:** system objects / attributes / operations

**Deliverable:** work product delivered to client

## Unified Modelling Language

**UML** is **a tool** for expressing **system models**:
- **functional models**
  - use-case diagrams
- **dynamic models**
  - state-machine diagrams
  - sequence diagrams
  - activity diagrams
- **object models**
  - class diagrams

# Section 2: Requirements Analysis

The **goals** of the requirement analysis phase is:
1. to understand the problem
2. model the application domain

## Results of Requirements Analysis
- **functional requirements**
  - functional model
- **non-functional requirements**
  - the dynamic model
- **analysis object model**

## Functional Model

System behaviour from user's point of view.
- use-case diagrams [scenarios]

## Dynamic Model

Internal system behaviour from user's point of view.
- state-machine diagrams [states]
- sequence diagrams [order of events]
- activity diagrams [concurrency]

## Object Model

Objects + their attributes + their operations.
- class diagrams [object associations]

# Section 3: High-Level System Design

The goal of high-level system design is to turn the analysis products into a system design model.
- figure out what the **subsystems** are _[inital subsystem decomposition]_
  - then what is the best suited **architecture** [refined subsystem decomposition]

## Results of High-Level System Design

**System design model:**
- subsystem decomposition
- system architecture strategies

## Initial Subsystem Decomposition

This phase is about determining:
- **design goals** [based on functional / non-functional requirements]
- **initial subsystem decomposition**

## Refined Subsystem Decomposition

This phase is about determining:
- refined subsystem **decomposition**
  - subsystems organized into _layers + partitions_
- system architecture **strategies**

## Subsystems

Subsystems are made up of a group of related classes.
- they should be highly related
  - they should have **high cohesion**

Subsystems should be as independent as possible
- they should have **loose coupling**

The public facing members of a subsystem is called an **interface**
- the set of _public operations_ provided by the system
  - these operations can be grouped into **services**

## Layers

Subsystems can be grouped into layers.
- layers should never know about their above layers

**Closed Architecture:** only access immediately adjacent lower layer
- good for low coupling
  - but adds overhead [since you have to go through many layers]

**Open Architecture:** access any lower layers
- bad for coupling [increases number of associations]
  - no increased overhead

## Partitions

Subsystems can be grouped into partitions.
- partitions are loosely coupled
  - and can operate independently

## Architectural Strategies

These are template solutions for common design problems, that can be modified and adjusted to serve individual problem.

### Repository

One single data structure accessed by all subsystems.
- all subsystems loosely coupled [good]
  - except to repository (high coupling) [bad]
- all communication happens through repository
- **good for:**
  - complex data
  - adding new services
- **bad:**
  - repository is the bottleneck

### MVC

Model-View-Controller.
- model and view subsystems are loosely coupled [good]
  - but highly coupled to control subsystem [bad]
- based on _Observer Design Pattern_
- **good:**
  - for adding multiple views with shared models
  - maps well to _entity + boundary + control_ objects

### Client-Server

Server subsystem provides services to client subsystems.
- communications through Remote Procedure Calls (RPC)
- client subsystems interact with the users
- like repository but with remote database
- **good for:**
  - distributed systems
- **bad:**
  - can result in deadlock with blocking waits

### Peer-to-Peer

Generalization of client-server
- subsystems can be client + server
- **good for:**
  - distributed systems
    - without a central database
- **bad for:**
  - higher risk of deadlock than client server

### 3-Tier

3-Tiers: Interface + Application Logic + Storage
- Like MVC but model logic moved to application logic
  - _in other words just doesn't implement observer design pattern_

### 4-Tier

4-Tiers: Client Interface + Server Interface + Application Logic + Storage
- client interface is the UI
- server interface is an API
- **good for:**
  - implementing multiple UIs for different clients
  - having an API as well as a UI interface
- e.g. _facebook_

### Pipe and Filter

Each filter is a subsystem
- pipes are used as the association between subsystems
- **good for** data streams
- **bad for** complex interactions between filters
  - e.g. _bash shell_

## Design Goals

| _Performance_     | Defintion                         |
| ----------------- | --------------------------------- |
| response time     | time to acknowledge user requests |
| throughput        | how man tasks per unit time       |
| memory efficiency | how much memory does it need      |

| _Dependability_ | Defintion                                |
| --------------- | ---------------------------------------- |
| robustness      | ability to survive invalid input         |
| reliability     | deviation of expected + actual behaviour |
| fault tolerance | can it survive + correct faults          |
| security        | survive attacks                          |
| safety          | not endanger people                      |

| _Cost_         | Defintion                        |
| -------------- | -------------------------------- |
| development    | cost of developing system        |
| deployment     | cost of deploying                |
| upgrade        | cost of upgrading                |
| maintenance    | cost of enhancements + bug fixes |
| administration | cost of upkeep / admin           |

| _Maintenance_ | Defintion                          |
| ------------- | ---------------------------------- |
| extensibility | adding functionality               |
| modifiability | adjusting functionality            |
| adaptability  | moving between application domains |
| portability   | moving between platforms           |
| readability   | understanding system from code     |
| traceability  | mapping code back to requirements  |

| _End User_ | Defintion                   |
| ---------- | --------------------------- |
| utility    | how useful is to the client |
| usability  | how easy is it to use       |

# Section 4: Detailed Object Design

# Section 5: Implementation

# Section 6: Testing

# Section 8: Professional Ethics
