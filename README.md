Welcome to fAARS-who-is-the-rooster API Documentation
========================

fAARS - Rocketfuel Games, Who's the Rooster?

# fAARS API Documentation

_Current base URI:_ http://faars-rocketfuel.javakafe.com/

_[gameKey]:_ who_is_the_rooster

_[gameInstanceKey]:_ rooster1

_Base system:_ CentOS release 6.2 (Final)

_Base Kernel:_ Linux 2.6.32.28-xenU #1 SMP Thu Jan 20 00:41:40 UTC 2011 i686 i686 i386 GNU/Linux

This is the version 1.0 of the fAARS API. It encompasses a set of features that allows read and write access. 
The v1.0 API introduces a number of features that were not available in the prototype version, including:
* Fully Game-Object management
* Access to internal actions and operations from RESTful interfaces
* Create an unlimited number of variables for any given Game-Object
* Unlimited Multiple inheritance defined by a Groups structure
* Multiple game instances running in parallel for multiple virtual scenarios
* Support for multiplayer modality
* Among other multiple proper RESTful POST, PUT, GET, DELETE operations

The platform works entirely using JSON files, which is a very lightweight and natural file structure/format for supporting interactions among multiple platforms and environments. Although XML and other formats can be easily supported, they will become available in future releases.

## Game >> Game-Instance >> Game-Group/Game-Object data types
Although Game and Game-Instance can be considered a data type in the context of fAARS, operations, actions and events can only be performed over/by Game-Group/Game-Object data types.

## Game-Group
A Game-Group data type is an abstraction that groups Game-Objects together in order to allow the fAARS platform to perform operations, actions, and events over/by all the members of a given group. A Game-Group doesn't contain any attributes, but it provides abstract methods to Game-Objects. Game-Group data types can be seen as interfaces to allow Game-Objects to inherit the same set of actions, operations, and events among multiple groups. At the same time, this allows to express fAARS ECA game rules at the group level. 

## Game-Object
A Game-Object data type is the minimal and essential component of every game deployed on fAARS. It contains a specific set of default attributes, but it also allows support for an unlimited multiple inheritance and 'game developer-created' attributes.

### Default list of Game-Object attributes
* _fullObjectName_: Title or full name of the Game-Object. Used for displaying purposes only. It can contain either a number or a string value.
* _objectKey_: This is a unique value that represents a particular Game-Object in an instance of a game. It can contain either a number or a string value.
* _allowLogin_: Specifies whether a particular Game-Object is part of the pool of the login information. It can contain either '1' or '0' as value.
* _loginInfo_: This is a struct that contains a 'username' and 'password' fields for a particular Game-Object. The 'username' and 'password' fields can contain either a number or a string value.
* _currentStateKey_: Contains the current state of a Game-Object in the game. This can contain either a number or a string value.
* _active_: Defines whether a Game-Object is active or not. In other words, whether a Game-Object should be considered to be part of the fAARS game rules processing. It can contain either '1' or '0' as value.
* _transient_: Allows to differentiate between temporal and essential objects in a game instance during cloning of a game in fAARS. It can contain either '1' or '0' as value.
* _currentGPSLocation_: A struct composed by 'currentLat' and 'currentLon', which allows to determine the current GPS position of a Game-Object. 'currentLat' and 'currentLon' should contain interger values.
* _currentZone_: Determines the current abstract location of an object in a game on fAARS. It can contain either a number or a string value.

### Groups
Groups are contained in the "groups" attribute set. Every group element contained in the "groups" attribute set is specified by two parameters:
* _groupKey_: Name of a group that a particular Game-Object belongs to. It can contain either a number or a string value.
* _active_: Defines whether a Game-Object is actively part of a group to be considered to be part of the fAARS game rules processing.  It can contain either '1' or '0' as value.

### Extra attributes
Besides the default list of Game-Object attributes, any number of extra attributes can be supported in the "attributes" attribute set. Every extra attribute contained in the "attributes" attribute set is specified by three parameters:
* _attributeKey_: Name of the attribute. It can contain either a number or a string value.
* _value_: Value that contains a specific attribute. It can contain either a number or a string value.
* _active_: Whether to consider a partiular attribute as part of the fAARS game rules.

### Operations
All the Game-Object data types support the primitive set of operations "add/substract/divide/multiply" over any of their default and extra set of attributes. Any Game-Object data type can access any of the primitive operations.

### Actions
There is a set of internal actions (functionality) like push-notifications, email, etc; that can be accessed internally (via fAARS ECA game rules) or through RESTful interfaces. Any Game-Object data type can access any of the internal built-in fAARS functionality.

### Events
Events are domain specific, which means that the name of the events embedded in the URL is decided by the game creator. The name of the events are entered in the fAARS ECA game rules, and they are contained as part of the RESTful URL structure. The scope and set of events that a Game-Object can perform is defined via the fAARS ECA game rules.

## HTTP-based & RESTful
The fAARS API is currently entirely based on HTTP requests, and conforms to the design principles of Representational State Transfer (REST). The three main data types are represented hierarchically in the URL in the same way they are related, i.e. game >> game instance >> groups/game objects >> (operations/actions/events). RESTful access uses the HTTP verbs to determine which action to perform:
* GET : Used to retrieve data. Retrieves information about game objects and game state.
* PUT : Used to update data in fAARS. Updates a game object and triggers events, operations and actions.
* POST : Used to store new game objects.
* DELETE : Used to delete game objects.

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