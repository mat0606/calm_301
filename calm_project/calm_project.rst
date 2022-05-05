.. _calm_project:

Pre-Requisites:
+++++++++++++++

This lab is created using Nutanix Calm 3.5.0 and Prism Central pc.2022.1.02

Create a Project in Calm
++++++++++++++++++++++++

Projects are the logical construct that integrate Calm with Nutanix’s native Self-Service Portal (SSP) capabilities, allowing an administrator to assign both infrastructure resources and the roles/permissions of Active Directory users/groups to specific Blueprints and Applications.


#. Click on **Project** in the left hand toolbar .  Click on **Create Project**.

   .. figure:: images/project_list.png

#. Click on **Add Account**.

   .. figure:: images/project_namel.png

#. Fill in the Project Name. Eg Trainee_Project_Name.  Click on **Create**.

   .. figure:: images/Project_Detail.png

Add Account in Project
......................

#. Click on **Select Account**.  Select **NTNX_LOCAL_AZ**

   .. figure:: images/Add_Account.png

#. Click on **Configure Resources**.  Click on **Select VPCs & Subnets**

   .. figure:: images/add-cluster2.png

#. Select **VPC**.  Select the Overlay Subnet **SG-AMK** Network.  Click on **Confirm**.

   .. figure:: images/select-vpc.png


#. Select **Confirm**.  

   .. figure:: images/confirm-vpc.png

#. Click on **Save Accounts & Project**

   .. figure:: images/Save-Account2.png

#. Click on **Save & Configure Environment**

   .. figure:: images/project_quota.png

Configure the Environment in Project
....................................

#. The environment play a critical role to allow the **Consumer** role user to launch a marketplace item with pre-defined hardware specification, guest customization and credentials required in the execution of the blueprint.

#. Click on **Create Environment**

   .. figure:: images/Create_Environment.png

#. Fill in the name for the environment.  Eg **Default Environment**.  Click on **Account**

   .. figure:: images/Environment_Name.png

#. Select **NTNX_LOCAL_AZ**

   .. figure:: images/Environment_Account.png

#. Click on **VM Configuration**

   .. figure:: images/Environment_Detail.png

#. Click on **Linux**.  Fill in the following hardware specification.

   .. figure:: images/Linux_HW.png

#. Copy the **cloud-init** contents into the **Guest Customization**
  
   .. code-block:: bash
   
    #cloud-config
    users:
    - name: centos
    ssh-authorized-keys:
      - @@{centos_public_key}@@
    sudo: ['ALL=(ALL) NOPASSWD:ALL'] 

   .. note::

#.  Expand the **DISK** section.  Select the disk image as shown.

   .. figure:: images/Env-Disk-Image.png

#.  Expand the **Network Adapter** section.  Select the Network Adapter: **Primary**.

   .. figure:: images/Env-Network-Adapter.png

#.  Expand the **Connection** section.  Click on **Add New Credential**.

   .. figure:: images/Env-Connection.png

#. Create the credential for centos.  Fill out the following fields:


   - **Credential Name** - centos
   - **Username** - centos
   - **Secret Type** - ssh private key
   - **Key** - Paste in your own private key, or use:
   ::

     -----BEGIN RSA PRIVATE KEY-----
     MIIEowIBAAKCAQEAii7qFDhVadLx5lULAG/ooCUTA/ATSmXbArs+GdHxbUWd/bNG
     ZCXnaQ2L1mSVVGDxfTbSaTJ3En3tVlMtD2RjZPdhqWESCaoj2kXLYSiNDS9qz3SK
     6h822je/f9O9CzCTrw2XGhnDVwmNraUvO5wmQObCDthTXc72PcBOd6oa4ENsnuY9
     HtiETg29TZXgCYPFXipLBHSZYkBmGgccAeY9dq5ywiywBJLuoSovXkkRJk3cd7Gy
     hCRIwYzqfdgSmiAMYgJLrz/UuLxatPqXts2D8v1xqR9EPNZNzgd4QHK4of1lqsNR
     uz2SxkwqLcXSw0mGcAL8mIwVpzhPzwmENC5OrwIBJQKCAQB++q2WCkCmbtByyrAp
     6ktiukjTL6MGGGhjX/PgYA5IvINX1SvtU0NZnb7FAntiSz7GFrODQyFPQ0jL3bq0
     MrwzRDA6x+cPzMb/7RvBEIGdadfFjbAVaMqfAsul5SpBokKFLxU6lDb2CMdhS67c
     1K2Hv0qKLpHL0vAdEZQ2nFAMWETvVMzl0o1dQmyGzA0GTY8VYdCRsUbwNgvFMvBj
     8T/svzjpASDifa7IXlGaLrXfCH584zt7y+qjJ05O1G0NFslQ9n2wi7F93N8rHxgl
     JDE4OhfyaDyLL1UdBlBpjYPSUbX7D5NExLggWEVFEwx4JRaK6+aDdFDKbSBIidHf
     h45NAoGBANjANRKLBtcxmW4foK5ILTuFkOaowqj+2AIgT1ezCVpErHDFg0bkuvDk
     QVdsAJRX5//luSO30dI0OWWGjgmIUXD7iej0sjAPJjRAv8ai+MYyaLfkdqv1Oj5c
     oDC3KjmSdXTuWSYNvarsW+Uf2v7zlZlWesTnpV6gkZH3tX86iuiZAoGBAKM0mKX0
     EjFkJH65Ym7gIED2CUyuFqq4WsCUD2RakpYZyIBKZGr8MRni3I4z6Hqm+rxVW6Dj
     uFGQe5GhgPvO23UG1Y6nm0VkYgZq81TraZc/oMzignSC95w7OsLaLn6qp32Fje1M
     Ez2Yn0T3dDcu1twY8OoDuvWx5LFMJ3NoRJaHAoGBAJ4rZP+xj17DVElxBo0EPK7k
     7TKygDYhwDjnJSRSN0HfFg0agmQqXucjGuzEbyAkeN1Um9vLU+xrTHqEyIN/Jqxk
     hztKxzfTtBhK7M84p7M5iq+0jfMau8ykdOVHZAB/odHeXLrnbrr/gVQsAKw1NdDC
     kPCNXP/c9JrzB+c4juEVAoGBAJGPxmp/vTL4c5OebIxnCAKWP6VBUnyWliFhdYME
     rECvNkjoZ2ZWjKhijVw8Il+OAjlFNgwJXzP9Z0qJIAMuHa2QeUfhmFKlo4ku9LOF
     2rdUbNJpKD5m+IRsLX1az4W6zLwPVRHp56WjzFJEfGiRjzMBfOxkMSBSjbLjDm3Z
     iUf7AoGBALjvtjapDwlEa5/CFvzOVGFq4L/OJTBEBGx/SA4HUc3TFTtlY2hvTDPZ
     dQr/JBzLBUjCOBVuUuH3uW7hGhW+DnlzrfbfJATaRR8Ht6VU651T+Gbrr8EqNpCP
     gmznERCNf9Kaxl/hlyV5dZBe/2LIK+/jLGNu9EJLoraaCBFshJKF
     -----END RSA PRIVATE KEY-----

   .. figure:: images/centos_credential.png

#. Click on **Done**.  Click on **Next**

#. Click on **Save Environment**.

   .. figure:: images/Save_Environment.png

Verify the Environment
......................


#. Verify the environment was created.  Click on **1 environment added**

   .. figure:: images/Project_Detail2.png

#. Click on **Update Environment**

   .. figure:: images/Update_Environment.png   

#. Click on **Account**

   .. figure:: images/Environment_Name.png   

#. Verify the **Ready for Marketplace usage, Linux only**

   .. figure:: images/Linux_Verification.png   





