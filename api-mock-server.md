# API and mock server setup

More often than not when developing an application you need some sort of data. This can be achieved in many ways, but a quick simple way to do so is by using the `json-server` library which can be found [here](https://github.com/typicode/json-server). 

Create a `db.json` file and add some data like the example below.

```json
/db.json

{
  "users": [
    {"id": "23", "firstName": "Fred", "age":32},
    {"id": "47", "firstName": "Wilma", "age":31},
    {"id": "66", "firstName": "Dino", "age":56},
    {"id": "98", "firstName": "BamBam", "age":1}
  ]
}

```