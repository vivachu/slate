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
curl "http://api.parade.pet/entries"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'search=Black Lab named Waggie'
  -d 'type=Dog'
  -d 'sort=created'
```

> The above command returns JSON structured like this:

```json 
{
	"entries": [
	{ 
	  "id": 129,
	  "caption": "Glad to be home",
	  "location": "Greenwich Point",
	  "image": 234,
	  "points": 10,
	  "numFaceOffs": 2,
	  "numTreats": 0,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": {
          "id": 11720,
          "name": "Chris Anderson",
          "image": 26649
        },	  
	  	"type": "Dog"
	  }
	},
	{ 
	  "id": 130,
	  "caption": "Having fun",
	  "location": "Miami Beach, FL",
	  "image": 235,
	  "points": 90,
	  "numFaceOffs": 291,
	  "numTreats": 12,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": {
          "id": 11720,
          "name": "Chris Anderson",
          "image": 26649
        },
	  	"type": "Dog"
	  }
	},
	{ 
	  "id": 131,
	  "caption": "Woof woof",
	  "location": "San Mateo, CA",
	  "image": 236,
	  "points": 100,
	  "numFaceOffs": 198,
	  "numTreats": 19,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": {
          "id": 11720,
          "name": "Chris Anderson",
          "image": 26649
        },
	  	"type": "Dog"
	  }
	}
	]
}
```

Search all entries by name, pet type, and breed. Return sorted list of entries by points or by created date descending.  If no query parameters are passed, then the top 300 entries across all pets types are returned sorted by points descending.  

### HTTP Request

`GET http://api.parade.pet/entries`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
search | false | Search by name, pet type or breed.  If no search query is passed then return the top 300 listings by points descending.  
type | false | Comma separated list of pet types:  "Dog,Cat,Horse,Bird"
sort | false | Sort by either "created" or "points" descending.  Default value is "points."  

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
  "canPost": true
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
```

> The above command returns JSON structured like this:

```json 
{
  "boost": {
    "numBoosted": 25,
    "price": 50,
    "numFaceOffs": 0,
    "numWins": 0,
    "numPoints": 0,
    "id": 12
  },
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
price | false | The purchase price in gold.

<aside class="success">
Returns the newly created boost object and the user's gold balance after purchasing the boost.
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
  "goldBalance": 80
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
  -d 'locationAddress=Old Greenwich, CT 06870'
  -d 'locationLocale=US'
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
locationName | false | The location name as returned from Google Place API.
locationPlaceId | false | The location placeId as returned from Google Place API.
locationAddress | false | The location address as returned from Google Place API.
locationLocale | false | The location locale as returned from Google Place API.
shareOnFacebook | false | Whether or not to share the entry on Facebook.
shareOnTwitter | false | Whether or not to share the entry on Twitter.

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
