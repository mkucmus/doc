Settings API
============

These endpoints will allow you to see the list of settings taken in the Open Loyalty.



Get list of translations
------------------------

To retrieve a paginated list of translations you will need to call the ``/api/admin/translations`` endpoint with the ``GET`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/admin/translations
	
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	

Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/admin/translations \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json
	
	{
	  "translations": [
		{
		  "name": "english",
		  "key": "english.json",
		  "updatedAt": "2018-02-19T11:59:27+0100"
		}
	  ],
	  "total": 1
	}	




Create new translations
-----------------------

To add new translations you will need to call the ``/api/admin/translations`` endpoint with the ``POST`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/admin/translations

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| translation[name]                              | query          |  Translation name                                                          |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| translation[content]                           | query          |  Translation content                                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/admin/translations \
	    -X "POST" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: json

	
Get translations based on the key
---------------------------------

To retrieve a paginated list of translations you will need to call the ``/api/admin/translations/<key>`` endpoint with the ``GET`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/admin/translations/<key>

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| <key>                                          | query          |  Translation key                                                           |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	
 	
Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/admin/translations/english.json \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json	
	
	{
  "name": "english",
  "key": "english.json",
  "content": "
      {\n  \"global\": 
	  {\n    \"configuration\": \"Configuration\",
	  \n    \"users\": \"Users\",
	  \n   
	  }
	...
	}
	
	
	
	
Get list of settings
--------------------

To retrieve a paginated list of settings you will need to call the ``/api/settings`` endpoint with the ``GET`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/settings

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
	
Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/settings \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "settings": {
		"excludedLevelCategories": [
		  "category_excluded_from_level"
		],
		"customerStatusesEarning": [
		  "active"
		],
		"customerStatusesSpending": [
		  "active"
		],
		"returns": true,
		"pointsDaysActive": 30,
		"currency": "eur",
		"timezone": "Europe/Warsaw",
		"programName": "Loyalty Program",
		"programPointsSingular": "Point",
		"programPointsPlural": "Points",
		"tierAssignType": "transactions",
		"defaultFrontendTranslations": "english.json",
		"excludedDeliverySKUs": [],
		"excludedLevelSKUs": [],
		"allTimeActive": false,
		"excludeDeliveryCostsFromTierAssignment": false,
		"customersIdentificationPriority": [
		  {
			"priority": 1,
			"field": "email"
		  },
		  {
			"priority": 2,
			"field": "loyaltyCardNumber"
		  }
		],
		"logo": {
		  "path": "logo/045a0a8e8d02c32427f7f1e6734f4eec.html",
		  "originalName": "logo.svg",
		  "mime": "image/svg+xml"
		}
	  }
	}
	

	
	
	
Get list of available email settings
------------------------------------

To retrieve a complete list of available email settings you will need to call the ``/api/settings/emails`` endpoint with the ``GET`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/settings/emails

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	

Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/settings/emails \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: json

	{
	  "emails": [
		{
		  "id": "c60f1033-b1d0-4033-b9fe-7a3c230c4479",
		  "key": "OpenLoyaltyUserBundle:email:registration.html.twig",
		  "subject": "Account created",
		  "content": "Email content", 
		  "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
        },
		 {
		  "id": "cf83d86a-538c-42f7-8d8d-3b46109a864d",
          "key": "OpenLoyaltyUserBundle:email:registration_with_temporary_password.html.twig",
          "subject": "Account created",
          "content": "Email content",
		  "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
		},
		{
          "id": "d08481f5-7e79-4e80-9e74-5a8cf776849d",
          "key": "OpenLoyaltyUserBundle:email:password_reset.html.twig",
          "subject": "Password reset requested",
          "content": "Email content",
		  "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
        },
		{
          "id": "f4f0e1f9-3677-4bdb-9685-416a961bc319",
          "key": "OpenLoyaltyUserBundle:email:customer_reward_bought.html.twig",
          "subject": "{{ program_name }} - new reward",
          "content": "Email content",
		  "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
        },
		{
          "id": "a9964f68-d2af-4db2-88ba-de99af707aec",
          "key": "OpenLoyaltyUserBundle:email:new_points.html.twig",
          "subject": "{{ program_name }} - new points",
          "content": "Email content",
		  "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
        },
		{
          "id": "7824f1fb-9dee-45a8-b8c7-434f5130da60",
          "key": "OpenLoyaltyUserBundle:email:new_level.html.twig",
          "subject": "{{ program_name }} - new level",
          "content": "Email content",
          "sender_name": "open@oloy.com",
          "sender_email": "open@oloy.com",
          "updatedAt": "2018-02-19T09:45:00+0100"
        }
        ],
        "total": 6
    }		
		

		
Get details of email setting
----------------------------

To retrieve details of particular email setting you will need to call the ``/api/settings/emails/<emailId>`` endpoint with the ``GET`` method.


Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/settings/emails/<emailId>		

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| <emailId>                                      | query          |  Email ID                                                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	
	
	
Example
^^^^^^^

curl http://localhost:8181/api/settings/emails/c60f1033-b1d0-4033-b9fe-7a3c230c4479 \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^		

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "entity": {
		"id": "c60f1033-b1d0-4033-b9fe-7a3c230c4479",
		"key": "OpenLoyaltyUserBundle:email:registration.html.twig",
		"subject": "Account created",
		"content": "Email content",
		"sender_name": "open@oloy.com",
        "sender_email": "open@oloy.com",
        "updatedAt": "2018-02-19T09:45:00+0100"
      },
	  "additional": {
        "variables": [
        "url"
       ],
	  "preview": "Email preview"
	  }
	}

	
Update email details ???
--------------------

To remove a logo you will need to call the ``/api/settings/emails/<email>`` endpoint with the ``PUT`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    PUT /api/settings/emails/<email>

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| <email>                                        | query          |  Email ID                                                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| email[key]                                     | request        |  Email keys                                                                |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| email[subject]                                 | request        |  Email subject                                                             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| email[content]                                 | request        |  Email content                                                             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	
| email[sender_name]                             | request        |  Sender name                                                               |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	
| email[sender_email]                            | request        |  Sender email                                                              |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	
	
Example
^^^^^^^	
		
.. code-block:: bash

curl http://localhost:8181/api/settings/emails/f4f0e1f9-3677-4bdb-9685-416a961bc319 \
	    -X "PUT" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "id": "f4f0e1f9-3677-4bdb-9685-416a961bc319"
	}

		

Remove logo
-----------

To remove a logo you will need to call the ``/api/settings/logo`` endpoint with the ``DELETE`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    DELETE /api/settings/logo
	
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
	
Example
^^^^^^^	
		
.. code-block:: bash

curl http://localhost:8181/api/settings/logo \
	    -X "DELETE" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	No Content



	
Get logo
--------

To retrieve a logo you will need to call the ``/api/settings/logo`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/settings/logo

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+	

Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/settings/logo \
	    -X "GET" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

<svg version="1.1" id="openLoyaltyLogo" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 200 70" style="enable-background:new 0 0 200 70;" xml:space="preserve"><style type="text/css">	.st0{fill:#FFFFFF;}	.st1{opacity:0.7;}</style><g>	<path class="st0" d="M109.2,27.4c3.9,0,7,3.2,7,7c0,3.9-3.2,7-7,7c-3.9,0-7-3.2-7-7S105.3,27.4,109.2,27.4 M109.2,26.4		c-4.5,0-8.1,3.6-8.1,8.1s3.6,8.1,8.1,8.1s8.1-3.6,8.1-8.1C117.3,30,113.6,26.4,109.2,26.4"></path>	<path class="st0" d="M55.4,31.2c0,1.7-0.6,3-1.7,3.9C52.6,36,51,36.4,49,36.4h-1.7v6h-2.6v-16h4.6c2,0,3.5,0.4,4.5,1.2		C54.9,28.4,55.4,29.6,55.4,31.2 M47.4,34.2h1.4c1.4,0,2.3-0.2,3-0.7c0.6-0.5,0.9-1.2,0.9-2.2c0-0.9-0.3-1.6-0.8-2.1		c-0.6-0.5-1.4-0.7-2.6-0.7h-1.8v5.7C47.5,34.2,47.4,34.2,47.4,34.2z"></path>	<polygon class="st0" points="67.8,42.5 58.7,42.5 58.7,26.4 67.8,26.4 67.8,28.6 61.3,28.6 61.3,33 67.4,33 67.4,35.2 61.3,35.2 		61.3,40.2 67.8,40.2 	"></polygon>	<path class="st0" d="M85.4,42.5h-3.2l-7.9-12.9h-0.1l0.1,0.7c0.1,1.4,0.2,2.6,0.2,3.8v8.4h-2.4V26.4h3.2l7.9,12.8h0.1		c0-0.2,0-0.8-0.1-1.8c0-1.1-0.1-1.9-0.1-2.5v-8.5h2.4L85.4,42.5L85.4,42.5z"></path>	<polygon class="st0" points="92,42.5 92,26.4 93.1,26.4 93.1,41.4 100.8,41.4 100.8,42.5 	"></polygon>	<polygon class="st0" points="124.5,35.2 129.2,26.4 130.5,26.4 125.1,36.3 125.1,42.5 123.9,42.5 123.9,36.4 118.5,26.4 		119.8,26.4 	"></polygon>	<path class="st0" d="M140.5,36.8H134l-2.3,5.7h-1.2l6.5-16.2h0.7l6.4,16.2h-1.3L140.5,36.8z M134.4,35.8h5.8L138,30		c-0.2-0.5-0.4-1.1-0.7-1.9c-0.2,0.7-0.4,1.3-0.7,1.9L134.4,35.8z"></path>	<polygon class="st0" points="147.6,42.5 147.6,26.4 148.8,26.4 148.8,41.4 156.5,41.4 156.5,42.5 	"></polygon>	<polygon class="st0" points="162.1,42.5 161,42.5 161,27.4 155.7,27.4 155.7,26.4 167.3,26.4 167.3,27.4 162.1,27.4 	"></polygon>	<polygon class="st0" points="174.8,35.2 179.5,26.4 180.7,26.4 175.3,36.3 175.3,42.5 174.2,42.5 174.2,36.4 168.8,26.4 		170.1,26.4 	"></polygon>	<g class="st1">		<circle class="st0" cx="30.3" cy="33" r="1.7"></circle>	</g>	<g class="st1">		<path class="st0" d="M22.6,42.2l1.3-2.2c-1.3-1.5-2.1-3.5-2.1-5.6c0-4.7,3.9-8.6,8.6-8.6s8.6,3.9,8.6,8.6c0,2.2-0.8,4.1-2.1,5.6			l1.3,2.2c2-2,3.3-4.8,3.3-7.8c0-6.1-4.9-11-11-11s-11,4.9-11,11C19.3,37.4,20.5,40.2,22.6,42.2z"></path>	</g>	<g class="st1">		<polygon class="st0" points="35.6,46.6 30.8,38.2 29.8,38.2 25,46.6 22.9,45.4 28.4,35.8 32.2,35.8 37.7,45.4 		"></polygon>	</g></g></svg>


Add logo
--------

To add a logo you will need to call the ``/api/settings/logo`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/settings/logo
		
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| photo[file]                                    | request        |  Path of logo file                                                         |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
	
Example
^^^^^^^

.. code-block:: bash

curl http://localhost:8181/api/settings/logo \
	    -X "POST" \
	    -H "Accept: application/json" \
	    -H "Content-type: application/x-www-form-urlencoded" \
	    -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	No Content
