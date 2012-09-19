# TESTS

## [Game Manager]
### createObject
curl -i -X POST -H 'Content-Type: application/json' -d '{"fullObjectName":"fullName","objectKey":"objectKeyTest","allowLogin":"1","loginInfo":[{"username":"email@mail.com","password":"passwordObject"}],"currentStateKey":"initialState","active":"0","transient":"1","attributes":[{"attributeKey":"attr1","value":"val","active":"1"},{"attributeKey":"attr2","value":"val","active":"0"},{"attributeKey":"attr3","value":"val","active":"1"}],"groups":[{"groupKey":"group4","active":"1"},{"groupKey":"group5","active":"0"},{"groupKey":"group6","active":"0"}],"collections":[{"collectionKey":"coll1","value":[1,2,3],"active":"1"},{"collectionKey":"coll2","value":[4,5,6],"active":"1"},{"collectionKey":"coll3","value":[7,8,9],"active":"1"}],"currentGPSLocation":[{"currentLat":"1000000","currentLon":"1000000"}],"currentZone":"initialZone"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects


* Receives a JSON file via POST method:
{
    "fullObjectName": "fullName",
    "objectKey": "objectKeyTest",
    "allowLogin": "1",
    "loginInfo": [
        {
            "username": "email@mail.com",
            "password": "passwordObject"
        }
    ],
    "currentStateKey": "initialState",
    "active": "0",
    "transient": "1",
    "attributes": [
        {
            "attributeKey": "attr1",
            "value": "val",
            "active": "1"
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
    "groups": [
        {
            "groupKey": "group4",
            "active": "1"
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
    "collections": [
        {
            "collectionKey": "coll1",
            "value": [1,2,3],
            "active": "1"
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
    "currentGPSLocation": [
        {
            "currentLat": "1000000",
            "currentLon": "1000000"
        }
    ],
    "currentZone": "initialZone"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "createObject",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 1,
    "message": "SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'objectKeyTest-1' for key 'objectKey'",
    "details": {
        "action": "createObject",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


### getObjectByKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKey21


* Sample Response 'On Success':
{
    "fullObjectName": "fullName",
    "objectKey": "objectKeyTest",
    "currentStateKey": "initialState",
    "currentZone": "initialZone",
    "allowLogin": "1",
    "transient": "1",
    "active": "0",
    "currentGPSLocation": {
        "currentLat": "1000000",
        "currentLon": "1000000"
    },
    "loginInfo": {
        "username": "email@mail.com",
        "password": "passwordObject"
    },
    "attributes": {
        "attr1": {
            "attributeKey": "attr1",
            "value": "val",
            "active": "1"
        },
        "attr2": {
            "attributeKey": "attr2",
            "value": "val",
            "active": "0"
        },
        "attr3": {
            "attributeKey": "attr3",
            "value": "val",
            "active": "1"
        }
    },
    "groups": {
        "group4": {
            "groupKey": "group4",
            "active": "1"
        },
        "group5": {
            "groupKey": "group5",
            "active": "0"
        },
        "group6": {
            "groupKey": "group6",
            "active": "0"
        }
    },
    "collections": {
        "coll1": {
            "collectionKey": "coll1",
            "value": [
                "1",
                "2",
                "3"
            ],
            "active": "1"
        },
        "coll2": {
            "collectionKey": "coll2",
            "value": [
                "4",
                "5",
                "6"
            ],
            "active": "1"
        },
        "coll3": {
            "collectionKey": "coll3",
            "value": [
                "7",
                "8",
                "9"
            ],
            "active": "1"
        }
    },
    "status": 0,
    "details": {
        "action": "getObjectByKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey21"
    }
}


### getAllGameObjectsByGameInstanceKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "fullObjectName": "Who is the Rooster?",
            "objectKey": "game_instance_1",
            "currentStateKey": "running",
            "currentZone": "noZone",
            "allowLogin": "0",
            "transient": "0",
            "active": "1",
            "currentGPSLocation": {
                "currentLat": "0",
                "currentLon": "0"
            },
            "loginInfo": {
                "username": "",
                "password": ""
            },
            "attributes": {
                "version": {
                    "attributeKey": "version",
                    "value": "1.0",
                    "active": "0"
                }
            },
            "groups": {
                "system": {
                    "groupKey": "system",
                    "active": "1"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "game_instance_1",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "Lucio Gutierrez",
            "objectKey": "lucio_gutierrez",
            "currentStateKey": "idle",
            "currentZone": "uofa",
            "allowLogin": "1",
            "transient": "1",
            "active": "1",
            "currentGPSLocation": {
                "currentLat": "0",
                "currentLon": "0"
            },
            "loginInfo": {
                "username": "lucio@ualberta.ca",
                "password": "blabla"
            },
            "attributes": {
                "score": {
                    "attributeKey": "score",
                    "value": "0",
                    "active": "1"
                }
            },
            "groups": {
                "players": {
                    "groupKey": "players",
                    "active": "1"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "lucio_gutierrez",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest10",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email11@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest10",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest11",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email12@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest11",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest12",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email13@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest12",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "Plot Point 1",
            "objectKey": "plot_point_1",
            "currentStateKey": "plotPointUnlockedForMobileAndWeb",
            "currentZone": "comp_sci",
            "allowLogin": "0",
            "transient": "0",
            "active": "1",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "",
                "password": ""
            },
            "attributes": {
                "nickame": {
                    "attributeKey": "nickame",
                    "value": "nickname",
                    "active": "0"
                }
            },
            "groups": {
                "plotpoints": {
                    "groupKey": "plotpoints",
                    "active": "1"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "plot_point_1",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "getAllGameObjectsByGameInstanceKey",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 2,
    "message": "No game ID or game instance ID found",
    "details": {
        "action": "getGameInstanceID",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster"
    }
}


### getAllGameObjectsByGroupKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/groups/group2


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest10",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email11@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest10",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest11",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email12@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest11",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "fullObjectName": "fullName",
            "objectKey": "objectKeyTest12",
            "currentStateKey": "initialState",
            "currentZone": "initialZone",
            "allowLogin": "1",
            "transient": "1",
            "active": "0",
            "currentGPSLocation": {
                "currentLat": "1000000",
                "currentLon": "1000000"
            },
            "loginInfo": {
                "username": "email13@mail.com",
                "password": "passwordObject"
            },
            "attributes": {
                "attr1": {
                    "attributeKey": "attr1",
                    "value": "val",
                    "active": "1"
                },
                "attr2": {
                    "attributeKey": "attr2",
                    "value": "val",
                    "active": "0"
                },
                "attr3": {
                    "attributeKey": "attr3",
                    "value": "val",
                    "active": "1"
                }
            },
            "groups": {
                "group4": {
                    "groupKey": "group4",
                    "active": "1"
                },
                "group5": {
                    "groupKey": "group5",
                    "active": "0"
                },
                "group6": {
                    "groupKey": "group6",
                    "active": "0"
                }
            },
            "collections": {
		        "coll1": {
		            "collectionKey": "coll1",
		            "value": [
		                "1",
		                "2",
		                "3"
		            ],
		            "active": "1"
		        },
		        "coll2": {
		            "collectionKey": "coll2",
		            "value": [
		                "4",
		                "5",
		                "6"
		            ],
		            "active": "1"
		        },
		        "coll3": {
		            "collectionKey": "coll3",
		            "value": [
		                "7",
		                "8",
		                "9"
		            ],
		            "active": "1"
		        }
		    },
            "status": 0,
            "details": {
                "action": "getObjectByKey",
                "objectKey": "objectKeyTest12",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "getAllGameObjectsByGroupKey",
        "groupKey": "group4",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 13,
    "message": "No game object entries found in database with given object group key",
    "details": {
        "action": "getAllGameObjectsByGroupKey",
        "groupKey": "group",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


### deleteObjectByKey
curl -i -X DELETE http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKey2


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "deleteObjectByKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey2"
    }
}


### deleteAllGameObjectsByGroupKey
curl -i -X DELETE http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/groups/group2


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest1",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest2",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest3",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "deleteAllGameObjectsByGroupKey",
        "groupKey": "group2",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 13,
    "message": "No game object entries found in database with given object group key",
    "details": {
        "action": "getAllGameObjectsByGroupKey",
        "groupKey": "group2",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


### deleteAllGameObjectsByGameInstanceKey
curl -i -X DELETE http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects


* Sample Response 'On Success':
{
    "gameObjects": [
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest4",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest5",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        },
        {
            "status": 0,
            "details": {
                "action": "deleteObjectByKey",
                "objectKey": "objectKeyTest6",
                "gameKey": "who_is_the_rooster",
                "gameInstanceKey": "rooster1"
            }
        }
    ],
    "status": 0,
    "details": {
        "action": "deleteAllGameObjectsByGameInstanceKey",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 12,
    "message": "No game object entries found in database with given game instance key",
    "details": {
        "action": "getAllGameObjectsByGameInstanceKey",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


### updateObjectByKey
curl -i -X PUT -H 'Content-Type: application/json' -d '{"fullObjectName":"fullName","objectKey":"objectKeyTest","allowLogin":"1","loginInfo":[{"username":"email@mail.com","password":"passwordObject"}],"currentStateKey":"initialState","active":"0","transient":"1","attributes":[{"attributeKey":"attr1","value":"val","active":"1"},{"attributeKey":"attr2","value":"val","active":"0"},{"attributeKey":"attr3","value":"val","active":"1"}],"groups":[{"groupKey":"group4","active":"1"},{"groupKey":"group5","active":"0"},{"groupKey":"group6","active":"0"}],"collections":[{"collectionKey":"coll1","value":[1,2,3],"active":"1"},{"collectionKey":"coll2","value":[4,5,6],"active":"1"},{"collectionKey":"coll3","value":[7,8,9],"active":"1"}],"currentGPSLocation":[{"currentLat":"1000000","currentLon":"1000000"}],"currentZone":"initialZone"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKey6


* Receives a JSON file via PUT method:
{
    "fullObjectName": "fullName",
    "objectKey": "objectKeyTest",
    "allowLogin": "1",
    "loginInfo": [
        {
            "username": "email@mail.com",
            "password": "passwordObject"
        }
    ],
    "currentStateKey": "initialState",
    "active": "0",
    "transient": "1",
    "attributes": [
        {
            "attributeKey": "attr1",
            "value": "val",
            "active": "1"
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
    "groups": [
        {
            "groupKey": "group4",
            "active": "1"
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
    "collections": [
        {
            "collectionKey": "coll1",
            "value": [1,2,3],
            "active": "1"
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
    "currentGPSLocation": [
        {
            "currentLat": "1000000",
            "currentLon": "1000000"
        }
    ],
    "currentZone": "initialZone"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "updateObjectByKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey6"
    }
}


### verifyObjectLogin
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/verifyObjectLogin/email2@mail.com/passwordObject2


* Sample Response 'On Success':
{
    "objectKey": "objectKeyTest2",
    "active": "0",
    "allowLogin": "1",
    "status": 0,
    "details": {
        "action": "verifyObjectLogin",
        "username": "email2@mail.com",
        "password": "passwordObject2",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1"
    }
}


* Sample Reponse 'On Failure':
{
    "status": 2,
    "message": "No game ID or game instance ID found",
    "details": {
        "action": "getGameInstanceID",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooter1"
    }
}


### updatePrimaryObjectAttributeByObjectKey
curl -i -X PUT -H 'Content-Type: application/json' -d '{"attributeKey":"currentStateKey","value":"plotPointLocked","operation":"set"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/plot_point_1/primaryAttributes


* Receives a JSON file via PUT method:
{
    "attributeKey": "currentStateKey",
    "value": "plotPointLocked",
    "operation": "set"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "updatePrimaryObjectAttributeByObjectKey",
        "objectKey": "plot_point_1",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "currentStateKey"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "plot_point_"
    }
}


### addSecodaryAttributeByObjectKey
curl -i -X POST -H 'Content-Type: application/json' -d '{"attributeKey":"lonely","value":"-1","active":"1"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/secondaryAttributes


* Receives a JSON file via POST method:
{
    "attributeKey": "lonely",
    "value": "-1",
    "active": "1"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "addSecondaryAttributeByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "lonely"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "plot_point_"
    }
}


### addCollectionByObjectKey
curl -i -X POST -H 'Content-Type: application/json' -d '{"collectionKey":"collN","value":["a",1,"b",2],"active":"1"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/collections


* Receives a JSON file via POST method:
{
    "collectionKey": "collN",
    "value": ["a",1,"b",2],
    "active": "1"
}


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "addCollectionByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "collN"
    }
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "plot_point_"
    }
}


### collectionExistsInObjectByObjectKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/collections/collectionExists/coll2


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "collectionExistsInObjectByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll2"
    },
    "collectionExists": "true"
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey21"
    }
}


### secondaryAttributeExistsInObjectByObjectKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/secondaryAttributes/attributeExists/lonely


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "secondaryAttributeExistsInObjectByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "lonely"
    },
    "attributeExists": "true"
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey21"
    }
}


### getSecondaryAttributeValueInObjectByObjectKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/secondaryAttributes/lonely


* Sample Response 'On Success':
{
    "status": 0,
    "details": {
        "action": "getSecondaryAttributeValueInObjectByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "attributeKey": "lonely"
    },
    "value": "-1"
}


* Sample Response 'On Failure':
{
    "status": 8,
    "message": "No game object ID found",
    "details": {
        "action": "getGameObjectID",
        "objectKey": "objectKey21"
    }
}


### getCollectionValueInObjectByObjectKey
curl -i -X GET http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/gameObjects/objectKeyTest/collections/coll3


* Sample Response 'On Success':
{
    "value": [
        "7",
        "8",
        "9"
    ],
    "status": 0,
    "details": {
        "action": "getCollectionValueInObjectByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll3"
    }
}


* Sample Response 'On Failure':
{
    "status": 23,
    "message": "No game object collections entry found in database with given keys",
    "details": {
        "action": "getCollectionValueInObjectByObjectKey",
        "objectKey": "objectKeyTest",
        "gameKey": "who_is_the_rooster",
        "gameInstanceKey": "rooster1",
        "collectionKey": "coll36"
    }
}