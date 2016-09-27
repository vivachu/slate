# Game Play

## Initialize the game

```shell
curl "http://api.parade.pet/game/init"
  -H "Authorization:  Bearer meowmeowmeow"
  -d "entry=283"
```

> The above command returns JSON structured like this:

```json 
{
	"faceOffSet": {
		"id": 29,
		"type": "dogs vs cats", 
		"numJudged": 4,
		"size": 10,
		"activeFaceOff": { 
			"id": 224789,
			"entryA": {
				"id":123,
				"image": 2292,
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
				"pet": {
					"id": 908,
					"name": "Tom",
					"image": 211,
					"points": 282
				}
			} 	
		}
	},
	"coins": {
		"silver": 300,
		"gold": 20
	},
	"dogs": [
	{ 
	  "entry": 129,
	  "image": 234
	},
	{ 
	  "entry": 282,
	  "image": 123
	},
	{ 
	  "entry": 1282,
	  "image": 567
	}
	],
	"cats": [
	{ 
	  "entry": 2182,
	  "image": 678
	},
	{ 
	  "entry": 18,
	  "image": 480
	},
	{ 
	  "entry": 128,
	  "image": 170
	}
	],
	"critters": [
	{ 
	  "entry": 282,
	  "image": 681
	},
	{ 
	  "entry": 8878,
	  "image": 481
	},
	{ 
	  "entry": 8982,
	  "image": 801
	}
	],
	"award": {
		"silver": 5,
		"points": 10
	},
	"alerts": {
		"faceoffs": 8,
		"treats": 4
	},
	"messages": [
	  "SIGNED IN USER CANNOT OWN ENTRY",
	  "USER HAS EXCEEDED 50 POINTS ON THIS ENTRY"
	]
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
  		"pet": {
  			"id": 292,
  			"name": "Sparky",
  			"image": 92,
  			"points": 9282
  		}
  	},
  	"entryB": {
  		"id":456,
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

<aside class="success">
Returns "OK" or an error message.  The client does not need to wait for this call and can use the award values returned from /game/init to increment the user's silver and the pet's points returned from /faceoff/start. 
</aside>

## End FaceOffSet

```shell
curl "http://api.parade.pet/game/faceoffset/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'faceOffSet=224789'
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
  ]
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

<aside class="success">
Returns the award for completing the set and the new active FaceOffSet.  Valid award type values are treat, silver, or gold.  If the award type is "treat," then the value is the treat object.  If the award type is silver or gold, then the value is the amount of coins awarded.  It also returns the winners of the completed FaceOffSet, with number of points you gave to each winner.
</aside>

