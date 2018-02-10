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

In short, you will use your API key in the ``Authorization`` header.

Sample Call in NodeJS Request:

.. code-block:: javascript

  var request = require("request");

  var options = {
    method:  "GET",
    url:     "/",
    headers: { Authorization: "YOUR-API-KEY" }
  };

  request(options, function (error, response, body) {
    if (error) throw new Error(error);
    console.log(body);
  });

SIM
===

Retrieve SIM
------------

- Method

  ::

    GET

- URL

  ::

    /sim

- Data Params

  ========= ======== =====================
  Parameter Required Default Description
  ========= ======== =====================
  id        *        9 digit ID of the SIM
  ========= ======== =====================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "id":     "192837465",
               "alias":  "4512345678",
               "active": true }

- Error Codes

  ==== =============
  Code Error
  ==== =============
  400  id_invalid
  403  id_forbidden
  404  sim_not_found
  ==== =============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method:  "GET",
      url:     "/sim",
      headers: { Authorization:  "YOUR-API-KEY" },
      json:    { id: "192837465" }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Create SIM
----------

- Method

  ::

    POST

- URL

  ::

    /sim

- Data Params

  ========= ======== ======= =====================
  Parameter Required Default Description
  ========= ======== ======= =====================
  id        *                9 digit ID of the SIM
  alias                      TODO
  active             true    TODO
  ========= ======== ======= =====================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== ==============
  Code Error
  ==== ==============
  400  id_invalid
  400  alias_invalid
  400  active_invalid
  403  id_forbidden
  409  alias_conflict
  ==== ==============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method:  "POST",
      url:     "/sim",
      headers: { Authorization:  "YOUR-API-KEY" },
      json:    { id:     "192837465",
                 alias:  "My-Lego-Drone01",
                 active: true }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Update SIM
----------

- Method

  ::

    PUT

- URL

  ::

    /sim

- Data Params

  ========= ======== ======= =====================
  Parameter Required Default Description
  ========= ======== ======= =====================
  id        *                9 digit ID of the SIM
  alias                      TODO
  active             true    TODO
  ========= ======== ======= =====================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== ==============
  Code Error
  ==== ==============
  400  id_invalid
  400  alias_invalid
  400  active_invalid
  403  id_forbidden
  404  sim_not_found
  409  alias_conflict
  ==== ==============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method:  "PUT",
      url:     "/sim",
      headers: { Authorization:  "YOUR-API-KEY" },
      json:    { id:     "192837465",
                 alias:  "My-Lego-Drone01",
                 active: false }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Delete SIM
----------

- Method

  ::

    DELETE

- URL

  ::

    /sim

- Data Params

  ========= ======== ======= =====================
  Parameter Required Default Description
  ========= ======== ======= =====================
  id        *                9 digit ID of the SIM
  ========= ======== ======= =====================

- Success Response

  .. code-block:: javascript

    Code: 200
    Content: { "message": "OK" }

- Error Codes

  ==== =============
  Code Error
  ==== =============
  400  id_invalid
  403  id_forbidden
  404  sim_not_found
  ==== =============

- Sample Call in NodeJS Request

  .. code-block:: javascript

    var request = require("request");

    var options = {
      method:  "DELETE",
      url:     "/sim",
      headers: { Authorization:  "YOUR-API-KEY" },
      json:    { id: "192837465" }
    };

    request(options, function (error, response, body) {
      if (error) throw new Error(error);
      console.log(body);
    });

Connector
=========

Retrieve Connector
------------------

- Method

  ::

    GET

- URL

  ::

    /connector

- Data Params

  ========= ===================
  Parameter Description
  ========= ===================
  id        ID of the Connector
  ========= ===================

- Success Response

  .. code-block:: javascript

    TODO

- Error Codes

    TODO

- Sample Call in NodeJS Request

  .. code-block:: javascript

    TODO

Create Connector
----------------

- Method

  ::

    POST

- URL

  ::

    /connector

- Data Params

  ========= ===================
  Parameter Description
  ========= ===================
  id        ID of the Connector
  ========= ===================

- Data Params

  TODO

- Success Response

  .. code-block:: javascript

    TODO

- Error Codes

    TODO

- Sample Call in NodeJS Request

  .. code-block:: javascript

    TODO

Update Connector
----------------

- Method

  ::

    PUT

- URL

  ::

    /connector

- Data Params

  ========= ===================
  Parameter Description
  ========= ===================
  id        ID of the Connector
  ========= ===================

- Data Params

  TODO

- Success Response

  .. code-block:: javascript

    TODO

- Error Codes

    TODO

- Sample Call in NodeJS Request

  .. code-block:: javascript

    TODO

Delete Connector
----------------

- Method

  ::

    DELETE

- URL

  ::

    /connector

- Data Params

  ========= ===================
  Parameter Description
  ========= ===================
  id        ID of the Connector
  ========= ===================

- Success Response

  .. code-block:: javascript

    TODO

- Error Codes

    TODO

- Sample Call in NodeJS Request

  .. code-block:: javascript

    TODO
