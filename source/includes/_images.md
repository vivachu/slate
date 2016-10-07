# Images

## Create Image

```shell
curl "http://api.parade.pet/image/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'platform=ios'
  -d 'directory=129292323903238'
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

<aside class="success">
Returns the ID of the newly created image along with the pet type of the image.  
</aside>

## Pay Entry Fee

```shell
curl "http://api.parade.pet/image/payEntryFee"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'image=1292'
  -d 'fee=10'
```

> The above command returns JSON structured like this:

```json 
{
  "entryFee": {
    "image": 40128,
    "goldFee": 10,
    "user": 15157,
    "silverFee": 0,
    "id": 2
  },
  "goldBalance": 180
}

{
  "err": "The user does not have enough gold."
}

```

This endpoint creates the EntryFee object and charges the user the fee in goldCoins.  The user's goldBalance is returned after deducting the fee. 

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
fee| true | The fee to pay in gold coins. 

<aside class="success">
Returns the EntryFee object and the user's goldBalance after the fee has been deducted.
</aside>
