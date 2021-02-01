---
title: Buclist API 

language_tabs: # must be one of https://git.io/vQNgJ
  - json: json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Buclist is a simple API, that can be used to store your bucket lists or the things you want to do before you die. It allows consumers to perform CRUD operations on bucketlists. You can use the same API to even manage a ToDo application A bucketlist has many items and belongs to a user.

This API documentation page was created with [Slate](https://github.com/slatedocs/slate). 

# User

## CREATE A NEW USER
This endpoint signs up a new user.

### EndPoint

> POST/signup

### HTTP Request

> REQUEST

> <code>Headers</code>

```json
    "Content-Type: application/json"

```

>Body

```json

  {
    "firstname": "kim",
    "lastname": "boy",
    "email": "kemmymsabeni@gmail.com",
    "password": "@Passw0rd"
  },

```

> RESPONSE : <code>201</code>

>Headers


```json
    "Content-Type: application/json"

```

>Body

```json

{
    "message": "Account created successfully",
    "auth_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE2MTIxNTI5OTJ9.EgLL3tdJetZXWCbDrN4_yQfH867p3VYWhzQ2DfrPUWY"
}

```



`POST http://localhost:3000/signup`


### Query Parameters

Parameter | Description
--------- | -----------
firstname | User's firstname.
lastname  | User's lastname.
email     | User's email.
password  | A User password.





## LOGIN AS A USER

This endpoint serves to login existing users. It expects email and password for authentication and returns a token that expires 24 hours from the time it’s created.

### EndPoint

> POST/login

### HTTP Request

> REQUEST

> <code>Headers</code>

```json
    "Content-Type: application/json"

```

>Body

```json

  {
    "email": "kemmymsabeni@gmail.com",
    "password": "@Passw0rd"
  }

```

> RESPONSE : <code>200</code>

>Headers


```json
    "Content-Type: application/json"

```

>Body

```json

{
    "auth_token": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE2MTIxNjA2NTJ9.NqLyzKhbUsTSxtPKH_5tO62uQ2J5Z08SvF81qPA4LlU",
    "message": "Logged in successfully"
}

```



`POST http://localhost:3000/auth/login`


### Query Parameters

Parameter | Description
--------- | -----------
email     | User's email.
password  | A User password.







## USER LOGOUT

This endpoint logs out a user. Once a user is logged out, that token is invalidated.

### EndPoint

> POST/logout

### HTTP Request

> REQUEST

><code>Headers</code>

```json
    "Content-Type: application/json"
```


> RESPONSE : <code>200</code>

>Headers

```json
    "Content-Type: application/json"
```

>Body

```json

 {
  "message": "Logged out successfully"
 }

```


`GET http://localhost:3000/auth/logout`



# Bucketlists

## CREATE A NEW BUCKET LIST
This endpoint creates a new bucket list.

### EndPoint

> POST/bucketlists

### HTTP Request

> REQUEST

><code>Headers</code>

```json
    "Content-Type: application/json"
```
> Body

```json

  {
    "name": "Empire’s eradication"
  }

```

>RESPONSE : <code>201</code>

> Headers

```json
    "Content-Type: application/json"
```

>Body

```json
  {
     "name": "Empire’s eradication"
     "id": 15,
     "items": [],
     "date_created": "2016-11-04  8:12:05",
     "date_modified": "2016-11-04  8:12:05",
     "created_by": "Darth Vader"
  }
```

`POST http://localhost:3000/bucketlists`

## LIST ALL BCKET LISTS
This end point lists all the created bucke
t lists
### EndPoint

> GET/bucketlists

### HTTP Request

>RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```

>Body

```json
  [
  {
    "id": 1,
    "name": "Resurrect from The Empire Strikes",
    "items": [
      {
        "id": 9,
        "name": "shoot Greedo",
        "date_created": "2016-11-13  3:15:16",
        "date_modified": "2016-11-13  3:15:16",
        "done": false
      }
    ],
    "date_created": "2016-11-13  3:13:50",
    "date_modified": "2016-11-13  3:13:50",
    "created_by": "Han Solo"
  },
  {
    "id": 2,
    "name": "Find R2-D2",
    "items": [
      {
        "id": 9,
        "name": "Talk to C3PO",
        "date_created": "2016-11-13  3:15:16",
        "date_modified": "2016-11-13  3:15:16",
        "done": false
      }
    ],
    "date_created": "2016-11-13  3:13:50",
    "date_modified": "2016-11-13  3:13:50",
    "created_by": "Luke Skywalker"
   }
  ]
```

`GET http://localhost:3000/bucketlists`

## GET A SINGLE BUCKET LIST
This endpoint shows a single bucket list

### EndPoint
> GET/bucketlists/< id>

### HTTP Request

> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```

> Body

```json
  {
  "id": 15,
  "name": "Empire’s eradication",
  "items": [
    {
      "id": 4,
      "name": " become a Sith Lord",
      "date_created": "2016-11-04  8:12:05",
      "date_modified": "2016-11-04  8:12:05",
      "done": false
    }
  ],
  "created_by": "Darth Vader"
}
```
`GET http://localhost:3000/bucketlists/15`

## UPDATE A BUCKET LIST
This endpoint updates an existing specified bucket list.

### EndPoint
> PUT/bucketlists/< id>

### HTTP Request

>REQUEST

><code>Headers</code>

```json
    "Content-Type: application/json"
```
> Body

```json

  {
    "name": "Jabba the hut"
  }

```

> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
  {
  "id": 15,
  "name": "Jabba the hut",
  "items": [
    {
      "id": 4,
      "name": " become a Sith Lord",
      "date_created": "2016-11-04  8:12:05",
      "date_modified": "2016-11-04  8:22:05",
      "done": false
    }
   ],
   "created_by": "Darth Vader"
  }
```
`PUT http://localhost:3000/bucketlists/15`


## DELETE A BUCKET LIST
This endpoint deletes an existing specified bucket list.

### EndPoint
> DELETE/bucketlists/< id>

### HTTP Request

> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
{
  "message": "Bucketlist deleted successfully"
}

```

`DELETE http://localhost:3000/bucketlists/15`

# Item
This end point serves all bucket list items belonging to a particular bucket list.

## CREATE A NEW ITEM
creates a new item in the bucket list.

### EndPoint
> POST/bucketlists/< id>/items

### HTTP REQUEST
>REQUESTS

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
  {
  "name": "plan to bring my father back"
  }
```
> RESPONSE : <code>201</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
[
  {
    "id": 4,
    "name": "plan to bring my father back",
    "date_created": "2016-11-04  8:12:05",
    "date_modified": "2016-11-04  8:12:05",
    "done": false
  }
]
```

`POST http://localhost:3000/bucketlists/15/items`

## GET ALL BUCKET LIST ITEMS
Lists all the created items in a bucket list

### EndPoint
> GET/bucketlists/< id>/items

### HTTP REQUEST

>RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
[
  {
    "id": 4,
    "name": "become a Sith Lord",
    "date_created": "2016-11-04  8:12:05",
    "date_modified": "2016-11-04  8:12:05",
    "done": false
  },
  {
    "id": 5,
    "name": "serve Sidious",
    "date_created": "2016-11-14  8:12:05",
    "date_modified": "2016-11-14  8:12:05",
    "done": false
  }
]
```
`GET http://localhost:3000/bucketlists/3/items`


## GET A SINGLE ITEM IN THE BUCKET LIST
Gives you a single item you have specified in a bucket list

### EndPoint
> GET/bucketlists/< id>/items/< id>

### HTTP REQUEST
> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
{
  "id": 4,
  "name": "plan to bring my father back",
  "date_created": "2016-11-04  8:12:05",
  "date_modified": "2016-11-04  8:12:05",
  "done": false
}
```
`GET http://localhost:3000/bucketlists/15/items/4`

## UPDATE AN ITEM
Updates a bucket list item

### EndPoint
> PUT/bucketlists/< id>/items/< item_id>

### HTTP REQUEST
>REQUESTS

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
{
  "done": true
}
```
> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
> Body

```json
{
  "id": 4,
  "name": "plan to bring my father back",
  "date_created": "2016-11-04  8:12:05",
  "date_modified": "2016-11-04  8:12:05",
  "done": true
}
```
`PUT http://localhost:3000/bucketlists/15/items/4`

## DELETE AN ITEM
Deletes an item in a bucket list

### EndPoint
> DELETE/bucketlists/< id>/items/< item_id>

### HTTP REQUEST
> RESPONSE : <code>200</code>

> Headers

```json
    "Content-Type: application/json"
```
>Body

```json
{
  "message": "Item deleted successfully"
}
```
`DELETE http://localhost:3000/bucketlists/15/items/4`


