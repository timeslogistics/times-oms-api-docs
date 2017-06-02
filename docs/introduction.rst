Introduction
============

Specification
-------------

TEC Client API implements REST API interface.

All endpoints accept HTTP POST variables as input, and JSON as output.

All operations use standard HTTP verbs (GET, POST, PATCH, PUT, DELETE) and all response use HTTP status codes.

Example verbs::

    GET /order/MTK00000001            # Get Order Detail
    POST /order                       # Create an Order
    PUT /order/MTK00000001            # Replace an Order
    PATCH /order/MTK00000001          # Update an Order
    DELETE /order/MTK00000001         # Delete an Order

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

Client Implementation
---------------------
The API is language independent.

While this document provides PHP and Java sample code.

Any client/library that can correctly handle `Authorization` HTTP header and HTTP verbs can be used.

Recommended Libraries:

* PHP: Guzzle - http://guzzlephp.org/
* Java: Okhttp - http://square.github.io/okhttp/
