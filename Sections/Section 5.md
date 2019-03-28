# Section 4: Implementation

## Sections Table of Contents

Section 1: [Introduction to Software Engineering](Section%201.md)<br>
Section 2: [Requirement Analysis](Section%202.md)<br>
Section 3: [High-Level System Design](Section%203.md)<br>
Section 4: [Detailed Object Design](Section%204.md)<br>
Section 5: [Implementation](Section%205.md)<br>
Section 6: [Testing](Section%206.md)<br>

## Section 5 Table of Contents

Section 5.1: [Overview](#section-5.1-overview)<br>
Section 5.2: [Mapping to Collections](#section-5.2-mapping-to-collections)<br>
Section 5.3: [Mapping to Storage](#section-5.3-mapping-to-storage)<br>

# Section 5.1: Overview
`// fill this out`

## Model Transformation
`// fill this out`

### Refactoring
`// fill this out`

### Forward Engineering
`// fill this out`

### Reverse Engineering
`// fill this out`

### Transformation Principles
`// fill this out`

### Optimizing the Object Model
`// fill this out`

## Mapping Contracts
`// fill this out`

# Section 5.2: Mapping to Collections
`// fill this out - overview`

## Mapping Association
`// fill this out`

### Unidirectional One-to-One Associations
`// fill this out`

### Bidirectional One-to-One Associations
`// fill this out`

### One-to-Many Associations
`// fill this out`

### Many-to-Many Associations
`// fill this out`

## Optimizing Associations
`// fill this out`

## Qualified Associations
`// fill this out`

### Association Classes
`// fill this out`

# Section 5.3: Mapping to Collections
`// fill this out - overview`

## Relational Database Concepts
`// fill this out`

## Mapping Classes and Attributes
`// fill this out`

## Mapping Associations
`// fill this out`

## Mapping Inheritance Relationships
`// fill this out`

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
`// fill this out`