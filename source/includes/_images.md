# Images

## Create Image

```shell
curl "http://api.parade.pet/image/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'image=s3://assets.parade.pet/ios/289182882.jpg'
```

> The above command returns JSON structured like this:

```json 
{
	"image": 12922
}
```

This endpoint creates the image with the user owner set to the authorized user. The endpoint returns the ID of the newly created image.  The endpoint kicks off the process of creating all approvals and thumbnails based off the original image uploaded to S3.    

### HTTP Request

`POST http://api.parade.pet/image/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
s3Path | true | The S3 URL to the directory in which to find orig.jpg and edited.jpg image files.  The client is responsible for uploading the image to S3.   

<aside class="success">
Returns the ID of the newly created image.
</aside>
