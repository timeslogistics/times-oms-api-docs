Authentication
================

Specification
-------------

As a REST API, no any session state is stored on the server side.

A "Token" MUST be supplied in every request in HTTP request header.

Please note than "API Token" is different from "Webhook Secret" used in Webhooks.

Obtaining API Token
-------------------

The API token can be obtained in Times OMS, or provide by IT department of Times E-commerce.

Resetting API Token
-------------------

If you believe that your API token is leaked, you can request token reset in Times OMS.

After reset, a new token will be issued and the old token is immediately invalidated.

Token Lifetime
--------------

Token never expire unless being reset.

Example Token Usage
-------------------

Bare Minimal HTTP Request for API Token piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc::

    GET /api/orders/MTK00000001 HTTP/1.1
    Authorization: Bearer piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc
