API Endpoints API Webhooks
==========================

API Endpoints
-------------

API Endpoins are used from your server to TEC servers and can be used to Search, Create, Update or Delete data.

Authentication MUST be provided to invoke API Endpoint calls.

API Webhooks
------------

API Webhooks are automated calls from TEC servers to your server triggered when a specific event happened.

For example, an order status update and you want to know about it in real time.

You MAY register a webhook url in our system, so we can make a HTTP POST requests to "push" data to your server.

You SHOULD validate HTTP requests before doing any actions with the data received.

While we support both HTTP/HTTPS urls for webhook, HTTPS is RECOMMENDED for better security.
