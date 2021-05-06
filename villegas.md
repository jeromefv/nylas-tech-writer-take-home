# Create a new `Pet`

Learn how to create a new Pet in your application with JSON.

To create a Pet, send a POST request to `/pet`.

```shell
curl --location --request POST `http://api.nylas.com/pet` \
--header 'Authorization: Bearer <access_token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "category": {
    "name": "Rescue",
    "sub": {
      "prop1": "local"
    }
  },
  "name": "Guru",
  "photoUrls": [
    "https://raw.githubusercontent.com/jigsawpieces/dog-api-images/7f8ca46438aacf6aa6ed23a8c421368180370da1/husky/n02110185_9712.jpg"
  ],
  "tags": [
    {
      "name": "husky"
    }
  ],
  "status": "pending_adoption",
  "petType": "dog",
  "scopes": {
    "write:pets": "modify pets in your account",
    "read:pets": "read your pets"
  }
}'
```

## `Pet` Object

| Attribute | Type | Description |
| --- | --- | --- |
| `"name"` | `string` | **REQUIRED.** The name of the parameter. Parameter names are *case sensitive*. |
| `"prop1"` | `string` | The identifying subcategory for `Pet` category. |
| `"photoUrls"` | `string` | The URL of an online photo. |
| `"status"` | `string` | The status of the pet's adoption and MUST be exactly one of the following: `available`, `pending_adoption`, or `adopted`. |
| `"petType"` | `string` | The type of pet with `cat`, `dog`, `rabbit`, and `fish` currently available. |
| `"scopes"` | Map[`string`, `string`] | REQUIRED. The available scopes for `Pet`. A map between the scope name and a short description for it. |

## Server Response

| Status Code | Description | Reason |
| --- | --- | --- |
| `200` | Created | Your `Pet` was created successfully. |
| `405` | Invalid Input | Your request was malformed or contained an invalid parameter. The most common issue is invalid JSON. |