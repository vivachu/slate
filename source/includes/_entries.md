# Entries

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
	  	"owner": "Chris Anderson",
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
	  	"owner": "Chris Anderson",
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
	  	"owner": "Chris Anderson",
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
	  	"owner": "Chris Anderson",
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
	  	"owner": "Chris Anderson",
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

