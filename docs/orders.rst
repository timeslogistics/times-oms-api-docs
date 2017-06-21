Orders
======

Create order [POST /orders/{trackingNumber}]
--------------------------------------------

+ Parameters
    + consigneeCompanyName: (string, required) -
    + consigneeContactName: (string, required) -
    + consigneePhone: (string, required) -
    + consigneeAddress: (string, required) -
    + consigneeCountry: (string, required) - 
    + consigneePostalCode: (string, required) -
    + shipperCompanyName: (string, required) -
    + shipperContactName: (string, required) -
    + shipperPhone: (string, required) -
    + shipperAddress: (string, required) -
    + shipperCountry: (string, required) - 
    + shipperPostalCode: (string, required) -
    + parcelValue: (decimal, required) -
    + paymentMethod: (string, required) -
    + shipmentType: (string, required) -
    + containBattery: (boolean, required) - Possible values: [1/0]
    + referenceNumber: (string, optional) -
    + instruction: (string, optional) - Possible values: [UNPACK], UNPACK indicates this parcel need to be unpacked to scan parcels inside
    + sortCode: (string, optional/required) - Specify sort code manually, required if both items.categoryId and items.categoryName are not provided
    + items[]: (array, required) - Array of items
    + items[][categoryId]: (string, optional/required) - Required if sort code is not specified
    + items[][categoryName]: (string, optional/required) - Required if sort code is not specified
    + items[][description]: (string, required) -
    + items[][pieces]: (integer, required) -
    + items[][unitPrice]: (decimal, required) -
    + items[][unitPriceCurrency]: (string, required) - ISO 4217 Code

+ Request (application/x-www-form-urlencoded)

Body::

          consigneeCompanyName=foo&... (HTTP POST variables)


+ Response 201 (application/json)

.. code-block:: json

            {
                "message": "Success"
            }


+ Response 409 (application/json)

.. code-block:: json

            {
                "message": "Order already exist"
            }

+ Response 412 (application/json)

.. code-block:: json

            {
                "message": "Invalid parameter"
            }

+ Response 428 (application/json)

.. code-block:: json

            {
                "message": "Missing parameter"
            }


Get order [GET /orders/{trackingNumber}]
----------------------------------------

+ Response 200 (application/json)

.. code-block:: json

            {
                "trackingNumber": "MTK00000001",
                "milestones": {
                    "upload": "2017-01-01 00:00:00",
                    "inbound": "2017-01-01 01:00:00",
                    "outbound": "2017-01-01 02:00:00",
                    "close_box": "2017-01-01 03:00:00",
                    "handover_linehaul": null,
                    "pickup": null,
                    "export": null,
                    "uplift": null,
                    "import": null,
                    "handover_lastmile": null
                }
            }

+ Response 404 (application/json)

.. code-block:: json

            {
                "message": "Order not found"
            }
