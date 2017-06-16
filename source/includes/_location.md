# Location

## Find Online Stores

```shell
curl "http://api.parade.pet/location/onlinePetStores"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'startsWith="
```

> The above command returns JSON structured like this:

```json 
[
  "BarkBox",
  "Chewy",
  "Petco",
  "PetSmart",
  "Amazon",
  "Walmart",
  "Target",
  "Doctor Foster and Smith",
  "PetFlow",
  "Only Natural Pet",
  "PetEdge",
  "1-800-PetMeds",
  "Pet Valu",
  "1-800 Pet Supplies",
  "NuVet",
  "Chow Hound",
  "PupLife"
]
```
Returns a list of online pet stores.  The optional parameter "startsWith" returns a subset of this list if there are matches.

### HTTP Request

`GET http://api.parade.pet/location/onlinePetStores`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
startsWith | false | Text string used to narrow down the list of online pet stores


<aside class="success">
This endpoint returns a list of online pet stores.
</aside>

## Find Top Location Leaderboards

```shell
curl "http://api.parade.pet/location/top
  -H "Authorization:  Bearer meowmeowmeow"
  -d "limit=50"
```

> The above command returns JSON structured like this:

```json 
[
    {
      "name": "Texas",
      "placeId": "ChIJGWX8w2t_b4YRLFJWSGka37E",
      "count": 312
    },
    {
      "name": "California",
      "placeId": "ChIJvWVL3UDMkIARvE9eGaSLWEg",
      "count": 146
    },
    {
      "name": "New York",
      "placeId": "ChIJgc1ChHnb3IkRYg4uANW_g6w",
      "count": 142
    },
    {
      "name": "Missouri",
      "placeId": "ChIJ1cOynQSaeIgRgxmUgdI3T-g",
      "count": 139
    },
    {
      "name": "Little River, MO",
      "placeId": "ChIJ1cOynQSaeIgRgxmUgdI3T-g",
      "count": 139
    },
    {
      "name": "Celeste, TX",
      "placeId": "ChIJ6akkvNiSS4YRErv6N_ZS8Xo",
      "count": 129
    },
    {
      "name": "Brownsville, TX",
      "placeId": "ChIJGWX8w2t_b4YRLFJWSGka37E",
      "count": 115
    },
    {
      "name": "Arkansas",
      "placeId": "ChIJ5UTQkHCu1YcRxtzZD8B4qso",
      "count": 99
    },
    {
      "name": "Yarbo Place, AR",
      "placeId": "ChIJ5UTQkHCu1YcRxtzZD8B4qso",
      "count": 96
    },
    {
      "name": "Camp Earnest, CA",
      "placeId": "ChIJvWVL3UDMkIARvE9eGaSLWEg",
      "count": 93
    }
]
```
Returns a list of locations ordered by number of pets in that location.

### HTTP Request

`GET http://api.parade.pet/location/top`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
type | false |  if used, either "city" or "state"; if not used, location list a mix of city and state
limit | false | maximum number of locations to list


<aside class="success">
This endpoint returns a list of locations ordered by number of pets in that location.
</aside>