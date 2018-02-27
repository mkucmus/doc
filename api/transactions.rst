Transactions
============

These endpoints will allow you to easily manage transactions.

	
Method allows to assign customer to specific transaction.
---------------------------------------------------------

To assign customer to specific transaction you will need to call the ``/api/admin/transaction/customer/assign`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/admin/transaction/customer/assign

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[transactionDocumentNumber]   | query          | Transaction Document Number                       |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerId]                  | query          | Customer ID                                       |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerLoyaltyCardNumber]   | query          | Customer Loyalty Number                           |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerPhoneNumber]         | query          | Customer Phone Number                             |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/admin/transaction/customer/assign \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..." \
		-d "assign[transactionDocumentNumber]=888 \
		-d "assign[customerId]=57524216-c059-405a-b951-3ab5c49bae14 \
		-d "assign[customerLoyaltyCardNumber]=333 \
		-d "assign[customerPhoneNumber]=333333"

.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "transactionId": "00000000-0000-1111-0000-000000000002"
	}
	
Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 400 Bad Request

.. code-block:: json

	{
	  "form": {
		"children": {
		  "transactionDocumentNumber": {
			"errors": [
			  "Customer is already assign to this transaction"
			]
		  },
		  "customerId": {},
		  "customerLoyaltyCardNumber": {},
		  "customerPhoneNumber": {}
		}
	  },
	  "errors": []
	}
	
	
Method allows to assign customer to specific transaction (seller).
------------------------------------------------------------------

To assign customer to specific transaction you will need to call the ``/api/seller/transaction/customer/assign`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/seller/transaction/customer/assign

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[transactionDocumentNumber]   | query          | Transaction Document Number                       |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerId]                  | query          | Customer ID                                       |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerLoyaltyCardNumber]   | query          | Customer Loyalty Number                           |
+-------------------------------------+----------------+---------------------------------------------------+
| assign[customerPhoneNumber]         | query          | Customer Phone Number                             |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/seller/transaction/customer/assign \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		-d "assign[transactionDocumentNumber]=123 \
		-d "assign[customerId]=57524216-c059-405a-b951-3ab5c49bae14 \
		-d "assign[customerLoyaltyCardNumber]=333 \
		-d "assign[customerPhoneNumber]=333333"
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "transactionId": "00000000-0000-1111-0000-000000000005"
	}

	
Method will return complete list of all transactions (customer).
----------------------------------------------------------------

To return complete list of all transactions you will need to call the ``/api/customer/transaction`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/customer/transaction

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_loyaltyCardNumber      | query          | *(optional)* Loyalty Card Number                  |
+-------------------------------------+----------------+---------------------------------------------------+
| documentType                        | query          | *(optional)* Document Type                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_name                   | query          | *(optional)* Customer Name                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_email                  | query          | *(optional)* Customer Email                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_phone                  | query          | *(optional)* Customer Phone                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerId                          | query          | *(optional)* Customer ID                          |
+-------------------------------------+----------------+---------------------------------------------------+
| documentNumber                      | query          | *(optional)* Document Number                      |
+-------------------------------------+----------------+---------------------------------------------------+
| posId                               | query          | *(optional)* POS ID                               |
+-------------------------------------+----------------+---------------------------------------------------+
| page                                | query          | *(optional)* Start from page, by default 1        |
+-------------------------------------+----------------+---------------------------------------------------+
| perPage                             | query          | *(optional)* Number of items to display per page, |
|                                     |                | by default = 10                                   |
+-------------------------------------+----------------+---------------------------------------------------+
| sort                                | query          | *(optional)* Sort by column name                  |
+-------------------------------------+----------------+---------------------------------------------------+
| direction                           | query          | *(optional)* Direction of sorting [ASC, DESC],    |
|                                     |                | by default = ASC                                  |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/customer/transaction \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "transactions": [
		{
		  "grossValue": 3,
		  "transactionId": "00000000-0000-1111-0000-000000000003",
		  "documentNumber": "456",
		  "purchaseDate": "2018-02-20T09:45:04+0100",
		  "purchasePlace": "wroclaw",
		  "documentType": "sell",
		  "customerId": "00000000-0000-474c-b092-b0dd880c07e1",
		  "customerData": {
			"email": "user@oloy.com",
			"name": "Jan Nowak",
			"nip": "aaa",
			"phone": "123",
			"loyaltyCardNumber": "sa2222",
			"address": {
			  "street": "Bagno",
			  "address1": "12",
			  "province": "Mazowieckie",
			  "city": "Warszawa",
			  "postal": "00-800",
			  "country": "PL"
			}
		  },
		  "items": [
			{
			  "sku": {
				"code": "SKU1"
			  },
			  "name": "item 1",
			  "quantity": 1,
			  "grossValue": 1,
			  "category": "aaa",
			  "maker": "sss",
			  "labels": [
				{
				  "key": "test",
				  "value": "label"
				},
				{
				  "key": "test",
				  "value": "label2"
				}
			  ]
			},
			{
			  "sku": {
				"code": "SKU2"
			  },
			  "name": "item 2",
			  "quantity": 2,
			  "grossValue": 2,
			  "category": "bbb",
			  "maker": "ccc",
			  "labels": []
			}
		  ],
		  "currency": "eur",
		  "pointsEarned": 6.9
		},
		{
		  "grossValue": 3,
		  "transactionId": "00000000-0000-1111-0000-000000000005",
		  "documentNumber": "888",
		  "purchaseDate": "2018-02-20T09:45:04+0100",
		  "purchasePlace": "wroclaw",
		  "documentType": "sell",
		  "customerId": "57524216-c059-405a-b951-3ab5c49bae14",
		  "customerData": {
			"email": "o@lo.com",
			"name": "Jan Nowak",
			"nip": "aaa",
			"phone": "123",
			"loyaltyCardNumber": "sa21as222",
			"address": {
			  "street": "Bagno",
			  "address1": "12",
			  "province": "Mazowieckie",
			  "city": "Warszawa",
			  "postal": "00-800",
			  "country": "PL"
			}
		  },
		  "items": [
			{
			  "sku": {
				"code": "SKU1"
			  },
			  "name": "item 1",
			  "quantity": 1,
			  "grossValue": 1,
			  "category": "aaa",
			  "maker": "sss",
			  "labels": [
				{
				  "key": "test",
				  "value": "label"
				},
				{
				  "key": "test",
				  "value": "label2"
				}
			  ]
			},
			{
			  "sku": {
				"code": "SKU2"
			  },
			  "name": "item 2",
			  "quantity": 2,
			  "grossValue": 2,
			  "category": "bbb",
			  "maker": "ccc",
			  "labels": []
			}
		  ],
		  "currency": "eur",
		  "pointsEarned": 6
		}
	  ],
	  "total": 2
	}
	
Method will return transaction details.
---------------------------------------

To return transaction details you will need to call the ``/api/customer/transaction/{transaction}`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/customer/transaction/{transaction}
	
+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| transaction                         | query          | Transaction ID                                    |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/customer/transaction/{transaction} \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "grossValue": 3,
	  "transactionId": "00000000-0000-1111-0000-000000000003",
	  "documentNumber": "456",
	  "purchaseDate": "2018-02-20T09:45:04+0100",
	  "purchasePlace": "wroclaw",
	  "documentType": "sell",
	  "customerId": "00000000-0000-474c-b092-b0dd880c07e1",
	  "customerData": {
		"email": "user@oloy.com",
		"name": "Jan Nowak",
		"nip": "aaa",
		"phone": "123",
		"loyaltyCardNumber": "sa2222",
		"address": {
		  "street": "Bagno",
		  "address1": "12",
		  "province": "Mazowieckie",
		  "city": "Warszawa",
		  "postal": "00-800",
		  "country": "PL"
		}
	  },
	  "items": [
		{
		  "sku": {
			"code": "SKU1"
		  },
		  "name": "item 1",
		  "quantity": 1,
		  "grossValue": 1,
		  "category": "aaa",
		  "maker": "sss",
		  "labels": [
			{
			  "key": "test",
			  "value": "label"
			},
			{
			  "key": "test",
			  "value": "label2"
			}
		  ]
		},
		{
		  "sku": {
			"code": "SKU2"
		  },
		  "name": "item 2",
		  "quantity": 2,
		  "grossValue": 2,
		  "category": "bbb",
		  "maker": "ccc",
		  "labels": []
		}
	  ],
	  "currency": "eur",
	  "pointsEarned": 6.9
	}
	
	
Method will return complete list of all transactions (seller).
----------------------------------------------------------------

To return complete list of all transactions you will need to call the ``/api/seller/transaction`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/seller/transaction

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_loyaltyCardNumber      | query          | *(optional)* Loyalty Card Number                  |
+-------------------------------------+----------------+---------------------------------------------------+
| documentType                        | query          | *(optional)* Document Type                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_name                   | query          | *(optional)* Customer Name                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_email                  | query          | *(optional)* Customer Email                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_phone                  | query          | *(optional)* Customer Phone                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerId                          | query          | *(optional)* Customer ID                          |
+-------------------------------------+----------------+---------------------------------------------------+
| documentNumber                      | query          | *(optional)* Document Number                      |
+-------------------------------------+----------------+---------------------------------------------------+
| posId                               | query          | *(optional)* POS ID                               |
+-------------------------------------+----------------+---------------------------------------------------+
| page                                | query          | *(optional)* Start from page, by default 1        |
+-------------------------------------+----------------+---------------------------------------------------+
| perPage                             | query          | *(optional)* Number of items to display per page, |
|                                     |                | by default = 10                                   |
+-------------------------------------+----------------+---------------------------------------------------+
| sort                                | query          | *(optional)* Sort by column name                  |
+-------------------------------------+----------------+---------------------------------------------------+
| direction                           | query          | *(optional)* Direction of sorting [ASC, DESC],    |
|                                     |                | by default = ASC                                  |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/customer/transaction\
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "transactions": [
		 {
      "grossValue": 3,
      "transactionId": "00000000-0000-1111-0000-000000000004",
      "documentNumber": "789",
      "purchaseDate": "2018-02-20T09:45:04+0100",
      "purchasePlace": "wroclaw",
      "documentType": "sell",
      "customerId": "00000000-0000-474c-b092-b0dd880c07e2",
      "customerData": {
        "email": "user-temp@oloy.com",
        "name": "Jan Nowak",
        "nip": "aaa",
        "phone": "123",
        "loyaltyCardNumber": "sa2222",
        "address": {
          "street": "Bagno",
          "address1": "12",
          "province": "Mazowieckie",
          "city": "Warszawa",
          "postal": "00-800",
          "country": "PL"
        }
      },
      "items": [
        {
          "sku": {
            "code": "SKU1"
          },
          "name": "item 1",
          "quantity": 1,
          "grossValue": 1,
          "category": "aaa",
          "maker": "sss",
          "labels": [
            {
              "key": "test",
              "value": "label"
            },
            {
              "key": "test",
              "value": "label2"
            }
          ]
        },
        {
          "sku": {
            "code": "SKU2"
          },
          "name": "item 2",
          "quantity": 2,
          "grossValue": 2,
          "category": "bbb",
          "maker": "ccc",
          "labels": []
        }
      ],
      "currency": "eur"
    },
    {
      "grossValue": 3,
      "transactionId": "00000000-0000-1111-0000-000000000002",
      "documentNumber": "345",
      "purchaseDate": "2018-02-20T09:45:04+0100",
      "purchasePlace": "wroclaw",
      "documentType": "sell",
      "customerId": "57524216-c059-405a-b951-3ab5c49bae14",
      "customerData": {
        "email": "open@oloy.com",
        "name": "Jan Nowak",
        "nip": "aaa",
        "phone": "123",
        "loyaltyCardNumber": "sa2222",
        "address": {
          "street": "Bagno",
          "address1": "12",
          "province": "Mazowieckie",
          "city": "Warszawa",
          "postal": "00-800",
          "country": "PL"
        }
      },
      "items": [
        {
          "sku": {
            "code": "SKU1"
          },
          "name": "item 1",
          "quantity": 1,
          "grossValue": 1,
          "category": "aaa",
          "maker": "sss",
          "labels": [
            {
              "key": "test",
              "value": "label"
            },
            {
              "key": "test",
              "value": "label2"
            }
          ]
        },
        {
          "sku": {
            "code": "SKU2"
          },
          "name": "item 2",
          "quantity": 2,
          "grossValue": 2,
          "category": "bbb",
          "maker": "ccc",
          "labels": []
        }
      ],
      "currency": "eur",
      "pointsEarned": 6
        }
      ],
	  "total": 2
	}

Method will return logged in customer transactions (seller).
------------------------------------------------------------

To return logged in customer transactions you will need to call the ``/api/seller/transaction/customer/{customer}`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

     GET  /api/seller/transaction/customer/{customer}

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| documentNumber                      | query          | *(optional)* Document Number                      |
+-------------------------------------+----------------+---------------------------------------------------+
| page                                | query          | *(optional)* Start from page, by default 1        |
+-------------------------------------+----------------+---------------------------------------------------+
| perPage                             | query          | *(optional)* Number of items to display per page, |
|                                     |                | by default = 10                                   |
+-------------------------------------+----------------+---------------------------------------------------+
| sort                                | query          | *(optional)* Sort by column name                  |
+-------------------------------------+----------------+---------------------------------------------------+
| direction                           | query          | *(optional)* Direction of sorting [ASC, DESC],    |
|                                     |                | by default = ASC                                  |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/seller/transaction/customer/{customer} \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json
	
??????????????!!!!!!!_TO_DO_!!!!!!!??????????
??????????????!!!!!!!!!!!!!!!!!!!!!??????????





Method will return transactions with provided document number (seller).
-----------------------------------------------------------------------

To return transactions with provided document number you will need to call the ``/api/seller/transaction/{documentNumber}`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

	GET /api/seller/transaction/{documentNumber}
	
+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| documentNumber                      | query          | *(optional)* Document Number                      |
+-------------------------------------+----------------+---------------------------------------------------+


Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/seller/transaction/{documentNumber} \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json
	
??????????????!!!!!!!_TO_DO_!!!!!!!??????????
??????????????!!!!!!!!!!!!!!!!!!!!!??????????





Method will return complete list of all transactions.
-----------------------------------------------------

To return complete list of all transactions you will need to call the ``/api/transaction`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET  /api/transaction

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_loyaltyCardNumber      | query          | *(optional)* Loyalty Card Number                  |
+-------------------------------------+----------------+---------------------------------------------------+
| documentType                        | query          | *(optional)* Document Type                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_name                   | query          | *(optional)* Customer Name                        |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_email                  | query          | *(optional)* Customer Email                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerData_phone                  | query          | *(optional)* Customer Phone                       |
+-------------------------------------+----------------+---------------------------------------------------+
| customerId                          | query          | *(optional)* Customer ID                          |
+-------------------------------------+----------------+---------------------------------------------------+
| documentNumber                      | query          | *(optional)* Document Number                      |
+-------------------------------------+----------------+---------------------------------------------------+
| posId                               | query          | *(optional)* POS ID                               |
+-------------------------------------+----------------+---------------------------------------------------+
| page                                | query          | *(optional)* Start from page, by default 1        |
+-------------------------------------+----------------+---------------------------------------------------+
| perPage                             | query          | *(optional)* Number of items to display per page, |
|                                     |                | by default = 10                                   |
+-------------------------------------+----------------+---------------------------------------------------+
| sort                                | query          | *(optional)* Sort by column name                  |
+-------------------------------------+----------------+---------------------------------------------------+
| direction                           | query          | *(optional)* Direction of sorting [ASC, DESC],    |
|                                     |                | by default = ASC                                  |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/transaction \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "transactions": [
		{
		  "grossValue": 3,
		  "transactionId": "00000000-0000-1111-0000-000000000003",
		  "documentNumber": "456",
		  "purchaseDate": "2018-02-20T09:45:04+0100",
		  "purchasePlace": "wroclaw",
		  "documentType": "sell",
		  "customerId": "00000000-0000-474c-b092-b0dd880c07e1",
		  "customerData": {
			"email": "user@oloy.com",
			"name": "Jan Nowak",
			"nip": "aaa",
			"phone": "123",
			"loyaltyCardNumber": "sa2222",
			"address": {
			  "street": "Bagno",
			  "address1": "12",
			  "province": "Mazowieckie",
			  "city": "Warszawa",
			  "postal": "00-800",
			  "country": "PL"
			}
		  },
		  "items": [
			{
			  "sku": {
				"code": "SKU1"
			  },
			  "name": "item 1",
			  "quantity": 1,
			  "grossValue": 1,
			  "category": "aaa",
			  "maker": "sss",
			  "labels": [
				{
				  "key": "test",
				  "value": "label"
				},
				{
				  "key": "test",
				  "value": "label2"
				}
			  ]
			},
			{
			  "sku": {
				"code": "SKU2"
			  },
			  "name": "item 2",
			  "quantity": 2,
			  "grossValue": 2,
			  "category": "bbb",
			  "maker": "ccc",
			  "labels": []
			}
		  ],
		  "currency": "eur",
		  "pointsEarned": 6.9
		},
		{
		  "grossValue": 3,
		  "transactionId": "00000000-0000-1111-0000-000000000005",
		  "documentNumber": "888",
		  "purchaseDate": "2018-02-20T09:45:04+0100",
		  "purchasePlace": "wroclaw",
		  "documentType": "sell",
		  "customerId": "57524216-c059-405a-b951-3ab5c49bae14",
		  "customerData": {
			"email": "o@lo.com",
			"name": "Jan Nowak",
			"nip": "aaa",
			"phone": "123",
			"loyaltyCardNumber": "sa21as222",
			"address": {
			  "street": "Bagno",
			  "address1": "12",
			  "province": "Mazowieckie",
			  "city": "Warszawa",
			  "postal": "00-800",
			  "country": "PL"
			}
		  },
		  "items": [
			{
			  "sku": {
				"code": "SKU1"
			  },
			  "name": "item 1",
			  "quantity": 1,
			  "grossValue": 1,
			  "category": "aaa",
			  "maker": "sss",
			  "labels": [
				{
				  "key": "test",
				  "value": "label"
				},
				{
				  "key": "test",
				  "value": "label2"
				}
			  ]
			},
			{
			  "sku": {
				"code": "SKU2"
			  },
			  "name": "item 2",
			  "quantity": 2,
			  "grossValue": 2,
			  "category": "bbb",
			  "maker": "ccc",
			  "labels": []
			}
		  ],
		  "currency": "eur",
		  "pointsEarned": 6
		}
	  ],
	  "total": 2
	}


Method allows to register new transaction in system.
----------------------------------------------------

To register new transaction in system you will need to call the ``/api/transaction`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST  /api/transaction

+----------------------------------------------+----------------+---------------------------------------------------+
| Parameter                                    | Parameter type | Description                                       |
+==============================================+================+===================================================+
| Authorization                                | header         | Token received during authentication              |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction                      			   | query          | Transaction ID                                    |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[transactionData]	    		   | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[revisedDocument]	               | query          | *(optional)* ?_TO_DO_?                            |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][]	                       | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][sku]	                   | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][sku][code]              | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][name]	               | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][quantity]	           | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][grossValue]	           | query          | Gross value                                       |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][category]	           | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][maker]	               | query          | *(optional)* ?_TO_DO_?                            |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][labels][]               | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][labels][][key]          | header         | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][][labels][][value]        | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData]	                   | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][name]	           | query          | Customer name                                     |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][email]	           | query          | *(optional)* Customer email                       |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][phone]	           | query          | *(optional)* Customer phone                       |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][loyaltyCardNumber] | query          | *(optional)* Customer Loyalty card number         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][nip]	           | query          | *(optional)* Customer NIP                          |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address]	       | query          | ?_TO_DO_?                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][street]   | query          | *(optional)* Street                               |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][address1] | query          | *(optional)* ?_TO_DO_?                            |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][address2] | query          | *(optional)* ?_TO_DO_?                            |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][postal]   | query          | *(optional)* Postal code                          |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][city]	   | query          | *(optional)* City                                 |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][province] | query          | *(optional)* ?_TO_DO_?                            |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[customerData][address][country]  | query          | *(optional)* Country                              |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[pos]	                           | query          | *(optional)* POS name                             |
+----------------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/transaction \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

??????????????!!!!!!!_TO_DO_!!!!!!!??????????
??????????????!!!!!!!!!!!!!!!!!!!!!??????????








Method will return available labels.
------------------------------------

To return available labels you will need to call the ``/api/transaction/item/labels`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/transaction/item/labels

+----------------------------------------------+----------------+---------------------------------------------------+
| Parameter                                    | Parameter type | Description                                       |
+==============================================+================+===================================================+
| Authorization                                | header         | Token received during authentication              |
+----------------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/transaction/item/labels \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.

.. note::

    The *label* or *label2* are an exemplary values. You can name labels as you like.	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "labels": {
		"test": [
		  "label",
		  "label2"
		]
	  }
	}


Method will return number of points which can be obtained after registering such transaction.<br/> It will not change anything in the system.
---------------------------------------------------------------------------------------------------------------------------------------------

To return number of points which can be obtained after registering such transaction you will need to call the ``/api/transaction/simulate`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

	POST /api/transaction/simulate 

+----------------------------------------------+----------------+---------------------------------------------------+
| Parameter                                    | Parameter type | Description                                       |
+==============================================+================+===================================================+
| Authorization                                | header         | Token received during authentication              |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction                                  | query          | Transaction ID                                    |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][sku][code]             | query          | SKU code                                          |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][name]              	   | query          | _TO_DO_                                           |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][quantity]       	   | query          | _TO_DO_                                           |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][grossValue]       	   | query          | Gross value                                       |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][category]        	   | query          | _TO_DO_                                           |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][maker]            	   | query          | _TO_DO_                                           |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][labels][0]    		   | query          | _TO_DO_                                           |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][labels][0][key]        | query          | Label key                                         |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[items][0][labels][0][value]      | query          | Label value                                       |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction[purchaseDate]           	       | query          | Purchase date                                     |
+----------------------------------------------+----------------+---------------------------------------------------+


Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/transaction/simulate \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..." \
		-d "transaction=00000000-0000-1111-0000-000000000099 \
		-d "transaction[items][0][sku][code]=SKU1 \
		-d "transaction[items][0][name]=item+8 \
		-d "transaction[items][0][quantity]=1 \
		-d "transaction[items][0][grossValue]=1 \
		-d "transaction[items][0][category]=aaa \
		-d "transaction[items][0][maker]=sss \
		-d "transaction[items][0][labels][0]=labels \
		-d "transaction[items][0][labels][0][key]=test \
		-d "transaction[items][0][labels][0][value]=label \
		-d "transaction[purchaseDate]=2022-02-20T09:45:04+0100"
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json	
		
	{
	  "points": 2
	}		


Method will return transaction details.
---------------------------------------

To return transaction details you will need to call the ``/api/transaction/{transaction}`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET  /api/transaction/{transaction}

+----------------------------------------------+----------------+---------------------------------------------------+
| Parameter                                    | Parameter type | Description                                       |
+==============================================+================+===================================================+
| Authorization                                | header         | Token received during authentication              |
+----------------------------------------------+----------------+---------------------------------------------------+
| transaction                      			   | query          | Transaction ID                                    |
+----------------------------------------------+----------------+---------------------------------------------------+


Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/transaction/{transaction} \
        -X "GET" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "grossValue": 3,
	  "transactionId": "00000000-0000-1111-0000-000000000005",
	  "documentNumber": "888",
	  "purchaseDate": "2018-02-20T09:45:04+0100",
	  "purchasePlace": "wroclaw",
	  "documentType": "sell",
	  "customerId": "57524216-c059-405a-b951-3ab5c49bae14",
	  "customerData": {
		"email": "o@lo.com",
		"name": "Jan Nowak",
		"nip": "aaa",
		"phone": "123",
		"loyaltyCardNumber": "sa21as222",
		"address": {
		  "street": "Bagno",
		  "address1": "12",
		  "province": "Mazowieckie",
		  "city": "Warszawa",
		  "postal": "00-800",
		  "country": "PL"
		}
	  },
	  "items": [
		{
		  "sku": {
			"code": "SKU1"
		  },
		  "name": "item 1",
		  "quantity": 1,
		  "grossValue": 1,
		  "category": "aaa",
		  "maker": "sss",
		  "labels": [
			{
			  "key": "test",
			  "value": "label"
			},
			{
			  "key": "test",
			  "value": "label2"
			}
		  ]
		},
		{
		  "sku": {
			"code": "SKU2"
		  },
		  "name": "item 2",
		  "quantity": 2,
		  "grossValue": 2,
		  "category": "bbb",
		  "maker": "ccc",
		  "labels": []
		}
	  ],
	  "currency": "eur",
	  "pointsEarned": 6
	}
