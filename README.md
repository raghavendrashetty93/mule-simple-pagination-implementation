# mule-simple-pagination-implementation
Simple pagination describes the technique and support of systems of record to provide paginated results without too much additional logic or complex implementation

## About Project
Based on inputs provided in queryParameters from API consumer, gets paginated payload from backend system.
For this project a database of 500 employee records in a CSV file has been used as datasource.

## About Pagination 
Pagination is a method used to divide digital content into discrete pages, thus making it more manageable and easier to navigate.
A technique to retrieve data in sets of fixed number from a desired position instead of getting all the data from backend system.

## Setting Up Prerequisites
Create a RAML definition using below snippet.
```
#%RAML 1.0
title: simple-pagination
mediaType:
  - application/json
version: 1.0.0
protocols:
  - HTTP

/products:
  get:
    queryParameters:
      offset:
        type: number
        example: 1
        format: int
      limit:
        type: number
        example: 10
        format: int
    responses:
      200:
        body:
          type: object
          properties:
            nextOffset: integer
            morePages: boolean
            results:
              type: array
              items:
                properties:
                  recNum: number
                  first_name: string
                  last_name: string
```

## Setting Up Mulesoft Application
Implement the flow which calculates pagination variables.

## Running the application

- Run the project as Mule App and Navigate to http://localhost:8081/console/

- Click on /products GET endpoint, provide value for offset, limit and send the request.
![pagi-1](https://github.com/raghavendrashetty93/mule-simple-pagination-implementation/assets/77000179/36172508-1731-49c5-9e3a-ed8045158182)

- Observe that paginated response is received.
![pagi-2](https://github.com/raghavendrashetty93/mule-simple-pagination-implementation/assets/77000179/a83ec979-4ee2-437b-af80-e1a56738b18e)


