# Treats

## Send Treatgift

```shell
curl "https://api.parade.pet/v2/treat/send"
  -H "Authorization: Bearer meowmeowmeow"
  -d "treat=15"
  -d "entry=597384"
  -d "match=3"
  -d "type=user"
```

> The above command returns JSON structured like this:

```json
"OK"
```

Use this endpoint to send a treatgift.

### HTTP Request

`POST http://api.parade.pet/v2/treat/send`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
treat | true | Treat ID
entry | true | Entry ID
match | true | ID of UserMatch or TournamentMatch
type | true | Either 'user' or 'tournament'

<aside class="success">
Returns OK
</aside>

## Accept Treatgift

```shell
curl "https://api.parade.pet/v2/treat/accept"
  -H "Authorization: Bearer meowmeowmeow"
  -d "id=150"
```

> The above command returns JSON structured like this:

```json
"OK"
```

Use this endpoint to accept a treatgift.

### HTTP Request

`POST http://api.parade.pet/v2/treat/accept`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | TreatGift ID

<aside class="success">
Returns OK
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
			"id": 19221,
			"name": "Jamie Oliver",
			"profileImage": 213,
			"socialImageUrl": null,
			"gaveTreatsTo": [
				{
					"name": "Coder",
					"numTreats": 1,
					"points": 2
				}
			],
			"pets": [{
				"id": 80539,
				"name": "Mr.Fuzzy",
				"onTreatBreak": 0,
				"entry": 252951,
				"image": 337923,
				"points": 267504,
				"type": "Cat"
			}, 
			{
				"id": 80540,
				"name": "Kuddles",
				"onTreatBreak": 0,
				"entry": 252951,
				"image": 337923,
				"points": 267504,
				"type": "Dog"	
			}]				
		}
	],
	"treatAll": [
		{
			"id": 123,
			"name": "T-bone Steak",
			"type": "dogs",
			"points": 100,
			"price": 50,
			"isPremium": true, 
			"count": 3,
			"totalPrice": 300,
			"pets": [
				{"id": 80540, "name": "Kuddles", 
				  "onTreatBreak": 0,
                   "entry": 457394,
                   "image": 626416,
                   "points": 28881,
                   "type": "Dog"}
			]
		},
		{
			"id": 124,
			"name": "Turducken",
			"type": "dogs",
			"points": 150,
			"price": 100,
			"isPremium": true,
			"count": 1,
			"totalPrice": 150,
			"pets": [
				{"id": 80540, "name": "Kuddles", 
				  "onTreatBreak": 0,
                   "entry": 457394,
                   "image": 626416,
                   "points": 28881,
                   "type": "Dog"}
			]
		},
		{
			"id": 12,
			"name": "Tuna Steak",
			"type": "cats",
			"points": 150,
			"price": 100,
			"isPremium": true,
			"count": 2,
			"totalPrice": 300,
			"pets": [
				{"id": 80542, "name": "Mr Fuzzy", 
				  "onTreatBreak": 0,
                   "entry": 457394,
                   "image": 626416,
                   "points": 28881,
                   "type": "Cat"},
				{"id": 80543, "name": "Kitten", 
				  "onTreatBreak": 0,
                   "entry": 457394,
                   "image": 626416,
                   "points": 28881,
                   "type": "Cat"}                		
			]
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
