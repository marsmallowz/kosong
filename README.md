# API Spec

## Authentication

All API must use this authentication

Request :
- Header :
    - X-Api-Key : "your secret api key"

## Register

Request :
- Method : POST
- Endpoint : `/api/auth/v1`
- Header :
    - Content-Type: application/json
    - Accept: application/json
- Body :

```json 
{
    "nim" : "string",
    "email" : "string",
    "username" : "string",
    "password" : "string"    
}
```

Response :

```json 
{
    "status" : "number"
}
```

## LOGIN

Request :
- Method : POST
- Endpoint : `/api/auth/v2`
- Header :
    - Content-Type: application/json
    - Accept: application/json
- Body :

```json 
{
    "nim" : "string",
    "password" : "string"    
}
```

Response :

```json 
{
    "status" : "number",
    "data" : {
         "token" : "string",
         "user" : {
            "username" : "string",
         }
     }
}
```

## Update Product

Request :
- Method : PUT
- Endpoint : `/api/products/{id_product}`
- Header :
    - Content-Type: application/json
    - Accept: application/json
- Body :

```json 
{
    "name" : "string",
    "price" : "long",
    "quantity" : "integer"
}
```

Response :

```json 
{
    "code" : "number",
    "status" : "string",
    "data" : {
         "id" : "string, unique",
         "name" : "string",
         "price" : "long",
         "quantity" : "integer",
         "createdAt" : "date",
         "updatedAt" : "date"
     }
}
```

## List Product

Request :
- Method : GET
- Endpoint : `/api/products`
- Header :
    - Accept: application/json
- Query Param :
    - size : number,
    - page : number

Response :

```json 
{
    "code" : "number",
    "status" : "string",
    "data" : [
        {
             "id" : "string, unique",
             "name" : "string",
             "price" : "long",
             "quantity" : "integer",
             "createdAt" : "date",
             "updatedAt" : "date"
        },
        {
             "id" : "string, unique",
             "name" : "string",
             "price" : "long",
             "quantity" : "integer",
             "createdAt" : "date",
             "updatedAt" : "date"
         }
    ]
}
```

## Delete Product

Request :
- Method : DELETE
- Endpoint : `/api/products/{id_product}`
- Header :
    - Accept: application/json

Response :

```json 
{
    "code" : "number",
    "status" : "string"
}
```
