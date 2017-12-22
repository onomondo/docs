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

  POST /cdr
  Host: www.example.com
  Content-Type: application/json
  Authorization: OUR-API-KEY

The webhooks is served over HTTPS. To ensure data privacy, unencrypted HTTP is not supported.

Location Update
===============

Sample of Location Update:

.. code-block:: javascript

  { "time":                  "2018-01-01 01:23:45",
    "imsi":                  "238731234567890",
    "imei":                  "1234567890987654",
    "type":                  "cs",
    "country_code":          "dk",
    "country_code_previous": "de" }

CDR
===

Sample of CDR:

.. code-block:: javascript

  { "time":         "2018-01-01 01:23:45",
    "type":         "voice",
    "operation":    "finalize",
    "billid":       "1234567890-1234",
    "direction":    "incoming",
    "reason":       null,
    "status":       "answered",
    "caller":       "4512345678",
    "called":       "4587654321",
    "duration":     "30",
    "billtime":     "20",
    "ringtime":     "10",
    "retries":      "0",
    "imsi":         "238731234567890",
    "download":     "0",
    "upload":       "0",
    "country_code": "dk" }

Receive SMS
===========

Sample of incoming SMS:

.. code-block:: javascript

  TODO
