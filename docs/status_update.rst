Status Update API Webhooks
==========================

Order Status Update
-------------------

+ HTTP POST Parameters
    + tracking_number: (string, always present)
    + upload: (datetime, maybe empty)
    + inbound: (datetime, maybe empty)
    + outbound: (datetime, maybe empty)
    + handover_linehaul: (datetime, maybe empty)

.. code-block:: text

  POST /webhook/status HTTP/1.1
  Host: your-server.com
  Authorization: Bearer piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc

  tracking_number=MTK00000001&upload=2017-01-01 00:00:00&inbound=2017-01-01 01:00:00&outbound=2017-01-01 02:00:00&close_box=2017-01-01 03:00:00&handover_linehaul=
