zwnet_init
=============

Initialize network and return network handle

----

Declaration
--------------

:func: `int zwnet_init(const zwnet_init_p init, zwnet_p* net)`

.. code-block:: groovy

	int zwnet_init(const zwnet_init_p init, zwnet_p* net)

Parameters
--------------

   [in] init 
      User filled initialization information

   [out] net 
      Handle to network for use in other zwnet_xxx API calls

Returns
--------------      

      ZW_ERR_NONE on success; else ZW_ERR_XXX          

Description
--------------

This call runs a state-machine to acquire the ZIPGW attached controller Home ID,
controller’s Node ID, HAN address and node list of the HAN. An internal network
data structure is created and initialized with each of the node id found in the
acquired node list. User application could get access to the controller Home ID
and Node ID by calling zwnet_get_desc API only after the zwnet_notify_fn
callback function returns status is ZW_ERR_NONE.

To populate the internal network data structure with endpoints and interfaces,
this API tries to retrieve the node information from an internally maintained
database. For those nodes found in the controller routing table but do not have
corresponding node information in the database, the node info state-machine is
invoked to get the information (CCs supported, CC version, node name & location,
manufacturer id, product type id, product id and multi-instance/channel
endpoints, etc) directly from the node device.


zwnet_init_p
---------------

bla bla bla