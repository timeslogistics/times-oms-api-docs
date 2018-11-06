ASNs
========

Create ASN
--------------

Create ASN [POST /asns]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Postman Collections: https://www.getpostman.com/collections/3120f45724992dcc5913

+ Parameters
    + consigneeCompanyName: (string, optional) -
    + consigneeContactName: (string, optional) -
    + consigneePhone: (string, required) -
    + consigneeAddress: (string, optional) -
    + consigneeSubdistrict: (string, required) -
    + consigneeDistrict: (string, required) -
    + consigneeProvince: (string, required) -
    + consigneeCountry: (string, required) - Full name of Consignee Country in English (Thailand, Taiwan, etc)
    + consigneeCompanyNameLocale: (string, optional) - In Destination official language
    + consigneeContactNameLocale: (string, required) - In Destination official language
    + consigneeIdCardNumber: (string, optional/required) - Consignee ID card number. 如目的地为中国台湾, 总货价大或等於3000当地货币必须
    + consigneeAddressLocale: (string, required) - In Destination official language
    + consigneePostalCode: (string, required) -
    + shipperCompanyName: (string, required) -
    + shipperContactName: (string, required) -
    + shipperPhone: (string, required) -
    + shipperAddress: (string, required) -
    + shipperSubdistrict: (string, required) -
    + shipperDistrict: (string, required) -
    + shipperProvince: (string, required) -
    + shipperCountry: (string, required) -
    + shipperPostalCode: (string, required) -
    + paymentMethod: (string, required) -
    + productType: (string, optional) -
    + shipmentType: (string, optional) -
    + salePlatformName: (string, required) -
    + referenceNumber: (string, required) - Unique per parcel
    + items[]: (array, required) - Array of items
    + items[][sku]: (string, required) -
    + items[][categoryId]: (string, optional/required) - 
    + items[][categoryName]: (string, optional/required) - 
    + items[][description]: (string, required) -
    + items[][specification]: (string, optional) -
    + items[][descriptionOriginal]: (string, optional) - Description in Origin offical language
    + items[][specificationOriginal]: (string, optional) - Specification in Origin official language
    + items[][brand]: (string, optional/required) - Required if shipmentType is "Mobile & Tablet"
    + items[][model]: (string, optional/required) - Required if shipmentType is "Mobile & Tablet"
    + items[][pieces]: (integer, required) - 
    + items[][unitPrice]: (decimal, required) - Price per unit (DO NOT times pieces)
    + items[][unitPriceCurrency]: (string, required) - ISO 4217 Code
    + items[][CODValue]: (decimal, optional/required) - Total COD value (pieces * cod unit price), required if paymentMethod = COD


Request (application/json)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Body (Example)
"""""""""""""""""

.. code-block:: json

      {
        "consigneeCompanyName": "Supachai Piamthong",
        "consigneeContactName": "Supachai Piamthong",
        "consigneePhone": "123456789",
        "consigneeAddress": "12 34 Moo 8 Chom Bueng Ratchaburi Ratchaburi Chom Bueng 70150",
        "consigneeSubdistrict":"ท่ายาง",
        "consigneeDistrict":"เมืองพิษณุโลก",
        "consigneeProvince":"Bangkok",
        "consigneeCountry": "Thailand",
        "consigneePostalCode": "70150",
        "consigneeCompanyNameLocale": "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07",
        "consigneeContactNameLocale": "\u0e28\u0e38\u0e20\u0e0a\u0e31\u0e22  \u0e40\u0e1b\u0e35\u0e48\u0e22\u0e21\u0e17\u0e2d\u0e07",
        "consigneeAddressLocale": "90 100 \u0e21 8 \u0e15 \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  \u0e23\u0e32\u0e0a\u0e1a\u0e38\u0e23\u0e35  Ratchaburi \u0e08\u0e2d\u0e21\u0e1a\u0e36\u0e07  Chom Bueng 70150",
        "shipperCompanyName": "ABC",
        "shipperContactName": "DEF",
        "shipperPhone": "(501) 123-4567",
        "shipperAddress": "Room 1, HaoQuan Building, 1st Jichangdongmen Road Jingtai Street, Baiyun District, Guangzhou province, China",
        "shipperSubdistrict":"Baoan",
        "shipperDistrict":"Shenzheng",
        "shipperProvince":"Guangdong",
        "shipperCountry": "China",
        "shipperPostalCode": "000000",
        "paymentMethod": "COD",
        "productType": "Express",
        "shipmentType": "Mobile & Tablet",
        "salePlatformName": "Amazon",
        "referenceNumber": "PTK0000156852",
        "items": [
            {
                 "sku": "sku-test-1234567890",
                 "categoryId": "ASQW987654",
                 "categoryName": "Mobile",
                 "description": "Apple new iphone 7 red 128g unlocked",
                 "brand": "Apple",
                 "model": "iphone 7",
                 "pieces": "2",
                 "unitPrice": "387",
                 "unitPriceCurrency": "THB",
                 "CODValue": "774"
            },
            {
                 "sku": "sku-test-9876543210",
                 "categoryId": "WERT987654",
                 "categoryName": "Mobile",
                 "description": "Xiaomu note 3 64gb",
                 "brand": "XiaoMu",
                 "model": "note 3",
                 "pieces": "1",
                 "unitPrice": "856",
                 "unitPriceCurrency": "THB",
                 "CODValue": "856"
            }
        ]
      }


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
