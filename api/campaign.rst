Campaign API
============

These endpoints will allow you to easily manage campaigns.

.. note::

    Each role in the Open Loyalty has individual endpoints to manage campaigns.

Creating a new campaign
-----------------------

To create a new campaign you will need to call the ``/api/campaign`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/campaign

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[reward]                               | request        |  Campaign type. Possible types:                                            |
|                                                |                |  discount_code, free_delivery_code, gift_code, event_code, value_code.     |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[name]                                 | request        |  Campaign name.                                                            |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[shortDescription]                     | request        |  *(optional)* A short description.                                         |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[conditionsDescription]                | request        |  *(optional)* A description of required conditions to apply.               |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[usageInstruction]                     | request        |  A short information about how to use coupons.                             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[active]                               | request        |  Set 1 if active, otherwise 0                                              |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[costInPoints]                         | request        |  How many points it costs                                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[target]                               | request        |  Set ``level`` to choose target from defined levels.                       |
|                                                |                |  Set ``segment`` to choose target from defined segments                    |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[levels]                               | request        |  Array of level IDs. *(required only if ``target=level``)*                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[segments]                             | request        |  Array of segment IDs. *(required only if ``target=segment``)*             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[unlimited]                            | request        |  Set 1 if unlimited, otherwise 0                                           |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[singleCoupon]                         | request        |  Set 1 if single coupon, otherwise 0                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[limit]                                | request        |  Global campaign usage limit. *(required only if ``unlimited=0``)*         |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[limitPerUser]                         | request        |  Customer campaign usage limit. *(required only if ``unlimited=0``)*       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[coupons]                              | request        |  Array of coupon codes.                                                    |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][allTimeVisible]   | request        |  Set 1 if always visible, otherwise 0                                      |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][visibleFrom]      | request        |  Campaign visible from YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``. |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][visibleTo]        | request        |  Campaign visible to YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.   |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][allTimeActive]      | request        |  Set 1 if always active, otherwise 0                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][activeFrom]         | request        |  Campaign active from YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.  |
|                                                |                |  *(required only if ``allTimeActive=0``)*                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][activeTo]           | request        |  Campaign visible to YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.   |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/campaign \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..." \
        -d "campaign[reward]=discount_code" \
        -d "campaign[name]=Discount+Code+Campaign" \
        -d "campaign[shortDescription]=A+short+description+of+discount+code+campaign" \
        -d "campaign[conditionsDescription]=Discount+code+for+registration" \
        -d "campaign[usageInstruction]=Use+discount+code+as+you+like" \
        -d "campaign[active]=1" \
        -d "campaign[costInPoints]=100" \
        -d "campaign[target]=level" \
        -d "campaign[levels][0]=e82c96cf-32a3-43bd-9034-4df343e5fd94" \
        -d "campaign[levels][1]=000096cf-32a3-43bd-9034-4df343e5fd94" \
        -d "campaign[unlimited]=0" \
        -d "campaign[singleCoupon]=0" \
        -d "campaign[limit]=10" \
        -d "campaign[limitPerUser]=1" \
        -d "campaign[coupons][0]=testCoupon" \
        -d "campaign[coupons][1]=DiscountCoupon" \
        -d "campaign[campaignVisibility][allTimeVisible]=0" \
        -d "campaign[campaignVisibility][visibleFrom]=2017-10-05+10:59" \
        -d "campaign[campaignVisibility][visibleTo]=2018-10-05+10:59" \
        -d "campaign[campaignActivity][allTimeActive]=0" \
        -d "campaign[campaignActivity][activeFrom]=2017-09-05+10:59" \
        -d "campaign[campaignActivity][activeTo]=2017-12-05+10:59"

.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.

.. note::

    The *e82c96cf-32a3-43bd-9034-4df343e5fd94* or *000096cf-32a3-43bd-9034-4df343e5fd94* id are an exemplary values.
    Your value can be different. Check in the list of all levels if you are not sure which id should be used.

.. note::

    The *testCoupon* or *DiscountCoupon* are an exemplary values. You can name code coupons as you like.

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
      "campaignId": "3062c881-93f3-496b-9669-4238c0a62be8"
    }

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/campaign \
        -X "POST" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 400 Bad Request

.. code-block:: json

    {
      "form": {
        "children": {
          "reward": {},
          "name": {},
          "shortDescription": {},
          "conditionsDescription": {},
          "usageInstruction": {},
          "active": {},
          "costInPoints": {},
          "target": {},
          "levels": {},
          "segments": {},
          "unlimited": {},
          "singleCoupon": {},
          "limit": {},
          "limitPerUser": {},
          "coupons": {},
          "campaignVisibility": {
            "children": {
              "allTimeVisible": {},
              "visibleFrom": {},
              "visibleTo": {}
            }
          },
          "campaignActivity": {
            "children": {
              "allTimeActive": {},
              "activeFrom": {},
              "activeTo": {}
            }
          }
        }
      },
      "errors": []
    }

Campaign Collection
-------------------

To retrieve a paginated list of campaigns you will need to call the ``/api/campaign`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/campaign

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
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

To see the first page of all campaigns use the below method:

Example
^^^^^^^

.. code-block:: bash

    curl http://localhost:8181/api/campaign \
        -X "GET" -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
      "campaigns": [
        {
          "levels": [
            "000096cf-32a3-43bd-9034-4df343e5fd94"
          ],
          "segments": [
            "00000000-0000-0000-0000-000000000002"
          ],
          "coupons": [
            "123"
          ],
          "campaignId": "000096cf-32a3-43bd-9034-4df343e5fd93",
          "reward": "discount_code",
          "name": "tests",
          "active": true,
          "costInPoints": 10,
          "singleCoupon": false,
          "unlimited": false,
          "limit": 10,
          "limitPerUser": 2,
          "campaignActivity": {
            "allTimeActive": false,
            "activeFrom": "2016-01-01T00:00:00+0100",
            "activeTo": "2018-01-01T00:00:00+0100"
          },
          "campaignVisibility": {
            "allTimeVisible": false,
            "visibleFrom": "2016-01-01T00:00:00+0100",
            "visibleTo": "2018-01-01T00:00:00+0100"
          },
          "segmentNames": {
            "00000000-0000-0000-0000-000000000002": "anniversary"
          },
          "levelNames": {
            "000096cf-32a3-43bd-9034-4df343e5fd94": "level2"
          },
          "usageLeft": 1,
          "visibleForCustomersCount": 0,
          "usersWhoUsedThisCampaignCount": 0
        },
        {
          "levels": [
            "000096cf-32a3-43bd-9034-4df343e5fd94"
          ],
          "segments": [
            "00000000-0000-0000-0000-000000000002"
          ],
          "coupons": [
            "123"
          ],
          "campaignId": "000096cf-32a3-43bd-9034-4df343e5fd92",
          "reward": "discount_code",
          "name": "for test",
          "active": false,
          "costInPoints": 10,
          "singleCoupon": false,
          "unlimited": false,
          "limit": 10,
          "limitPerUser": 2,
          "campaignActivity": {
            "allTimeActive": false,
            "activeFrom": "2016-01-01T00:00:00+0100",
            "activeTo": "2018-01-01T00:00:00+0100"
          },
          "campaignVisibility": {
            "allTimeVisible": false,
            "visibleFrom": "2016-01-01T00:00:00+0100",
            "visibleTo": "2018-01-01T00:00:00+0100"
          },
          "segmentNames": {
            "00000000-0000-0000-0000-000000000002": "anniversary"
          },
          "levelNames": {
            "000096cf-32a3-43bd-9034-4df343e5fd94": "level2"
          },
          "will_be_active_from": "2016-01-01T00:00:00+0100",
          "will_be_active_to": "2018-01-01T00:00:00+0100",
          "usageLeft": 1,
          "visibleForCustomersCount": 0,
          "usersWhoUsedThisCampaignCount": 0
        },
        {
          "levels": [
            "e82c96cf-32a3-43bd-9034-4df343e5fd94",
            "000096cf-32a3-43bd-9034-4df343e5fd94"
          ],
          "segments": [],
          "coupons": [
            "testCoupon",
            "DiscountCoupon"
          ],
          "campaignId": "3062c881-93f3-496b-9669-4238c0a62be8",
          "reward": "discount_code",
          "name": "Discount Code Campaign",
          "shortDescription": "A short description of discount code campaign",
          "conditionsDescription": "Discount code for registration",
          "active": true,
          "costInPoints": 100,
          "singleCoupon": false,
          "unlimited": false,
          "limit": 10,
          "limitPerUser": 1,
          "campaignActivity": {
            "allTimeActive": false,
            "activeFrom": "2017-09-05T10:59:00+0200",
            "activeTo": "2017-12-05T10:59:00+0100"
          },
          "campaignVisibility": {
            "allTimeVisible": false,
            "visibleFrom": "2017-10-05T10:59:00+0200",
            "visibleTo": "2018-10-05T10:59:00+0200"
          },
          "usageInstruction": "Use discount code as you like",
          "segmentNames": [],
          "levelNames": {
            "e82c96cf-32a3-43bd-9034-4df343e5fd94": "level1",
            "000096cf-32a3-43bd-9034-4df343e5fd94": "level2"
          },
          "usageLeft": 2,
          "visibleForCustomersCount": 0,
          "usersWhoUsedThisCampaignCount": 0
        }
      ],
      "total": 3
    }

Updating a campaign
-------------------

To fully update a campaign user you will need to call the ``/api/campaign/<campaign>`` endpoint with the ``PUT`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    PUT /api/campaign/<campaign>

+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| Parameter                                      | Parameter type |  Description                                                               |
+================================================+================+============================================================================+
| Authorization                                  | header         | Token received during authentication                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| <campaign>                                     | query          |  Campaign ID                                                               |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[reward]                               | request        |  Campaign type. Possible types:                                            |
|                                                |                |  discount_code, free_delivery_code, gift_code, event_code, value_code.     |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[name]                                 | request        |  Campaign name.                                                            |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[shortDescription]                     | request        |  *(optional)* A short description.                                         |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[conditionsDescription]                | request        |  *(optional)* A description of required conditions to apply.               |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[usageInstruction]                     | request        |  A short information about how to use coupons.                             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[active]                               | request        |  Set 1 if active, otherwise 0                                              |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[costInPoints]                         | request        |  How many points it costs                                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[target]                               | request        |  Set ``level`` to choose target from defined levels.                       |
|                                                |                |  Set ``segment`` to choose target from defined segments                    |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[levels]                               | request        |  Array of level IDs. *(required only if ``target=level``)*                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[segments]                             | request        |  Array of segment IDs. *(required only if ``target=segment``)*             |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[unlimited]                            | request        |  Set 1 if unlimited, otherwise 0                                           |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[singleCoupon]                         | request        |  Set 1 if single coupon, otherwise 0                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[limit]                                | request        |  Global campaign usage limit. *(required only if ``unlimited=0``)*         |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[limitPerUser]                         | request        |  Customer campaign usage limit. *(required only if ``unlimited=0``)*       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[coupons]                              | request        |  Array of coupon codes.                                                    |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][allTimeVisible]   | request        |  Set 1 if always visible, otherwise 0                                      |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][visibleFrom]      | request        |  Campaign visible from YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``. |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignVisibility][visibleTo]        | request        |  Campaign visible to YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.   |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][allTimeActive]      | request        |  Set 1 if always active, otherwise 0                                       |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][activeFrom]         | request        |  Campaign active from YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.  |
|                                                |                |  *(required only if ``allTimeActive=0``)*                                  |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+
| campaign[campaignActivity][activeTo]           | request        |  Campaign visible to YYYY-MM-DD HH:mm, for example ``2017-10-05 10:59``.   |
|                                                |                |  *(required only if ``allTimeVisible=0``)*                                 |
+------------------------------------------------+----------------+----------------------------------------------------------------------------+

Example
^^^^^^^

 To fully update a campaign with ``id = 3062c881-93f3-496b-9669-4238c0a62be8`` use the below method:

.. code-block:: bash

    curl http://localhost:8181/api/campaign/3062c881-93f3-496b-9669-4238c0a62be8 \
        -X "PUT" \
        -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..." \
        -d "campaign[reward]=discount_code" \
        -d "campaign[name]=Discount+Code+Campaign 1" \
        -d "campaign[shortDescription]=A+short+description+of+discount+code+campaign" \
        -d "campaign[conditionsDescription]=Discount+code+for+registration" \
        -d "campaign[usageInstruction]=Use+discount+code+as+you+like" \
        -d "campaign[active]=1" \
        -d "campaign[costInPoints]=100" \
        -d "campaign[target]=level" \
        -d "campaign[levels][0]=e82c96cf-32a3-43bd-9034-4df343e5fd94" \
        -d "campaign[levels][1]=000096cf-32a3-43bd-9034-4df343e5fd94" \
        -d "campaign[unlimited]=0" \
        -d "campaign[singleCoupon]=0" \
        -d "campaign[limit]=10" \
        -d "campaign[limitPerUser]=1" \
        -d "campaign[coupons][0]=testCoupon" \
        -d "campaign[coupons][1]=DiscountCoupon" \
        -d "campaign[campaignVisibility][allTimeVisible]=0" \
        -d "campaign[campaignVisibility][visibleFrom]=2017-10-05+10:59" \
        -d "campaign[campaignVisibility][visibleTo]=2018-10-05+10:59" \
        -d "campaign[campaignActivity][allTimeActive]=0" \
        -d "campaign[campaignActivity][activeFrom]=2017-09-05+10:59" \
        -d "campaign[campaignActivity][activeTo]=2017-12-05+10:59"

.. warning::

    Remember, you must update the whole data of the campaign.

.. note::

    The *eyJhbGciOiJSUzI1NiIsInR5cCI6...* authorization token is an exemplary value.
    Your value can be different. Read more about :doc:`Authorization in the </authorization>`.

.. note::

    The *e82c96cf-32a3-43bd-9034-4df343e5fd94* or *000096cf-32a3-43bd-9034-4df343e5fd94* id are an exemplary values.
    Your value can be different. Check in the list of all levels if you are not sure which id should be used.

.. note::

    The *testCoupon* or *DiscountCoupon* are an exemplary values. You can name code coupons as you like.

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
        "campaignId": "3062c881-93f3-496b-9669-4238c0a62be8"
    }

Getting campaign details
------------------------

To retrieve the details of a campaign you will need to call the ``/api/campaign/{campaign}`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/campaign/<campaign>

+---------------+----------------+--------------------------------------+
| Parameter     | Parameter type | Description                          |
+===============+================+======================================+
| Authorization | header         | Token received during authentication |
+---------------+----------------+--------------------------------------+
| <campaign>    | query          | Id of the campaign                   |
+---------------+----------------+--------------------------------------+

Example
^^^^^^^

To see the details of the admin user with ``campaign = 3062c881-93f3-496b-9669-4238c0a62be8`` use the below method:

.. code-block:: bash

    curl http://localhost:8181/api/campaign/3062c881-93f3-496b-9669-4238c0a62be8 \
        -X "GET" -H "Accept: application/json" \
        -H "Content-type: application/x-www-form-urlencoded" \
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
      "levels": [
        "e82c96cf-32a3-43bd-9034-4df343e5fd94",
        "000096cf-32a3-43bd-9034-4df343e5fd94"
      ],
      "segments": [],
      "coupons": [
        "testCoupon",
        "DiscountCoupon"
      ],
      "campaignId": "3062c881-93f3-496b-9669-4238c0a62be8",
      "reward": "discount_code",
      "name": "Discount Code Campaign 1",
      "shortDescription": "A short description of discount code campaign",
      "conditionsDescription": "Discount code for registration",
      "active": true,
      "costInPoints": 100,
      "singleCoupon": false,
      "unlimited": false,
      "limit": 10,
      "limitPerUser": 1,
      "campaignActivity": {
        "allTimeActive": false,
        "activeFrom": "2017-09-05T10:59:00+0200",
        "activeTo": "2017-12-05T10:59:00+0100"
      },
      "campaignVisibility": {
        "allTimeVisible": false,
        "visibleFrom": "2017-10-05T10:59:00+0200",
        "visibleTo": "2018-10-05T10:59:00+0200"
      },
      "usageInstruction": "Use discount code as you like",
      "segmentNames": [],
      "levelNames": {
        "e82c96cf-32a3-43bd-9034-4df343e5fd94": "level1",
        "000096cf-32a3-43bd-9034-4df343e5fd94": "level2"
      },
      "usageLeft": 2,
      "visibleForCustomersCount": 0,
      "usersWhoUsedThisCampaignCount": 0
    }

.. note::

    The *3062c881-93f3-496b-9669-4238c0a62be8* id is an exemplary value. Your value can be different.
    Check in the list of all admin users if you are not sure which id should be used.

Available campaign for a customer
---------------------------------

To check which campaigns are available for a specific customer you will need to call the ``/api/admin/customer/<customer>/campaign/available`` endpoint with the ``GET`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    GET /api/admin/customer/<customer>/campaign/available

+-------------------------------------+----------------+---------------------------------------------------+
| Parameter                           | Parameter type | Description                                       |
+=====================================+================+===================================================+
| Authorization                       | header         | Token received during authentication              |
+-------------------------------------+----------------+---------------------------------------------------+
| <customer>                          | query          | Customer ID                                       |
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

To see the list of campaigns for a customer with ID ``customer = 00000000-0000-474c-b092-b0dd880c07e2`` use the below method:


.. code-block:: bash

    curl http://localhost:8181/api/admin/customer/00000000-0000-474c-b092-b0dd880c07e2/campaign/available \
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
      "campaigns": [
        {
          "levels": [
            "000096cf-32a3-43bd-9034-4df343e5fd93",
            "e82c96cf-32a3-43bd-9034-4df343e5fd94",
            "000096cf-32a3-43bd-9034-4df343e5fd94"
          ],
          "segments": [],
          "coupons": [
            "123"
          ],
          "campaignId": "000096cf-32a3-43bd-9034-4df343e5fd93",
          "reward": "discount_code",
          "name": "tests",
          "active": true,
          "costInPoints": 10,
          "singleCoupon": false,
          "unlimited": false,
          "limit": 10,
          "limitPerUser": 2,
          "campaignActivity": {
            "allTimeActive": false,
            "activeFrom": "2016-01-01T00:00:00+0100",
            "activeTo": "2018-01-01T00:00:00+0100"
          },
          "campaignVisibility": {
            "allTimeVisible": false,
            "visibleFrom": "2016-01-01T00:00:00+0100",
            "visibleTo": "2018-01-01T00:00:00+0100"
          },
          "segmentNames": [],
          "levelNames": {
            "000096cf-32a3-43bd-9034-4df343e5fd93": "level0",
            "e82c96cf-32a3-43bd-9034-4df343e5fd94": "level1",
            "000096cf-32a3-43bd-9034-4df343e5fd94": "level2"
          },
          "usageLeft": 1,
          "usageLeftForCustomer": 1,
          "canBeBoughtByCustomer": true,
          "visibleForCustomersCount": 2,
          "usersWhoUsedThisCampaignCount": 0
        }
      ],
      "total": 1
    }

.. note::

    The *00000000-0000-474c-b092-b0dd880c07e2* id is an exemplary value. Your value can be different.
    Check in the list of all customers if you are not sure which id should be used.

Buy reward campaign for a specific customer
-------------------------------------------

To buy reward campaign for a specific customer you will need to cal the ``/api/admin/customer/<customer>/campaign/<campaign>/buy`` endpoint with the ``POST`` method.

Definition
^^^^^^^^^^

.. code-block:: text

    POST /api/admin/customer/<customer>/campaign/<campaign>/buy

+---------------+----------------+--------------------------------------+
| Parameter     | Parameter type | Description                          |
+===============+================+======================================+
| Authorization | header         | Token received during authentication |
+---------------+----------------+--------------------------------------+
| <customer>    | query          | Customer ID                          |
+---------------+----------------+--------------------------------------+
| <campaign>    | query          | Campaign ID                          |
+---------------+----------------+--------------------------------------+

Example
^^^^^^^

To buy reward campaign ``campaign = 000096cf-32a3-43bd-9034-4df343e5fd93`` for the customer ``customer = 00000000-0000-474c-b092-b0dd880c07e2``
use the below method:

.. code-block:: bash

    curl http://localhost:8181/api/admin/customer/00000000-0000-474c-b092-b0dd880c07e2/campaign/000096cf-32a3-43bd-9034-4df343e5fd93/buy
        -X "POST"
        -H "Accept: application/json"
        -H "Content-type: application/x-www-form-urlencoded"
        -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6..."

Exemplary Response
^^^^^^^^^^^^^^^^^^

.. code-block:: text

    STATUS: 200 OK

.. code-block:: json

    {
      "coupon": {
        "code": "123"
      }
    }

.. note::

    The *000096cf-32a3-43bd-9034-4df343e5fd93* id is an exemplary value. Your value can be different.
    Check in the list of all campaigns if you are not sure which id should be used.

.. note::

    The *00000000-0000-474c-b092-b0dd880c07e2* id is an exemplary value. Your value can be different.
    Check in the list of all customers if you are not sure which id should be used.
