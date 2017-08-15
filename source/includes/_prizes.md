# Prizes

## Get Prize Catalog

```shell
curl "http://api.parade.pet/prizes/dog"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "tickets": {
    "silver": 102,
    "gold": 12
  },
  "prizes": [
    {
      "type": "Dog",
      "name": "Puppy Teepee",
      "brand": "zoovilla",
      "isPremium": true,
      "description": "A stylish tent for your pup to play and lounge in.",
      "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/81njkstSTQL._SL600_.jpg",
      "id": 30,
      "ticketPrice": 416,
      "pinned": true
    },
    {
      "type": "Dog",
      "name": "Memory Foam Pet Bed",
      "brand": "LatitudeC",
      "isPremium": false,
      "description": "This ultra comfortable memory foam dog bed includes a fuzzy blanket. ",
      "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/71TpXNii47L._SL600_.jpg",
      "id": 29,
      "ticketPrice": 1499,
      "pinned": false
    }
    ]
}
```

Retrieve the Prize Catalog for the specified type: Parent, Dog, Cat or Critter.     

### HTTP Request

`GET http://api.parade.pet/prizes/:type`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | true | Either parent, dog, cat, or critter.

<aside class="success">
Returns prizes for the specified store type. The authorized user's ticket balance is also returned.
</aside>

## Get Prize

```shell
curl "http://api.parade.pet/prize/115"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "prize": {
        "type": "Critter",
        "name": "Pet Parade T-Shirt",
        "brand": null,
        "isPremium": false,
        "description": "Premium cotton purple tee with Pet Parade logo. Available in all adult and youth sizes.",
        "checkoutUrl": null,
        "imageUrl": "http://www.parade.pet/assets/images/T-Shirt-Logo.png",
        "state": 1,
        "prizeOption1": null,
        "prizeOption2": null,
        "prizeOption3": null,
        "prizeOption4": null,
        "fulfillmentTime": 3,
        "id": 194,
        "pinned": true,
        "pinnedId": 28,
        "ticketPrice": 560
    },
    "tickets": {
        "silver": 440,
        "gold": 1000
    }
}
```

Retrieve the Prize Catalog for the specified type: Dog, Cat or Critter.     

### HTTP Request

`GET http://api.parade.pet/prize/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | The id of the prize

<aside class="success">
Returns the prize details matching the id.  If no prize matches the id then 404 error is returned.
</aside>

## Get User Prizes

```shell
curl "http://api.parade.pet/prizes/user/1021"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "prizes": [
        {
            "id": 110,
            "name": "10 Gallon Aquarium",
            "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/81zvlOIT5nL._SL600_.jpg",
            "timestamp": 10081906.448,
            "action": "pinned"
        },
        {
            "id": 111,
            "name": "52\" Cat Tower",
            "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/41DAcsWFnJL.jpg",
            "timestamp": 10964373.447,
            "action": "redeemed",
            "tickets": 240,
            "isPremium": true
        },
        {
            "id": 117,
            "name": "T-Shirt with Your Cat's Photo",
            "imageUrl": "http://www.parade.pet/assets/images/T-Shirt-Cat.png",
            "timestamp": 10964579.448,
            "action": "pinned"
        }
}
```

Retrieve the list of prizes that the specified user has pinned or redeemed.  The timestamp for each prize is in seconds since the current time. If the prize has been redeemed, then the action is "redeemed" and the tickets and isPremium properties are set.  If isPremium = true, then the tickets are gold.  

### HTTP Request

`GET http://api.parade.pet/prizes/user/:userId`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userId | true | The ID of the User whose prizes you want to retrieve

<aside class="success">
Returns list of prizes that the user has pinned or redeemed.
</aside>


## Get Leaderboard Ticket Payouts

```shell
curl "http://api.parade.pet/tickets/payouts?type=dog"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "myTickets": {
        "silver": 24,
        "gold": 9
    },
    "payouts": [
        {
            "place": "1st",
            "week": {
                "tickets": 50,
                "type": "gold"
            },
            "month": {
                "tickets": 100,
                "type": "gold"
            }
        },
        {
            "place": "2nd",
            "week": {
                "tickets": 45,
                "type": "gold"
            },
            "month": {
                "tickets": 90,
                "type": "gold"
            }
        },
        {
            "place": "46-100",
            "week": {
                "tickets": 1,
                "type": "silver"
            },
            "month": {
                "tickets": 1,
                "type": "silver"
            }
        },
        {
            "place": "N",
            "week": {
                "tickets": 50,
                "type": "silver"
            },
            "month": {
                "tickets": 100,
                "type": "silver"
            }
        },
        {
            "place": "G",
            "week": {
                "tickets": 10,
                "type": "silver"
            },
            "month": {
                "tickets": 20,
                "type": "silver"
            }
        },
        {
            "place": "I",
            "week": {
                "tickets": 50,
                "type": "silver"
            },
            "month": {
                "tickets": 100,
                "type": "silver"
            }
        }
    ],
    "endOfWeek": "4d 6h",
    "endOfMonth": "6d 6h"
}    
    
```

Retrieve the ticket payouts for placing in the weekly and monthly leaderboards for the specified type.     

### HTTP Request

`GET http://api.parade.pet/tickets/payouts`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | false | The leaderboard: all, location, dog, cat, or critter

<aside class="success">
Returns tickets payouts for weekly and monthly for the specified leaderboard type. The authorized user's ticket balance is also returned and the time till the end of the week and month.
</aside>

## Accept Tickets

```shell
curl "http://api.parade.pet/tickets/accept"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'id=291'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to accept the tickets that were given to the user from the prize award after opening the Prize Box.

### HTTP Request

`POST http://api.parade.pet/tickets/accept`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | ID of the TicketAward object to accept

<aside class="success">
Returns OK if success or an error message and code if Ticket object does not exist, or the authorized user does not own the TicketAward object. The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>

## Redeem Prize

```shell
curl "http://api.parade.pet/prize/redeem"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'prize=2912'
  -d 'address=532'
  -d 'option1=red'
  -d 'option2=Medium'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to accept the tickets that were given to the user from the prize award after opening the Prize Box.

### HTTP Request

`POST http://api.parade.pet/prize/redeem`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
prize | true | ID of the Prize object to redeem
address | true | ID of the Address object to ship to
option1 | false | Custom option 1
option2 | false | Custom option 2
option3 | false | Custom option 3
option4 | false | Custom option 4

<aside class="success">
Returns OK if success or an error message if the user does not have enough tickets to redeem the prize.  
</aside>

## Pin Prize

```shell
curl "http://api.parade.pet/prize/pin"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'prize=100'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to pin a prize to the top of the list.

### HTTP Request

`POST http://api.parade.pet/prize/pin`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
prize | true | ID of the Prize object to pin

<aside class="success">
Returns OK if success. The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>

## Unpin Prize

```shell
curl "http://api.parade.pet/prize/unpin"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'prize=100'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is used to unpin a prize.

### HTTP Request

`POST http://api.parade.pet/prize/unpin`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
prize | true | ID of the Prize object to unpin

<aside class="success">
Returns OK if success. The design of this call is such that the client should call this asynchronously without waiting for it to return.  
</aside>
