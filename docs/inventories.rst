Inventories
========

Get inventories
-----------

Get inventory [GET /inventories/{clientCode}]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Response 200 (application/json)
""""""""""""""""""""""""""""""""""

.. code-block:: json

            {
                "result": "success",
                "message": "",
                "inventories": {
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
                "result": "fail",
                "message": "Order not found",
                "status_code": 404
            }
            

Client not found

.. code-block:: json

            {"status":1,"message":"Order not found"}
