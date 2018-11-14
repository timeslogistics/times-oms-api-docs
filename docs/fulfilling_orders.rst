Fullfilling Orders
========

Create order
--------------

Create order (Without lastmile delivery tracking number) [POST /orders]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+ Parameters
    + client_code: (string, required, 64) - Client code of client to be checked (provided by Times)
    + project_code: (string, optional, 64) - Project code of specific client to be checked (provided by Times)
    + warehouse_code: (string, required, 64) - Warehouse code (provided by Times)
    + consignee_company_name: (string, optional, 64) -
    + consignee_contact_name: (string, optional, 64) -
    + consignee_phone: (string, required, 32) -
    + consignee_address: (string, optional, 255) -
    + consignee_subdistrict: (string, required, 128) -
    + consignee_district: (string, required, 128) -
    + consignee_province: (string, required, 128) -
    + consignee_country: (string, required, 128) - Full name of Consignee Country in English (Thailand, Taiwan, etc)
    + consignee_company_name_locale: (string, optional, 128) - In Destination official language
    + consignee_contact_name_locale: (string, required, 128) - In Destination official language
    + consignee_id_card_number: (string, optional/required, 128) - Consignee ID card number. For TW, required for total value > TWD 3000
    + consignee_address_locale: (string, required, 512) - In Destination official language
    + consignee_postal_code: (string, required, 32) -
    + shipper_company_name: (string, required, 128) -
    + shipper_contact_name: (string, required, 128) -
    + shipper_phone: (string, required, 32) -
    + shipper_address: (string, required, 255) -
    + shipper_subdistrict: (string, required, 128) -
    + shipper_district: (string, required, 128) -
    + shipper_province: (string, required, 128) -
    + shipper_country: (string, required, 128) -
    + shipper_postal_code: (string, required, 32) -
    + payment_method: (string, required, 128) -
    + product_type: (string, optional) -
    + shipment_type: (string, optional) -
    + lastmile_courier: (string, optional) - Default 'times', value provided by times BD
    + reference_number: (string, required) - Unique per parcel
    + items[]: (array, required) - Array of items
    + items[][sku]: (string, required) -
    + items[][category_id]: (string, optional/required) - 
    + items[][category_name]: (string, optional/required) - 
    + items[][description]: (string, required) -
    + items[][specification]: (string, optional) -
    + items[][description_original]: (string, optional) - Description in Origin offical language
    + items[][specification_original]: (string, optional) - Specification in Origin official language
    + items[][brand]: (string, optional/required) - Required if shipmentType is "Mobile & Tablet"
    + items[][model]: (string, optional/required) - Required if shipmentType is "Mobile & Tablet"
    + items[][pieces]: (integer, required) - 
    + items[][unit_price]: (decimal, required) - Price per unit (DO NOT times pieces)
    + items[][unit_price_currency]: (string, required) - ISO 4217 Code
    + items[][cod_value]: (decimal, optional/required) - Total COD value (pieces * cod unit price), required if paymentMethod = COD



Response 201 (application/json)
""""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "message": "Success",
                "trackingNumber": "TN123456789",
                "sortCode": "SC1234"
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


Get order
-----------

Get order [GET /orders/{trackingNumber}]
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

Track order
------------

Track order [GET /orders/track/{trackingNumber}]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Response 200 (application/json)
""""""""""""""""""""""""""""""""""

Order found

.. code-block:: json

            {
              "status": 0,
              "shipper_country": "China",
              "consignee_country": "Thailand",
              "results": [
                {
                  "type": "Pending Time",
                  "timestamp": "2017-09-25 14:18:00",
                  "message": "Delivery unsuccessful, pending for action"
                },
                {
                  "type": "Close Box Time",
                  "timestamp": "2017-09-13 05:46:10",
                  "message": null
                },
                {
                  "type": "Sort Out Time",
                  "timestamp": "2017-09-13 05:45:43",
                  "message": null
                },
                {
                  "type": "Sort In Time",
                  "timestamp": "2017-09-13 01:48:59",
                  "message": null
                },
                {
                  "type": "Upload Time",
                  "timestamp": "2017-09-11 10:05:30",
                  "message": null
                }
              ]
            }

Order not found

.. code-block:: json

            {"status":1,"message":"Order not found"}
