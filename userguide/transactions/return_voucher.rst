.. index::
   single: return_voucher

Return "Voucher" for a Customer
================================

.. note:: 

    **this feature is related ONLY with Percentage discount code campaign type**

**Percentage discount code** is a value discount, which customer received after purchase based on registered order amount. 
Discount will be equal percentage value of registered order amount - percentage value is provided in *Transaction percentage value* field during reward creation.

**For example**

If Customer total amount of transaction is **100 EUR**, and *Transaction percentage value* is equal **10** (i.e. 10% of registered transaction total amount) he will receive **10 EUR** discount for next purchase 

Received value code can be used for next purchase to reduce the value of the order. But what happens if the customer decides to return the transaction to which he used the value code?

What will happen to customer's points and indicators of profitability is described in the :doc:`Return transactions </userguide/transactions/menu/returns>`.  

Used value code will be returned to Customer for next purchase, but it's value will depend on the return transaction value in propotion to the registered order amount (which is returned). Returned value code will have **the same expiration date as the one used**   

For better understanding please see **Example** below. 
