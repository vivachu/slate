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
	"petType": {id: 1, name: 'Dog'}
}

{
  "err": "Grrrrrr... That's not a pet."
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
