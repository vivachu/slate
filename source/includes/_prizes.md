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
      "ticketPrice": 416
    },
    {
      "type": "Dog",
      "name": "Memory Foam Pet Bed",
      "brand": "LatitudeC",
      "isPremium": false,
      "description": "This ultra comfortable memory foam dog bed includes a fuzzy blanket. ",
      "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/71TpXNii47L._SL600_.jpg",
      "id": 29,
      "ticketPrice": 1499
    }
    ]
}
```

Retrieve the Prize Catalog for the specified type: Dog, Cat or Critter.     

### HTTP Request

`GET http://api.parade.pet/prizes/:type`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | true | Either dog, cat, or critter.

<aside class="success">
Returns prizes for the specified store type. The authorized user's ticket balance is also returned.
</aside>


## Get Leaderboard Ticket Payouts

```shell
curl "http://api.parade.pet/tickets/leaderboard"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "tickets": {
    "silver": 0,
    "gold": 0
  },
  "week": [
    {
      "place": "1st",
      "gold": 25,
      "silver": 50
    },
    {
      "place": "2nd",
      "gold": 23,
      "silver": 45
    },
    {
      "place": "3rd",
      "gold": 20,
      "silver": 41
    },
  ],
  "month": [
    {
      "place": "1st",
      "gold": 50,
      "silver": 100
    },
    {
      "place": "2nd",
      "gold": 45,
      "silver": 90
    },
    {
      "place": "3rd",
      "gold": 41,
      "silver": 81
    },
  ]
}
```

Retrieve the ticket payouts for placing in the weekly and monthly leaderboards.     

### HTTP Request

`GET http://api.parade.pet/tickets/leaderboard`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------

<aside class="success">
Returns tickets payouts for weekly and monthly leaderboards. The authorized user's ticket balance is also returned.
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
