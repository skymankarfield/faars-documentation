# TESTS

## [Operations]
### performOperationByObjectKey
curl -i -X PUT -H 'Content-Type: application/json' -d '{"attributeKey":"attr1","value":"5","operation":"+"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest


* Receives a JSON file via PUT method:
{
	"attributeKey":"attr1",
	"value":"5",
	"operation":"+"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "performOperationByObjectKey",
        "objectKey": "objectKey6",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "attr1"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "ObjectKeyTest"
    }
}


### performOperationByGroupKey
curl -i -X PUT -H 'Content-Type: application/json' -d '{"attributeKey":"attr1","value":"5","operation":"+"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/groups/group2


* Receives a JSON file via PUT method:
{
	"attributeKey":"attr1",
	"value":"5",
	"operation":"+"
}


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest1",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest2",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest3",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "performOperationByGroupKey",
        "groupKey": "group2",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "attr1"
    }
}


* Sample Response 'On Failure':
{
    "status": 13,
    "message": "No game object entries found in database with given object group key",
    "details": {
        "action": "getAllGameObjectsByGroupKey",
        "groupKey": "group9",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


### performOperationByGameInstanceKey
curl -i -X PUT -H 'Content-Type: application/json' -d '{"attributeKey":"attr1","value":"5","operation":"+"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations


* Receives a JSON file via PUT method:
{
	"attributeKey":"attr1",
	"value":"5",
	"operation":"+"
}


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKey6",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest1",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest2",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest3",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 16,
            "message": "Values are not permitted for the requested operation",
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest4",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 16,
            "message": "Values are not permitted for the requested operation",
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest5",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        },
        {
            "status": 16,
            "message": "Values are not permitted for the requested operation",
            "details": {
                "action": "performOperationByObjectKey",
                "objectKey": "objectKeyTest6",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1",
                "attributeKey": "attr1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "performOperationByGameInstanceKey",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "attr1"
    }
}


* Sample Response 'On Failure':
{
    "status": 2,
    "message": "No game ID or game instance ID found",
    "details": {
        "action": "getGameInstanceID",
        "gameKey": "who_is_the_roost",
        "gameInstanceKey": "rooster1"
    }
}


### pushItemsToCollection
curl -i -X PUT -H 'Content-Type: application/json' -d '{"value":["x","y","z"]}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest/collections/coll1


* Receives a JSON file via PUT method:
{
    "value": [
        "x",
        "y",
        "z"
    ]
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "pushItemToCollection",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1"
    }
}


* Sample Response 'On Failure':
{
    "status": 7,
    "message": "A required game object attribute is empty: value",
    "details": {
        "action": "checkJSONByLevel"
    }
}


### itemExistsInCollection
curl -i -X GET -H 'Content-Type: application/json' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest/collections/coll1/itemExistsInCollection/g


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "itemExistsInCollection",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1",
        "itemValue": "g"
    },
    "valueExists": "false"
}


* Sample Response 'On Failure':
{
    "status": 23,
    "message": "No game object collections entry found in database with given keys",
    "details": {
        "action": "itemExistsInCollection",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "collx",
        "itemValue": "g"
    }
}


### getItemPositionInCollectionByValue
curl -i -X GET -H 'Content-Type: application/json' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest/collections/coll1/itemPositionByValue/1


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "getItemPositionInCollectionByValue",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1",
        "itemValue": "1"
    },
    "positions": [
        0,
        3,
        4,
        5
    ],
    "valueExists": "true"
}


* Sample Response 'On Failure':
{
    "status": 23,
    "message": "No game object collections entry found in database with given keys",
    "details": {
        "action": "itemExistsInCollection",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "collx",
        "itemValue": "g"
    }
}


### deleteItemFromCollectionByValue
curl -i -X DELETE -H 'Content-Type: application/json' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest/collections/coll1/deleteByValue/1


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "deleteItemFromCollectionByValue",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1",
        "itemValue": "1"
    }
}


* Sample Response 'On Failure':
{
    "status": 23,
    "message": "No game object collections entry found in database with given keys",
    "details": {
        "action": "itemExistsInCollection",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "collx",
        "itemValue": "g"
    }
}


### deleteItemFromCollectionByPosition
curl -i -X DELETE -H 'Content-Type: application/json' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/operations/ObjectKeyTest/collections/coll1/deleteByPosition/1


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "deleteItemFromCollectionByPosition",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1",
        "index": "1"
    }
}


* Sample Response 'On Failure':
{
    "status": 22,
    "message": "Error inserting game object collections into the database",
    "details": {
        "action": "deleteItemFromCollectionByPosition",
        "objectKey": "ObjectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll1",
        "index": "0"
    }
}