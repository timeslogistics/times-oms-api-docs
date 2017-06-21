Verification
============

Specification
-------------

A "Webhook Secret" is sent along with all API requests.

You SHOULD verify the HTTP requests before performing any actions with the data received.

Please note than "Webhook Secret" is different from "API Token" used in Endpoints.

Obtaining Webhook Secret
------------------------

The Webhook Secret can be obtained in Times OMS, or provide by IT department of Times E-commerce.

Resetting Webhook Secret
------------------------

If you believe that your Webhook Secret is leaked, you can request a reset in Times OMS.

After reset, a new Webhook Secret will be issued and the old Webhook Secret is intermediately invalidated.

Webhook Secret Lifetime
-----------------------

Webhook Secret never expire unless being reset.
