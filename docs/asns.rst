ASNs
========

Create ASN
--------------

Create ASN [POST /asns]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Postman Collections: https://www.getpostman.com/collections/3120f45724992dcc5913

+ Request Parameters
    + client_code: (string, required, 64) - Client code of client to be checked (provided by Times)
    + project_code: (string, optional, 64) - Project code of specific client to be checked (provided by Times)
    + warehouse_code: (string, required, 64) - Warehouse code (provided by Times)
    + asns[]: (array, required) - Array of contents
    + asns[][sku]: (string, required, 128) - SKU
    + asns[][quantity]: (int, required, 64) - Estimated quantity of SKU to be inbounded
    + asns[][uom]: (string, required, 64) - Unit of measure
    + asns[][expiry_date]: (string, optional, 64) - Expiry date in "YYYY-mm-dd" format
    
+ Response Parameters
    + result: (string, required, 16) - "success" or "fail"
    + message: (string, required, 128) - Message about fail condition, eg. "warehouse_code not found", "client_code not found"
    + asn_number: (string, required, 128) - ASN Number
    
    
Request (application/json)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Body (Example)
"""""""""""""""""

.. code-block:: json

            {
                "client_code": "101",
                "project_code": "1201",
                "warehouse_code": "1",
                "sku": "HGY-783612"
            }

Response 200 (application/json)
""""""""""""""""""""""""""""""""""

.. code-block:: json

    {
        "result": "success",
        "message": "success",
        "inventories": [
            {
                "client_code": "101",
                "project_code": "1201",
                "warehouse_code": "1",
                "sku": "HGY-783612",
                "quantity": "150",
                "allocated_quantity": "30",
                "non_allocated_quantity": "120",
                "uom": "cartons",
                "expiry_date": "2018-10-22"
            },
            {
                "client_code": "101",
                "project_code": "1201",
                "warehouse_code": "1",
                "sku": "HGY-783612",
                "quantity": "100",
                "allocated_quantity": "50",
                "non_allocated_quantity": "50",
                "uom": "cartons",
                "expiry_date": "2018-12-22"
            }
        ]
    }


Response 409 (application/json)
""""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "message": "Order already exist",
                "status_code": 409,
                "remarks": {
                    "trackingNumber": "TN123456789",
                    "sortCode": "SC1234"
                }
            }

Response 412 (application/json)
""""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "message": "Order already exist or invalid parameters",
                "status_code": 412,
                "remarks": {
                    "trackingNumber": "TN123456789",
                    "sortCode": "SC1234"
                }
            }

Response 428 (application/json)
""""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "message": "Missing parameter",
                "status_code": 428
            }


Get ASNs
-----------

Get ASNs [GET /asns/{asnNumber}]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Response 200 (application/json)
""""""""""""""""""""""""""""""""""

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
                    "handover_lastmile": null,
                    "delivering": null,
                    "pending": null,
                    "pending_reason": null,
                    "reject": null,
                    "reject_reason": null,
                    "return": null,
                    "receive": null
                }
            }

Response 404 (application/json)
""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "message": "Order not found",
                "status_code": 404
            }
