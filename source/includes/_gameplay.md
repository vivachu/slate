# Game Play

## Initialize the game

```shell
curl "http://api.parade.pet/game/init"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
	"faceOffSet": {
		"id": 29,
		"type": "dogs vs cats", 
		"activeFaceOff": {"id":29, "entryA": 222, "entryB": 292 },
		"numJudged": 4,
		"size": 10
	},
	"dogs": [
	{ 
	  "entry_id": 129,
	  "image_id": 234
	},
	{ 
	  "entry_id": 282,
	  "image_id": 123
	},
	{ 
	  "entry_id": 1282,
	  "image_id": 567
	}
	],
	"cats": [
	{ 
	  "entry_id": 2182,
	  "image_id": 678
	},
	{ 
	  "entry_id": 18,
	  "image_id": 480
	},
	{ 
	  "entry_id": 128,
	  "image_id": 170
	}
	],
	"other": [
	{ 
	  "entry_id": 282,
	  "image_id": 681
	},
	{ 
	  "entry_id": 8878,
	  "image_id": 481
	},
	{ 
	  "entry_id": 8982,
	  "image_id": 801
	}
	],
	"award": {
		"silver": 5,
		"points": 10
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

<aside class="success">
The endpoint returns the user's active FaceOffSet, which is where the user left off in the game. In the FaceOffSet returned, there will optionally be a activeFaceOff object returned which is the currently active FaceOff for the set if the user is returning to the game without having completed the FaceOff.  The return data also includes three arrays of possible entries organized by pet type that the game can use to create new FaceOffs. The return data also contains the award values for silver and points for successfully judging a FaceOff.
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
  			"points": 9282
  		}
  	},
  	"entryB": {
  		"id":456,
  		"pet": {
  			"id": 908,
  			"name": "Tom",
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
  	"value": {"id":292, "name": "Steak" }	
  },
  "faceOffSet": {
	"id": 29,
	"type": "dogs", 
	"size": 10
  }
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
Returns the award for completing the set and the new active FaceOffSet.  Valid award type values are treat, silver, or gold.  If the award type is "treat," then the value is the treat object.  If the award type is silver or gold, then the value is the amount of coins awarded.  
</aside>

