Authenticatation
================

Specification
-------------

As an REST API, there are not any session state stored on the server side.

A "Token" must be supplied in every request in HTTP request header.

Obtaining API Token
-------------------

The API token can be obtained in TEC Client Platform,

or provide by IT department of Times E-commerce.

Resetting API Token
-------------------

If you believe your API token is leaked, you can request an reset of token in TEC Client Platform.

After reset, a new token will be issued and the old token is intermediately invalidated.

Token Lifetime
--------------

The token never expire unless being reset.

Example
-------

Bare Minimal HTTP Request::

    GET /api/order/MTK00000001 HTTP/1.1
    Host: client-platform.indzz.net
    Authorization: Bearer piAOLkaYYBdscIv5YxsrYuiuFH7vwC231YlJ4kivW43iFJMp59blGLJGysKc
