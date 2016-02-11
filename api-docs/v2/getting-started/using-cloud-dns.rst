.. _using-cloud-dns:

<<<<<<< HEAD
Create and manage DNS domains
-----------------------------

You can use the examples in the following sections to create and manage domains
by using Cloud DNS API operations.

You will perform the following tasks:

- Creating two Cloud Servers
- Creating a DNS domain
- Listing domain details
- Adding records to your domains

The DNS service is not a regionalized service. DNS is therefore responsible for
appropriate replication, caching, and overall maintenance of DNS data across
regional boundaries to other DNS servers. The followings are examples
of service access endpoints for Cloud DNS.

- ``https://dns.api.rackspacecloud.com/v1.0/1234/``
- ``https://lon.dns.api.rackspacecloud.com/v1.0/1234/``

When making a Cloud DNS API call call, place the endpoint at the beginning of the
request URL,for example:``https://dns.api.rackspacecloud.com/v1.0/**your_acct_id**``,
as you can see in cURL request examples for this guide.

.. note::
     These examples use the ``$API_ENDPOINT``, ``$AUTH_TOKEN``, and ``$TENANT_ID`` environment
     variables to specify the API endpoint, authentication token, and project ID values
     for accessing the service. Make sure you
     :ref:`configure these variables<configure-environment-variables>` before running the
     code samples. 

.. note::
   All examples in this guide assume that you are operating against the US region.

.. include:: examples/gs-create-server.rst
.. include:: examples/gs-create-domain.rst
.. include:: examples/gs-list-domain.rst
.. include:: examples/gs-add-records.rst
=======
Create and manage DNS zones
---------------------------

You can use the examples in the following sections to create and manage zones
by using |apiservice| operations.

The Create zone API call provisions one or more new DNS zones, based on the configuration 
defined in the request object. To create a zone, you need to post to the **/zones** 
endpoint. If the corresponding request cannot be fulfilled due to insufficient or invalid 
data, an ``HTTP 400`` (Bad Request) error response will be returned with information 
regarding the nature of the failure in the body of the response. Failures in the
validation process are non-recoverable and require the caller to correct the cause of the 
failure and **POST** the request again.

This call returns an *asynchronous* response. In fact, **PUT**, **POST**, and **DELETE** 
|apiservice| calls are all *asynchronous*, since they may take some time to process. 
Therefore they return ``202 ACCEPTED`` responses containing information with a link URL, 
which allows the progress, status, and/or response information of the call to be
retrieved at a later point in time.

In this case, assume that you want to create a zone using ``name=example.org``.

..  note:: 

   If you want to substitute your own zone name, you can use any letter, numbers between 
   0 and 9, and the character "-". For example, you might use your first name and last 
   initial at the beginning of the name (for example, "bobmexample.org"). Ensure that you 
   add the final period (.) at the end of your fully qualified zone name.


Choose one of the following methods:

-  :ref:`Creating a zone with the CLI<cli-create-zone>`
-  :ref:`Creating a zone with cURL<curl-create-zone>`

.. include:: examples/cli-create-zone.rst
.. include:: examples/curl-create-zone.rst

The List API call provides detailed output for a specific zone. You can only query for 
zones that you have permission to query, which are ones created using your tenant ID.

Choose one of the following methods:

-  :ref:`Listing a zone with the CLI<cli-list-zone>`
-  :ref:`Listing a zone with cURL<curl-list-zone>`

.. include:: examples/cli-list-zone.rst
.. include:: examples/curl-list-zone.rst

Create and manage recordsets
-----------------------------

A record set groups together a list of related records of the same type. It is the essential
content of your zone file. Record sets are also referred to as “Resource Record Sets” or
“RRSets”. The following example creates an 'A' recordset. An 'A' recordset is used to map a
hostname to an IP address.

Choose one of the following methods:

-  :ref:`Creating a recordset with the CLI<cli-create-recordset>`
-  :ref:`Creating a recordset with cURL<curl-create-recordset>`

.. include:: examples/cli-create-recordset.rst
.. include:: examples/curl-create-recordset.rst

The List recordset API call provides detailed output for a specific recordset using the 
``recordset id``.

Choose one of the following methods:

-  :ref:`Listing a recordset with the CLI<cli-list-recordset>`
-  :ref:`Listing a recordset with cURL<curl-list-recordset>`

.. include:: examples/cli-list-recordset.rst
.. include:: examples/curl-list-recordset.rst
>>>>>>> 67e2a107191eb8bef87aa0a08dd3c73120a05f0c