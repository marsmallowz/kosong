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

## Login

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
            "admin" : boolean
         }
     }
}
```

## List Book v2

Request :
- Method : POST
- Endpoint : `/api/books`
- Header :
    - Content-Type: application/json
    - Accept: application/json
- Query Param :
    - size : number,
    - page : number,
    - sort : string,
    - search : string
- Body :

```json 
{
    
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
```

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
- Endpoint : `/api/books/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

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
- Endpoint : `/api/loans/:loan_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## List Loan from user

Request :
- Method : GET
- Endpoint : `/api/loans`
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
             "return" : boolean,
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
             "return" : boolean,
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

## Create Category

Request :
- Method : POST
- Endpoint : `/api/categories/`
- Header :
    - Content-Type: application/json
    - Accept: application/json
    - Authorization : Bearer your_token

- Body :

```json 
{
    "category" : "string", 
}
```

Response :

```json 
{
    "status" : "number"
}
```

## Update Category

Request :
- Method : PATCH
- Endpoint : `/api/categories/:category_id`
- Header :
    - Content-Type: application/json
    - Accept: application/json
    - Authorization : Bearer your_token

- Body :

```json 
{
    "category" : "string", 
}
```

Response :

```json 
{
    "status" : "number"
}
```


## Delete Category

Request :
- Method : DELETE
- Endpoint : `/api/categories/:category_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## Create Book

Request :
- Method : POST
- Endpoint : `/api/books/`
- Header :
    - Content-Type: application/json
    - Accept: application/json
    - Authorization : Bearer your_token

- Body :

```json 
{
    "title" : "string",
    "synopsis" : "string",
    "stock" : "number",
    "author" : "string",
    "image_url" : "string",
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
```

Response :

```json 
{
    "status" : "number"
}
```

## Update Book

Request :
- Method : PATCH
- Endpoint : `/api/categories/:book_id`
- Header :
    - Content-Type: application/json
    - Accept: application/json
    - Authorization : Bearer your_token

- Body :

```json 
{
    "title" : "string",
    "synopsis" : "string",
    "stock" : "number",
    "author" : "string",
    "image_url" : "string",
    "categories" : [
        {
            "id" : "string, unique",
            "category" : "string"
        }
    ]
}
```

Response :

```json 
{
    "status" : "number"
}
```


## Delete Book

Request :
- Method : DELETE
- Endpoint : `/api/categories/:book_id`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```

## Get Loans from admin

Request :
- Method : GET
- Endpoint : `/api/loans`
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
             "return" : boolean,
             "book" : {
                "id" : "string, unique","string, unique"
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
             "user": {
                "id" : "string, unique",
                "nim" : "string",
                "username" : "string",
             }
        },
        {
             "id" : "string, unique",
             "loan_time" : "datetime",
             "return" : boolean,
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
             },
             "user": {
                "id" : "string, unique",
                "nim" : "string",
                "username" : "string",
             }
        }
    ]
}
```

## Check Token Session

Request :
- Method : GET
- Endpoint : `/api/auth`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number",
    "data": {
        "user": {
            "username" : "string",
            "admin" : boolean
        },
        "there_is_loan_limit" : "true"
    }
}
```


## Resend Email Verification

Request :
- Method : POST
- Endpoint : `/api/auth/v3`
- Header :
    - Accept: application/json
    - Authorization : Bearer your_token

Response :

```json 
{
    "status" : "number"
}
```
