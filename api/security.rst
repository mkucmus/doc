Security
========

These endpoints will allow you to easily manage password.

	
Method will change logged user password.
----------------------------------------

To change logged user password you will need to call the ``/api/admin/password/change`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/admin/password/change

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| currentPassword                     | query          | Current password                                  |
+-------------------------------------+----------------+---------------------------------------------------+
| plainPassword                       | query          | New password                                      |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/admin/password/change \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
.. note::

     Your password must be at least 8 characters long.
     Your password must include both upper and lower case letters.
     Your password must include at least one number.
     Your password must contain at least one special character.	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "success": true
	}
	
Method will change logged user password (customer).
---------------------------------------------------

To change logged customer password you will need to call the ``/api/customer/password/change`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/customer/password/change

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| currentPassword                     | query          | Current password                                  |
+-------------------------------------+----------------+---------------------------------------------------+
| plainPassword                       | query          | New password                                      |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/customer/password/change \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
.. note::

     Your password must be at least 8 characters long.
     Your password must include both upper and lower case letters.
     Your password must include at least one number.
     Your password must contain at least one special character.	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "success": true
	}
	
Method will change logged user password (seller).
-------------------------------------------------

To change logged seller password you will need to call the ``/api/seller/password/change`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/seller/password/change

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| currentPassword                     | query          | Current password                                  |
+-------------------------------------+----------------+---------------------------------------------------+
| plainPassword                       | query          | New password                                      |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/seller/password/change \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
.. note::

     Your password must be at least 8 characters long.
     Your password must include both upper and lower case letters.
     Your password must include at least one number.
     Your password must contain at least one special character.	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "success": true
	}
	
Method allows to set new password after reset password requesting.
------------------------------------------------------------------

To reset logged user password you will need to call the ``/api/password/reset`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/password/reset

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| token                               | query          | Token received during resetting the password      |
+-------------------------------------+----------------+---------------------------------------------------+
| reset[plainPassword]                | query          | New password                                      |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/admin/password/change \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."
		
.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.
	
.. note::

     Your password must be at least 8 characters long.
     Your password must include both upper and lower case letters.
     Your password must include at least one number.
     Your password must contain at least one special character.	

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

	{
	  "success": true
	}
	
Purpose of this method is to provide "Forgot password" functionality.<br/>
Invoking this method will send message tot he user with password reset url.
---------------------------------------------------------------------------

To provide "Forgot password" functionality you will need to call the ``/api/password/reset/request`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/password/reset/request
	
+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| username                            | query          | User name who recovers the password               |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/password/reset/request \
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

	{
	  "success": true
	}
	
	
This method can be used to log out current user.<br/>
It will revoke all refresh tokens assigned to current user so it will not be possible to obtain new token based on stored refresh token.
----------------------------------------------------------------------------------------------------------------------------------------

To log out current user you will need to call the ``/api/token/revoke`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/token/revoke
	
+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/token/revoke \
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

	[]
	

	