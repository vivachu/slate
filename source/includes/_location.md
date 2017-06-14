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
  -d "type=state"
  -d "limit=50"
```

> The above command returns JSON structured like this:

```json 
[
  {
    "state": "GA",
    "count": 118,
    "type": "state"
  },
  {
    "state": "AR",
    "count": 94,
    "type": "state"
  },
  {
    "state": "NY",
    "count": 87,
    "type": "state"
  },
  {
    "state": "AK",
    "count": 79,
    "type": "state"
  },
  {
    "state": "VA",
    "count": 75,
    "type": "state"
  },
  {
    "state": "OR",
    "count": 73,
    "type": "state"
  },
  {
    "state": "WY",
    "count": 72,
    "type": "state"
  },
  {
    "state": "PR",
    "count": 57,
    "type": "state"
  },
  {
    "state": "AZ",
    "count": 55,
    "type": "state"
  },
  {
    "state": "MA",
    "count": 52,
    "type": "state"
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