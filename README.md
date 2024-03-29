# American Flights System API (Demo)
Welcome to the American Flights System API documentation. This API allows you to interact with a collection of flights, providing functionalities to retrieve a list of flights, create new flights, access details for specific flights and delete the flight.

## Demo Disclaimer
This API is a demo created for educational purposes and is associated with a blog post. It is not representing a fully functional or production-ready system. Please refer to the [blog post](https://productdock.com/exploring-the-future-of-integration-a-developers-dive-into-anypoint-code-builder-beta/) for insights into the concepts and use cases demonstrated by this API.

## To test the API
Explore the functionality through the user-friendly public portal:
- [API Developer Portal](https://anypoint.mulesoft.com/exchange/portals/productdock-48/)

The API is secured using Basic Authentication. Feel free to use any string as both the username and password when interacting with the Mocking Service.

<br>

# Endpoints
### Get Flights
**Endpoint**: `/flights`  
**Method**: `GET`  
**Description**: Retrieve a list of flights based on optional query parameters.  
**Query Parameters**:
- `destination` (optional): Filter flights by destination. Valid values: 'SFO', 'LAX', 'CLE'.  

**Response**:
- Status Code: 200 OK
- Content Type: application/json
- Body: Array of AmericanFlight objects
- Example:
  ```
  [
    {
      "ID": 1,
      "code": "rree0001",
      "price": 541.99,
      "departureDate": "2023-12-20",
      "origin": "MUA",
      "destination": "LAX",
      "emptySeats": 0,
      "plane": {
        "type": "Boeing 787",
        "totalSeats": 200
      }
    },
    {
      "ID": 2,
      "code": "eefd0123",
      "price": 300.99,
      "departureDate": "2023-12-20",
      "origin": "MUA",
      "destination": "CLE",
      "emptySeats": 7,
      "plane": {
        "type": "Boeing 747",
        "totalSeats": 345
      }
    }
  ]
  ```

### Create Flight
**Endpoint**: `/flights`  
**Method**: `POST`  
**Description**: Create a new flight.  
**Request Body**:
- Content Type: application/json
- Body: AmericanFlight object
- Example: 
  ```
  {
    "code": "rree0001",
    "price": 541.99,
    "departureDate": "2023-12-20",
    "origin": "MUA",
    "destination": "LAX",
    "emptySeats": 0,
    "plane": {
      "type": "Boeing 787",
      "totalSeats": 200
    }
  }
  ```

**Response**:
- Status Code: 201 Created
- Content Type: application/json
- Body: Message indicating the successful creation of the flight
- Example: `{ "message": "Flight successfully created" }`

### Get Flight by ID
**Endpoint**: `/flights/{ID}`  
**Method**: `GET`  
**Description**: Retrieve details for a specific flight identified by its unique ID.  
**Path Parameter**:
- `ID` (required): Unique identifier for the flight.

**Response**:
- Status Code: 200 OK
- Content Type: application/json
- Body: AmericanFlight object
- Example: 
  ```
  {
    "ID": 1,
    "code": "rree0001",
    "price": 541.99,
    "departureDate": "2023-12-20",
    "origin": "MUA",
    "destination": "LAX",
    "emptySeats": 0,
    "plane": {
      "type": "Boeing 787",
      "totalSeats": 200
    }
  }
  ```

### Delete Flight by ID
**Endpoint**: `/flights/{ID}`  
**Method**: `DELETE`  
**Description**: Delete a specific flight identified by its unique ID.  
**Path Parameter**:
- `ID` (required): Unique identifier for the flight.

**Response**:
- Status Code: 200 OK
- Content Type: application/json
- Body: Message indicating the successful deletion of the flight
- Example: `{ "message": "Flight successfully deleted" }`
<br><br>

# Error Handling
Every endpoint can throw some of those errors. Please make sure to handle errors appropriately in your client application.
```
  400:
      body:
          application/json:
              example: {"error": "Bad Request"}
  401:
      body:
          application/json:
              example: {"error": "Invalid Client"}
  404:
      body:
          application/json:
              example: {"error": "Resource not found"}
  405:
      body:
          application/json:
              example: {"error": "Method not allowed"}
  406:
      body:
          application/json:
              example: {"error": "Not acceptable"}
  415:
      body:
          application/json:
              example: {"error": "Unsuporrted media type"}
  429:
      body:
          application/json:
              example: {"error": "Quota has been exceeded"}
  500:
      body:
          application/json:
              example: {"error": "Internal server error"}
  501:
      body:
          application/json:
              example: {"error": "Not implemented"}
```
<brb><br>
Feel free to explore the API and use the provided examples to understand how to interact with each endpoint. If you have any questions or issues, please refer to the API documentation or contact the API maintainers.

# Licence
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
