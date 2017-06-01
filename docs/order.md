========
Order
========

# Order API [/order]

## Create order [POST /order]


+ Parameters
    + trackingNumber: (string, required) - 
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
    + parcelValue: (string, required) - 
    + paymentMethod: (string, required) - 
    + shipmentType: (string, required) - 
    + referenceNumber: (string, required) - 
    + sortCode: (string, optional) - Specify sort code manually, required if items.categoryId and categoryName are not specified
    + items[]: (array, required) - Array of items
    + items[][categoryId]: (string, optional) - Required if sort code is not specified
    + items[][categoryName]: (string, optional) - Required if sort code is not specified
    + items[][description]: (string, required) - 
    + items[][pieces]: (string, required) - 
    + items[][unitPrice]: (string, required) - 
    + items[][unitPriceCurrency]: (string, required) - ISO 4217 Code

+ Request (application/x-www-form-urlencoded)
    + Body

            trackingNumber=MTK00000001&consigneeCompanyName=foo&... (HTTP POST variables)

+ Response 201 (application/json)
    + Body

            {
                "message": "Success"
            }

+ Response 409 (application/json)
    + Body

            {
                "message": "Order already exist"
            }

+ Response 412 (application/json)
    + Body

            {
                "message": "Invalid parameter"
            }

+ Response 428 (application/json)
    + Body

            {
                "message": "Missing parameter"
            }

## Get order [GET /order/{trackingNumber}]


+ Parameters
    + trackingNumber: (string, required) - Tracking Number

+ Response 200 (application/json)
    + Body

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
    + Body

            {
                "message": "Order not found"
            }
