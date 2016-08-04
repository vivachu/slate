# Alerts

## Get Treats To Accept

```shell
curl "http://api.parade.pet/alerts/treats"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
	"alerts": [
		{ 
		  "timestamp": "1 hour",
		  "sender": {
		  	"id": 2912,
		  	"name": "John Snow",
		  	"image": 9287
		  },
		  "pet": {
		  	"id": 282,
		  	"name": "Petunia",
		  	"entry": 32192,
		  	"image": 2928,
		  	"points": 9287
		  },
		  "treats": [
		  	{
			  "accept": 129,
			  "name": "Ribeye",
			  "points": 100
		  	},
		  	{
			  "accept": 130,
			  "name": "T-Bone",
			  "points": 100
		  	}		  	
		  ]
		},
		{ 
		  "timestamp": "1 day",
		  "sender": {
		  	"id": 2812,
		  	"name": "Taylor Swift",
		  	"image": 276
		  },
		  "pet": {
		  	"id": 958,
		  	"name": "Fluffy",
		  	"entry": 32193,
		  	"image": 28892,
		  	"points": 300
		  },
		  "treats": [
		  	{
			  "accept": 2982,
			  "name": "Cute Sushi",
			  "points": 100
		  	}	  	
		  ]
		}		
	]
}
```

This endpoint retrieves the list of treats that the pet owner must accept in order to collect points for their pet. Only treats that have not been accepted are returned by this endpoint. 

### HTTP Request

`GET http://api.parade.pet/alerts/treats`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, sender, receiving pet, and array of one or more treats. The Sender is the user who sent the treat(s).  The Pet is the receiving pet along with the winning entry that prompted the treat. The image and points are the entry's image and points balance (not the pets).  
</aside>