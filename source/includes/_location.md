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
      "state": "TX",
      "placeId": "1234",
      "count": 312
    },
    {
      "name": "California",
      "state": "CA",
      "placeId": "2345",
      "count": 146
    },
    {
      "name": "New York",
      "state": "NY",
      "placeId": "4567",
      "count": 142
    },
    {
      "name": "Missouri",
      "state": "MO",
      "placeId": "5678",
      "count": 139
    },
    {
      "name": "Little River, MO",
      "state": "MO",
      "placeId": "6789",
      "count": 139
    },
    {
      "name": "Celeste, TX",
      "state": "TX",
      "placeId": "7890",
      "count": 129
    },
    {
      "name": "Brownsville, TX",
      "state": "TX",
      "placeId": "8901",
      "count": 115
    },
    {
      "name": "Arkansas",
      "state": "AR",
      "placeId": "9012",
      "count": 99
    },
    {
      "name": "Yarbo Place, AR",
      "state": "AR",
      "placeId": "123",
      "count": 96
    },
    {
      "name": "Camp Earnest, CA",
      "state": "CA",
      "placeId": "234",
      "count": 93
    }
]
```
Returns a list of locations ordered by number of pets in that location.  Note that placeId is now a string with the locationId (id value from Location table)

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
