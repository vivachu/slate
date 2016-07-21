## Exchange Coins

```shell
curl "http://api.parade.pet/coins/exchange"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'silver=1000'
```

> The above command returns JSON structured like this:

```json
{
  "gold:": 100
}
```

Call this endpoint to exchange silver coins to gold or gold to silver.  Pass in silver to return gold or pass gold to return silver at the current exchange rate of 1 gold = 10 silver.  The user's coin balance is automatically adjusted based upon the exchange.  

### HTTP Request

`POST http://api.parade.pet/coins/exchange`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
silver | false | Amount of silver to exchange for gold.  This value must be greater than or equal to 10 and in increments of 10.  
gold | false | Amount of gold to exchange for silver.  This value must be a positive integer.

<aside class="success">
Returns gold or silver based upon the input query parameter using the exchange rate of 10 silver per 1 gold. The user's coin balance is automatically adjusted based upon the exchange.  Returns an error message if the user does not have enough of the input coin specified.   
</aside>

