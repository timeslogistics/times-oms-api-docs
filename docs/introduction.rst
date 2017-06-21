Introduction
============

Specification
-------------

Times OMS API implements REST API interface.

All endpoints accept HTTP POST variables as input, and JSON as output.

All operations use standard HTTP verbs (GET, POST, PATCH, PUT, DELETE) and all response use HTTP status codes.

Example verbs::

    GET /orders/MTK00000001            # Get Order Detail
    POST /orders                       # Create an Order
    PUT /orders/MTK00000001            # Replace an Order
    PATCH /orders/MTK00000001          # Update an Order
    DELETE /orders/MTK00000001         # Delete an Order

* For example only, not all API are implemented

Common Status Code::

    200 - Okay / Query success, please check the response
    201 - Created / Order created
    401 - Unauthorized / Token missing or invalid
    403 - Forbidden / Operation not permited
    404 - Not Found / Order is not found
    409 - Conflict / Order already exist
    412 - Precondition Failed / Invalid parameter, check response message for reason
    428 - Precondition Required / Missing parameter, check response message for reason

* For detailed status code explanations, please refer to http://www.restapitutorial.com/httpstatuscodes.html

* All Key words ("MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL") in this document follows RFC2119 recommandations (https://tools.ietf.org/html/rfc2119).

Client Implementation
---------------------
The API is language independent.

While this document provides PHP and Java sample code.

Any client/library that can correctly handle `Authorization` HTTP header and HTTP verbs can be used.

Libraries used in sample code:

* PHP: Guzzle - http://guzzlephp.org/
* Java: Okhttp - http://square.github.io/okhttp/
* Java: org.json - https://mvnrepository.com/artifact/org.json/json
