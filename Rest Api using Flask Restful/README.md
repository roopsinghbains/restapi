## Rest API using Flask 

# Overview

This solution demonstrates the process of creating a REST API for Items resource using flask_restful which abstracts some of the complexity for us.
It also implements authentication using Flask-JWT library (JSON web token) for encrytion of data. 

# Pre-requisites (Installation and Imports)
``` 
pip install Flask-JWT
pip3.5 install Flask-JWT


```
Imports
```
from flask import Flask, request
from flask_restful import Resource, Api
from flask_jwt import JWT, jwt_required
from security import authentication, identity
``` 

#Code Structure

Main Logic - app.py
Authentication - security.py
User Info - user.py

# Actions Summary

ITEM Resource

| HTTP METHOD |                                      |              Description                                                                                                         |
|-------------|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
|             | URL                                  |                                                       																			|
|  GET        | /item/<string:name>                  | Get Item with given name and associated info with HTTP status 200 or returns none with HTTP Status code 404 (Resource Not Found) |      
|  POST       | /item/<string:item name>    data:{}  | Create an Item with HTTP status code 201 or returns error message with HTTPS status code 400 (Bad Request) if data already exists|                                  
|  PUT        | /item/<string:item name>    data:{}  | Create or Update an Item with HTTP status code 200 or 201                                                                        |
| DELETE      | /item/<string:item name>             | Delete item with HTTP status code 200.                                                                                           |

ITEMS Resource

| HTTP METHOD |                                      |                                                       |
|-------------|--------------------------------------|-------------------------------------------------------|
| GET         | /items                               | Gets list of all items                                |


# Sample Request && Response 

CREATE

POST /item/<string:name/> (for example /item/My Item)

Request body/payload
{
	"price":15.99
}
Response 

```
{
	"name":"My Item"
	"price":15.99
}
```

RETRIEVE

Get /item/<string:name/> (for example /item/My Item)

Item exists returns item with status code 200
```
{
  "name": "My Item",
  "price": 15
}
```

Item does not exists returns null with status code 404
```
{
 "item": null
}
```

Get /items

```
{  
 "items" : [
	{ 
		"name":"My Item"
		"price":15.99
	}
   ]
}
```

UPDATE

PUT /item/<string:name/> (for example /item/My Item)

Request body /payload

{
	"price":27.99
}

Response

{
	"name":"My Item"
	"price":27.99
}

DELETE

DELETE /item/<string:name/> (for example /item/My Item)

Response

{
	message: "Item deleted"
}

# Authentication

The code uses JWT authentication with user info (userId, username, userpassword) in security.py file.

-The client will send a username and password
-The REST API will send a response with JWT token containing the unique userId assciated with username and password.
-Finally the client sends the userId in JWT token with any request to REST API.

```
app = Flask(_name_)

# set a secret key
app.secret_key = "" 

jwt = JWT(app,authentication, identity) # creates endpoint /auth

```

# Side Notes

With flask_restful we no longer need to convert the response to JSON format (using Jsonify) but 
is created for us by inheriting from Resource as shown below.

```

class Item(Resource):
	def get(self, name):
		for item in items:
			if item["name"] == name:
				return item
		return {'item':None}, 404
		
```

In case of error, better debugging assistance can be achieved by modifying the existing code as below.

This will render a more descriptive error in HTML.

```
app.run(port=5000,debug=True)
```

The incoming request should also comply with format expected by the REST API.

In Header of Request

Content-Type : application/json 

In Order to not require the incoming request to mandatory Content-Type specified use request object with a default parameter as shown below.

```
Instead of 

data = request.get_json()

Use

data = request.get_json(force=True)
