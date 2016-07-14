# Treats

## Get Treats

```shell
curl "http://api.parade.pet/treats"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
	"owns": [
	{ 
	  "id": 22,
	  "treat": {
		  "id": 129,
		  "image": 234,
		  "name": "Ribeye"
	  }
	},
	{ 
	  "id": 23,
	  "treat": {
		  "id": 130,
		  "image": 235,
		  "name": "Chicken Drumstick"
	  }
	},
	{ 
	  "id": 24,
	  "treat": {
		  "id": 129,
		  "image": 234,
		  "name": "Ribeye"
	  }
	},
	],
	"forSale": [
	{ 
	  "id": 129,
	  "image": 234,
	  "name": "Ribeye",
	  "isPremium": true,
	  "price": 20,
	  "points": 100
	},
	{ 
	  "id": 130,
	  "image": 235,
	  "name": "Chicken Drumstick",
	  "isPremium": false,
	  "price": 20,
	  "points": 10
	},
	{ 
	  "id": 131,
	  "image": 236,
	  "name": "Yellow Dog Biscuit",
	  "isPremium": true,
	  "price": 10,
	  "points": 5
	}
	],
	"coins": {
		"silver": 50,
		"gold": 10
	}
}
```

A user may use her coins to purchase treats to send to a Pet.  In addition, users may acquire treats as awards for completing FaceOffSets.  This endpoint retrieves the list of treats that the user currently owns as well as a list of the treats that are available for sale. 

### HTTP Request

`GET http://api.parade.pet/treats`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
The endpoint returns the authorized user's owned treats acquired from completing FaceOffSets as well as a list of treats that are available for purchase.  The authorized user's coin balance is also returned.  
</aside>


## Send Treat

```shell
curl "http://api.parade.pet/treat/send"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'owned=291'
  -d 'treat=123'
  -d 'pet=29'
  -d 'entry=2922'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to send treats to a Pet.  If the user currently owns a treat, then the id of owned treat is passed via the "owned" query parameter. If the user does not own the treat, then the "owned" query parameter is omitted and the treat is purchased and immediately sent to the specified pet. 

### HTTP Request

`POST http://api.parade.pet/game/treat/send`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
owned | false | id value of TreatPurchase object representing the owned Treat.
treat | true | id value of Treat to send
pet | true | id value of Pet receiving the treat
entry | false | id value of Entry that referred the treat purchase

<aside class="success">
Returns OK if success or an error message and code if the user does not have enough coins.  The client should pre-check whether the user has enough coins before sending this request to the server.  The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>