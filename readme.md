# service-api-requisition api-listing 

This markdown file contains all api document Order-wise how does flow works of service-api-requisition

	baseProcurementUrl:
		https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/

# API Reference
The service-api-requisition is organized around REST. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

## Errors

Service Api Requisition uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the ```2xx``` range indicate success. Codes in the ```4xx``` range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.). Codes in the ```5xx``` range indicate an error with Stripe's servers (these are rare).

Some ```4xx``` errors that could be handled programmatically (e.g., a card is declined) include an error code that briefly explains the error reported.

 # HTTPS STATUS CODE SUMMRY

Code   | Summary
------------- | -------------
200 - OK  | Everything worked as expected.
400 - Bad Request  | The request was unacceptable, often due to missing a required parameter.
800 - NEGATIVE_ID_NOT_ALLOWED | Negative id not allowed 
801 - ID_NOT_FOUND | Id not found
802 - INVALID_INPUT | Invalid input

## Attributes

**type** *string*

The type of error returned. One of api_error, card_error, idempotency_error, or invalid_request_error

**code** *number*

For some errors that could be handled programmatically, a short string indicating the error code reported.

**message** *string*

A human-readable message providing more details about the error. For card errors, these messages can be shown to your users.

**object** *object*

If the error is parameter-specific, the parameter related to the error. For example, you can use this to display a message near the correct form field.

 # Error Type and Description

Error Type   | Description
------------- | -------------
api_error |	API errors cover any other type of problem (e.g., a temporary problem with Stripe's servers), and are extremely uncommon.
card_error |	Card errors are the most common type of error you should expect to handle. They result when the user enters a card that can't be charged for some reason.
invalid_request_error |	Invalid request errors arise when your request has invalid parameters.


## Entity list 
-->brief-intro


Entity Name | Endpoint | Methods
------------|----------|---------
Request | /request | GET, POST, PUT, DELETE
Product | /product| GET, POST, PUT, DELETE
Supplier | /supplier| GET, POST, PUT, DELETE
Currency | /currency| GET, POST, PUT, DELETE
Invoice | /invoice| GET, POST, PUT, DELETE
PurchseOrder | /purchase_order| GET, POST, PUT, DELETE

## **Request-Entity**

```json
{
    "id": 1,
    "details": {
        "createdBy": "requester id",
        "createdOn": "01-01-2022",
        "updatedBy": "updater name",
        "updatedOn": "01-01-2022",
        "approvedBy": "approverId",
        "approvedOn": "01-01-2022",
        "desiredDate": "01-01-2022",
        "location": "head office",
        "requestType": "purchase",
        "note": "This is note",
        "state": "pending",
        "progressStage": "new",
        "totalAmount": 824,
        "department": "development",
        "document": [
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            }
        ],
        "products": [
            {
                "item": {
                    "id": 3,
                    "itemName": "mouse",
                    "itemType": "product",
                    "unit": "each",
                    "category": "tech",
                    "price": 12,
                    "supplier": {
                        "id": 2,
                        "name": "raghav das",
                        "email": "this@gmail.com",
                        "contact": "+91 9876543210",
                        "telephoneNo": "012-65432",
                        "designationNo": "1233",
                        "automateSending": "true",
                        "city": "jaipur",
                        "state": "rajasthan",
                        "postalCode": "13468",
                        "country": "USA",
                        "paymentTerms": "terms",
                        "category": "cat",
                        "address": "Street no. B6, Miami",
                        "status": "active",
                        "company": {
                            "name": "flipkart",
                            "registrationNo": "123"
                        },
                        "bankDetails": {
                            "accountHolderName": "jitin",
                            "accountNo": "1234565789",
                            "bank": "ABCD",
                            "taxId": "DFS55465dFS",
                            "currency": {
                                "id": 1,
                                "code": "USD",
                                "name": "doller",
                                "countryName": "USA",
                                "countryCode": 1
                            }
                        },
                        "document": [
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            }
                        ]
                    }
                },
                "quantity": 1
            },
            {
                "item": {
                    "id": 2,
                    "itemName": "hp laptop",
                    "itemType": "product",
                    "unit": "each",
                    "category": "tech",
                    "price": 800,
                    "supplier": {
                        "id": 1,
                        "name": "andrew choudhary",
                        "email": "this@gmail.com",
                        "contact": "+91 9876543210",
                        "telephoneNo": "012-65432",
                        "designationNo": "1233",
                        "automateSending": "true",
                        "city": "jaipur",
                        "state": "rajasthan",
                        "postalCode": "13468",
                        "country": "USA",
                        "paymentTerms": "terms",
                        "category": "cat",
                        "address": "Street no. B6, Miami",
                        "status": "active",
                        "company": {
                            "name": "amazone",
                            "registrationNo": "123"
                        },
                        "bankDetails": {
                            "accountHolderName": "jitin",
                            "accountNo": "1234565789",
                            "bank": "ABCD",
                            "taxId": "DFS55465dFS",
                            "currency": {
                                "id": 1,
                                "code": "USD",
                                "name": "doller",
                                "countryName": "USA",
                                "countryCode": 1
                            }
                        },
                        "document": [
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            }
                        ]
                    }
                },
                "quantity": 1
            }
        ]
    }
}

```
  

## **Request**
    End Points
        POST /request
        PUT  /request
        GET  /request
        DELETE /request
        POST /request/approve

**/request**

Api to create request.

```json
    Method: POST
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		
*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/request' \
--header 'Content-Type: application/json' \
--data-raw '{
    "createdBy": "Jitin",
    "createdOn": "01-01-2022",
    "updatedBy": "updater name",
    "updatedOn": "01-01-2022",
    "approvedBy": "approverId",
    "approvedOn": "01-01-2022",
    "desiredDate": "01-01-2022",
    "location": "head office",
    "requestType": "purchase",
    "note": "Jitin",
    "state": "pending",
    "progressStage": "new",
    "totalAmount": 824,
    "department": "development",
    "document": [
        {
            "name": "name",
            "url": ""
        },
        {
            "name": "name",
            "url": ""
        },
        {
            "name": "name",
            "url": ""
        }
    ],
    "products": [
        {
            "item": {
                "id": 3,
                "itemName": "mouse",
                "itemType": "product",
                "unit": "each",
                "category": "tech",
                "price": 12,
                "supplier": {
                    "id": 2,
                    "name": "raghav das",
                    "email": "this@gmail.com",
                    "contact": "+91 9876543210",
                    "telephoneNo": "012-65432",
                    "designationNo": "1233",
                    "automateSending": "true",
                    "city": "jaipur",
                    "state": "rajasthan",
                    "postalCode": "13468",
                    "country": "USA",
                    "paymentTerms": "terms",
                    "category": "cat",
                    "address": "Street no. B6, Miami",
                    "status": "active",
                    "company": {
                        "name": "flipkart",
                        "registrationNo": "123"
                    },
                    "bankDetails": {
                        "accountHolderName": "jitin",
                        "accountNo": "1234565789",
                        "bank": "ABCD",
                        "taxId": "DFS55465dFS",
                        "currency": {
                            "id": 1,
                            "code": "USD",
                            "name": "doller",
                            "countryName": "USA",
                            "countryCode": 1
                        }
                    },
                    "document": [
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        }
                    ]
                }
            },
            "quantity": 1
        },
        {
            "item": {
                "id": 2,
                "itemName": "hp laptop",
                "itemType": "product",
                "unit": "each",
                "category": "tech",
                "price": 800,
                "supplier": {
                    "id": 1,
                    "name": "andrew choudhary",
                    "email": "this@gmail.com",
                    "contact": "+91 9876543210",
                    "telephoneNo": "012-65432",
                    "designationNo": "1233",
                    "automateSending": "true",
                    "city": "jaipur",
                    "state": "rajasthan",
                    "postalCode": "13468",
                    "country": "USA",
                    "paymentTerms": "terms",
                    "category": "cat",
                    "address": "Street no. B6, Miami",
                    "status": "active",
                    "company": {
                        "name": "amazone",
                        "registrationNo": "123"
                    },
                    "bankDetails": {
                        "accountHolderName": "jitin",
                        "accountNo": "1234565789",
                        "bank": "ABCD",
                        "taxId": "DFS55465dFS",
                        "currency": {
                            "id": 1,
                            "code": "USD",
                            "name": "doller",
                            "countryName": "USA",
                            "countryCode": 1
                        }
                    },
                    "document": [
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        }
                    ]
                }
            },
            "quantity": 1
        }
    ]
}'
```
**/request**

Api to update request.
```json
	Method: PUT
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/request' \
--header 'Content-Type: application/json' \
--data-raw '{
  "id": 31,
  "details": {
    "note": "Taaaaaaaaaa",
    "state": "aaaaaaaaaaa",
    "document": [
      {
        "url": "",
        "name": "aaaaaaaaaaa"
      },
      {
        "url": "",
        "name": "aaaaaaaa"
      },
      {
        "url": "",
        "name": "name"
      }
    ],
    "location": "aaaaaa",
    "products": [
      {
        "item": {
          "id": 3,
          "unit": "each",
          "price": 12,
          "category": "tech",
          "itemName": "mouse",
          "itemType": "product",
          "supplier": {
            "id": 2,
            "city": "jaipur",
            "name": "raghav das",
            "email": "this@gmail.com",
            "state": "rajasthan",
            "status": "active",
            "address": "Street no. B6, Miami",
            "company": {
              "name": "flipkart",
              "registrationNo": "123"
            },
            "contact": "+91 9876543210",
            "country": "USA",
            "category": "cat",
            "document": [
              {
                "url": "",
                "name": "name"
              },
              {
                "url": "",
                "name": "name"
              },
              {
                "url": "",
                "name": "name"
              }
            ],
            "postalCode": "13468",
            "bankDetails": {
              "bank": "ABCD",
              "taxId": "DFS55465dFS",
              "currency": {
                "id": 1,
                "code": "USD",
                "name": "doller",
                "countryCode": 1,
                "countryName": "USA"
              },
              "accountNo": "1234565789",
              "accountHolderName": "jitin"
            },
            "telephoneNo": "012-65432",
            "paymentTerms": "terms",
            "designationNo": "1233",
            "automateSending": "true"
          }
        },
        "quantity": 1
      },
      {
        "item": {
          "id": 2,
          "unit": "each",
          "price": 800,
          "category": "tech",
          "itemName": "hp laptop",
          "itemType": "product",
          "supplier": {
            "id": 1,
            "city": "jaipur",
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "state": "rajasthan",
            "status": "active",
            "address": "Street no. B6, Miami",
            "company": {
              "name": "amazone",
              "registrationNo": "123"
            },
            "contact": "+91 9876543210",
            "country": "USA",
            "category": "cat",
            "document": [
              {
                "url": "",
                "name": "name"
              },
              {
                "url": "",
                "name": "name"
              },
              {
                "url": "",
                "name": "name"
              }
            ],
            "postalCode": "13468",
            "bankDetails": {
              "bank": "ABCD",
              "taxId": "DFS55465dFS",
              "currency": {
                "id": 1,
                "code": "USD",
                "name": "doller",
                "countryCode": 1,
                "countryName": "USA"
              },
              "accountNo": "1234565789",
              "accountHolderName": "jitin"
            },
            "telephoneNo": "012-65432",
            "paymentTerms": "terms",
            "designationNo": "1233",
            "automateSending": "true"
          }
        },
        "quantity": 1
      }
    ],
    "createdBy": "requester id",
    "createdOn": "01-01-2022",
    "requestId": 1,
    "updatedBy": "updater name",
    "updatedOn": "01-01-2022",
    "approvedBy": "approverId",
    "approvedOn": "01-01-2022",
    "department": "development",
    "desiredDate": "01-01-2022",
    "requestType": "purchase",
    "totalAmount": 824,
    "progressStage": "new"
  }
}'

```
**/request**

Api to search request.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of result objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/request' \
--header 'Content-Type: application/json' \
--data-raw '{
     "id": 12
}'
```
**/request**

Api to deactivated request.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "request delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/request' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 31
}'
```

**/request/approve**

Api to request approve.

```json
	Method: POST
	RequestBody:
		{ "id" : 1 }
	Response:
	    {
            "code": 200,
            "message": "request approved successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json
    * TODO *
```


## **Product-Entity**
```json

{
    "id": 1,
    "details": {
        "itemName": "mouse",
        "price": 12,
        "unit": "each",
        "itemType": "product",
        "category": "tech",
        "imgUrl": "http://imgSynectiks.com",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        }
    }
}
```
  

## **Product**
    End Points
        POST /product
        PUT  /product
        GET  /product
        DELETE /product

**/product**

Api to create product.

```json
    Method: POST
    Request Body:
        {
        "itemName": "hp laptop",
        "itemType": "product",
        "unit": "each",
        "category": "tech",
        "price": 800,
        "imgUrl": "http://imgSynectiks.com",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        }
    }
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		

*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/product' \
--header 'Content-Type: application/json' \
--data-raw '{
        "itemName": "hp laptop",
        "itemType": "product",
        "unit": "each",
        "category": "tech",
        "price": 800,
        "imgUrl": "http://imgSynectiks.com",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        }
    }'
```
**/product**

Api to update product.
```json
	Method: PUT
    Request Body:
        {
            "id": 2,
            "details": {
                "itemName": "hp laptop",
                "itemType": "product",
                "unit": "every",
                "category": "tech",
                "price": 800,
                "imgUrl": "http://imgSynectiks.com",
                "supplier": {
                    "id": 1,
                    "name": "andrew choudhary",
                    "email": "this@gmail.com",
                    "contact": "+91 9876543210",
                    "telephoneNo": "012-65432",
                    "designationNo": "1233",
                    "automateSending": "true",
                    "city": "jaipur",
                    "state": "rajasthan",
                    "postalCode": "13468",
                    "country": "USA",
                    "paymentTerms": "terms",
                    "category": "cat",
                    "address": "Street no. B6, Miami",
                    "status": "active",
                    "company": {
                        "name": "amazone",
                        "registrationNo": "123"
                    },
                    "bankDetails": {
                        "accountHolderName": "jitin",
                        "accountNo": "1234565789",
                        "bank": "ABCD",
                        "taxId": "DFS55465dFS",
                        "currency": {
                            "id": 1,
                            "code": "USD",
                            "name": "doller",
                            "countryName": "USA",
                            "countryCode": 1
                        }
                    },
                    "document": [
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        }
                    ]
                }
            }
        }
	
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
 curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/product' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 2,
    "details": {
        "itemName": "hp laptop",
        "itemType": "product",
        "unit": "every",
        "category": "tech",
        "price": 800,
        "imgUrl": "http://imgSynectiks.com",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        }
    }
}'
```
**/product**

Api to search product.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of resultant objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/product' \
--header 'Content-Type: application/json' \
--data-raw '{
    "uhnit": "every"
}'
```
**/product**

Api to delete product.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json 
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/product' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":2
    
}'
```


## **Supplier-Entity**
```json
{
    "id": 47,
    "details": {
        "name": "raghuy",
        "email": "this@gmail.com",
        "contact": "+91 9876543210",
        "telephoneNo": "012-65432",
        "designationNo": "1233",
        "automateSending": "true",
        "city": "anupgarh",
        "state": "rajasthan",
        "postalCode": "13468",
        "country": "USA",
        "paymentTerms": "terms",
        "category": "cat",
        "address": "Street no. B6, Miami",
        "status": "active",
        "company": {
            "name": "flipkart",
            "registrationNo": "123"
        },
        "bankDetails": {
            "accountHolderName": "jitin",
            "accountNo": "1234565789",
            "bank": "ABCD",
            "taxId": "DFS55465dFS",
            "currency": {
                "id": 1,
                "code": "USD",
                "name": "doller",
                "countryName": "USA",
                "countryCode": 1
            }
        },
        "document": [
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            }
        ]
    }
}
```
  
## **supplier**
    End Points
        POST /supplier
        PUT  /supplier
        GET  /supplier
        DELETE /supplier

**/supplier**

Api to create supplier.

```json
    Method: POST
    Request Body:
       {
            "name": "raghav das",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "flipkart",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        }
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		

*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/supplier' \
--header 'Content-Type: application/json' \
--data-raw '{
        "name": "raghav das",
        "email": "this@gmail.com",
        "contact": "+91 9876543210",
        "telephoneNo": "012-65432",
        "designationNo": "1233",
        "automateSending": "true",
        "city": "jaipur",
        "state": "rajasthan",
        "postalCode": "13468",
        "country": "USA",
        "paymentTerms": "terms",
        "category": "cat",
        "address": "Street no. B6, Miami",
        "status": "active",
        "company": {
            "name": "flipkart",
            "registrationNo": "123"
        },
        "bankDetails": {
            "accountHolderName": "jitin",
            "accountNo": "1234565789",
            "bank": "ABCD",
            "taxId": "DFS55465dFS",
            "currency": {
                "id": 1,
                "code": "USD",
                "name": "doller",
                "countryName": "USA",
                "countryCode": 1
            }
        },
        "document": [
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            }
        ]
    }'
```
**/supplier**

Api to update supplier.
```json
	Method: PUT
    Request Body:
       {
            "id": 47,
            "details": {
                "name": "raghuy",
                "email": "this@gmail.com",
                "contact": "+91 9876543210",
                "telephoneNo": "012-65432",
                "designationNo": "1233",
                "automateSending": "true",
                "city": "anupgarh",
                "state": "rajasthan",
                "postalCode": "13468",
                "country": "USA",
                "paymentTerms": "terms",
                "category": "cat",
                "address": "Street no. B6, Miami",
                "status": "active",
                "company": {
                    "name": "flipkart",
                    "registrationNo": "123"
                },
                "bankDetails": {
                    "accountHolderName": "jitin",
                    "accountNo": "1234565789",
                    "bank": "ABCD",
                    "taxId": "DFS55465dFS",
                    "currency": {
                        "id": 1,
                        "code": "USD",
                        "name": "doller",
                        "countryName": "USA",
                        "countryCode": 1
                    }
                },
                "document": [
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    }
                ]
            }
        }
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
 curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/supplier' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 47,
    "details": {
        "name": "raghuy",
        "email": "this@gmail.com",
        "contact": "+91 9876543210",
        "telephoneNo": "012-65432",
        "designationNo": "1233",
        "automateSending": "true",
        "city": "anupgarh",
        "state": "rajasthan",
        "postalCode": "13468",
        "country": "USA",
        "paymentTerms": "terms",
        "category": "cat",
        "address": "Street no. B6, Miami",
        "status": "active",
        "company": {
            "name": "flipkart",
            "registrationNo": "123"
        },
        "bankDetails": {
            "accountHolderName": "jitin",
            "accountNo": "1234565789",
            "bank": "ABCD",
            "taxId": "DFS55465dFS",
            "currency": {
                "id": 1,
                "code": "USD",
                "name": "doller",
                "countryName": "USA",
                "countryCode": 1
            }
        },
        "document": [
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            },
            {
                "name": "name",
                "url": ""
            }
        ]
    }
}'
```
**/supplier**

Api to search supplier.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of resultant objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/supplier' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "raghu"
}'
```
**/supplier**

Api to delete supplier.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json 
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/supplier' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":2
}'
```

## **currency-Entity**
```json
{
    "id": 2,
    "details": {
        "code": "INRP",
        "name": "Rupee",
        "countryName": "INDIA",
        "countryCode": 91
    }
}
```
  
## **currency**
    End Points
        POST /currency
        PUT  /currency
        GET  /currency
        DELETE /currency

**/currency**

Api to create currency.

```json
    Method: POST
    Request Body:
       {
            "code": "INR",
            "name": "Rupee",
            "countryName": "INDIA",
            "countryCode": 91
        }   
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		

*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/currency' \
--header 'Content-Type: application/json' \
--data-raw '{
    "code": "INR",
    "name": "Rupee",
    "countryName": "INDIA",
    "countryCode": 91
}'
```
**/currency**

Api to update currency.
```json
	Method: PUT
    Request Body:
       {
            "id": 2,
            "details": {
                "code": "INRP",
                "name": "Rupee",
                "countryName": "INDIA",
                "countryCode": 91
            }
        }   
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
 curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/currency' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 2,
    "details": {
        "code": "INRP",
        "name": "Rupee",
        "countryName": "INDIA",
        "countryCode": 91
    }
}'
```
**/currency**

Api to search currency.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of resultant objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/currency' \
--header 'Content-Type: application/json' \
--data-raw '{
    "code": "USD"
}'
```
**/currency**

Api to delete currency.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json 
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/currency' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":1
}'
```

## **Invoice-Entity**
```json
{
    "id": 47,
    "details": {
        "url": "http://invoice-location.com",
        "issueDate": "15-01-2022",
        "invoiceDueDate": "15-01-2022",
        "amount": 24,
        "tax": "+20VAT",
        "purchaseOrder": {
            "id": 2,
            "requesterId": 1,
            "fromDate": "01-01-2022",
            "toDate": "02-01-2022",
            "createdOn": "03-01-2022",
            "updatedOn": "05-01-2022",
            "createdBy": "Creater Name",
            "updatedBy": "Updater Name",
            "deliveryDate": "10-01-2022",
            "status": "Pending | Unpaid | Undelivered | Delivered",
            "totalNumberOfProduct": "1",
            "totalAmount": 24,
            "paymentTerm": "30 Net",
            "shippingMethod": "Store Pickup",
            "paymentWith": "Credit card",
            "shippingTerms": "FOB",
            "notes": "this is notes for Purchase Order",
            "supplier": {
                "id": 2,
                "name": "raghav das",
                "email": "this@gmail.com",
                "contact": "+91 9876543210",
                "telephoneNo": "012-65432",
                "designationNo": "1233",
                "automateSending": "true",
                "city": "jaipur",
                "state": "rajasthan",
                "postalCode": "13468",
                "country": "USA",
                "paymentTerms": "terms",
                "category": "cat",
                "address": "Street no. B6, Miami",
                "status": "active",
                "company": {
                    "name": "flipkart",
                    "registrationNo": "123"
                },
                "bankDetails": {
                    "accountHolderName": "jitin",
                    "accountNo": "1234565789",
                    "bank": "ABCD",
                    "taxId": "DFS55465dFS",
                    "currency": {
                        "id": 1,
                        "code": "USD",
                        "name": "doller",
                        "countryName": "USA",
                        "countryCode": 1
                    }
                },
                "document": [
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    }
                ]
            },
            "requestsDetail": [
                {
                    "requestId": 1,
                    "ids": [
                        1
                    ]
                }
            ],
            "purchaseOrderProduct": [
                {
                    "item": {
                        "id": 1,
                        "itemName": "mouse",
                        "itemType": "product",
                        "unit": "each",
                        "category": "tech",
                        "supplier": "flipkart",
                        "price": 12
                    },
                    "quantity": 2
                }
            ]
        },
        "currency": {
            "currencyId": 2,
            "code": "INR",
            "Name": "Rupee",
            "countryName": "INDIA",
            "countryCode": "91"
        }
    }
}
```
  
## **Invoice**
    End Points
        POST /invoice
        PUT  /invoice
        GET  /invoice
        DELETE /invoice

**/invoice**

Api to create invoice.

```json
    Method: POST
    Request Body:
       {
            "url": "http://invoice-location.com",
            "issueDate": "15-01-2045",
            "invoiceDueDate": "15-01-2022",
            "amount": 24,
            "tax": "+18VAT",
            "purchaseOrder": {
                "id": 2,
                "requesterId": 1,
                "fromDate": "01-01-2022",
                "toDate": "02-01-2022",
                "createdOn": "03-01-2022",
                "updatedOn": "05-01-2022",
                "createdBy": "Creater Name",
                "updatedBy": "Updater Name",
                "deliveryDate": "10-01-2022",
                "status": "Pending | Unpaid | Undelivered | Delivered",
                "totalNumberOfProduct": "1",
                "totalAmount": 24,
                "paymentTerm": "30 Net",
                "shippingMethod": "Store Pickup",
                "paymentWith": "Credit card",
                "shippingTerms": "FOB",
                "notes": "this is notes for Purchase Order",
                "supplier": {
                    "id": 2,
                    "name": "raghav das",
                    "email": "this@gmail.com",
                    "contact": "+91 9876543210",
                    "telephoneNo": "012-65432",
                    "designationNo": "1233",
                    "automateSending": "true",
                    "city": "jaipur",
                    "state": "rajasthan",
                    "postalCode": "13468",
                    "country": "USA",
                    "paymentTerms": "terms",
                    "category": "cat",
                    "address": "Street no. B6, Miami",
                    "status": "active",
                    "company": {
                        "name": "flipkart",
                        "registrationNo": "123"
                    },
                    "bankDetails": {
                        "accountHolderName": "jitin",
                        "accountNo": "1234565789",
                        "bank": "ABCD",
                        "taxId": "DFS55465dFS",
                        "currency": {
                            "id": 1,
                            "code": "USD",
                            "name": "doller",
                            "countryName": "USA",
                            "countryCode": 1
                        }
                    },
                    "document": [
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        }
                    ]
                },
                "requestsDetail": [
                    {
                        "requestId": 1,
                        "ids": [
                            1
                        ]
                    }
                ],
                "purchaseOrderProduct": [
                    {
                        "item": {
                            "id": 1,
                            "itemName": "mouse",
                            "itemType": "product",
                            "unit": "each",
                            "category": "tech",
                            "supplier": "flipkart",
                            "price": 12
                        },
                        "quantity": 2
                    }
                ]
            },
            "currency": {
                "currencyId": 2,
                "code": "INR",
                "Name": "Rupee",
                "countryName": "INDIA",
                "countryCode": "91"
            }
        }
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		

*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/invoice' \
--header 'Content-Type: application/json' \
--data-raw '{
        "url": "http://invoice-location.com",
        "issueDate": "15-01-2045",
        "invoiceDueDate": "15-01-2022",
        "amount": 24,
        "tax": "+18VAT",
        "purchaseOrder": {
            "id": 2,
            "requesterId": 1,
            "fromDate": "01-01-2022",
            "toDate": "02-01-2022",
            "createdOn": "03-01-2022",
            "updatedOn": "05-01-2022",
            "createdBy": "Creater Name",
            "updatedBy": "Updater Name",
            "deliveryDate": "10-01-2022",
            "status": "Pending | Unpaid | Undelivered | Delivered",
            "totalNumberOfProduct": "1",
            "totalAmount": 24,
            "paymentTerm": "30 Net",
            "shippingMethod": "Store Pickup",
            "paymentWith": "Credit card",
            "shippingTerms": "FOB",
            "notes": "this is notes for Purchase Order",
            "supplier": {
                "id": 2,
                "name": "raghav das",
                "email": "this@gmail.com",
                "contact": "+91 9876543210",
                "telephoneNo": "012-65432",
                "designationNo": "1233",
                "automateSending": "true",
                "city": "jaipur",
                "state": "rajasthan",
                "postalCode": "13468",
                "country": "USA",
                "paymentTerms": "terms",
                "category": "cat",
                "address": "Street no. B6, Miami",
                "status": "active",
                "company": {
                    "name": "flipkart",
                    "registrationNo": "123"
                },
                "bankDetails": {
                    "accountHolderName": "jitin",
                    "accountNo": "1234565789",
                    "bank": "ABCD",
                    "taxId": "DFS55465dFS",
                    "currency": {
                        "id": 1,
                        "code": "USD",
                        "name": "doller",
                        "countryName": "USA",
                        "countryCode": 1
                    }
                },
                "document": [
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    }
                ]
            },
            "requestsDetail": [
                {
                    "requestId": 1,
                    "ids": [
                        1
                    ]
                }
            ],
            "purchaseOrderProduct": [
                {
                    "item": {
                        "id": 1,
                        "itemName": "mouse",
                        "itemType": "product",
                        "unit": "each",
                        "category": "tech",
                        "supplier": "flipkart",
                        "price": 12
                    },
                    "quantity": 2
                }
            ]
        },
        "currency": {
            "currencyId": 2,
            "code": "INR",
            "Name": "Rupee",
            "countryName": "INDIA",
            "countryCode": "91"
        }
    }'
```
**/invoice**

Api to update invoice.
```json
	Method: PUT
    Request Body:
      {
            "id": 47,
            "details": {
                "url": "http://invoice-location.com",
                "issueDate": "15-01-2022",
                "invoiceDueDate": "15-01-2022",
                "amount": 24,
                "tax": "+20VAT",
                "purchaseOrder": {
                    "id": 2,
                    "requesterId": 1,
                    "fromDate": "01-01-2022",
                    "toDate": "02-01-2022",
                    "createdOn": "03-01-2022",
                    "updatedOn": "05-01-2022",
                    "createdBy": "Creater Name",
                    "updatedBy": "Updater Name",
                    "deliveryDate": "10-01-2022",
                    "status": "Pending | Unpaid | Undelivered | Delivered",
                    "totalNumberOfProduct": "1",
                    "totalAmount": 24,
                    "paymentTerm": "30 Net",
                    "shippingMethod": "Store Pickup",
                    "paymentWith": "Credit card",
                    "shippingTerms": "FOB",
                    "notes": "this is notes for Purchase Order",
                    "supplier": {
                        "id": 2,
                        "name": "raghav das",
                        "email": "this@gmail.com",
                        "contact": "+91 9876543210",
                        "telephoneNo": "012-65432",
                        "designationNo": "1233",
                        "automateSending": "true",
                        "city": "jaipur",
                        "state": "rajasthan",
                        "postalCode": "13468",
                        "country": "USA",
                        "paymentTerms": "terms",
                        "category": "cat",
                        "address": "Street no. B6, Miami",
                        "status": "active",
                        "company": {
                            "name": "flipkart",
                            "registrationNo": "123"
                        },
                        "bankDetails": {
                            "accountHolderName": "jitin",
                            "accountNo": "1234565789",
                            "bank": "ABCD",
                            "taxId": "DFS55465dFS",
                            "currency": {
                                "id": 1,
                                "code": "USD",
                                "name": "doller",
                                "countryName": "USA",
                                "countryCode": 1
                            }
                        },
                        "document": [
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            },
                            {
                                "name": "name",
                                "url": ""
                            }
                        ]
                    },
                    "requestsDetail": [
                        {
                            "requestId": 1,
                            "ids": [
                                1
                            ]
                        }
                    ],
                    "purchaseOrderProduct": [
                        {
                            "item": {
                                "id": 1,
                                "itemName": "mouse",
                                "itemType": "product",
                                "unit": "each",
                                "category": "tech",
                                "supplier": "flipkart",
                                "price": 12
                            },
                            "quantity": 2
                        }
                    ]
                },
                "currency": {
                    "currencyId": 2,
                    "code": "INR",
                    "Name": "Rupee",
                    "countryName": "INDIA",
                    "countryCode": "91"
                }
            }
        }
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
 curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/invoice' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 47,
    "details": {
        "url": "http://invoice-location.com",
        "issueDate": "15-01-2022",
        "invoiceDueDate": "15-01-2022",
        "amount": 24,
        "tax": "+20VAT",
        "purchaseOrder": {
            "id": 2,
            "requesterId": 1,
            "fromDate": "01-01-2022",
            "toDate": "02-01-2022",
            "createdOn": "03-01-2022",
            "updatedOn": "05-01-2022",
            "createdBy": "Creater Name",
            "updatedBy": "Updater Name",
            "deliveryDate": "10-01-2022",
            "status": "Pending | Unpaid | Undelivered | Delivered",
            "totalNumberOfProduct": "1",
            "totalAmount": 24,
            "paymentTerm": "30 Net",
            "shippingMethod": "Store Pickup",
            "paymentWith": "Credit card",
            "shippingTerms": "FOB",
            "notes": "this is notes for Purchase Order",
            "supplier": {
                "id": 2,
                "name": "raghav das",
                "email": "this@gmail.com",
                "contact": "+91 9876543210",
                "telephoneNo": "012-65432",
                "designationNo": "1233",
                "automateSending": "true",
                "city": "jaipur",
                "state": "rajasthan",
                "postalCode": "13468",
                "country": "USA",
                "paymentTerms": "terms",
                "category": "cat",
                "address": "Street no. B6, Miami",
                "status": "active",
                "company": {
                    "name": "flipkart",
                    "registrationNo": "123"
                },
                "bankDetails": {
                    "accountHolderName": "jitin",
                    "accountNo": "1234565789",
                    "bank": "ABCD",
                    "taxId": "DFS55465dFS",
                    "currency": {
                        "id": 1,
                        "code": "USD",
                        "name": "doller",
                        "countryName": "USA",
                        "countryCode": 1
                    }
                },
                "document": [
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    }
                ]
            },
            "requestsDetail": [
                {
                    "requestId": 1,
                    "ids": [
                        1
                    ]
                }
            ],
            "purchaseOrderProduct": [
                {
                    "item": {
                        "id": 1,
                        "itemName": "mouse",
                        "itemType": "product",
                        "unit": "each",
                        "category": "tech",
                        "supplier": "flipkart",
                        "price": 12
                    },
                    "quantity": 2
                }
            ]
        },
        "currency": {
            "currencyId": 2,
            "code": "INR",
            "Name": "Rupee",
            "countryName": "INDIA",
            "countryCode": "91"
        }
    }
}'
```
**/invoice**

Api to search invoice.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of resultant objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/invoice' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":3
}'
```
**/invoice**

Api to delete invoice.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json 
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/invoice' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 1
}'
```

## **Purchase order-Entity**
```json
{
    "id": 2,
    "details": {
        "requesterId": 1,
        "fromDate": "01-01-2022",
        "toDate": "02-01-2022",
        "createdOn": "03-01-2022",
        "updatedOn": "05-01-2022",
        "createdBy": "Creater Name",
        "updatedBy": "Updater Name",
        "deliveryDate": "10-01-2022",
        "status": "Pending | Unpaid | Undelivered | Delivered",
        "totalNumberOfProduct": "3",
        "totalAmount": 824,
        "paymentTerm": "30 Net",
        "shippingMethod": "Store Pickup",
        "paymentWith": "Credit card",
        "shippingTerms": "FOB",
        "notes": "this",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        },
        "requestsDetail": [
            {
                "requestId": 1,
                "ids": [
                    2
                ]
            },
            {
                "requestId": 2,
                "ids": [
                    1
                ]
            }
        ],
        "purchaseOrderProducts": [
            {
                "item": {
                    "id": 2,
                    "itemName": "hp laptop",
                    "itemType": "product",
                    "unit": "each",
                    "supplier": "amazone",
                    "category": "tech",
                    "price": 800
                },
                "quantity": 1
            },
            {
                "item": {
                    "id": 1,
                    "itemName": "mouse",
                    "itemType": "product",
                    "unit": "each",
                    "category": "tech",
                    "supplier": "amazone",
                    "price": 12
                },
                "quantity": 2
            }
        ]
    }
}
```
  
## **Purchase order**
    End Points
        POST /purchase_order
        PUT  /purchase_order
        GET  /purchase_order
        DELETE /purchase_order

**/purchase_order**

Api to create purchase_order.

```json
    Method: POST
    Request Body:
        {
            "requesterId": 1,
            "fromDate": "01-01-2022",
            "toDate": "02-01-2022",
            "createdOn": "03-01-2022",
            "updatedOn": "05-01-2022",
            "createdBy": "Creater Name",
            "updatedBy": "Updater Name",
            "deliveryDate": "10-01-2022",
            "status": "Pending | Unpaid | Undelivered | Delivered",
            "totalNumberOfProduct": "3",
            "totalAmount": 824,
            "paymentTerm": "30 Net",
            "shippingMethod": "Store Pickup",
            "paymentWith": "Credit card",
            "shippingTerms": "FOB",
            "notes": "this is notes for Purchase Order",
            "supplier": {
                "id": 1,
                "name": "andrew choudhary",
                "email": "this@gmail.com",
                "contact": "+91 9876543210",
                "telephoneNo": "012-65432",
                "designationNo": "1233",
                "automateSending": "true",
                "city": "jaipur",
                "state": "rajasthan",
                "postalCode": "13468",
                "country": "USA",
                "paymentTerms": "terms",
                "category": "cat",
                "address": "Street no. B6, Miami",
                "status": "active",
                "company": {
                    "name": "amazone",
                    "registrationNo": "123"
                },
                "bankDetails": {
                    "accountHolderName": "jitin",
                    "accountNo": "1234565789",
                    "bank": "ABCD",
                    "taxId": "DFS55465dFS",
                    "currency": {
                        "id": 1,
                        "code": "USD",
                        "name": "doller",
                        "countryName": "USA",
                        "countryCode": 1
                    }
                },
                "document": [
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    },
                    {
                        "name": "name",
                        "url": ""
                    }
                ]
            },
            "requestsDetail": [
                {
                    "requestId": 1,
                    "ids": [
                        2
                    ]
                },
                {
                    "requestId": 2,
                    "ids": [
                        1
                    ]
                }
            ],
            "purchaseOrderProducts": [
                {
                    "item": {
                        "id": 2,
                        "itemName": "hp laptop",
                        "itemType": "product",
                        "unit": "each",
                        "supplier": "amazone",
                        "category": "tech",
                        "price": 800
                    },
                    "quantity": 1
                },
                {
                    "item": {
                        "id": 1,
                        "itemName": "mouse",
                        "itemType": "product",
                        "unit": "each",
                        "category": "tech",
                        "supplier": "amazone",
                        "price": 12
                    },
                    "quantity": 2
                }
            ]
        }
    Response:
    {
        "code": 200,
        "message": "added successfully",
        "type": "object",
        "object": []
    }
```
		

*CURL*
```json
curl --location --request POST 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/purchase_order' \
--header 'Content-Type: application/json' \
--data-raw ' {
        "requesterId": 1,
        "fromDate": "01-01-2022",
        "toDate": "02-01-2022",
        "createdOn": "03-01-2022",
        "updatedOn": "05-01-2022",
        "createdBy": "Creater Name",
        "updatedBy": "Updater Name",
        "deliveryDate": "10-01-2022",
        "status": "Pending | Unpaid | Undelivered | Delivered",
        "totalNumberOfProduct": "3",
        "totalAmount": 824,
        "paymentTerm": "30 Net",
        "shippingMethod": "Store Pickup",
        "paymentWith": "Credit card",
        "shippingTerms": "FOB",
        "notes": "this is notes for Purchase Order",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        },
        "requestsDetail": [
            {
                "requestId": 1,
                "ids": [
                    2
                ]
            },
            {
                "requestId": 2,
                "ids": [
                    1
                ]
            }
        ],
        "purchaseOrderProducts": [
            {
                "item": {
                    "id": 2,
                    "itemName": "hp laptop",
                    "itemType": "product",
                    "unit": "each",
                    "supplier": "amazone",
                    "category": "tech",
                    "price": 800
                },
                "quantity": 1
            },
            {
                "item": {
                    "id": 1,
                    "itemName": "mouse",
                    "itemType": "product",
                    "unit": "each",
                    "category": "tech",
                    "supplier": "amazone",
                    "price": 12
                },
                "quantity": 2
            }
        ]
    }'
```
**/purchase_order**

Api to update purchase_order.
```json
	Method: PUT
    Request Body:
      {
            "id": 2,
            "details": {
                "requesterId": 1,
                "fromDate": "01-01-2022",
                "toDate": "02-01-2022",
                "createdOn": "03-01-2022",
                "updatedOn": "05-01-2022",
                "createdBy": "Creater Name",
                "updatedBy": "Updater Name",
                "deliveryDate": "10-01-2022",
                "status": "Pending | Unpaid | Undelivered | Delivered",
                "totalNumberOfProduct": "3",
                "totalAmount": 824,
                "paymentTerm": "30 Net",
                "shippingMethod": "Store Pickup",
                "paymentWith": "Credit card",
                "shippingTerms": "FOB",
                "notes": "this",
                "supplier": {
                    "id": 1,
                    "name": "andrew choudhary",
                    "email": "this@gmail.com",
                    "contact": "+91 9876543210",
                    "telephoneNo": "012-65432",
                    "designationNo": "1233",
                    "automateSending": "true",
                    "city": "jaipur",
                    "state": "rajasthan",
                    "postalCode": "13468",
                    "country": "USA",
                    "paymentTerms": "terms",
                    "category": "cat",
                    "address": "Street no. B6, Miami",
                    "status": "active",
                    "company": {
                        "name": "amazone",
                        "registrationNo": "123"
                    },
                    "bankDetails": {
                        "accountHolderName": "jitin",
                        "accountNo": "1234565789",
                        "bank": "ABCD",
                        "taxId": "DFS55465dFS",
                        "currency": {
                            "id": 1,
                            "code": "USD",
                            "name": "doller",
                            "countryName": "USA",
                            "countryCode": 1
                        }
                    },
                    "document": [
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        },
                        {
                            "name": "name",
                            "url": ""
                        }
                    ]
                },
                "requestsDetail": [
                    {
                        "requestId": 1,
                        "ids": [
                            2
                        ]
                    },
                    {
                        "requestId": 2,
                        "ids": [
                            1
                        ]
                    }
                ],
                "purchaseOrderProducts": [
                    {
                        "item": {
                            "id": 2,
                            "itemName": "hp laptop",
                            "itemType": "product",
                            "unit": "each",
                            "supplier": "amazone",
                            "category": "tech",
                            "price": 800
                        },
                        "quantity": 1
                    },
                    {
                        "item": {
                            "id": 1,
                            "itemName": "mouse",
                            "itemType": "product",
                            "unit": "each",
                            "category": "tech",
                            "supplier": "amazone",
                            "price": 12
                        },
                        "quantity": 2
                    }
                ]
            }
        }
	Response:
		{
            "code": 200,
            "message": "successfully updated",
            "type": "object",
            "object": []
        }
```

*CURL*

```json
 curl --location --request PUT 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/purchase_order' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 2,
    "details": {
        "requesterId": 1,
        "fromDate": "01-01-2022",
        "toDate": "02-01-2022",
        "createdOn": "03-01-2022",
        "updatedOn": "05-01-2022",
        "createdBy": "Creater Name",
        "updatedBy": "Updater Name",
        "deliveryDate": "10-01-2022",
        "status": "Pending | Unpaid | Undelivered | Delivered",
        "totalNumberOfProduct": "3",
        "totalAmount": 824,
        "paymentTerm": "30 Net",
        "shippingMethod": "Store Pickup",
        "paymentWith": "Credit card",
        "shippingTerms": "FOB",
        "notes": "this",
        "supplier": {
            "id": 1,
            "name": "andrew choudhary",
            "email": "this@gmail.com",
            "contact": "+91 9876543210",
            "telephoneNo": "012-65432",
            "designationNo": "1233",
            "automateSending": "true",
            "city": "jaipur",
            "state": "rajasthan",
            "postalCode": "13468",
            "country": "USA",
            "paymentTerms": "terms",
            "category": "cat",
            "address": "Street no. B6, Miami",
            "status": "active",
            "company": {
                "name": "amazone",
                "registrationNo": "123"
            },
            "bankDetails": {
                "accountHolderName": "jitin",
                "accountNo": "1234565789",
                "bank": "ABCD",
                "taxId": "DFS55465dFS",
                "currency": {
                    "id": 1,
                    "code": "USD",
                    "name": "doller",
                    "countryName": "USA",
                    "countryCode": 1
                }
            },
            "document": [
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                },
                {
                    "name": "name",
                    "url": ""
                }
            ]
        },
        "requestsDetail": [
            {
                "requestId": 1,
                "ids": [
                    2
                ]
            },
            {
                "requestId": 2,
                "ids": [
                    1
                ]
            }
        ],
        "purchaseOrderProducts": [
            {
                "item": {
                    "id": 2,
                    "itemName": "hp laptop",
                    "itemType": "product",
                    "unit": "each",
                    "supplier": "amazone",
                    "category": "tech",
                    "price": 800
                },
                "quantity": 1
            },
            {
                "item": {
                    "id": 1,
                    "itemName": "mouse",
                    "itemType": "product",
                    "unit": "each",
                    "category": "tech",
                    "supplier": "amazone",
                    "price": 12
                },
                "quantity": 2
            }
        ]
    }
}'
```
**/purchase_order**

Api to search purchase_order.

```json
	Method: GET
    Request Body:
        { "Key" : "value for search" }
	Response:
		{
            "code": 200,
            "message": "search successfully",
            "type": "object",
            "object": [ *Array of resultant objects* ]
        } 
```

*CURL*
```json
curl --location --request GET 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/purchase_order' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 2
}'
```
**/purchase_order**

Api to delete purchase_order.

```json 
	Method: DELETE
	Request Body:
        { "id" : 1 }
	Response:
		{
            "code": 200,
            "message": "delete successfully",
            "type": "object",
            "object": []
        }
```

*CURL*
```json 
curl --location --request DELETE 'https://u4kzlb58qh.execute-api.us-east-1.amazonaws.com/procurement-dev/purchase_order' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id":1
}'
```



















### Who do I talk to? ###
	Please mail us on
	info@syenctiks.com
Footer
© 2022 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About





