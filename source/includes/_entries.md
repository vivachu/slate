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
  "location": "Vancouver, Canada",
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
  }
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
	]
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

## Create Entry

```shell
curl "http://api.parade.pet/entry/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'caption=My good boy playing'
  -d 'image=129827'
  -d 'pet=29722'
  -d 'location=Myrtle Beach, SC'
  -d 'shareOnFacebook=true'
  -d 'shareOnTwitter=true'
  -d 'shareOnGoogle=false'
  -d 'shareOnInstagram=true'
```

> The above command returns JSON structured like this:

```json 
{
	"entry": 12922
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
caption | false | The name of the pet  
image | true | The ID of the image.   
pet | true | The ID of the pet.    
location | false | The location string.
shareOnFacebook | false | Whether or not to share the entry on Facebook.
shareOnTwitter | false | Whether or not to share the entry on Twitter.
shareOnGoogle | false | Whether or not to share the entry on Google.
shareOnInstagram | false | Whether or not to share the entry on Instagram.

<aside class="success">
Returns the ID of the newly created entry.
</aside>
