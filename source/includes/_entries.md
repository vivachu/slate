# Entries

## Get Entry

```shell
curl "http://api.parade.pet/entry/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 283,
  "caption": "Arvel",
  "location": "Chicago",
  "locationPlaceId": "ChIJ7cv00DwsDogRAMDACa2m4K8",
  "image": 19878,
  "points": 880,
  "numFaceOffs": 172,
  "numTreats": 47,
  "pet": {
    "id": 9864,
    "name": "Arvel",
    "owner": {
      "id": 10027,
      "name": "Emery McLaughlin",
      "image": 19877
    },
    "type": "Dog"
  },
  "comments": [
    {
      "replies": [],
      "user": {
        "id": 104,
        "name": "Paula Pickles",
        "profileImage": 713,
        "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
      },
      "entry": 6280,
      "parent": null,
      "comment": "Mmmm smells so good",
      "id": 1523,
      "timestamp": 8162.516
    },
    {
      "replies": [
        {
          "id": 2049,
          "user": {
            "id": 104,
            "name": "Paula Pickles",
            "profileImage": 713,
            "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
          },
          "entry": 6280,
          "parent": 2048,
          "comment": "The best ever",
          "timestamp": 4167.518
        },
        {
          "id": 2050,
          "user": {
            "id": 104,
            "name": "Paula Pickles",
            "profileImage": 713,
            "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
          },
          "entry": 6280,
          "parent": 2048,
          "comment": "My dog eats my socks",
          "timestamp": 51.519
        },
        {
          "id": 2051,
          "user": {
            "id": 212,
            "name": "concetta78 ",
            "profileImage": null,
            "socialImageUrl": null
          },
          "entry": 6280,
          "parent": 2048,
          "comment": "Mine get into the laundry",
          "timestamp": 3.52
        }
      ],
      "user": {
        "id": 1090,
        "name": "Viva Chu",
        "profileImage": null,
        "socialImageUrl": null
      },
      "entry": 6280,
      "parent": null,
      "comment": "My dog loves stinky fee too",
      "id": 2048,
      "timestamp": 4214.521
    }
  ]  
}
```
Return a specific entry based on entryId value. A single entry is returned.

### HTTP Request

`GET http://api.parade.pet/entry/<id>`

### Header Parameters

None. This endpoint is open to the outside world.

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  entryId value, passed in the url path


<aside class="success">
Return a single entry based on entryId
</aside>

## Delete Entry

```shell
curl -X "DELETE" "http://api.parade.pet/entry/<id>"
```

> The above command returns JSON structured like this:

```
	"OK"
```
Return OK if the entry was deleted successfully.  Error otherwise.

### HTTP Request

`DELETE http://api.parade.pet/entry/<entry_id>`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry_id | true |  entryId value, passed in the url path


<aside class="success">
Return OK if the entry was successfully deleted.  
</aside>


## Search Entries

```shell
curl -X "POST" "http://api.parade.pet/entries/search"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'petName=Wilson'
  -d 'petType=1'
  -d 'state=NY'
```

> The above command returns JSON structured like this:

```json
{
    "entries": [
        {
            "id": 719153,
            "image": 968895,
            "owner": {
                "id": 109063,
                "name": "Vickie Kolody",
                "location": "Pataskala, NY",
                "lastGamePlayed": "2018-01-10T11:30:53.000Z"
            },
            "pet": {
                "id": 144396,
                "name": "Wilson ",
                "petType": 1,
                "breed": 4688
            }
        },
        {
            "id": 719154,
            "image": 968896,
            "owner": {
                "id": 109063,
                "name": "Vickie Kolody",
                "location": "Pataskala, NY",
                "lastGamePlayed": "2018-01-10T11:30:53.000Z"
            },
            "pet": {
                "id": 144396,
                "name": "Wilson ",
                "petType": 1,
                "breed": 4688
            }
        }]
}
```

Search all entries by pet name, owner name, pet type, breed, city, and state. Returns list of entries matching ALL parameters with values.  At least one parameter is required.  

### HTTP Request

`POST http://api.parade.pet/entries/search`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
petName | false | The pet's name
ownerName | false | The first, last or full name of the pet owner
type | false | A single pet type.  This is the numeric id of the pet type object as returned from /pettype, i.e. 1 = Dogs, 2 = Cats, 8 = Rabbit
breed | false | The name of the pet breed, i.e. Pitbull, Terrier, Mix  
city | false | The city in which the owner lives, i.e. Oakland
state | false | The 2 letter abbreviation in which the owner lives, i.e. CA = California.


<aside class="success">
Return sorted list of entries matching search query by points or by created date descending.
</aside>

## My Entries

```shell
curl "http://api.parade.pet/entries/me"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "entries": [
    {
      "id": 4469,
      "caption": "Love my dog Cheyanne",
      "location": "Toronto, Ontario",
      "image": 25459,
      "points": 950,
      "numFaceOffs": 0,
      "numTreats": 0,
      "numFaceoffs": 36,
      "winPercent": 42,
      "cuteness": 16,
      "timestamp": 6948791.919,
      "activeBoost": {
        "numBoosted": 50,
        "price": 100,
        "numFaceOffs": 0,
        "numWins": 0,
        "numPoints": 0,
        "completed": null,
        "id": 3
      },
      "pet": {
        "id": 11259,
        "name": "Cheyanne",
        "image": 25458,
        "type": "Dog"
      }
    },
    {
      "id": 4468,
      "caption": "That lil guy",
      "location": "Toronto, Ontario",
      "image": 25458,
      "points": 660,
      "numFaceOffs": 0,
      "numTreats": 0,
      "numFaceoffs": 36,
      "winPercent": 42,
      "cuteness": 16,
      "timestamp": 8210362.925,
	  "activeBoost": null,
      "pet": {
        "id": 11259,
        "name": "Cheyanne",
        "image": 25458,
        "type": "Dog"
      }
    }
	],
  "coins": {
    "silver": 1000,
    "gold": 640
  },
  "canPost": true,
  "pricing": {
    "entryFee": {
      "type": "silver",
      "fee": 100
    },
    "boost": [
      {
        "num": 10,
        "type": "gold",
        "fee": 20
      },
      {
        "num": 25,
        "type": "gold",
        "fee": 50
      },
      {
        "num": 50,
        "type": "silver",
        "fee": 1000
      },
      {
        "num": 100,
        "type": "silver",
        "fee": 2000
      }
    ],
    "shareReward": {
    	"type": "gold",
    	"reward": 5
    }    
  },
	"referralBonus": {
		"amount": 25,
		"type": "goldTickets"
	},
	"showTutorial": 4,
	"showAds": true  
}
```

Return sorted list of authenticated user's entries ordered by created date descending.

### HTTP Request

`GET http://api.parade.pet/entries/me`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


<aside class="success">
Return sorted list of entries owned by user ordered by created date descending.
</aside>

## Boost Entry

```shell
curl "http://api.parade.pet/entry/boost"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=1223'
  -d 'numBoosted=100'
  -d 'price=200'
  -d 'priceType=gold'
```

> The above command returns JSON structured like this:

```json
{
  "boost": {
    "numBoosted": 25,
    "price": 50,
    "isPriceGold": true,
    "numFaceOffs": 0,
    "numWins": 0,
    "numPoints": 0,
    "id": 12
  },
  "silverBalance": 1010,
  "goldBalance": 640
}
```

This endpoint creates a boost for the entry and deducts the price from the user's gold balance.  

### HTTP Request

`POST http://api.parade.pet/entry/boost`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry being boosted.   
numBoosted | true | The number of Face Offs purchased.    
price | true | The purchase price in coins;  by default the value is in gold; pass in the priceType to set to silver.
priceType | false | Either gold or silver.

<aside class="success">
Returns the newly created boost object and the user's silver and gold balance after purchasing the boost.
</aside>

## Get Boost

```shell
curl "http://api.parade.pet/boost/<id>"
```

> The above command returns JSON structured like this:

```json
{
  "boost": {
    "entry": {
      "id": 292,
      "image": 755
    },
    "numBoosted": 10,
    "price": 20,
    "numFaceOffs": 10,
    "numWins": 5,
    "numPoints": 0,
    "completed": "2016-10-24T21:10:28.000Z",
    "id": 1
  },
  "goldBalance": 80,
  "boostRemaining": 9,
  "showAds": true
}
```
Return a specific boost based on boost id value. A single boost is returned.

### HTTP Request

`GET http://api.parade.pet/boost/<id>`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  boostId value, passed in the url path


<aside class="success">
Return a single boost based on boostId
</aside>


## Create Entry

```shell
curl "http://api.parade.pet/entry/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'image=129827'
  -d 'pet=29722'
  -d 'contest=1'
  -d 'entryFee=123'
  -d 'caption=My good boy playing'
  -d 'locationName=Old Greenwich'
  -d 'locationPlaceId=ChIJ40eAhsuYwokRQRwdUvcEqH4'
  -d 'city=Old Greenwich'
  -d 'state=CT'
  -d 'country=United States'
  -d 'locationAddress=Old Greenwich, CT 06870'
  -d 'locationLocale=US'
  -d 'shareOnFacebook=true'
  -d 'shareOnTwitter=true'
  -d 'effect=2'
  -d 'sound=3'
```

> The above command returns JSON structured like this:

```json
{
  "entry": {
    "image": 39976,
    "pet": 11259,
    "contest": 1,
    "caption": "My dog is da bomb",
    "entryFee": 10,
    "location": 35,
    "owner": 11422,
    "numFaceOffs": 0,
    "numWins": 0,
    "numTreats": 0,
    "numPoints": 0,
    "id": 8731
  }
}
```

This endpoint creates the entry for the specified pet and user and shares the post to the specified social networks.  The endpoint returns the ID of the newly created entry.  

### HTTP Request

`POST http://api.parade.pet/entry/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
image | true | The ID of the image.   
pet | true | The ID of the pet.    
contest | true | The ID of the contest.    
entryFee | false | The entry fee paid   
caption | false | The description of the entry  
locationName | false | The location name (place name or street address) as returned from Bing Places API
locationPlaceId | false | The location placeId as returned from Google Places API (deprecated)
locationAddress | false | The location full address as returned from Bing Places API
locationLocale | false | The location locale as returned from Google Places API  (deprecated)
city | false | city name
state | false | 2-letter state abbreviation (e.g., NY)
country | false | full country name (e.g., United States)
shareOnFacebook | false | Whether or not to share the entry on Facebook.
shareOnTwitter | false | Whether or not to share the entry on Twitter.
isAnimated | false | Whether or not entry is a video
effect | false | Video effect (integer)
sound | false | Video sound (integer)

<aside class="success">
Returns the newly created entry.
</aside>

## Update Entry

```shell
curl "http://api.parade.pet/entry/update"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=127'
  -d 'pet=29722'
  -d 'caption=My good boy playing'
  -d 'locationName=Old Greenwich'
  -d 'locationPlaceId=ChIJ40eAhsuYwokRQRwdUvcEqH4'
  -d 'shareOnFacebook=true'
  -d 'shareOnTwitter=true'
```

> The above command returns JSON structured like this:

```json
{
  "entry": {
    "image": 39976,
    "pet": 11259,
    "contest": 1,
    "caption": "My dog is da bomb",
    "entryFee": 10,
    "location": 35,
    "owner": 11422,
    "numFaceOffs": 0,
    "numWins": 0,
    "numTreats": 0,
    "numPoints": 0,
    "id": 8731
  }
}
```

This endpoint updates the entry for the specified pet and user and shares the post to the specified social networks.  The endpoint returns the updated entry.  

### HTTP Request

`POST http://api.parade.pet/entry/update`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry being updated.    
pet | true | The ID of the pet.    
caption | false | The description of the entry  
locationName | false | The location name as returned from Google Place API.
locationPlaceId | false | The location placeId as returned from Google Place API.
locationAddress | false | The location address as returned from Google Place API.
locationLocale | false | The location locale as returned from Google Place API.
shareOnFacebook | false | Whether or not to share the entry on Facebook.
shareOnTwitter | false | Whether or not to share the entry on Twitter.

<aside class="success">
Returns the updated entry.
</aside>

## Report Entry

```shell
curl "http://api.parade.pet/entry/report"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=8372'
  -d 'reason=Not pet'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint reports an entry that the user finds questionable.

### HTTP Request

`POST http://api.parade.pet/entry/report`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry being reported.   
reason | true | The reason the user is reporting. Valid reasons:  Not pet, Spam, Objectionable   

<aside class="success">
Returns OK
</aside>

## Comment On Entry

```shell
curl "http://api.parade.pet/entry/comment"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=8372'
  -d 'comment=She is sooo cute'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint creates a comment on entry.

### HTTP Request

`POST http://api.parade.pet/entry/comment`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry being commented on.   
comment | true | The comment
parent | false | The id of the parent comment if replying to a comment

<aside class="success">
Returns OK
</aside>

## Smart Comments

```shell
curl "http://api.parade.pet/entry/smartComments/2012"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```
[
    "❤️❤️❤️",
    "Soo cute 😍",
    "Gizmo 💜💜💜",
    "Great photo!",
    "Awww... so adorable"
]
```

This endpoint gets the smart comments for an entry.

### HTTP Request

`GET http://api.parade.pet/entry/smartComment:entryId`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entryId | true | The ID of the entry being commented on.   

<aside class="success">
Returns an array of comment suggestions for the user on the entry.
</aside>


## Delete Comment

```shell
curl -X "DELETE" "http://api.parade.pet/entry/comment/<commentId>"
```

> The above command returns JSON structured like this:

```
	"OK"
```
Return OK if the comment was deleted successfully.  Error otherwise.

### HTTP Request

`DELETE http://api.parade.pet/entry/comment/<commentId>`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
commentId | true |  commentId value, passed in the url path


<aside class="success">
Return OK if the comment was successfully deleted.  Note all child replies to the comment will also be deleted.
</aside>

## Report Comment

```shell
curl "http://api.parade.pet/entry/comment/report"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'comment=8372'
  -d 'reason=Not pet'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint reports a comment that the user finds questionable.

### HTTP Request

`POST http://api.parade.pet/entry/comment/report`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
comment | true | The ID of the comment being reported.   
reason | true | The reason the user is reporting. Valid reasons:  Not pet, Spam, Objectionable   

<aside class="success">
Returns OK
</aside>

## Read Comment

```shell
curl "http://api.parade.pet/entry/comment/read"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'comment=8372'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint marks a comment as read

### HTTP Request

`POST http://api.parade.pet/entry/comment/read`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
comment | true | The ID of the comment being read.   

<aside class="success">
Returns OK
</aside>

## Log Shared Entry

```shell
curl "http://api.parade.pet/entry/shared"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=8372'
  -d 'reward=5'
  -d 'rewardType=gold'
```

> The above command returns JSON structured like this:

```
"OK"
```

This records the entry as being shared and optionally gives the user a share reward.

### HTTP Request

`POST http://api.parade.pet/entry/shared`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry that was shared
reward | false | Optional reward value in coins
rewardType | false | Either gold or silver

<aside class="success">
Returns OK
</aside>

## Log Ad Watched from Entry

```shell
curl "http://api.parade.pet/entry/adWatched"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entry=8372'
  -d 'reward=5'
  -d 'rewardType=gold'
```

> The above command returns JSON structured like this:

```
"OK"
```

This records an ad being watched tied to the entry and gives the user a reward.

### HTTP Request

`POST http://api.parade.pet/entry/adWatched`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entry | true | The ID of the entry that was shared
reward | false | Optional reward value in coins
rewardType | false | Either gold or silver

<aside class="success">
Returns OK
</aside>

## Top 10 Featured Entries

```shell
curl "http://api.parade.pet/entries/topTenFeatured"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 49489,
    "image": 64599,
    "imageUrl": "http://stage-assets.parade.pet/images/64599/medium.jpg",
    "link": "https://pets.test-app.link/?channel=Email&campaign=top-10-daily&source=mailchimp&$desktop_url=http://share-stage.parade.pet/vote/49489&link=http://parade.pet/entry/49489",
    "petName": "Bear",
    "petType": "Dog",
    "breed": "Bernese Mountain Dog",
    "numFaceOffs": 247,
    "numWins": 180,
    "winRate": 0.7287,
    "cuteness": 68
  },
  {
    "id": 49225,
    "image": 64245,
    "imageUrl": "http://stage-assets.parade.pet/images/64245/medium.jpg",
    "link": "https://pets.test-app.link/?channel=Email&campaign=top-10-daily&source=mailchimp&$desktop_url=http://share-stage.parade.pet/vote/49225&link=http://parade.pet/entry/49225",
    "petName": "Bennie",
    "petType": "Cat",
    "breed": "Tabby",
    "numFaceOffs": 149,
    "numWins": 108,
    "winRate": 0.7248,
    "cuteness": 83
  },
  {
    "id": 48252,
    "image": 62939,
    "imageUrl": "http://stage-assets.parade.pet/images/62939/medium.jpg",
    "link": "https://pets.test-app.link/?channel=Email&campaign=top-10-daily&source=mailchimp&$desktop_url=http://share-stage.parade.pet/vote/48252&link=http://parade.pet/entry/48252",
    "petName": "Lexie",
    "petType": "Cat",
    "breed": "Persian",
    "numFaceOffs": 278,
    "numWins": 147,
    "winRate": 0.5288,
    "cuteness": 37
  },
  {
    "id": 49205,
    "image": 64213,
    "imageUrl": "http://stage-assets.parade.pet/images/64213/medium.jpg",
    "link": "https://pets.test-app.link/?channel=Email&campaign=top-10-daily&source=mailchimp&$desktop_url=http://share-stage.parade.pet/vote/49205&link=http://parade.pet/entry/49205",
    "petName": "Lyra",
    "petType": "Dog",
    "breed": "Black Labrador Retriever4",
    "numFaceOffs": 438,
    "numWins": 255,
    "winRate": 0.5822,
    "cuteness": 23
  },
  {
    "id": 49016,
    "image": 63972,
    "imageUrl": "http://stage-assets.parade.pet/images/63972/medium.jpg",
    "link": "https://pets.test-app.link/?channel=Email&campaign=top-10-daily&source=mailchimp&$desktop_url=http://share-stage.parade.pet/vote/49016&link=http://parade.pet/entry/49016",
    "petName": "Squeak ",
    "petType": "Hamster",
    "breed": "Dwarf Chinese ",
    "numFaceOffs": 477,
    "numWins": 249,
    "winRate": 0.522,
    "cuteness": 17
  },
]
```

Returns the top ten featured entries for the day.

### HTTP Request

`GET http://api.parade.pet/entries/topTenFeatured`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | false | The number of days since today to grab the entries
end | false | The ending day expressed as the number of days since today to count backwards.  This should be more than the start day.
limit | false | The number of entries to return

<aside class="success">
Return list of top ten featured entries.
</aside>

## Recent Entries

```shell
curl "http://api.parade.pet/entries/recent"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 49489,
    "image": 64599,
    "numFaceoffs": 36,
    "winPercent": 42,
    "cuteness": 16,
  },
  {
    "id": 49225,
    "image": 64245,
    "numFaceoffs": 36,
    "winPercent": 42,
    "cuteness": 33,
  },
  {
    "id": 48252,
    "image": 62939,
    "numFaceoffs": 36,
    "winPercent": 42,
    "cuteness": 98,
  }
]
```

Returns a randomized list of entries created within the last 2 days.

### HTTP Request

`GET http://api.parade.pet/entries/recent`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | false | Filter by pettype, i.e. 1=Dog, 2=Cat.
limit | false | Number of entries to return.

<aside class="success">
Return list of entries that were created within the last 2 days.
</aside>

## Friends Entries

```shell
curl "http://api.parade.pet/entries/friends"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 49489,
    "image": 64599
  },
  {
    "id": 49225,
    "image": 64245
  },
  {
    "id": 48252,
    "image": 62939
  }
]
```

Returns the most recent entries of your friends sorted by entry.createdAt date.

### HTTP Request

`GET http://api.parade.pet/entries/friends`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------

<aside class="success">
Returns the 200 most recent entries of your friends sorted by entry.createdAt date.
</aside>
