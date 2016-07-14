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
	  "points": 10900
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Spanky",
	  "place": 201,
	  "points": 10800
	},
	{ 
	  "id": 876,
	  "image": 202,
	  "name": "Donald",
	  "place": 3,
	  "points": 10500
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
size | false | The total number of pets to return.
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
	  "points": 900
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Sparks",
	  "place": 989,
	  "points": 1010
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