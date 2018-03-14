# Images
## Analyze Image

```shell
curl "http://api.parade.pet/image/analyze"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'platform=ios'
  -d 'directory=129292323903238'
```

> The above command returns JSON structured like this:

```json 
{
	"petType": {
		"id": 1, 
		"name": "Dog"
	}
}

{
  "err": "Grrrrrr... That's not a pet."
}

{
  "err": "Grrrrrr... That's inappropriate."
}


```

This endpoint analyzes the image at the specified path and returns whether the image passed.  If the image failed, then the endpoint returns a 401 error code with an error message stating why the image failed.  If the image passes, it returns a 200 code with metadata about the image.  Note that the petType maybe null. 
### HTTP Request

`POST http://api.parade.pet/image/analyze`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
platform | true | Either web, ios, or android
directory| true | The unique directory under the platform containing the orig.jpg and cropped.jpg files

<aside class="success">
Returns the metadata about the image.
</aside>

## Create Image

```shell
curl "http://api.parade.pet/image/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'platform=ios'
  -d 'directory=129292323903238'
  -d 'mode=profile'
```

> The above command returns JSON structured like this:

```json 
{
	"image": 12922,
	"petType": {
		"id": 1, 
		"name": "Dog"
	}
}

{
  "err": "Grrrrrr... That's not a pet."
}

{
  "err": "Grrrrrr... That's inappropriate."
}


```

This endpoint creates the image with the user owner set to the authorized user. The endpoint returns the ID of the newly created image or an error message stating why the image was not created. 

### HTTP Request

`POST http://api.parade.pet/image/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
platform | true | Either web, ios, or android
directory| true | The unique directory under the platform containing the orig.jpg and cropped.jpg files
mode | false | This parameter is set to "profile" when uploading a user profile image
skipAnalyze | false | Set this to true if skipping image verification

<aside class="success">
Returns the ID of the newly created image along with the pet type of the image.  
</aside>

## Pay Entry Fee

```shell
curl "http://api.parade.pet/image/payEntryFee"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'image=1292'
  -d 'fee=10'
  -d 'feeType=silver'
  -d 'stickers=92,928,392,2393'
```

> The above command returns JSON structured like this:

```json 
{
  "entryFee": {
    "image": 40128,
    "goldFee": 110,
    "user": 15157,
    "silverFee": 292,
    "id": 2
  },
  "goldBalance": 180,
  "silverBalance": 90
}

{
  "err": "The user does not have enough gold."
}

```

This endpoint creates the EntryFee object and charges the user the total fee adding up the sum of the entry fee plus the cost of all stickers.  The user's gold and silver balance is returned after deducting the fee. 

### HTTP Request

`POST http://api.parade.pet/image/payEntryFee`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
image | true | The image to pay the fee on.
fee| true | The fee to pay in gold or silver coins. 
feeType| true | Whether to pay in gold or silver coins. 
stickers| false | Comma separated list of sticker IDs to purchase. 

<aside class="success">
Returns the EntryFee object and the user's gold and silver balance after the fee has been deducted.
</aside>

## Get Sticker Collections

```shell
curl "http://api.parade.pet/stickers/collections"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
{
  "coins": {
    "silver": 4135,
    "gold": 1015
  },
  "stickerCollections": [
    {
      "name": "Chinese New Year",
      "path": "cny",
      "id": 1
    },
    {
      "name": "Winter",
      "path": "winter",
      "id": 2
    },
    {
      "name": "Expressions",
      "path": "expressions",
      "id": 3
    }
  ]
}
```

This endpoint returns the user's current silver and gold coin balance along with an array of stickerCollections.

### HTTP Request

`GET http://api.parade.pet/stickers/collections`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------


<aside class="success">
Returns the user's coin balance and stickerCollections available.
</aside>

## Get Stickers

```shell
curl "http://api.parade.pet/stickers/1"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
[
  {
    "collection": 1,
    "name": "Rooster Doll",
    "path": "cny/rooster_doll",
    "price": 100,
    "isPremium": false,
    "isFont": false,
    "isAnimated": true,
    "id": 1
  },
  {
    "collection": 1,
    "name": "Chinese Girl Hari",
    "path": "cny/chinese_girl_hari",
    "price": 100,
    "isPremium": false,
    "isFont": false,
    "isAnimated": false,
    "id": 16
  },
  {
    "collection": 1,
    "name": "Lotus Flower",
    "path": "cny/lotus_flower",
    "price": 100,
    "isPremium": false,
    "isFont": false,
    "isAnimated": false,
    "id": 17
  }
]
```

This endpoint returns the stickers that belong to the specified collection

### HTTP Request

`GET http://api.parade.pet/stickers/:collectionId`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------


<aside class="success">
Returns the stickers belonging to the specified collection.
</aside>
