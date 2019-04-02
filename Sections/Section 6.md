# Section 6: Testing

## Sections Table of Contents

Section 1: [Introduction to Software Engineering](Section%201.md)<br>
Section 2: [Requirement Analysis](Section%202.md)<br>
Section 3: [High-Level System Design](Section%203.md)<br>
Section 4: [Detailed Object Design](Section%204.md)<br>
Section 5: [Implementation](Section%205.md)<br>
Section 6: [Testing](Section%206.md)<br>

## Section 6 Table of Contents

Section 6.1: [Overview](#section-6.1-overview)<br>
Section 6.2: [Unit Testing](#section-6.2-unit-testing)<br>
Section 6.3: [Integration Testing](#section-6.3-integration-testing)<br>
Section 6.4: [System Testing](#section-6.4-system-testing)<br>

# Section 6.1: Overview

**Unit Testing:** for black-box / white-box testing<br>
**Integration Testing:** selecting testing integration strategy, and for stubs and driver test cases<br>
**System Testing:** for test cases based on functional model

**Testing** is a **systematic attempt** to find faults – deviation between **specified + observed system behaviour**.

**Failure:** deviation of specified / observed behaviour<br>
**Error State:**a state where further processing will lead to failure<br>
**Fault:** a defect / bug; the cause of an error<br>

## Basic Concepts

- software reliability
- code reviews
- testing approach
- black-box / white-box testing
- faults / error states / failures
- test cases
- test stubs and drivers
- corrections

### Software Reliability
`// fill this out`

**Software Reliability** is the degree to which the specified behaviour **matches** observed behaviour.
- to increase reliability:
  - fault avoidance / detection / tolerance

### Code Reviews
`// fill this out`

### Testing Approach
`// fill this out`

**Testing Planning:**
  - create plan for unit and integration testing beforehand

**Usability Testing:**
- Testing the UI

**Unit test:**
- testing use case objects and subsystems

**Testing Planning:**
- testing how components work together
- including structural testing – all components together

### Black-box / White-box Testing
`// fill this out`

A **test component** is a part of the system that is isolated for testing.
- can be:
  - object(s)
  - subsystem(s)

**Black-box:** testing output based on input
- no access to internal components<br>
**White-box:** testing internal components
- testing dynamic model states
  - and object interactions

`Unit testing includes: black-box + white-box tests`

### Faults / Error States / Failures
`// fill this out`

**Algorithmic:**
- due to incorrect implementation

**Mechanical:**
- due mechanical faults
  - _e.g. power failure_

### Test Cases
`// fill this out`

**Test case dependencies:**
- functional testing
- unit testing

**Test case associations:**
- aggregation
- precedence

### Test Stubs and Drivers
`// fill this out`

- testing isolated components
  - we need to simulate missing components

**Test Drivers:** call the test component
- passes test inputs
- shows test results

**Test Stubs:** simulate missing components
- _e.g. generates test data and API response_

### Corrections
`// fill this out`

A **correction** is a modification to repair a fault in a tested component.
- _this may introduce a new fault_

## Usability Testing
`// fill this out`

# Section 6.2: Unit Testing
`// fill this out - overview`

## Techniques for Unit Testing
`// fill this out`

### Equivalence Testing
`// fill this out`

### Boundary Testing
`// fill this out`

### Path Testing
`// fill this out`

### State-Based Testing
`// fill this out`

### Polymorphism Testing
`// fill this out`

# Section 6.3: Integration Testing
`// fill this out - overview`

**Focus:** testing small group of already unit-tested components.
- allows for more complex tests

**Optimal:** All tests in parallel<br>
**Horizontal:** testing according to **layers**<br>
**Horizontal:** testing according to **functionality**

## Horizontal Integration
`// fill this out`

### Big Bang Testing
`// fill this out`

Unit test every component individually.
- then test them all together
- difficult to determine which / where components fail

### Bottom-Up Testing
`// fill this out`

Start with **bottom** layer components.
- then test with one layer **up**
  - and so on
- only requires test **drivers**

### Top-Down Testing
`// fill this out`

Start with **top** layer components.
- then test with one layer **down**
  - and so on
- only requires test **stubs**

### Bottom-Up vs. Top-Down Testing
`// fill this out`

**Bottom-up:**
- advantage: _interface faults found more easily_
- disadvantage: _UI faults found last_

**Top-down:**
- advantage: _UI faults found first_
- disadvantage: _requires many test stubs_

### Sandwich Testing
`// fill this out`

A **combination** of top-down and bottom-up approaches.
- means there are **no unit tests**
- **no test drivers / test stubs** required

**The system is divided into:**
- target layer
- layer above target
- layer below target

### Modified Sandwich Testing
`// fill this out`

Test three layers individually before integration.
- top layer with **test stub** [target layer]
- target layer with **test driver** [top layer] + **test stub** [bottom layer]
- bottom layer with **test driver** [target layer]

Then start test layers together until you have full integration of the three layers.
- allows for parallelism
- requires additional test drivers / test stubs

## Vertical Integration
`// fill this out`

**Vertical integration:**
- all components for a given use case are fully implemented
- these components are tested together
- similar to prototyping, but prototypes are not releasable

**Disadvantages:**
  - system evolves more incrementally
  - design is more subject to change

# Section 6.4: System Testing
`// fill this out`

## Functional Testing
`// fill this out`

## Performance Testing
`// fill this out`

## Acceptance Testing
`// fill this out`

## Testing Recap
`// fill this out`