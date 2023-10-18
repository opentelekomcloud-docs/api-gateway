:original_name: apig-specifications.html

.. _apig-specifications:

Specifications
==============

Dedicated Gateway Specifications
--------------------------------

:ref:`Table 1 <apig-specifications__en-us_topic_0200876799_table139041229163716>` lists the specifications of dedicated API gateways.

.. _apig-specifications__en-us_topic_0200876799_table139041229163716:

.. table:: **Table 1** Specifications of dedicated gateways

   ============ =====================================
   Edition      Maximum Number of Requests per Second
   ============ =====================================
   Basic        2000
   Professional 4000
   Enterprise   6000
   Platinum     10,000
   ============ =====================================

.. note::

   -  For dedicated gateways, you can adjust the maximum number of requests per second for each API.
   -  The specifications of dedicated gateways cannot be modified.
   -  The dedicated gateway specifications are obtained by testing in the following conditions:

      -  Protocol: HTTPS
      -  Connection type: long connection
      -  Concurrent requests: 100
      -  Authentication mode: none
      -  Size of returned data: 1 KB
      -  Bandwidth: 10 MB/s
