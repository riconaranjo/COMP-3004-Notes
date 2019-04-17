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

# Section 3.1: High-Level System Design

The goal of high-level system design is to turn the analysis products into a system design model.
- figure out what the **subsystems** are _[inital subsystem decomposition]_
  - then what is the best suited **architecture** [refined subsystem decomposition]

## Results of High-Level System Design

**System design model:**
- subsystem decomposition
- system architecture strategies

## Initial Subsystem Decomposition

This phase is about determining:
- **design goals** [based on functional + non-functional requirements]
- **initial subsystem decomposition**

### Design Goals

1. use functional requirements + non-functional requirements to decide on design goals
    - _performance + dependability + cost + maintenance + end user_
2. establish trade-offs

### Subsystem Decomposition

1. assign objects in a use-case to a single subsystem
2. create subsystems to move data between subsystems
3. refine:
    - ensure all objects in a subsystem are related
    - minimize subsytem associations

## Refined Subsystem Decomposition

This phase is about determining:
- refined subsystem **decomposition**
  - subsystems organized into _layers + partitions_
- system architecture **strategies**

# Section 3.2: Initial System Decomposition

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

# Section 3.3: Design Patterns

- **creational:** object creation [mechanisms]
  - _abstract factory_
- **structural:** simplification of object associations / relationships
  - _adapter_
  - _bridge_
  - _composite_
  - _façade_
  - _proxy_
- **behavioural:** communication patterns between objects
  - _command_
  - _observer_
  - _strategy_

### Abstract Factory

An **Abstract Factory** design pattern **enables creation of objects**, _independent of the client_.
- it provides an interface to inherited factory classes, with different implementations.
  - _e.g. products from different manufacturers_

![arena-factory](/img/arena-factory.png)

### Adapter

An **adapter** design pattern exists as a **wrapper around existing / legacy code** to provide a new interface to the client.
- _e.g. new user interface for an old command line application_

`// only works if it's a wrapper for existing code`

![adapter](/img/adapter.png)

### Bridge

A **Bridge** design pattern allows for alternate implementations with a single interface.
- like Adapter, but for **new code**
- e.g. _different storage implementations for one store_

![bridge](/img/bridge.png)

In this picture, the store would be the abstraction, and the concrete implementors would be different storage implementations.

## Composite

A **Composite** design pattern represents a **recursive hierarchy**.
- Composite class inherits from _Component_ class
  - and Component class has many _Component_ objects
- allows for encapsulation of hierarchies
- e.g. _UI toolkits such as Java Swing_

![composite](/img/composite.png)

## Façade

A **Façade** design pattern is used to **encapsulate subsystems**.
- provides a high-level / abstract interface for class operations.

![facade](/img/facade.png)

## Proxy

A **Proxy** design pattern encapsulates expensive objects [expensive: performance / security].
- they provide a gateway to a real object

![proxy](/img/proxy.png)

## Command

A **Command** design pattern is used to **encapsulate control flow**.
- used to provide generic user requests
- e.g. _execute, undo, store in Adobe Illustrator_

![command](/img/command.png)

## Observer

An **Observer** design pattern is used to **seperate entity objects from the view**.
- subscriber / observer are notified
  - when changes to subject / publisher object occur
- used for propagating model changes across multiple views
- e.g. _MVC architecture style_

![observer](/img/observer.png)

## Strategy

A **Strategy** design pattern is used to **encapsulate algorithms / context**.
- used for dynamically selecting behaviour based on context
  - like bridge, but implementation is decided by client
- e.g. _selecting network connections (Wi-Fi, Ethernet, etc)_

![strategy](/img/strategy.png)

# Section 3.4: Refined System Decomposition

1. **Group subsystems into components and nodes**
  - components: group of 1+ subsystems
  - nodes: physical environment on which components run
2. **Identify:**
  - persistent data
  - access control
  - global control flow
  - boundary conditions
3. **Then identify**
  - subsystem services / interfaces

**Components:** a single or group of subsystems

**Runtime components:** component with a unique _process_

**Node:** the physical device / environment running a component

**System:** a group of runtime components
- may be distributed across multiple nodes

## System Strategies

**Software / Hardware Mapping:**
- used for off-the-shelf / legacy components
  - for hardware configuration
  - for internode communications

**Data Management:**
- used for identification of:
  - persistent data
  - storage locations
  - acces mechanisms

**Access Control:**
- used for:
  - _authetication_
  - _authorization_
  - _confidentiality_

**Control Flow:**
- used for control + concurrency

**Boundary conditions:**
- used for system initialization / shutdown
- edge cases

## Refined Decomposition Activities

1. Mapping subsystems to components
2. Storing persistent data
3. Providing access control
4. Designing global control flow
5. Identifying services
6. Identifying boundary conditions

## Mapping Subsystems to Components

Steps for **mapping subsystems to components:**
1. **select hardware configuration + platform**
    - decide on nodes + select hardware
    - determine communication methods
    - determine software
      - OS / legacy software / COTS software
2. **allocate objects + subsystems to nodes**
    - to enable equitable distribution:
      - of functionality
      - processing power

## Storing Persistent Data

In order to **select a storage management strategy:**
- you must take into account _non-functional requirements_

### Persistent Storage Strategies

**Flat Files:**
- low-level sequence of bytes
- can be very fast
- issues with concurrency / data loss

**Relational Database:**
- tables of a predefined schema
- mapping objects to schema may be complex
- built in concurrency / access control / crash recovery
  - _most common approach_

**OO Database:**
- supports objects and their associations
  - _can do association based queries_
- slower than relational database

## Access Control

**Static access control:** modelled as object attributes

**Dynamic access control:** implemented with _Proxy_ design pattern

### Access Matrix

- if it's on the table, it's a permission

![access-matrix](/img/access-matrix.png)

### Rule-Based Access Matrix

- a list of all existing permissions

![access-matrix-rule](/img/access-matrix-rule.png)

## Identifying Services

To **identify subsystem services**
- first review subsystem dependencies
- then defined an interface for each service

## Identifying Boundary Conditions

1. **analyze configuration of persistent objects**
2. **analyze start-up / shutdown of each component**
3. **handle exceptions for each component failure**

# Section 4: Detailed Object Design

## Tasks

1. Identify opportunities for **software reuse**
    - COTS components
    - design patterns
2. Specify **services**
    - interface specification
    - this becomes the API
3. **Restructure** object model
    - for _understandability + maintainability_
4. **Optimize** object model
    - for _performance requirements_

## Code Reuse

### Specification Inheritance
- using inheritance to classify concepts into type hierarchies
  - "is-a" relationship between generalized + specialized classes
  - _classic inheritance_

### Implementation Inheritance
- **not** an **“is-a”** relationship
- use of inheritance purely for purposes of **code reuse**
- superclass functionality is reused by:
  - _sub-classing_
  - _refining behaviour_
- quick and dirty way to reuse operations
  - can result in unintended consequences
- not an intuitive use of inheritance

## Delegation

A better approach for code reuse than inheritance.
- e.g. _a FastSet that has a HashTable instead of inheriting from it_

**Strict inheritance:** when polymorphism is allowed.

## Encapsulating Legacy Components

**Adapter:**
- good for modifying a legacy / existing component interface
  - similar to bridge but with existing code
- e.g. _new UI for existing backend_

## Encapsulating Context

**Strategy design pattern:**
- good for dynamically changing between concrete implementations based on context
  - same as bridge but client decides implementation
- e.g. _changing network connection type dynamically_

## Encapsulating Platforms

**Abstract factory:**
- good for shielding client from object creation process
  - of related objects
  - and prevents use of incompatible objects
- e.g. _products from different manufacturers_

## Encapsulating Control Flow

**Command:**
- good for generic user requests
  - without having to know request contents
- e.g. _execute / undo / store_

## Encapsulating Hierarchies

**Composite:**
- good for representing recursive hierarchy
  - and adding new components without affecting existing ones
- e.g. _UI toolkits_

## Maintaining Consistency

**Observer:**
- good for propagating model changes across view
- e.g. _MVC architecture_

## Specifying Interfaces

**Steps:**
1. **identify missing attributes and operations**
    - augment object design model
1. **specify visibility and signatures**
    - decide on operations available to other objects and subsystems
    - determine operation signatures and return types
1. **specify contracts**
    - describe object and operation behaviour in terms of constraints

## Class Developer Roles (Part of Contracts)

**Class Developers** have three possible roles:
- class **implementer** [writes code]
- class **user** [uses the code]
- class **extender** [creates specializations]

## Contracts

They are **constraints** on a class.
- _invariant_
- _precondition_
- _postcondition_

Contracts are **mapped to exceptions**.
- _exception thrown when contract broken_

# Section 5: Implementation

## Model Transformation

**Model transformation** is when changes are applied to an existing object model.
- such as modifying classes / attributes / operations
- in order to:
  - _simplify_
  - _optimize_
  - _better meet requirements_
- e.g. _grouping related classes under same super-class_

**Forward Engineering:** model --> implementation

**Reverse Engineering:** model <-- implementation

## Optimizing the Object Model

**Optimizing access paths:**
- **repeated association traversals**
  - identify frequency operations with multiple association traversals
  - make these direct connections
    - this may introduce redundant associations but reduces bottlenecks
- **replace _many_ multiplicity associations**
  - with _one_ qualified association
  - _use key or indexing to associate objects_
- **for attributes only used for get / set operations**
  - move to calling class
  - _this may reduce the number of classes_

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
- e.g. _statistics object for generating league stats_

## Relational Database Concepts

### Schema

- data description
- the set of attributes stored for each object
  - _aka data meta-model_

### Primary Key

- set of attributes used to **uniquely** identify a record
  - _best if not made of attributes that can change_

### Foreign Key

- attribute that references primary key in another table
  - links data records between tables

## Mapping Classes and Attributes

| code      | database |
| --------- | -------- |
| class     | table    |
| attribute | column   |
| instance  | row      |

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

# Section 6.1: Testing

**Unit Testing:** for blackbox / whitebox testing
- **blackbox:** testing **output** based on **input**
  - no access to internal components
- **whitebox:** testing internal components
  - testing dynamic model states
    - and object interactions

**Integration Testing:** selecting testing integration strategy, and for stubs and driver test cases

**System Testing:** for test cases based on functional model

**Testing planning:**
- create test plan for unit + integration testing beforehand
  - as soon as model is stable

**Usability testing:**
- testing UI / UX

**Unit testing:**
- testing use-case objects + subsystems
  - must include whitebox + blackbox testing

**Integration testing:**
- testing how components work together
  - including structural testing _(all components together)_

**System testing:**
- testing system as a whole
  - including all scenarios + requirements + design goals
- **functional testing**
  - based on _requirements analysis document_
- **performance testing**
  - based on _system design document_
- **acceptance testing**
  - based on _project agreement_ (performed by client)

**Test Drivers:** simulates part of system that calls the test component
- passes test inputs
- shows test results

**Test Stubs:** simulate missing components
- hardcoded implementation of other components
  - _e.g. generates test data and API response_

## Usability Tests

**Scenario test:**
- present users with a scenario
- developers gauge user reactions
  - can use _storyboard or prototype_

**Prototype test:**
- present users with software implementing key aspect of system
  - **vertical prototype:** implements one use case completely
  - **horizontal prototype:** implements one layer (e.g. UI prototype)

**Product test:**
- present users with functional system

# Section 6.2: Unit Testing

## Equivalence Testing

**Equivalence testing** minimizes the number of test cases
- by grouping input into equivalent classes
- only one member of each equivalent class is tested
  - e.g. _testing only 1 month out of 12 possible_

## Boundary Testing

**Boundary testing** is a special case of equivalence testing.
- where the focus ins on boundary conditions
  - this reduces test coverage but simplifies tests
    - risks not finding some defects

## Path Testing

**Path testing** is a whitebox technique for finding faults by executing all possible paths through the code.
- by traversing all edges in a test component flow chart
- this does not test defects due to:
  - code omissions (i.e. _missing paths_)
  - invariants of data structures

## State-Based Testing

**State-based testing** compares the state of a system to an expected state, using classes.
- achieving a specific state can be complex

## Polymorphism Testing

**Polymorphic testing** checks all possible dynamic bindings.
- expands source code in order to:
  - **typecast** to possible subclasses
    - and **invoke operations** on subclass
  - construct flow graph _(due to type)_
  - perform path testing

Component testing ordering can be:

# Section 6.3: Integration Testing

- **Horizontal:** testing according to **layers**
- **Vertical:** testing according to **functionality**

## Horizontal Integration

### Big Bang Testing

Unit test **every component individually**.
- then test them **all together**
- difficult to determine which / where components fail

### Bottom-Up Testing

Start with **bottom** layer components.
- then test with **one layer** _up_
  - and repeat
- only requires test **drivers**

### Top-Down Testing

Start with **top** layer components.
- then test with **one layer** _down_
  - and repeat
- only requires test **stubs**

### Bottom-Up vs. Top-Down Testing

**Bottom-up:**
- advantage: _interface faults found more easily_
- disadvantage: _UI faults found last_

**Top-down:**
- advantage: _UI faults found first_
- disadvantage: _requires many test stubs_

### Sandwich Testing

A **combination** of top-down and bottom-up approaches in parallel.
- means there are **no unit tests**
- **no test drivers / test stubs** required

**The system is divided into:**
- _target layer_
- _layer above target_
- _layer below target_

**Approach:**
- top-down + bottom-up testing occur in parallel
  - incrementally

### Modified Sandwich Testing

**Test three layers individually** before integration.
- top layer with **test stub** [target layer]
- target layer with **test driver** [top layer] + **test stub** [bottom layer]
- bottom layer with **test driver** [target layer]

Then start **test layers together** until you have full integration of the three layers.
- replacing test drivers with top layer components
  - and test stubs with bottom layer components
- allows for parallelism
  - but requires additional test drivers / test stubs

## Vertical Integration

**Vertical integration:**
- *all components* for a given use-case are **fully implemented**
  - these components are tested together
  - similar to prototyping

**Disadvantages:**
- system evolves more incrementally
- design is more subject to change

# Section 6.4: System Testing

## Activities

1. **Functional Testing**
    - _does it meet functional requirements_
2. **Performance Testing**
    - _does it meet non-functional requirements_
3. **Acceptance Testing**
    - _does it serve the client's expectations / needs_
      - e.g. _beta  testing_

## Testing Recap

- **Unit testing:** testing individual objects + subsystems
- **Integration testing:** testing individual components
- **System testing:** testing all components
- **Test stubs:** layer for code called _(lower levels)_
- **Test driver:** layer for calling code _(higher levels)_

# Section 8: Professional Ethics

## Software Failures

## Patriot Missile System

- anti-air missile used in Gulf War
- was designed to be run for short amount of time
  - was in operation for 100+ hours
  - clock error lead to missile killing 28 people

## Ariane 5

- uncaught exception caused loss of $500 million worth of satellites
  - statement assigning `float` to `int` value
- in previous rocket values were smaller
  - thus exception could not occur in Ariane 4

## Therac-25

- Software built on older versions
  - older versions used hardware restrictions
  - but software restrictions were not properly implemented
- two investigations: very hard to find root cause
  - there was a race condition

**Machine had two modes:**
- `X`: X-ray
- `E`: Electron beam

**What happened:**
- mistake made where staff entered `X` and dosage
  - then magnets moved
- user fixed mistake to `E`
  - software only checked cursor location
  - and if it found it in the bottom right corner
    - it assumed no fields were changed
- system gave x-ray dose at high dosage

## Ethical Decisions

To make ethical decisions:
1. **Brainstorm**
    - identify actors + effects on them
    - identity courses of actions
2. **Analysis**
    - categorize courses of actions
      - _obligatory / prohibited / acceptable_
    - select + justify
3. **Execute**