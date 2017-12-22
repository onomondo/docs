===
API
===

General Info
============

The API is a HTTP RESTful API based around resource oriented URLs. It uses standard HTTP verbs and returns JSON on all requests.

Base URL
--------

All URLs referenced in the documentation have the following base:

::

  https://api.onomondo.com

The API is served over HTTPS. To ensure data privacy, unencrypted HTTP is not supported.

Authentication
--------------

HTTP requests to the API are protected with API key authentication.

In short, you will use your API key in the Authorization header.

Sample Call in NodeJS Request:

.. code-block:: javascript

  var request = require("request");

  var options = {
    method: "GET",
    url:    "/",
    headers:
      { Authorization: "YOUR-API-KEY" }
  };

  request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
  });

Retrieve SIM
============

- Method

  ::

    GET

- URL

  ::

    /sim/:imsi

  OR

  ::

    /sim/:msisdn

- URL Params

  ========= ========================
  Parameter Description
  ========= ========================
  imsi      15 digit IMSI of the SIM
  ========= ========================

  OR

  ========= ==========================================
  Parameter Description
  ========= ==========================================
  msisdn    Phone number in international E.164 format
  ========= ==========================================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "imsi":          "238731234567890",
               "msisdn":        "4512345678",
               "cs":            true,
               "ps":            true,
               "eps":           true,
               "cs_roaming":    true,
               "ps_roaming":    true,
               "ps_throttling": false }

- Error Codes

  ==== ==============
  Code Error
  ==== ==============
  400  imsi_invalid
  400  msisdn_invalid
  403  imsi_forbidden
  404  sim_not_found
  ==== ==============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method: "GET",
      url:    "/sim/4512345678",
      headers:
        { Authorization: "YOUR-API-KEY" }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Create SIM
==========

- Method

  ::

    POST

- URL

  ::

    /sim/:imsi

  OR

  ::

    /sim/:msisdn

- URL Params

  ========= ========================
  Parameter Description
  ========= ========================
  imsi      15 digit IMSI of the SIM
  ========= ========================

  OR

  ========= ==========================================
  Parameter Description
  ========= ==========================================
  msisdn    Phone number in international E.164 format
  ========= ==========================================

- Data Params

  ============= ============= ======= ================================================================
  Parameter     Required      Default Description
  ============= ============= ======= ================================================================
  imsi          * (or msisdn)         15 digit IMSI of the SIM
  msisdn        * (or imsi)           Phone number in international E.164 format
  cs                          true    Boolean to enable/disable circuit switching (calls/SMS over GSM)
  ps                          true    Boolean to enable/disable packet switching (data over GPRS/EDGE)
  eps                         true    Boolean to enable/disable evolved packet system (data over LTE)
  cs_roaming                  false   Boolean to enable/disable circuit switching roaming
  ps_roaming                  false   Boolean to enable/disable packet switching roaming
  ps_throttling               false   Boolean to enable/disable packet switching bandwidth throttling
  ============= ============= ======= ================================================================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== =========================
  Code Error
  ==== =========================
  400  imsi_invalid
  400  msisdn_invalid
  400  cs_invalid
  400  ps_invalid
  400  eps_invalid
  400  cs_roaming_invalid
  400  ps_roaming_invalid
  400  ps_throttling_invalid
  403  imsi_forbidden
  404  imsi_not_found
  409  imsi_conflict
  409  ps_ps_throttling_conflict
  ==== =========================

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method: "POST",
      url:    "/sim/4512345678",
      headers:
        { Authorization:  "YOUR-API-KEY",
          "content-type": "application/json" },
      form:
        { imsi:          "238731234567890",
          cs:            true,
          ps:            true,
          eps:           true,
          cs_roaming:    true,
          ps_roaming:    true,
          ps_throttling: false }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Update SIM
==========

- Method

  ::

    PUT

- URL

  ::

    /sim/:imsi

  OR

  ::

    /sim/:msisdn

- URL Params

  ========= ========================
  Parameter Description
  ========= ========================
  imsi      15 digit IMSI of the SIM
  ========= ========================

  OR

  ========= ==========================================
  Parameter Description
  ========= ==========================================
  msisdn    Phone number in international E.164 format
  ========= ==========================================

- Data Params

  ============= ================================================================
  Parameter     Description
  ============= ================================================================
  imsi          15 digit IMSI of the SIM
  msisdn        Phone number in international E.164 format
  cs            Boolean to enable/disable circuit switching (calls/SMS over GSM)
  ps            Boolean to enable/disable packet switching (data over GPRS/EDGE)
  eps           Boolean to enable/disable evolved packet system (data over LTE)
  cs_roaming    Boolean to enable/disable circuit switching roaming
  ps_roaming    Boolean to enable/disable packet switching roaming
  ps_throttling Boolean to enable/disable packet switching bandwidth throttling
  ============= ================================================================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== =========================
  Code Error
  ==== =========================
  400  imsi_invalid
  400  msisdn_invalid
  400  cs_invalid
  400  ps_invalid
  400  eps_invalid
  400  cs_roaming_invalid
  400  ps_roaming_invalid
  400  ps_throttling_invalid
  403  imsi_forbidden
  404  sim_not_found
  409  ps_ps_throttling_conflict
  ==== =========================

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method: "PUT",
      url:    "/sim/4512345678",
      headers:
        { Authorization:  "YOUR-API-KEY",
          "content-type": "application/json" },
      form:
        { imsi:          "238731234567890",
          cs:            true,
          ps:            true,
          eps:           true,
          cs_roaming:    true,
          ps_roaming:    true,
          ps_throttling: false }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Delete SIM
==========

- Method

  ::

    DELETE

- URL

  ::

    /sim/:imsi

  OR

  ::

    /sim/:msisdn

- URL Params

  ========= ========================
  Parameter Description
  ========= ========================
  imsi      15 digit IMSI of the SIM
  ========= ========================

  OR

  ========= ==========================================
  Parameter Description
  ========= ==========================================
  msisdn    Phone number in international E.164 format
  ========= ==========================================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== ==============
  Code Error
  ==== ==============
  400  imsi_invalid
  400  msisdn_invalid
  403  imsi_forbidden
  404  sim_not_found
  ==== ==============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method: "DELETE",
      url:    "/sim/4512345678",
      headers:
        { Authorization: "YOUR-API-KEY" }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Send SMS
========

- Method

  ::

    POST

- URL

  ::

    /sms/:to

- URL Params

  ========= ==========================================
  Parameter Description
  ========= ==========================================
  to        Phone number in international E.164 format
  ========= ==========================================

- Data Params

  ========= ======================
  Parameter Description
  ========= ======================
  from      An alphanumeric string
  text      Text in UTF-8 encoding
  ========= ======================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== ============
  Code Error
  ==== ============
  400  to_invalid
  400  from_invalid
  400  text_invalid
  ==== ============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method: "POST",
      url:    "/sms/4512345678",
      headers:
        { Authorization:  "YOUR-API-KEY",
          "content-type": "application/json" },
      form:
        { from: "Onomondo",
          text: "Hello World" }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });
