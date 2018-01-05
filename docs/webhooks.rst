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

Country Change
==============

Sample of Country Change:

.. code-block:: javascript

  { "time":                  "2018-01-01 01:23:45",
    "imsi":                  "238731234567890",
    "imei":                  "1234567890987654",
    "type":                  "cs",
    "country_code":          "dk",
    "country_code_previous": "de" }

XDR
===

Sample of Voice Data Record:

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "type":         "voice",
    "operation":    "finalize",
    "billid":       "1234567890-1234",
    "direction":    "incoming",
    "error":        null,
    "status":       "answered",
    "caller":       "4512345678",
    "called":       "4587654321",
    "duration":     "30",
    "billtime":     "20",
    "ringtime":     "10",
    "imsi":         "238731234567890",
    "country_code": "dk" }

Sample of SMS Data Record:

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "type":         "sms",
    "billid":       "1234567890-1234",
    "direction":    "incoming",
    "error":        null,
    "to":           "4512345678",
    "from":         "4587654321",
    "retries":      "0",
    "imsi":         "238731234567890",
    "country_code": "dk" }

Sample of Data Data Record (yes, we know it's a pleonasm):

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "type":         "data",
    "operation":    "finalize",
    "billid":       "1234567890-1234",
    "download":     "0",
    "upload":       "0",
    "imsi":         "238731234567890",
    "country_code": "dk" }

Receive SMS
===========

Sample of incoming SMS:

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "billid":       "1234567890-1234",
    "to":           "4512345678",
    "from":         "4587654321",
    "text":         "Hello, World!",
    "imsi":         "238731234567890",
    "country_code": "dk" }
