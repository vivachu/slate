# Game Play

## Initialize the game

```shell
curl "http://api.parade.pet/game/init"
  -H "Authorization:  Bearer meowmeowmeow"
  -d "entry=283"
  -d "contest=2"
```

> The above command returns JSON structured like this:

```json
{
	"faceOffSet": {
		"id": 29,
		"type": "Cutest Pet of 2019",
		"typeId": 0,
		"contest": 1,
		"sponsor": {
            "name": "VitaPup",
            "path": "vp",
            "hexCode": "B6C800",
          	"id": 1
    },
		"numJudged": 4,
		"size": 10,
		"activeFaceOff": {
			"id": 224789,
			"entryA": {
				"id":123,
				"image": 2292,
				"pt": 1,
				"isAnimated": 1,
				"pet": {
					"id": 292,
					"name": "Sparky",
					"image": 92,
					"points": 9282
				}
			},
			"entryB": {
				"id":456,
				"image": 222,
				"pt": 2,
				"isAnimated": 0,
				"pet": {
					"id": 908,
					"name": "Tom",
					"image": 211,
					"points": 282
				}
			} 	
		}
	},
  "matches": [
    {
      "id": 6956,
      "type": "u",
      "entryA": {
        "id": 327920,
        "image": 446653,
        "isAnimated": 0
      },
      "entryB": {
        "id": 150559,
        "image": 194124,
        "isAnimated": 0
      }
    },
    {
      "id": 6968,
      "type": "u",
      "entryA": {
        "id": 2129915,
        "image": 2811444,
        "isAnimated": 0
      },
      "entryB": {
        "id": 198330,
        "image": 261390,
        "isAnimated": 0
      }
    },
    {
      "id": 6958,
      "type": "u",
      "entryA": {
        "id": 1245619,
        "image": 1672322,
        "isAnimated": 0
      },
      "entryB": {
        "id": 2317405,
        "image": 3057588,
        "isAnimated": 0
      }
    },
    {
      "id": 6981,
      "type": "u",
      "entryA": {
        "id": 1336282,
        "image": 1792389,
        "isAnimated": 0
      },
      "entryB": {
        "id": 1353338,
        "image": 1815319,
        "isAnimated": 0
      }
    },
    {
      "id": 7014,
      "type": "u",
      "entryA": {
        "id": 1293592,
        "image": 1736169,
        "isAnimated": 0
      },
      "entryB": {
        "id": 2007045,
        "image": 2653787,
        "isAnimated": 0
      }
    },
    {
      "id": 7035,
      "type": "u",
      "entryA": {
        "id": 870592,
        "image": 1176131,
        "isAnimated": 0
      },
      "entryB": {
        "id": 1938007,
        "image": 2565372,
        "isAnimated": 0
      }
    },
    {
      "id": 7059,
      "type": "u",
      "entryA": {
        "id": 2293165,
        "image": 3025832,
        "isAnimated": 0
      },
      "entryB": {
        "id": 850448,
        "image": 1148318,
        "isAnimated": 0
      }
    },
    {
      "id": 7011,
      "type": "u",
      "entryA": {
        "id": 98484,
        "image": 123649,
        "isAnimated": 0
      },
      "entryB": {
        "id": 165018,
        "image": 214737,
        "isAnimated": 0
      }
    },
    {
      "id": 7024,
      "type": "u",
      "entryA": {
        "id": 1842642,
        "image": 2444439,
        "isAnimated": 0
      },
      "entryB": {
        "id": 2387521,
        "image": 3155347,
        "isAnimated": 0
      }
    },
    {
      "id": 7058,
      "type": "u",
      "entryA": {
        "id": 223575,
        "image": 297072,
        "isAnimated": 0
      },
      "entryB": {
        "id": 1085274,
        "image": 1462330,
        "isAnimated": 0
      }
    }
  ],
	"coins": {
		"silver": 300,
		"gold": 20
	},
	"award": {
		"silver": 5,
		"points": 10
	},
	"alerts": {
		"faceoffs": 8,
		"treats": 4,
		"comments": 6,
		"prizes": 2,
        "prizeStore": {
            "parent": 4,
            "dog": 2,
            "cat": 1,
            "critter": 0,
            "total": 7
        },
		"myEntries": 0,
		"winTickets": 0
	},
	"messages": [
	  "SIGNED IN USER CANNOT OWN ENTRY",
	  "USER HAS EXCEEDED 50 POINTS ON THIS ENTRY"
	],
	"showAds": {
		"start": 1,
		"interval": 1,
		"adFree": {
		  "productId": "com.goodboystudios.petparade.adfree.2",
		  "interval": 6
		}		
	},
    "canPost": true,
    "entryFee": {
        "type": "silver",
        "fee": 50
    },
    "coinPromo": {
      	"coinBundle": 107,
    	"type": "gold",
    	"expires": 123115.598
  	}
}
```

This endpoint is called only once each time the app loaded. This call represents a game play session.

### HTTP Request

`GET http://api.parade.pet/game/init`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | false | id value of first faceOff entry
contest | false | id value of contest


<aside class="success">
The endpoint returns the user's active FaceOffSet, which is where the user left off in the game. In the FaceOffSet returned, there will optionally be a activeFaceOff object returned which is the currently active FaceOff for the set if the user is returning to the game without having completed the FaceOff.  The return data also includes three arrays of possible entries organized by pet type that the game can use to create new FaceOffs. If the entry parameter is specified, this entry will be added to the top of the appropriate dogs/cats/critters list, and will be used  as entryA in the first faceOff.

The alerts object contains the count of new faceoff and treat alerts to show in the Alerts tab.  The total number of alerts in the bottom nav is the sum of faceoff and treat alerts.

The return data also contains the award values for silver and points for successfully judging a FaceOff.

Also, a the "messages" field will is an array of warning messages for testing purposes, and to be used by the client if necessary.
</aside>


## Start FaceOff

```shell
curl "http://api.parade.pet/game/faceoff/start"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entryA=123'
  -d 'entryA=456'
  -d 'faceOffSet=29122'
```

> The above command returns JSON structured like this:

```json
{
  "faceOff": {
  	"id": 224789,
  	"entryA": {
  		"id":123,
  		"image": 456,
  		"pet": {
  			"id": 292,
  			"name": "Sparky",
  			"image": 92,
  			"points": 9282
  		}
  	},
  	"entryB": {
  		"id":456,
  		"image": 789,
  		"pet": {
  			"id": 908,
  			"name": "Tom",
  			"image": 211,
  			"points": 282
  		}
  	} 	
  },
  "coins": {
  	"silver": 300,
  	"gold": 20
  }
}
```

This endpoint is called at the start of a new FaceOff. The client is responsible for randomly selecting pairings of entries to create new FaceOff's from the array lists returned.  

### HTTP Request

`POST http://api.parade.pet/game/faceoff/start`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entryA | true | id value of Pet entry A
entryB | true | id value of Pet entry B
faceOffSet | true | id value of FaceOffSet to assign the FaceOff.

<aside class="success">
Returns the newly created FaceOff along with the Pet name and point balances for each entry in the FaceOff and the user's current coin balances.  The point and coin balances are displayed by the client after the winner is picked.  
</aside>


## End FaceOff

```shell
curl "http://api.parade.pet/game/faceoff/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'faceOff=274661'
  -d 'winner=123'
  -d 'matchId=6956'
  -d 'matchType=u'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is called at the end of a FaceOff.

### HTTP Request

`POST http://api.parade.pet/game/faceoff/end`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
faceOff | true | id value of active FaceOff
winner | true | id value of winning Pet
matchId | true | id of match
matchType | true | u for UserMatch, t for TournamentMatch

<aside class="success">
Returns "OK" or an error message.  The client does not need to wait for this call and can use the award values returned from /game/init to increment the user's silver and the pet's points returned from /faceoff/start.
</aside>

## End FaceOffSet

```shell
curl "http://api.parade.pet/game/faceoffset/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'faceOffSet=224789'
  -d 'contest=2'
```

> The above command returns JSON structured like this:

```json
{
  "award": {
  	"type": "treat",
  	"value": {"id":292, "name": "Steak", "image": 2912 }
  },
  "faceOffSet": {
	  "id": 29,
	  "type": "Dogs vs Critters",
	  "size": 10
  },
  "winners": [
    {
	  "id": 88,
      "name": "Sparks",
      "entry": 123,
      "image": 282,
      "points": 30,
      "place": 212,
      "type": "Dog"
    },
    {
	  "id": 927,
      "name": "Petunia",
      "entry": 456,
      "image": 2292,
      "points": 30,
      "place": 87,
      "type": "Rabbit"
    },
    {
	  "id": 288,
      "name": "Dhalia",
      "entry": 789,
      "image": 2828,
      "points": 20,
      "place": 928,
      "type": "Horse"
    }
    ],
	"alerts": {
		"faceoffs": 8,
		"treats": 4,
		"comments": 6,
		"prizes": 2,
        "prizeStore": {
            "parent": 4,
            "dog": 2,
            "cat": 1,
            "critter": 0,
            "total": 7
        },
		"myEntries": 0,
		"winTickets": 0       
	},
	 "shareReward": {
		"type": "gold",
		"reward": 5
	  },
	  "watchAdReward": {
		"type": "gold",
		"reward": 5
	  },
	"showTutorial": 0
}
```

This endpoint is called when a FaceOffSet has been completed.  The call automatically closes the currently active set and creates a new active FaceOffSet for the user.  

### HTTP Request

`POST http://api.parade.pet/game/faceoffset/end`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
faceOffSet | true | id value of the FaceOffSet to end.
contest | false | id value of current contest

<aside class="success">
Returns the award for completing the set and the new active FaceOffSet.  Valid award type values are treat, silver, or gold.  If the award type is "treat," then the value is the treat object.  If the award type is silver or gold, then the value is the amount of coins awarded.  It also returns the winners of the completed FaceOffSet, with number of points you gave to each winner.
</aside>

## Collect XP

```shell
curl "http://api.parade.pet/game/collect/xp"
  -H "Authorization: Bearer meowmeowmeow"
  -d 'faceOffId=1565666813'
  -d 'petId=132045'
  -d 'winner=416769'
```

> The above command returns JSON structured like this:

```json
{
    "awardedXP": 2,
    "userLevel": {
        "number": 1,
        "xp": 11,
        "xpToNextLevel": 50
    }
}
```

This endpoint updates the collectXP field in the faceOff cache to 1 for the faceOff retrieved using petId and faceOffId.  It also updates the totalXP field on the user object based on whether the faceOff entry was the winner or loser.

### HTTP Request

`POST http://api.parade.pet/game/collect/xp`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
faceOffId | true | faceOff id from /alerts/faceoffs
petId | true | pet id from /alerts/faceoffs
winner | true | winning entry id from /alerts/faceoffs

<aside class="success">
Returns number of XP awarded to user and the current userLevel.
</aside>
