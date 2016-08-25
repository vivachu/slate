# Pets

## Leaderboard

```shell
curl "http://api.parade.pet/pet/leaderboard"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'start=2016-06-01'
  -d 'end=2016-06-30'
  -d 'place=200'
  -d 'size=3'  
  -d 'type=dog'
  -d 'contest=1'
```

> The above command returns JSON structured like this:

```json 
{
	"leaderboard": [
	{ 
	  "id": 129,
	  "image": 234,
	  "name": "Fluffy",
	  "place": 200,
	  "points": 10900,
	  "numFaceOffs": 900,
	  "numTreats": 212
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Spanky",
	  "place": 201,
	  "points": 10800,
	  "numFaceOffs": 1029,
	  "numTreats": 29
	},
	{ 
	  "id": 876,
	  "image": 202,
	  "name": "Donald",
	  "place": 202,
	  "points": 10500,
	  "numFaceOffs": 872,
	  "numTreats": 450
	}
	]
}
```

Pets accumulate points for FaceOff wins and Treats received.  The leaderboard endpoint returns an ordered list of pets using the sum total of points across all entries for a specified contest over a set time period.  If no contest is specified, then the leaderboard sums points across all contests (default).

### HTTP Request

`GET http://api.parade.pet/pet/leaderboard`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | false | Start date in yyyy-mm-dd format to limit results. If no start date is defined, the first day of the current month is assumed as the time period.  
end | false | End date in yyyy-mm-dd format to limit results.  The end date is inclusive, meaning if 2016-06-30 is specified then points scored any time on 6/30 are included. If no end date is defined, the last day of the start month is assumed as the time period. 
place | false | The placement position to start the return results.
type | false | The type of pet to filter against: dog, cat, other.  No value indicates all pets.
contest | false | id value of the Contest to filter the results against.  If no contest is specified, then the points are summed across all contests.  

<aside class="success">
This endpoint returns the leaderboard for the specified time period, contest, and pet type.  By default if no parameters are passed, then the top 100 pets for the current month across all contests are returned. 
</aside>


## Get My Pets

```shell
curl "http://api.parade.pet/pets"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'start=2016-06-01'
  -d 'end=2016-06-30'
  -d 'contest=1'
```

> The above command returns JSON structured like this:

```json 
{
	"pets": [
	{ 
	  "id": 129,
	  "image": 234,
	  "name": "Mr Big",
	  "place": 1292,
	  "points": 900,
	  "numFaceOffs": 98,
	  "numTreats": 9	  
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Sparks",
	  "place": 989,
	  "points": 1010,
	  "numFaceOffs": 289,
	  "numTreats": 21
	}
	]
}
```

This endpoint returns the authorized user's pets and their points total and placement over the specified time period and contest.  By default if no parameters are passed, then the pet's points balance and placement are calculated for the current month across all contests. 

### HTTP Request

`GET http://api.parade.pet/pets`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | false | Start date in yyyy-mm-dd format over which to calculate points and placement. If no start date is defined, the first day of the current month is assumed as the time period.  
end | false | End date in yyyy-mm-dd format over which to calculate points and placement. If no end date is defined, the last day of the start month is assumed as the time period. 
contest | false | id value of the Contest to filter the results against.  If no contest is specified, then the points are summed across all contests.  

<aside class="success">
Returns the authorized user's pets and their points total and placement over the specified time period and contest.  By default if no parameters are passed, then the pet's points balance and placement are calculated for the current month across all contests. 
</aside>

## Pet Types

```shell
curl "http://api.parade.pet/pettype"
```

> The above command returns JSON structured like this:

```json 
[
  {
    "name": "Dog",
    "id": 1,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Cat",
    "id": 2,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Bird",
    "id": 3,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Horse",
    "id": 4,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Other",
    "id": 16,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  }
]
```

Return list of pet types.

### HTTP Request

`GET http://api.parade.pet/pettype`


<aside class="success">
Return list of pet types.
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
	  "image": 234,
	  "points": 10,
	  "numFaceOffs": 2,
	  "numTreats": 0,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": "Chris Anderson",
	  	"type": "Dog"
	  }
	},
	{ 
	  "id": 130,
	  "image": 235,
	  "points": 90,
	  "numFaceOffs": 291,
	  "numTreats": 12,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": "Chris Anderson",
	  	"type": "Dog"
	  }
	},
	{ 
	  "id": 131,
	  "image": 236,
	  "points": 100,
	  "numFaceOffs": 198,
	  "numTreats": 19,
	  "pet": {
	  	"id": 298,
	  	"name": "Waggie",
	  	"owner": "Chris Anderson",
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
