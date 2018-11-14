Inventories
========

Obtain inventories
-----------

Obtain inventory [GET /inventories]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


+ Request Parameters
    + client_code: (string, required, 64) - Client code of client to be checked (provided by Times)
    + project_code: (string, optional, 64) - Project code of specific client to be checked (provided by Times)
    + warehouse_code: (string, required, 64) - Warehouse code (provided by Times)
    + sku: (string, optional, 128) - SKU
    
+ Response Parameters
    + result: (string, required, 16) - "success" or "fail"
    + message: (string, required, 128) - Message about fail condition, eg. "warehouse_code not found", "client_code not found"
    + inventories[]: (array, required) - Array of contents
    + inventories[][client_code]: (string, required, 64) - Client Code
    + inventories[][project_code]: (string, optional, 64) - Project code
    + inventories[][warehouse_code]: (string, required, 64) - Warehouse code
    + inventories[][sku]: (string, required, 128) - SKU
    + inventories[][quantity]: (int, required, 64) - Total in stock quantity, allocated + non allocated quantity
    + inventories[][allocated_quantity]: (int, required, 64) - Allocated quantity
    + inventories[][non_allocated_quantity]: (int, required, 64) - Non allocated quantity, called available quantity as well
    + inventories[][uom]: (string, required, 64) - Unit of measure
    + inventories[][expiry_date]: (string, required, 64) - Expiry date in "YYYY-mm-dd" format
    
    
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

Response 404 (application/json)
""""""""""""""""""""""""""""""""""

Client not found

.. code-block:: json

            {
                "result": "fail",
                "message": "client_code not found",
                "status_code": 404
            }
            

Warehouse not found

.. code-block:: json

            {
                "result": "fail",
                "message": "warehouse_code not found",
                "status_code": 404
            }

Response 500 (application/json)
"""""""""""""""""""""""""""""""""""

Server internal error

.. code-block:: json

            {
                "result": "fail",
                "message": "server error",
                "status_code": 500
            }
