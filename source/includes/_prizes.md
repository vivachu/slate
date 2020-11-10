# Prizes

## Get Prize Catalog

```shell
curl "http://api.parade.pet/prizes/parent"
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
            "type": "Parent",
            "name": "Custom Dog Tag",
            "brand": "Field Trip",
            "price": 14.99,
            "shippingCost": 0,
            "isPremium": false,
            "description": "A beautiful floral dog tag with your pet's name and your phone number. Make a statement in style!",
            "checkoutUrl": "https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4EHGLVD8U8R8E",
            "imageUrl": "http://assets.parade.pet/prizes/1502412591285.jpeg",
            "state": 1,
            "prizeOption1": {
                "name": "Pet Name",
                "type": 0,
                "options": [
                    ""
                ]
            },
            "prizeOption2": {
                "name": "Phone Number",
                "type": 0,
                "options": [
                    ""
                ]
            },
            "prizeOption3": null,
            "prizeOption4": null,
            "fulfillmentTime": "Ships in 3-6 days.",
            "isCharity": false,
            "id": 201,
            "pinned": false,
            "isNew": true,
            "ticketPrice": 1499,
            "promo": {
                "type": "price",
                "value": 10.49,
                "expires": 109325.671
            }
    },
    {
            "type": "Parent",
            "name": "Mug With Your Pet's Pic",
            "brand": "Country Crafts",
            "price": 16.99,
            "shippingCost": 0,
            "isPremium": false,
            "description": "Add your pet's photo and name to this versatile mug!",
            "checkoutUrl": "https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=6RZS85LNVVE2N",
            "imageUrl": "http://assets.parade.pet/prizes/1502411684348.jpeg",
            "state": 1,
            "prizeOption1": null,
            "prizeOption2": null,
            "prizeOption3": null,
            "prizeOption4": null,
            "fulfillmentTime": "Ships in 5-10 days.",
            "isCharity": false,
            "id": 198,
            "pinned": false,
            "isNew": false,            
            "ticketPrice": 1699,
            "promo": null
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

## Get Prizes based on Price Tier

```shell
curl "http://api.parade.pet/prizes/tier/2"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "tickets": {
    "silver": 558,
    "gold": 4355
  },
  "prizes": [
    {
      "type": "Parent",
      "name": "Pet Parade Bumper Sticker",
      "brand": "Pet Parade",
      "price": 2,
      "shippingCost": 0.49,
      "isPremium": true,
      "description": "Get this bumper sticker to show everyone in town that you have the cutest pet on Pet Parade!",
      "checkoutUrl": "http://localhost:1337/checkout/314/1090",
      "imageUrl": "https://assets.parade.pet/prizes/1509557777535.jpeg",
      "state": 1,
      "prizeOption1": null,
      "prizeOption2": null,
      "prizeOption3": null,
      "prizeOption4": null,
      "fulfillmentTime": "Ships within 14 days.",
      "isCharity": false,
      "sortOrder": null,
      "id": 314,
      "pinned": false,
      "isNew": false,
      "buyButton": "GET IT NOW",
      "ticketPrice": 250,
      "promo": null
    },
    {
      "type": "Cat",
      "name": "Claw Protectors",
      "brand": "Foreveryang",
      "price": 4.99,
      "shippingCost": 0,
      "isPremium": true,
      "description": "Cap your cat's nails to save your furniture from their claws.",
      "checkoutUrl": "https://www.amazon.com/gp/product/B01N3Q82WU/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=petparade02-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=B01N3Q82WU&linkId=783a1f1fef0f6516910f5b387b170ab5",
      "imageUrl": "https://images-na.ssl-images-amazon.com/images/I/61NdejU%2BzOL._SL1280_.jpg",
      "state": 1,
      "prizeOption1": null,
      "prizeOption2": null,
      "prizeOption3": null,
      "prizeOption4": null,
      "fulfillmentTime": "Ships within 14 days.",
      "isCharity": false,
      "sortOrder": null,
      "id": 124,
      "pinned": false,
      "isNew": false,
      "buyButton": "GET IT NOW",
      "ticketPrice": 250,
      "promo": {
          "type": "price",
          "value": 10.49,
          "expires": 109325.671
      }
    }
  ]
}
```

Retrieve the Prize Catalog for the specified prize tier.     

### HTTP Request

`GET http://api.parade.pet/prizes/tier/:prizeTier`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
prizeTier | true | Prize tier ID.

<aside class="success">
Returns prizes for the specified prize tier. The authorized user's ticket balance is also returned.
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
        "type": "Parent",
        "name": "Custom Dog Tag",
        "brand": "Field Trip",
        "price": 14.99,
        "shippingCost": 0,
        "isPremium": false,
        "description": "A beautiful floral dog tag with your pet's name and your phone number. Make a statement in style!",
        "checkoutUrl": "https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=4EHGLVD8U8R8E",
        "imageUrl": "http://assets.parade.pet/prizes/1502412591285.jpeg",
        "state": 1,
        "prizeOption1": {
            "name": "Pet Name",
            "type": 0,
            "options": [
                ""
            ]
        },
        "prizeOption2": {
            "name": "Phone Number",
            "type": 0,
            "options": [
                ""
            ]
        },
        "prizeOption3": null,
        "prizeOption4": null,
        "fulfillmentTime": "Ships in 3-6 days.",
        "isCharity": false,
        "id": 201,
        "pinned": false,
        "pinnedId": null,
        "ticketPrice": 1499,
        "isNew": true,
        "promo": {
            "type": "price",
            "value": 10.49,
            "expires": 109230.869
        }
    },
    "tickets": {
        "silver": 48,
        "gold": 10
    }
}
```

Retrieve the Prize for the specified prize.     

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

## Get Special Offers

```shell
curl "http://api.parade.pet/tickets/offers"
```

> The above command returns JSON structured like this:

```json
[
    {
        "title": "INVITE FRIENDS",
        "description": "Get 25 gold tickets per friend who enters the contest using your code.",
        "image": "http://assets.parade.pet/offers/friend-referral.png",
        "awardAmount": 25,
        "awardType": 1,
        "buttonText": "SHARE MY CODE",
        "link": "/invite-friends",
        "linkType": "internal"
    },
    {
        "title": "BARKBOX SUBSCRIPTION",
        "description": "Get 50 gold tickets when you subscribe to BarkBox.",
        "image": "http://assets.parade.pet/offers/barkbox.png",
        "awardAmount": 50,
        "awardType": 1,
        "buttonText": "GET BARKBOX",
        "link": "https://barkbox.evyy.net/c/391283/307028/1369",
        "linkType": "external"
    }
]     
```

Retrieve an array of special offers.     

### HTTP Request

`GET http://api.parade.pet/tickets/offers`


<aside class="success">
Returns list of special offers.  Valid values for awardType are 0 = silver tickets and 1 = gold tickets.  The linkType is either "internal" or "external" and indicates whether to launch an external web link outside of the app or link to a page internal to the app.   
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

## Get Prize Tiers

```shell
curl "http://api.parade.pet/prize/tiers"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this :

```json
{
  "tickets": 4355,
  "prizeTiers": [
    {
      "id": 1,
      "tier": 100,
      "progress": 1
    },
    {
      "id": 2,
      "tier": 250,
      "progress": 1
    },
    {
      "id": 3,
      "tier": 500,
      "progress": 1
    },
    {
      "id": 4,
      "tier": 1000,
      "progress": 1
    },
    {
      "id": 5,
      "tier": 2500,
      "progress": 1
    },
    {
      "id": 6,
      "tier": 5000,
      "progress": 0.871
    },
    {
      "id": 7,
      "tier": 7500,
      "progress": 0
    },
    {
      "id": 8,
      "tier": 10000,
      "progress": 0
    },
    {
      "id": 9,
      "tier": 25000,
      "progress": 0
    }
  ]
}
```

Retrieve the list of prize tiers.

### HTTP Request

`GET http://api.parade.pet/prize/tiers`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Return the authorized user's gold ticket balance and the list of prize tiers along with user's progress in each tier.
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
curl "http://api.parade.pet/prize/redemption"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'prize=2912'
  -d 'address=532'
  -d 'option1=red'
  -d 'option2=Medium'
```

> The above command returns JSON structured like this:

```json
{
	"shareUrl": "https://share.parade.pet/prize/won/9281"
}
```

This endpoint is used to accept the tickets that were given to the user from the prize award after opening the Prize Box.

### HTTP Request

`POST http://api.parade.pet/prize/redemption`

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
Returns a 200 response with a shareUrl string if success or an error code and message if the user does not have enough tickets to redeem the prize.  
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

## Charity Goals

```shell
curl "http://api.parade.pet/charitygoals"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "tickets": 722,
    "goals": [
        {
            "id": 1,
            "name": "Save A Rescue Dog",
            "description": "Adopt-A-Dog's mission is to save, socialize and secure loving homes for unwanted or abandoned dogs.  Adopt-A-Dog accomplishes this goal by providing the highest standard of care for dogs in need with a particular focus on ensuring that all aspects of their overall health and well-being are addressed.",
            "dollarGoal": 1000,
            "ticketGoal": 100000,
            "ticketsRaised": 114334,
            "numGivers": 780,
            "state": 1,
            "moreInfoUrl": "https://adopt-a-dog.org/who-we-are/",
            "cashDonateUrl": "https://adopt-a-dog.org/support/",
            "dollarsRaised": 1143.34,
            "path": "https://assets.parade.pet/partners/adopt-a-dog/creatives/jan-2019/",
            "partner": {
                "id": 10,
                "name": "Adopt-A-Dog",
                "path": "adopt-a-dog",
                "description": "Adopt-A-Dog's mission is to save, socialize and secure loving homes for unwanted or abandoned dogs."
            },
            "donated": 2343,
            "angelLevels": {
                "platinum": 1000,
                "gold": 500,
                "silver": 250,
                "bronze": 100
            }
        },
        {
            "id": 2,
            "name": "Winter Charity Campaign",
            "description": "Animal shelters across the nation are forced to stretch their resources to the brink to accommodate an overwhelming population of homeless and at-risk animals.",
            "dollarGoal": 2500,
            "ticketGoal": 750000,
            "ticketsRaised": 90705,
            "numGivers": 661,
            "state": 1,
            "moreInfoUrl": "https://aspca.org",
            "cashDonateUrl": "https://secure.aspca.org/donate/donate",
            "dollarsRaised": 302.35,
            "path": "https://assets.parade.pet/partners/aspca/creatives/winter-2018/",
            "partner": {
                "id": 11,
                "name": "ASPCA",
                "path": "aspca",
                "description": "We give all adoptable pets the best possible chance of finding loving homes."
            },
            "donated": 1330,
            "angelLevels": {
                "platinum": 1000,
                "gold": 500,
                "silver": 250,
                "bronze": 100
            }
        }
    ]
}
```

This endpoint is used to get all active Charity Goals. 

### HTTP Request

`GET http://api.parade.pet/charitygoals`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns charity goals with each of its progress and amount of tickets donated by authenticated user for each charity.
</aside>

## Random Charity Goal

```shell
curl "http://api.parade.pet/charityGoal/serve"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 4,
  "name": "Another Charity Test",
  "description": "Description of another charity test",
  "dollarGoal": 1000,
  "ticketGoal": 100,
  "ticketsRaised": 120,
  "numGivers": 0,
  "state": 1,
  "dollarsRaised": 0,
  "moreIntoUrl": "https://more.info.url/",
  "cashDonateUrl": "https://cash.donate.url/",
  "userTickets": 5000,
  "path": "https://assets.parade.pet/partners/vp/creatives/another-test-path/",
  "partner": {
    "id": 2,
    "name": "VitaPup",
    "path": "vp",
    "description": "Super healthy treats for your super pup."
  },
  "donated": 100,
  "angelLevels": {
    "platinum": 10,
    "gold": 10,
    "silver": 10,
    "bronze": 10
  },
  "angels": [
    {
      "id": 1,
      "name": "John Doe",
      "profileImage": 12345,
      "socialImageUrl": null,
      "ticketsDonated": 100
    },
    {
      "id": 2,
      "name": "Jane Doe",
      "profileImage": null,
      "socialImageUrl": "https://graph.facebook.com/v2.7/1234567890/picture?height=100&width=100",
      "ticketsDonated": 20
    }
  ]
}
```

This endpoint is used to get one random Charity Goal. 

### HTTP Request

`GET http://api.parade.pet/charityGoal/serve`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns one random charity goal with its progress and amount of tickets donated by authenticated user.
</aside>

## Donate to Charity 

```shell
curl "http://api.parade.pet/charityGoal/donate"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'charityGoal=1'
  -d 'ticketAmount=100'
```

> The above command returns JSON structured like this:

```
{
  "periodType": 1,
  "isPremium": false,
  "periodStart": "2018-12-30",
  "periodEnd": "2019-01-05",
  "acceptDate": "2019-01-01T08:58:58.176Z",
  "tickets": 0,
  "category": "Angel:vp:VitaPup",
  "award": "Gold",
  "user": 302804
}
```

This endpoint is used donate tickets to a charity.

### HTTP Request

`POST http://api.parade.pet/charityGoal/donate`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
ticketAmount | true | amount of gold ticket that authenticated user would like to donate 
charityGoal | true | ID of the Charity Goal 

<aside class="success">
Returns Prize Award data.
</aside>

## Verify Address

```shell
curl "http://api.parade.pet/verifyAddress"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "isValid": true,
  "inputAddress": {
    "street": "1200 Park Ave",
    "city": "Emeryville",
    "state": "CA",
    "postalCode": "94608"
  },
  "uspsAddress": {
    "street": "1200 PARK AVE",
    "city": "EMERYVILLE",
    "state": "CA",
    "postalCode": "94608"
  }
}
```

This endpoint is used to verify an address against US Postal Service database.

### HTTP Request

`POST http://api.parade.pet/verifyAddress`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
street | false | Address street
city | false | Address city 
state | false | Address state
postalCode | false | Address postal code

<aside class="success">
Returns both user inputted and USPS verified addresses.  
</aside>
