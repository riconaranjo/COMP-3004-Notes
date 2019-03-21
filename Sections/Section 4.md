# Section 4.2: Reusing Pattern Solutions

* Reusing already exiting tools/frameworks/subsystems is faster and cheaper than designing form scratch
* allows for
  * modifiability 
  * extensibility

## Application and Solution Objects
What are application objects? 
* also known as domain objects
* they represent concepts from the application domain
* they must be relevant to the system

What are solution objects?
* objects specific to the solution domain
* they do not have an application domain counterpart 
* for example: persistent data stores, UI objects

## Specification and Implementation Inheritance
_In c++ one has many inheritance tools at their disposal_
* All inheritance relationships should be within the same subsystem, since inheritance is _"the strongest"_ relationship two classes can have.

Focus of inheritance in analysis phase
* set up generalization/specialization taxonomy

## Specification and Implementation Inheritance
What is implementation inheritance? 
* not an “is-a” relationship
* use of inheritance purely for purposes of code reuse
* superclass functionality is reused by:
  * subclassing 
  * refining behaviour
* quick and dirty way to reuse operations
  * usually results in unintended consequences
  * you get more than you bargained for 
* not an intuitive use of inheritance

### Example:
> When creating a class named _MyStack_ which is a FIFO stack implementation that uses the c++ vector implementation, the programmer is presented with 2 choices:
> 1. Compose MyStack with Vector
> 2. Make MyStack inherit from Vector (implementation inheritance)
> 
> If option 2 was chosen it would likely yield the unwanted consequence of inheriting all the Vector methods from Vector onto MyStack (even through MyStack shouldn't support those operations)

## Liskov Substitution Principle
What is this principle?
* assume T is a superclass and S is a subclass of T
* “if an object of type S can be substituted in all places where an object of type T is expected, then S is a subtype of T”

Consequences:
* an operation on T can be called on instances of S, without knowing that it is called on a subclass instance
* client classes using operations on T don’t have to change when new subclasses of T are added

Strict inheritance
* when all inheritance associations are specification inheritance

_In essence, wherever one can use *polymorphism*, strict inheritance is present_

# Section 4.3 Specifying Interfaces
Goal
* specify boundaries between objects
* integrate all existing, partial models into one coherent whole

Steps
* dentify missing attributes and operations 
  * augment object design model
* specify visibility and signatures
  * decide on operations available to other objects and subsystems
  * determine operation signatures and return types 
* specify contracts
  * describe object and operation behaviour in terms of constraints

## Class Developer Roles (Part of Contracts)
Three roles
* class implementer (person who writes the code)
* class user 
* class extender

#### Class implementer 
* implements the class
* designs the internal data structures 
* implements the code for the operations 
* designs the interface specification

#### Class user
* invokes the class operations from another class, called the client class
* uses the interface specification as boundary to the class

#### Class extender
* develops specializations of the class
* uses interface specification as indication of:
  * the behaviour of the class 
  * the constraints on the class

## Contracts
What is a contract?
* specifies constraints on a class that:
  * must be ensured by:
    * class implementer
    * class extender
  * must be met by:
    * class user

Contracts include three types of constraints: 
* invariant
* precondition 
* postcondition

### What is an _invariant_?
* predicate that is always true for all instances of a class 
* associated with a class or an interface
* used to specify consistency constraints among attributes

#### Example:
> maximum number of players in tournament must be greater than 0 
> given a Tournament object t: 
```pascal
t.getMaxNumPlayers() > 0
```

### What is an _precondition_?
* predicate that must be true before an operation is invoked 
* associated with an operation
* used to specify constraints that class user must meet before invoking the operation

#### Example
> example of precondition for acceptPlayer() operation: 
> * player must not already be accepted, and the current number of players must be less than the maximum 
> * given a Tournament object t and player p: 
```pascal
!t.isPlayerAccepted(p) and
  t.getNumPlayers() < t.getMaxNumPlayers()

```

### What is an postcondition?
* predicate that must be true after an operation executes 
* associated with an operation
* used to specify constraints that class implementer and extender must ensure after execution

#### Example
> example of precondition for acceptPlayer() operation: 
> * accepting a player must increase the player count by 1
> * given a Tournament object t and player p: 
```pascal
t.getNumPlayers_afterAccept() =
  t.getNumPlayers_beforeAccept() + 1

```

## Object Constraint Language
What is OCL?
* it’s a formal language to specify constraints

How is OCL used?
* may be used for constraints on: 
  * single model elements
    * attributes, operations, classes 
  * groups of model elements
    * associations, participating classes 
* syntax is Pascal-like
* represents constraints as boolean expressions

```go
# `=` is comparison
1 = 2 
# => false

# `=:` is assignment
a = 1
a
# => 1
```
