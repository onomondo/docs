========
Webhooks
========

General Info
============

The endpoints has 15 seconds to accept the event. If a success HTTP status code has not been returned within these 15 seconds, the event will be discarded.

Authentication
--------------

The webhooks authenticate against the endpoints using API key authentication:

.. code-block:: javascript

  POST /xdr
  Host: www.example.com
  Content-Type: application/json
  Authorization: OUR-API-KEY

The webhooks is served over HTTPS. To ensure data privacy, unencrypted HTTP is not supported.

XDR
===

Sample of Data Data Record (yes, we know it's a pleonasm):

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "bill_id":      "1234567890-1234",
    "sim_id":       "192837465",
    "country_code": "dk",
    "operation":    "finalize",
    "upload":       "0",
    "download":     "0" }

Country Change Approval
=======================

Sample of Country Change:

.. code-block:: javascript

  { "time":                  "2018-01-01 01:23:45",
    "sim_id":                "192837465",
    "imei":                  "1234567890987654",
    "type":                  "GSM",
    "country_code":          "dk",
    "country_code_previous": "de" }

Country Change
==============

Sample of Country Change:

.. code-block:: javascript

  { "time":                  "2018-01-01 01:23:45",
    "sim_id":                "192837465",
    "imei":                  "1234567890987654",
    "country_code":          "dk",
    "country_code_previous": "de" }
