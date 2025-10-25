#1 
Navigate to your AIPatrolSettings JSON file.

For me this is located here.
C:\\Steam\steamapps\common\DayZServer\mpmissions\dayzOffline.chernarusplus\expansion\settings 
(Note: for some people config can be named profile instead)

#2
Delete the "LoadBalancingCategories" parameter:
"LoadBalancingCategories": {
        "Global": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 10,
                "MaxPatrols": 10
            },
            {
                "MinPlayers": 11,
                "MaxPlayers": 20,
                "MaxPatrols": 8
            },
            {
                "MinPlayers": 21,
                "MaxPlayers": 30,
                "MaxPatrols": 6
            },
            {
                "MinPlayers": 31,
                "MaxPlayers": 40,
                "MaxPatrols": 4
            },
            {
                "MinPlayers": 41,
                "MaxPlayers": 50,
                "MaxPatrols": 2
            },
            {
                "MinPlayers": 51,
                "MaxPlayers": 255,
                "MaxPatrols": 0
            }
        ],
        "Example": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": -1
            }
        ],
        "Quest": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": -1
            }
        ],
        "ObjectPatrol": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": 5
            }
        ],
        "HelicopterWreck": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": 3
            }
        ],
        "ContaminatedArea": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": 2
            }
        ],
        "Patrol": [
            {
                "MinPlayers": 0,
                "MaxPlayers": 255,
                "MaxPatrols": 5
            }
        ]
    },
(Note: delete Patrol but leave the Patrols plurial parameter intact)

