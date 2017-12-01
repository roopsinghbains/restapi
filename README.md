# Rest API for Items in a store

## Prerequisites

```
pip install flask (Python 2.7 version)
pip3.5 install flask(Python 3.5 version)

```

## Config

By default the REST API is listening on port 5000, you can modify it by modifying app.py file as  follows.

```
from flask import Flask

app = Flask(_name_)

app.run(port=5000)
```
## Usage
Python Flask should be running and listening for requests.

Run the app.py file as shown below in the command line interface from the folder where the file 
is present.

```
python3.5 app.py
```

## Repository Overview
| Project | Description |
|--------------------------------------------------------------------|---------------------------------------|
| [REST API using Flask](https://github.com/roopsinghbains/restapi/tree/master/Rest%20Api%20(Default)) | Raw Rest Api implementation using Flask|
| [Flask Restful API](https://github.com/roopsinghbains/restapi/tree/master/Rest%20Api%20using%20Flask%20Restful) | Rest Api utilizing FlaskRestful features|
| [REST API with Sql Storage](https://github.com/roopsinghbains/restapi/tree/master/Rest%20Api%20with%20Sql%20Storage) | REST Api with Sqlite for data persistence| 



