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
    + consigneeCompanyNameLocale: (string, optional/required) - Required for TH/PH
    + consigneeContactNameLocale: (string, optional/required) - Required for TH/PH
    + consigneeAddressLocale: (string, optional/required) - Required for TH/PH
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
    + items[][sku]: (string, optional) -
    + items[][categoryId]: (string, optional/required) - Required if sort code is not specified
    + items[][categoryName]: (string, optional/required) - Required if sort code is not specified
    + items[][description]: (string, required) -
    + items[][pieces]: (integer, required) -
    + items[][unitPrice]: (decimal, required) -
    + items[][unitPriceCurrency]: (string, required) - ISO 4217 Code
    + items[][codValue]: (decimal, optional/required) - Single SKU COD value (pieces * cod unit price), required if paymentMethod = COD

+ Request (application/json)

Body (Example)::

      {
        "consigneeCompanyName":"Supachai Piamthong",
        "consigneeContactName":"Supachai Piamthong",
        "consigneePhone":"0899024444",
        "consigneeAddress":"90 100 Moo 8 Chom Bueng Ratchaburi Ratchaburi Chom Bueng 70150",
        "consigneeCountry":"Thailand",
        "consigneePostalCode":"70150",
        "consigneeCompanyNameLocale":"\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07",
        "consigneeContactNameLocale":"\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07",
        "consigneeAddressLocale":"90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150",
        "consigneeDistrict":"Bangkok",
        "shipperCompanyName":"ABC",
        "shipperContactName":"Gilbert",
        "shipperPhone":"(501) 328-3428",
        "shipperAddress":"Room 57, HaoQuan Building, 1st Jichangdongmen Road Jingtai Street, Baiyun District，Guangzhou province，China",
        "shipperCountry":"China",
        "shipperPostalCode":"N/A",
        "paymentMethod":"COD",
        "parcelValue":387,
        "CODValue":"387",
        "productType":"Express",
        "shipmentUploadDate":"2017-03-09 14:37:45",
        "referenceNumber":"PTK0000156852",
        "shipmentType":"General Shipment",
        "salePlatformName":"Amazon",
        "instruction":"",
        "sortCode":"",
        "items":[
            {
                 "sku": "sku-test-1234567890",
                 "categoryId":"category-motors-automotive-car-care-interior-care",
                 "categoryName":"Motors/Automotive/Car Care/Interior Care",
                 "description":"New Turn Signal Cruise Control Switch 84632 34011 For Toyota Camry Corolla Lexus",
                 "pieces":1,
                 "unitPrice":387,
                 "unitPriceCurrency":"THB"
            }
        ]
      }


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
