# API Spec


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

## List Book

Request :
- Method : GET
- Endpoint : `/api/books`
- Header :
    - Accept: application/json
- Query Param :
    - size : number,
    - page : number

Response :

```json 
{
    "status" : "number",
    "data" : [
        {
             "id" : "string, unique",
             "title" : "string",
             "synopsis" : "string",
             "stock" : "number",
             "author" : "string",
             "image_url" : "string",
             "createdAt" : "datetime",
             "updatedAt" : "datetime",
             "categories" : [
                {
                    "id" : "string, unique",
                    "category" : "string"
                },
                {
                    "id" : "string, unique",
                    "category" : "string"
                }
             ]
        },
         {
             "id" : "string, unique",
             "title" : "string",
             "synopsis" : "string",
             "stock" : "number",
             "author" : "string",
             "image_url" : "string",
             "createdAt" : "datetime",
             "updatedAt" : "datetime",
               "categories" : [
                {
                    "id" : "string, unique",
                    "category" : "string"
                }
             ]
        }
    ]
}
```

## Book Details

Request :
- Method : GET
- Endpoint : `/api/books/:id`
- Header :
    - Accept: application/json

Response :

```json 
{
    "status" : "number",
    "data" : {
         "id" : "string, unique",
         "title" : "string",
         "synopsis" : "string",
         "stock" : "number",
         "author" : "string",
         "image_url" : "string",
         "createdAt" : "datetime",
         "updatedAt" : "datetime",
         "categories" : [
            {
                "id" : "string, unique",
                "category" : "string"
            },
            {
                "id" : "string, unique",
                "category" : "string"
            }
         ]    
    }
    
}
```

## Add Book to Cart

Request :
- Method : POST
- Endpoint : `/api/carts/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## Delete Book at Cart

Request :
- Method : DELETE
- Endpoint : `/api/carts/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## Add Book to Loan

Request :
- Method : POST
- Endpoint : `/api/loans/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## Returning loan books

Request :
- Method : PATCH
- Endpoint : `/api/loans/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## List Loan

Request :
- Method : GET
- Endpoint : `/api/loans/:user_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number",
    "data" : [
        {
             "id" : "string, unique",
             "loan_time" : "datetime",
             "book" : {
                "id" : "string, unique",
                "title" : "string",
                "synopsis" : "string",
                "stock" : "number",
                "author" : "string",
                "image_url" : "string",
                "createdAt" : "datetime",
                "updatedAt" : "datetime",
                "categories" : [
                    {
                        "id" : "string, unique",
                        "category" : "string"
                    },
                    {
                        "id" : "string, unique",
                        "category" : "string"
                    }
                ]    
             }
        },
        {
             "id" : "string, unique",
             "loan_time" : "datetime",
             "book" : {
                "id" : "string, unique",
                "title" : "string",
                "synopsis" : "string",
                "stock" : "number",
                "author" : "string",
                "image_url" : "string",
                "createdAt" : "datetime",
                "updatedAt" : "datetime",
                "categories" : [
                    {
                        "id" : "string, unique",
                        "category" : "string"
                    }
                ]    
             }
        }
    ]
}
```


