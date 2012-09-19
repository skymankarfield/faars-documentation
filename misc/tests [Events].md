# TESTS

## [Events]
### catchEvent
curl -i -X PUT -H 'Content-Type: application/json' -d '{"eventKey":"unlock","eventGeneratorKey":"game_instance_1","eventRecipientKey":"plot_point_1"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/events


* Receives a JSON file via PUT method:
{
	"eventKey":"unlock",
	"eventGeneratorKey":"game_instance_1",
	"eventRecipientKey":"plot_point_1"
}


* Sample Response 'On Success':
{
    "gameECARules": [
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_in_24hrs",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_in_2hrs",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_locked",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 0
                }
            ],
            "status": 0,
            "actions": [
                {
                    "actionKey": "updatePrimaryObjectAttributeByObjectKey",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "output": {
                        "status": 0,
                        "details": {
                            "action": "updatePrimaryObjectAttributeByObjectKey",
                            "objectKey": "plot_point_1",
                            "gameKey": "who_is_the_rooster",
                            "gameInstanceKey": "rooster1",
                            "attributeKey": "currentStateKey"
                        }
                    },
                    "status": 0
                }
            ]
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_via_mobile",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_via_mobile_web",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        }
    ],
    "status": 0,
    "details": {
        "action": "catchEvent",
        "eventGeneratorKey": "game_instance_1",
        "eventRecipientKey": "plot_point_1",
        "eventKey": "unlock",
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


### addScheduledEvent
curl -i -X POST -H 'Content-Type: application/json' -d '{"objectKey":"event1","eventKey":"unlock","eventGeneratorKey":"game_instance_1","eventRecipientKey":"plot_point_1","year":"2012","month":"9","day":"16","hour":"15","minute":"30","second":"10"}' http://faars-rocketfuel.javakafe.com/who_is_the_rooster/rooster1/scheduledEvent


* Receives a JSON file via PUT method:
{
	"objectKey":"event1",
	"eventKey":"unlock",
	"eventGeneratorKey":"game_instance_1",
	"eventRecipientKey":"plot_point_1",
	"year":"2012",
	"month":"9",
	"day":"3",
	"hour":"16",
	"minute":"30",
	"second" : "10"
}


* Sample Response 'On Success':
{
    "gameECARules": [
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_in_24hrs",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_in_2hrs",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_locked",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 0
                }
            ],
            "status": 0,
            "actions": [
                {
                    "actionKey": "updatePrimaryObjectAttributeByObjectKey",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "output": {
                        "status": 0,
                        "details": {
                            "action": "updatePrimaryObjectAttributeByObjectKey",
                            "objectKey": "plot_point_1",
                            "gameKey": "who_is_the_rooster",
                            "gameInstanceKey": "rooster1",
                            "attributeKey": "currentStateKey"
                        }
                    },
                    "status": 0
                }
            ]
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_via_mobile",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        },
        {
            "gameECARuleKey": "update_plot_point_to_unlocked_via_mobile_web",
            "conditions": [
                {
                    "conditionKey": "checkPrimaryAttribute",
                    "objectScope": "recipient",
                    "objectKey": "plot_point_1",
                    "status": 1
                }
            ],
            "status": 1
        }
    ],
    "status": 0,
    "details": {
        "action": "catchEvent",
        "eventGeneratorKey": "game_instance_1",
        "eventRecipientKey": "plot_point_1",
        "eventKey": "unlock",
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