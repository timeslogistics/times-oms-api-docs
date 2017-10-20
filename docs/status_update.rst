Status Update
=============

Order Status Update
-------------------

+ HTTP POST Parameters
    + tracking_number: (string, always present)
    + reference_number: (string, always present)
    + upload: (datetime, maybe empty)
    + inbound: (datetime, maybe empty)
    + outbound: (datetime, maybe empty)
    + handover_linehaul: (datetime, maybe empty)
    + delivering: (datetime, maybe empty)
    + pending: (datetime, maybe empty)
    + pending_reason: (string, maybe empty)
    + reject: (datetime, maybe empty)
    + reject_reason: (string, maybe empty)
    + return: (datetime, maybe empty)
    + receive: (datetime, maybe empty)

.. code-block:: text

  POST /webhook/status HTTP/1.1
  Host: your-server.com
  Authorization: Bearer piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc

  tracking_number=MTK00000001&reference_number=ABC123456789&upload=2017-01-01+00%3A00%3A00&inbound=2017-01-01+01%3A00%3A00&outbound=2017-01-01+02%3A00%3A00&close_box=2017-01-01+03%3A00%3A00&receive=2017-01-01+03%3A00%3A00
