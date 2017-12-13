# Treats

## Get Treats

```shell
curl "http://api.parade.pet/treats"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
	"dogs": {
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
		]
	},
	"cats": {
		"owns": [
		{ 
		  "id": 27,
		  "treat": {
			  "id": 18,
			  "image": 18,
			  "name": "Goldfish"
		  }
		}
		],
		"forSale": [
		{ 
		  "id": 229,
		  "image": 334,
		  "name": "Fatty Tuna",
		  "isPremium": true,
		  "price": 20,
		  "points": 100
		},
		{ 
		  "id": 230,
		  "image": 335,
		  "name": "Kitten Kibble",
		  "isPremium": false,
		  "price": 20,
		  "points": 10
		},
		{ 
		  "id": 231,
		  "image": 336,
		  "name": "Yellowtail Sashimi",
		  "isPremium": true,
		  "price": 10,
		  "points": 50
		}
		]
	},
	"critters": {
		"owns": [],
		"forSale": [
		{ 
		  "id": 329,
		  "image": 434,
		  "name": "Baby Carrots",
		  "isPremium": true,
		  "price": 20,
		  "points": 100
		},
		{ 
		  "id": 330,
		  "image": 435,
		  "name": "Hay",
		  "isPremium": false,
		  "price": 20,
		  "points": 10
		},
		{ 
		  "id": 331,
		  "image": 436,
		  "name": "Alfafa Srouts",
		  "isPremium": true,
		  "price": 10,
		  "points": 50
		}
		]
	},	
	"coins": {
		"silver": 50,
		"gold": 10
	}
}
```

A user may use her coins to purchase treats to send to a Pet.  In addition, users may acquire treats as awards for completing FaceOffSets.  This endpoint retrieves the list of treats that the user currently owns as well as a list of the treats that are available for sale. The treats are organized into three separate arrays based upon pet type: dogs, cats, and others.  Pets are only allowed to eat treats that match the pet type. When /game/faceoffset/end is called, the winners list contains the pets with the type returned as a string.  If the pet type is anything other than "Dog" or "Cat" then it is a critter.  

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

This endpoint is used to send treats to a Pet.  If the user currently owns a treat, then the id of owned treat is passed via the "owned" query parameter. If the user does not own the treat, then the "owned" query parameter is omitted and the treat is purchased and immediately sent to the specified pet.  If the sender is the same as pet owner of the receiving pet, then the treat is immediately accepted.  

### HTTP Request

`POST http://api.parade.pet/treat/send`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
pet | true | id value of Pet receiving the treat
owned | false | id value of TreatPurchase object representing the owned Treat.
treat | false | id value of Treat to send
entry | false | id value of Entry that referred the treat purchase

<aside class="success">
Returns OK if success or an error message and code if the user does not have enough coins.  The client should pre-check whether the user has enough coins before sending this request to the server.  The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>

## Accept Treat

```shell
curl "http://api.parade.pet/treat/accept"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'id=291,8272,8272'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to accept the treat(s) that were given to authorized user's Pet by another user.

### HTTP Request

`POST http://api.parade.pet/treat/accept`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | comma separated list of id values of TreatPurchase objects to accept

<aside class="success">
Returns OK if success or an error message and code if TreatPurchase object does not exist, or the authorized user does not own the Pet who was the target of the treat. The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>

## Get Treat Jars

```shell
curl "http://api.parade.pet/treatjars"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
	"user": {  
		"initials": "VC",
		"profileImage": 12,
		"socialImageUrl": null,
		"silverCoins": 1020,
		"goldCoins": 200
	},
	"basic": [
		{	
			"size": 5,
			"price": 10,
			"type": "silver"
		},
		{	
			"size": 10,
			"price": 20,
			"type": "silver"
		}
	],
	"premium": [
		{	
			"size": 5,
			"price": 10,
			"type": "gold"
		},
		{	
			"size": 10,
			"price": 20,
			"type": "gold"
		}
	]
}
```

This endpoint returns a list of TreatJars that the user may purchase.

### HTTP Request

`GET http://api.parade.pet/treatjars`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
The endpoint returns the authorized user's current coin balance along with a list of basic and premium treat jars for sale.  Each TreatJar has a size and a price in silver or gold coins.  
</aside>

## Buy Treat Jar

```shell
curl "http://api.parade.pet/treatjar/buy"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'type=premium'
  -d 'size=10'
```

> The above command returns JSON structured like this:

```json
{
	"id": 129,
	"user": { 
		"initials": "VC",
		"profileImage": 12,
		"socialImageUrl": null,
		"silverCoins": 1020,
		"goldCoins": 200,
		"pets": [
			{
				"name": "Coder", 
				"id": 1039, 
				"entry": 921, 
				"image": 1199,
				"startingPoints": 1022,  
				"endingPoints": 1132,  
				"treatsAccepted": [
					{
						"id": 100922,
						"name": "T-bone Steak",
						"points": 100,
						"sender": {
							"name": "Jamie Oliver",
							"profileImage": 213,
							"socialImageUrl": null
						}
					},
					{
						"id": 100922,
						"name": "Kibble",
						"points": 10,
						"sender": {
							"name": "Eliza Tarry",
							"profileImage": null,
							"socialImageUrl": "http://facebook.com/1292.jpg"
						}
					},
				]
			}
		]
	},
	"usersToTreatBack": [  
		{
			"name": "Jamie Oliver",
			"profileImage": 213,
			"socialImageUrl": null,
			"pets": [{
				"name": "Terry",
				"type": "Dog",
				"entry": 1231,
				"image": 1229
			}, 
			{
				"name": "Tom",
				"type": "Cat",
				"entry": 12312,
				"image": 122912			
			}]				
		}
	],
	"treatAll": [
		{
			"id": 123,
			"name": "T-bone Steak",
			"points": 100,
			"price": 50,
			"isPremium": true, 
			"count": 3,
			"totalPrice": 300
		},
		{
			"id": 124,
			"name": "Turducken",
			"points": 150,
			"price": 100,
			"isPremium": true,
			"count": 1,
			"totalPrice": 150
		},
		{
			"id": 12,
			"name": "Tuna Steak",
			"points": 150,
			"price": 100,
			"isPremium": true,
			"count": 2,
			"totalPrice": 300
		},
	]
}
```

This endpoint is used to purchase a Treat Jar to collect treats automatically for a user.  If the TreatJar is purchased successfully, the id of the TreatJar is returned along with the list of treats collected for each of the user's pets and a list of users and their pets to treat back along with a list of treats to purchase in a Treat All option.   

### HTTP Request

`POST http://api.parade.pet/treatjar/buy`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | true | string value: basic or premium
size | true | the size of the treat jar to purchase

<aside class="success">
Returns treatJar object with id of the treatJar purchased along with user's coin balance, list of pets and treats accepted and the list of pet owners and pets to treat back and list of treats to purchase in treat all option.
</aside>


## Treat Back All

```shell
curl "http://api.parade.pet/treatjar/treatback"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'treatJar=291'
```

> The above command returns the user's coin balance on success or an error message if the user does not have enough coins.

```json
{
	"silver": 3921, 
	"gold": 1021
}
```

This endpoint is used to send treats back to all pet owners' pets who originally sent treats to the buyer of the TreatJar.   

### HTTP Request

`POST http://api.parade.pet/treatjar/treatback`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
treatJar | true | id value of Treat Jar to fetch list of pet owners and their pets to send treats back to.  

<aside class="success">
Returns user's ending coin balance if success or an error message and code if the user does not have enough coins.  The client should pre-check whether the user has enough coins before sending this request to the server.  The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>

## Treats Email

```shell
curl "http://api.parade.pet/treats/email"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'id=291,8272,8272'
```

> The above command returns an array of user emails and treats for the users pets

```
[
  {
    "email": "24-petparade@mailinator.com",
    "treats": [
      {
        "pet": "CaliGrace",
        "sender": "Stephanie Smith",
        "points": 3,
        "treat": "California Roll",
        "treatImage": "http://stage-assets.parade.pet/cats/california_roll/california_roll_t@2x.png"
      }
    ]
  },
  {
    "email": "25-petparade@mailinator.com",
    "treats": [
      {
        "pet": "Goldie",
        "sender": "Beth Downs ",
        "points": 5,
        "treat": "Oatmeal Cookie",
        "treatImage": "http://stage-assets.parade.pet/critters/oatmeal_cookie/oatmeal_cookie_t@2x.png"
      },
      {
        "pet": "Goldie",
        "sender": "Stephanie Betancurt",
        "points": 2,
        "treat": "Pet Pellets",
        "treatImage": "http://stage-assets.parade.pet/critters/pet_pellets/pet_pellets_t@2x.png"
      },
      {
        "pet": "Goldie",
        "sender": "Kaylyn bourassa",
        "points": 15,
        "treat": "Blueberries",
        "treatImage": "http://stage-assets.parade.pet/critters/blueberries/blueberries_t@2x.png"
      }
    ]
  }
]
```

This endpoint requires authentication from a valid admin user.

### HTTP Request

`POST http://api.parade.pet/treats/email`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated Admin user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
hours | false | The number of hours to look back from the current day to limit the amount of treats and users to return.  For example, a value of 12 looks for treats that were given since 12 hours from the current time.  The default is 168 hours (7 days).
test | false | If this parameter is set, then all email addresses in the return data will be set to the value of this parameter.  For example, set test=yourEmail@you.com to send email to yourself. 

<aside class="success">
Returns an array of email addresses mapped to treats for the specific user.  
</aside>