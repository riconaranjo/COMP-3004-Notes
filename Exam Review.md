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
- better not to split up high-level use-case based on users
- best local + remote content

## High-level

### Access Local Content
- premium **initiates**

### Access Remote Content
- regular **initiates**
- premium **initiates**
- third-party **participates**
  - _this implies they participate with all derived use-cases_

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

![sequence-exam-1](/img/sequence-exam-1.png)

# Exercise 2: UML Use-Case Diagram

- social media service with API for other remote social media sites
  - allows users of remote sites to:
    - **manage newsfeed** [high-level]
      - by retrieving other users' posts [detailed]
      - modifying newsfeed settings [detailed]
    - **mange posts** [high-level]
      - post new status updates [detailed]
      - upload photos / videos [detailed]

## High-level

### Manage Newsfeed
- third-party site user **initiates**
- **includes** retrieve newsfeed posts
  - **extends** connection error
- **includes** modify settings
  - **extends** connection error

### Manage Posts
- third-party site user **initiates**
- **includes** retrieve post new status updates
  - **extends** connection error
- **includes** upload photos / videos
  - **extends** connection error

## Sequence Diagram: Retrieve Newsfeed
![sequence-exam-2](/img/sequence-exam-2.png)

# Sequence Diagram Steps

1. figure out which actor **initiates** use-case
2. select **boundary object** used to initiate use-case
    - named with a _noun-phrase_
    - e.g. _candidates: download option, submit form request_
3. **boundary object** creates **control object**
    - named with a _verb-phrase_
      - e.g. _DownloadMusicControl_
4. **control object** dictates logic
    - entity object may be created then saved
    - information may be saved directly
    - new boundary object may be created
      - reply / notification to initial actor
      - to communicate with third-party actor
5. all created objects are **destroyed**
    - original boundary object remains

# Types of Design Problems

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