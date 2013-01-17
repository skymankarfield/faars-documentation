Welcome to the fAARS API Documentation v1.0
========================

fAARS - Zenfri, Clandestine: Anomaly

_Current base URI:_ http://faars-zenfri.javakafe.com/

_[gameKey]:_ clandestine_anomaly

_[gameInstanceKey]:_ clandestine1

##Technical specs
_Base system:_ Running on CentOS release 6.3 (Final)

_Base Kernel:_ Linux 2.6.32.28-xenU #1 SMP Thu Jan 20 00:41:40 UTC 2011 i686 i686 i386 GNU/Linux

_Programming language:_ PHP 5.3.17 (cli) (built: Sep 18 2012 13:39:21) with Slim Framework to allow access via a RESTful interface

_Database manager Server:_ MySQL version: 5.5.27 accessed via internal Linux socket

_Web Server_: Apache/2.2.15 (CentOS)

##Introduction
This is the version 1.0 of the fAARS API. This documentation provides a description of the set of features that allows CRUD operations over fully customizable objects, operations and game rules. 
The v1.0 API introduces a number of features that were not available in the prototype version of this work, including:
* Fully Game-Object customization and management
* Access to internal actions and operations from RESTful interfaces
* Add/Create an unlimited number of variables, collections and groups for any given Game-Object
* Unlimited Multiple inheritance defined by a Groups structure
* Multiple game instances running in parallel for multiple virtual scenarios
* Support for multiplayer modality
* Among many other multiple proper RESTful POST, PUT, GET, DELETE operations

The fAARS platform is a back-end engine that has been designed and implemented according to the Event-Driven SOA (Service Oriented Architecture) architectural style. The fAARS internal components interact with each other through a well-defined RESTful interface that allows for the extension or replacement of already implemented parts.

The platform works entirely using JSON files for data transmission, which is a very lightweight and very straightforward file structure and format for supporting interactions among multiple platforms and environments. Although XML and other formats can be easily supported, they will become available in future releases.

High Level details of fAARS can be found in the PDF document [http://hdl.handle.net/10402/era.25362], specifically in Chapter 3 "Design and Implementation of fAARS". 

Also, I am pleased to announce that our work fAARS has been accepted to be presented in the 11th edition of the conference ICEC2012 (International Conference on Entertainment Computing - http://icec2012.org/). Since this is a private environment, I can share this paper here with you. A copy of this paper called [faars_published_paper.pdf] can be found in this repository, which describes the characteristics and capabilities of the fAARS platform and how it was used to develop two different games, in a summarized version of only 14 pages. In this paper, specifically in section 3.2, you can also find high level instructions on how to create and play a game in fAARS.

## fAARS Software Architecture
![My image](http://github.com/skymankarfield/faars-documentation/raw/master/misc/img/architecture.jpg)

As shown in the figure above, the fAARS platform consists of two main components: (a) the Actors/Game-Objects (and their devices), (b) the Game Engine, which is responsible for recognizing the Actors/Game-Objects actions and inferring the next game state based on the game rules. The Actors/Game-Objects access the game engine through the fAARS API. Furthermore, external components (i.e., Subscribers) can be integrated with the Game Engine through the Subscribers API. The fAARS platform is implemented according to the Event-Driven SOA (Service Oriented Ar-chitecture) style. The fAARS components interact with each other through a well-defined RESTful interface that allows for their extension and/or reimplementa-tion.
## Important pieces of fAARS
### Objects and Actors [objects_and_actors_README]
In the context of the fAARS platform, every player and object of a game is represented by an instance of a Game-Object component in the game, which enables the player to interact (and detect interactions) with players across the real and virtual worlds. These interactions are called Events.
### Event-driven Game Engine for Game ECA Rules Processing [game_ECA_rules_README]
This is the component that receives the Events produced by the Game-Objects in order to process the game rules and update the state of the Actors and Objects accordingly. Its functionality is exposed through web services.
### Event Subscribers [external_systems_README]
The fAARS platform provides a web service that allows external systems to register as observers of a game in fAARS. This is to allow external components to provide further downstream functionality to fAARS games as if they were part of the platform.
### RESTful APIs
All the functionality of fAARS can be accessed through a RESTful interface and via game ECA rules.
* fAARS [Events]
* fAARS [Game Manager]
* fAARS [Operations] 
* misc

## HTTP-based & RESTful
The fAARS API is currently entirely based on HTTP requests, and conforms to the design principles of Representational State Transfer (REST). The three main data types are represented hierarchically in the URL in the same way they are related, i.e. game >> game instance >> groups/game objects >> (operations/actions/events). RESTful access uses the HTTP verbs to determine which action to perform:
* GET : Used to retrieve data. Retrieves information about game objects and game state.
* PUT : Used to update data in fAARS. Allows to update Game-Object data and trigger events, operations and actions.
* POST : Used to store new Game-Objects.
* DELETE : Used to delete Game-Objects.

## HTTP Status Codes
The fAARS API attempts to return appropriate HTTP status codes (see http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) for every request.

### Common status codes include:
* 200 OK: request processed successfully.
* 401 Not Authorized: either you need to provide authentication credentials, or the credentials provided aren't valid.
* 403 Forbidden: fAARS understands your request, but refuses to fulfill it. An accompanying error message should explain why.
* 404 Not Found: You're requesting an invalid URI.
* 405 Method not allowed: fAARS understands your requests, but doesn't allow you to execute a resource using a specified method PUT, GET, DELETE, etc.
* 500 Internal Server Error: Something went wrong...

## Summary of fAARS response codes
Whenever appropriate, some of the fAARS APIs will return a JSON formatted {"status":0} when the requested API successfully completes performing an operation. There will be times when the operation won't be completed, and the following is a list of some of the returned messages by some of the fAARS APIs:
* 1 = SQL Execution Error
* 2 = No game ID or game instance ID found
* 3 = Error inserting game object into the database
* 4 = Error inserting game object attributes into the database
* 5 = Error inserting game object groups into the database
* 6 = A game object attribute is missing: <attributeName>
* 7 = A required game object attribute is empty: <attributeName>
* 8 = No game object ID found
* 9 = No game object entry found in database with given keys
* 10 = No game object attributes entry found in database with given keys
* 11 = No game object groups entry found in database with given keys
* 12 = No game object entries found in database with given game instance key
* 13 = No game object entries found in database with given object group key
* 14 = No game object attribute entry found in database with given keys
* 15 = No valid operation
* 16 = Values are not permitted for the requested operation
* 17 = Update operation was not successful, or there is nothing to update
* 18 = Game-Object not found with given username and password
* 19 = Provided username and password value pair already exists
* 20 = Either the eventGenerator or eventRecipient is not activated
* 21 = No game ECA rules corresponding to this event were found
* 22 = Error inserting game object collections into the database
* 23 = No game object collections entry found in database with given keys
* 24 = Error creating scheduled event. The time set is in the past
