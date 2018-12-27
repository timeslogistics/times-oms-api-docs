Items
========

Create Item Master
--------------

Create Item Master [POST /items/create]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


+ Request Parameters
    + client_code: (string, required, 64) - Client code of client to be checked (provided by Times)
    + project_code: (string, optional, 64) - Project code of specific client to be checked (provided by Times)
    + warehouse_code: (string, required, 64) - Warehouse code (provided by Times)
    + asn_number: (string, required, 128) - ASN Number
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
                "asn_number": "CU-ASN-20180411001",
                "asns": [
                    {
                        "sku": "HGY-783612",
                        "quantity": "150",
                        "uom": "cartons",
                        "expiry_date": "2018-10-22"
                    },
                    {
                        "sku": "HGY-783612",
                        "quantity": "100",
                        "uom": "cartons",
                        "expiry_date": "2018-12-22"
                    }
                ]
            }

Response 200 (application/json)
""""""""""""""""""""""""""""""""""

.. code-block:: json

    {
        "result": "success",
        "message": "success",
        "asn_number": "CU-ASN-20180411001"
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


