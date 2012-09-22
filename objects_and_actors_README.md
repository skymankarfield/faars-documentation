Objects and/or Actors
========================

## Game >> Game-Instance >> Game-Group/Game-Object data types
Although Game and Game-Instance can be considered a data type in the context of fAARS, operations, actions and events can only be performed over/by Game-Group/Game-Object data types.

## Game-Group
A Game-Group data type is an abstraction that groups Game-Objects together in order to allow the fAARS platform to perform operations, actions, and events over/by all the members of a given group. A Game-Group doesn't contain any attributes, but it provides abstract methods to Game-Objects. Game-Group data types can be seen as interfaces to allow Game-Objects to inherit the same set of actions, operations, and events among multiple groups. At the same time, this allows to express fAARS ECA game rules at the group level. 

## Game-Object
A Game-Object data type is the minimal and essential component of every game deployed on fAARS. It contains a specific set of default/primary attributes, and it also supports multiple inheritance, secondary attributes created by a game developer, and an unlimited number of collections.

### Primary Game-Object attributes
* _fullObjectName_: Title or full name of the Game-Object. Used for displaying purposes only. It can contain either a number or a string value.
* _objectKey_: This is a unique value/ID that represents a particular Game-Object in an instance of a game. It can contain either a number or a string value.
* _allowLogin_: Specifies whether a particular Game-Object is part of the pool of the login information. It can contain either '1' or '0' as value.
* _loginInfo_: This is a struct that contains a 'username' and 'password' fields for a particular Game-Object. The 'username' and 'password' fields can contain either a number or a string value.
* _currentStateKey_: Contains the current state of a Game-Object in a game. This can contain either a number or a string value.
* _active_: Defines whether a Game-Object is active or not. In other words, whether a Game-Object should be considered to be part of the fAARS game rules processing/evaluation. It can contain either '1' or '0' as value.
* _transient_: Allows to differentiate between temporal and essential objects in a game instance during cloning of a game in fAARS. It can contain either '1' or '0' as value.
* _currentGPSLocation_: A struct composed by 'currentLat' and 'currentLon', which allows to determine the current GPS position of a Game-Object. 'currentLat' and 'currentLon' should contain interger values.
* _currentZone_: Determines the current abstract location of an object in a game on fAARS. It can contain either a number or a string value.

### Groups
Groups are contained in the "groups" attribute set. Every group element contained in the "groups" attribute set is specified by two parameters:
* _groupKey_: Name of a group that a particular Game-Object belongs to. It can contain either a number or a string value.
* _active_: Defines whether a Game-Object is actively part of a group to be considered part of the fAARS game rules processing/evaluation.  It can contain either '1' or '0' as value.

### Secondary Game-Object attributes
Besides the primary list of Game-Object attributes, any number of secondary attributes can be supported in the "attributes" attribute set. Every secondary attribute contained in the "attributes" attribute set is specified by three parameters:
* _attributeKey_: Name of the attribute. It can contain either a number or a string value.
* _value_: Value that contains a specific attribute. It can contain either a number or a string value.
* _active_: Whether to consider a partiular attribute as part of the fAARS game rules.

### Operations
All the Game-Object data types support the primitive set of operations "add/substract/divide/multiply" over any of their primary and secondary set of attributes. Any Game-Object data type can access any of the primitive operations.

### Actions
There is a set of internal actions (functionality) like push-notifications, email, etc; that can be accessed internally (via fAARS ECA game rules) or through RESTful interfaces. Any Game-Object data type can access any of the internal built-in fAARS functionality.

### Events
Events are domain specific, which means that the name of the events embedded in the URL is decided by the game creator. The name of the events are entered in the fAARS ECA game rules, and they are contained as part of the RESTful URL structure. The scope and set of events that a Game-Object can perform is defined via the fAARS ECA game rules.
