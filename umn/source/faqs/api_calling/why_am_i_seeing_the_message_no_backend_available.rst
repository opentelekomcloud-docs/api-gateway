:original_name: apig-faq-181016018.html

.. _apig-faq-181016018:

Why Am I Seeing the Message "No backend available"?
===================================================

-  Check whether the backend service is accessible, and modify the backend service if it is inaccessible.

-  Check the ECS security group configurations of the backend service and verify that the required port has been enabled.

-  Check whether the backend service address is a public IP address. If yes, enable outbound access on the **Gateways** > **Access Console** > **Gateway Information** page.

-  Check whether ACL configurations of the VPC restrict the communication between the API gateway and the subnet where the backend service is located.

-  If you use a VPC channel, check whether the service port, health check port, and backend servers of the VPC channel have been correctly configured.

   .
