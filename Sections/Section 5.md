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
`// todo: fill this out`

## Model Transformation
`// todo: fill this out`

### Refactoring
`// todo: fill this out`

### Forward Engineering
`// todo: fill this out`

### Reverse Engineering
`// todo: fill this out`

### Transformation Principles
`// todo: fill this out`

### Optimizing the Object Model
`// todo: fill this out`

## Mapping Contracts
`// todo: fill this out`

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