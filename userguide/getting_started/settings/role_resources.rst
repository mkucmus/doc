.. index::
   single: role_resources

Role Resources 
================

Access to the following resources can be assigned to any admin user role. 

See the **Resources** linked page to learn more about the capabilities thyat are associated with. 

.. image:: /userguide/_images/resources.png
   :alt:   Resources list

.. note:: 

    Regardless of the permissions granted, User can edit his password and view the basic information of his account at any time

ACL 
^^^^^^

Defines access to the :doc:`ACL  </userguide/getting_started/settings/acl>` settings section and its individual elements

+----------------------------------------+----------------------------------------+
| VIEW                                   | MODIFY                                 |
+========================================+========================================+
|- Roles list preview                    | All **View** permissions, and more:    |     
|                                        |                                        |
|                                        | - Roles details preview                |
|                                        | - New role creation                    |
|                                        | - Existing roles edition               |
|                                        | - Existing role deletion               | 
+----------------------------------------+----------------------------------------+

.. warning:: 

    Default **Super admin** role can not be deleted 
    
.. warning:: 

    When assigning resources, be sure to don't give an any access to the **ACL** section if you are limiting access for a given role. 
    
    **Otherwise, users will be able to modify their own permissions** 


Admins 
^^^^^^

Defines access to the Admin :doc:`Users  </userguide/getting_started/settings/users>` settings section and its individual elements

+----------------------------------------+----------------------------------------+
| VIEW                                   | MODIFY                                 |
+========================================+========================================+
|- Users list preview                    | All **View** permissions, and more:    |     
|                                        |                                        |
|                                        | - New User account creation*           |
|                                        | - Existing user account edition*       |
+----------------------------------------+----------------------------------------+

.. note:: 

    To enable user edition and creation, you must have at least an **ACL View access** (*Roles* field is required). 
    
    If there is no ACL access, then you can not even see roles in the drop-down list. 

.. note:: 

    Remember, that granting *View* access for ACL section (to enable new users account creation and edition), you give an access to the entire ACL section (in accordance with the permissions listed in the ACL table in *View* column) 
    

    

Audit
^^^^^^

Defines access to the :doc:`System logs  </userguide/getting_started/settings/system_logs>` settings section and its individual elements


+-------------------------------------------------+
| VIEW & MODIFY                                   |                                 
+=================================================+
|- System logs list preview                       |    
|- filter and sorting options of system logs list |
|- search logs from time period                   | 
+-------------------------------------------------+

.. tip:: 

    Regardless of access level, user has the same options in both - **View and Modify**
  
  

Customers
^^^^^^^^^^

Defines access to the :doc:`Customers  </userguide/customers/index>` section and its individual menu elements

+---------------------------------------------------------+
| VIEW                                                    | 
+=========================================================+
|- List of customers accounts preview*                    | 
|- Filter and sorting options of customers accounts list  |  
|- Referred customers list preview                        | 
|- Filter and sorting options of referred customers list  | 
|- Customer profile details: Profitability, Loyalty       | 
|  Profile details and Agreements sections (defualt)**    | 
|                                                         | 
+---------------------------------------------------------+

+--------------------------------------------------------+
| MODIFY                                                 |
+========================================================+
| All **View** permissions, and more:                    |     
|                                                        |
| - Customer account creation**                          |
| - Import customers list                                |
| - Updating Customer account**                          |
| - Deactivate a Customer’s account                      |
| - Level assigned manually mechanism**                  | 
+--------------------------------------------------------+


.. tip:: 

    **List of customers accounts preview***
    
    Even if User has no access to the Levels section, in All customers grid information about current level will be displayed

.. note:: 

    **Customer account creation & edition***
    
    To enable full customer account edition & creation, and display all Customer profile details, you must have at least an **View access** to the following: 
     - *Levels* - to assigne level and display in Profile details 
     - *POS* - to assigne POS and display in Profile details
     - *Merchants* - to assigne merchant and display in Profile details
     - *Segments* - to display segments to which customer belongs in Profile details 
     - *Transactions* - to display all customer registered transactions in Profile details 
     - *Points transfers* - to display all customer adding/spending points transfer in Profile details 
     - *Available rewards* - to display all rewards accessible for customer in Profile details 
     - *Redeemed rewards* - to display all redeemed rewards by customer in Profile details 
    
    If there is no access to any of this section, then you can not see options or tabs. 

.. image:: /userguide/_images/acl_customer.PNG
   :alt:   No levels, merchants and pos access 


.. note:: 

    Remember, that granting *View* access for every section (to enable new users account creation and edition or display information in profile details), you give an access to the entire menu section (in accordance with the permissions listed in the particular tables in *View* column) 



Dashboard
^^^^^^^^^^

Defines access to the :doc:`Dashboard  </userguide/getting_started/admin/dashboard>` section and its individual elements

+-------------------------------------------------------------------------------+
| VIEW & MODIFY                                                                 |                                 
+===============================================================================+
|- Blocks with factors describing the current state of referral program preview |    
|- Chart shows the number of new customer accounts within last 30 days          |
|- Levels grid preview*                                                         | 
+-------------------------------------------------------------------------------+

.. tip:: 

    Regardless of access level, user has the same options in both - **View and Modify**

.. note:: 

    To enable Levels grid preview you must have at least an **Levels View access**. 
    
    If there is no Levels access, then you can not see the grid. 

.. note:: 

    Remember, that granting *View* access for Levels section (to enable levels grid preview), you give an access to the entire Levels menu section (in accordance with the permissions listed in the Levels table in *View* column) 



Earning rules
^^^^^^^^^^^^^^


Levels
^^^^^^^^^^^^^^



Merchants
^^^^^^^^^^^^^^



Points transfers
^^^^^^^^^^^^^^^^^^


POS
^^^^^^^


Reward Campaign
^^^^^^^^^^^^^^^^^^



Segments
^^^^^^^^^^^^^^^^^^



Settings
^^^^^^^^^^^^^^^^^^


Transactions
^^^^^^^^^^^^^^^^^^



Utilities
^^^^^^^^^^^^^^^^^^
