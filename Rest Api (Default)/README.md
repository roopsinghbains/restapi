## Rest API using Flask 

# Overview

This solution demonstrates the process of creating a basic implementation of REST API. 

# Actions Summary

STORE Resource


| HTTP METHOD |                        |                                                                      |
|-------------|------------------------|----------------------------------------------------------------------|
|             | URL                    | Description                                                          |
| POST        | /store data:{name}     | Create new store with given name                                     |
| GET         | /store/<string:name>   | Get store with given name and associated info                        |
| GET         | /store                 | Returns a list of stores                                             |
| POST        | /store/<string:name>/item data:{} | create an item inside a specific store with the given name|
| GET         | /store/<string:name>/item | Get all items in a specific store                                 |

ITEM Resource

| HTTP METHOD |                                      |                                                       |
|-------------|--------------------------------------|-------------------------------------------------------|
|             | URL                                  |                                                       |
|  GET        | /item/<string:name>                  | Get Item with given name and associated info          |
|  POST       | /item/<string:item name>    data:{}  | Create an Item                                        |
|  PUT        | /item/<string:item name>    data:{}  | Create or Update an Item                              |
| DELETE      | /item/<string:item name>             | Delete  item                                          |

ITEMS Resource

| HTTP METHOD |                                      |                                                       |
|-------------|--------------------------------------|-------------------------------------------------------|
| GET         | /items                               | Gets list of all items                                |


# Sample Response 

Get /store

```
{ 
  "stores" : [
  {   
     "items" : [
        { 
            "name":"My Item"
            "price":15.99
        }
       ],
   "name": "My Wonderful Store"
   }
  ]
}
```
# Example (Invocation / Consuming REST API)

Using Javascript

```
<script type="text/javascript">
    function httpGetAsync(theUrl, callback) {
        var xmlHttp = new XMLHttpRequest();
        xmlHttp.onreadystatechange = function() {
            if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
                callback(xmlHttp.responseText);
        }
        xmlHttp.open("GET", theUrl, true); // true for asynchronous
        xmlHttp.send(null);
    }

    httpGetAsync('http://127.0.0.1:5000/store', function(response) {
        alert(response);
    } )

</script>
```



