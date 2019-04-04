# Exam Review Exercises

# Exercise 1: UML Use-Case Diagram

Remote content provider using an **existing** third-party content provider.

`// 'existing' makes the third party an actor`

**Actors:**
- regular users
- premium users
- third-party content provider

**Regular users:**
- _can browse video content from external content provider_ [detailed]
- _can steam video content from external content provider_ [detailed]

**Premium users:**
- _can browse video content from external content provider_ [detailed]
- _can steam video content from external content provider_ [detailed]
- can download video content from external content provider [detailed]
- can browse video content locally [detailed]
- can steam video content locally [detailed]

## Tips
- better not to split up high-level use case based on users
- best local + remote content

## High-level

### Access Local Content
- premium **initiates**

### Access Remote Content
- regular **initiates**
- premium **initiates**
- third-party **participates**
  - _this implies they participate with all derived use cases_

## Detailed

### Access Local Content
- **includes** browse local video
- **includes** stream local video
- **includes** download + store video
  - third-party **participates**

### Access Remote Content
- **includes** browse remote video
  - **extends** connection error
- **includes** stream remote video
  - **extends** connection error

## Sequence Diagram: Download + Store Video
