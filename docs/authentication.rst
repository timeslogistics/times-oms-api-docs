Authenticatation
================

Specification
-------------

As a REST API, no any session state is stored on the server side.

A "Token" MUST be supplied in every request in HTTP request header.

Obtaining API Token
-------------------

The API token can be obtained in TEC Client Platform, or provide by IT department of Times E-commerce.

Resetting API Token
-------------------

If you believe that your API token is leaked, you can request token reset in TEC Client Platform.

After reset, a new token will be issued and the old token is intermediately invalidated.

Token Lifetime
--------------

Token never expire unless being reset.

Example Token Usage
-------------------

Bare Minimal HTTP Request::

    GET /api/order/MTK00000001 HTTP/1.0
    Authorization: Bearer piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc
