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

### An example of a Game-Object in a JSON file ready to be entered to fAARS
{
    "fullObjectName": "fullName", (Long name of a Game-Object. It can take any value. A value is not required. It can contain an empty string)
    "objectKey": "objectKeyTest", (Unique key ID of a Game-Object. It can take any value. A value is required)
    "allowLogin": "1", (Whether to allow a Game-Object to login to the system. It can only take '0' or '1' as values. A value is required)
    "loginInfo": [ (Container for the login information. It can't be empty, and it should contain the 'username' and 'password' attributes specified)
        {
            "username": "email@mail.com", (Username to be used to login. It can take any value. A value is not required. It can contain an empty string)
            "password": "passwordObject" (Password to be used to login. It can take any value. A value is not required. It can contain an empty string)
        }
    ],
    "currentStateKey": "initialState", (Current state of a Game-Object in the system. It can take any value. A value is required)
    "active": "0", (Whether a Game-Object is active or not to be considered as part of the fAARS game rules processing. It can only take '0' or '1' as values. A value is required)
    "transient": "1", (Whether to allow copies of a Game-Object or not when creating new instances of a game. It can only take '0' or '1' as values. A value is required)
    "attributes": [ (Container for the list of secondary attributes of a Game-Object. It should contain at least one attribute specified)
        {
            "attributeKey": "attr1", (Key ID of an attribute. It should be unique within the context of a Game-Object. It can take any value. A value is required)
            "value": "val", (Value of an attribute. It can take any value. A value is required)
            "active": "1" (Whether an attribute is active or not to be considered as part of the fAARS game rules processig. It can only take '0' or '1' as values. A value is required)
        },
        {
            "attributeKey": "attr2",
            "value": "val",
            "active": "0"
        },
        {
            "attributeKey": "attr3",
            "value": "val",
            "active": "1"
        }
    ],
    "groups": [ (Container for the list of groups that a Game-Object belongs to. It should contain at least one group specified)
        {
            "groupKey": "group4", (Key ID of a group. It should be unique within the context of a Game-Object. It can take any value. A value is required)
            "active": "1" (Whether a group is active or not to be considered as part of the fAARS game rules processing. It can only take '0' or '1' as values. A value is required)
        },
        {
            "groupKey": "group5",
            "active": "0"
        },
        {
            "groupKey": "group6",
            "active": "0"
        }
    ],
    "collections": [ (Container for the list of collections of a Game-Object. It should contain at least one collection specified)
        {
            "collectionKey": "coll1", (Key ID of a collection. It should be unique within the context of a Game-Object. It can take any value. A value is required)
            "value": [1,2,3], (Values in the collection. It can take any values. A value is required)
            "active": "1" (Whether a collection is active or not to be considered as part of the fAARS game rules processig. It can only take '0' or '1' as values. A value is required)
        },
        {
            "collectionKey": "coll2",
            "value": [4,5,6],
            "active": "0"
        },
        {
            "collectionKey": "coll3",
            "value": [7,8,9],
            "active": "1"
        }
    ],
    "currentGPSLocation": [ (Container for the current GPS location of a Game-Object. It can't be empty, and it should contain the 'currentLat' and 'currentLon' attributes specified))
        {
            "currentLat": "1000000", (GPS latitude. It takes the GPS latitude value as an integer. A value is not required. It can contain an empty string)
            "currentLon": "1000000" (GPS longitude. It takes the GPS longitude value as an integer. A value is not required. It can contain an empty string)
        }
    ],
    "currentZone": "initialZone" (Contains the current location zone of a Game-Object. It can take any value. A value is not required. It can contain an empty string)
}