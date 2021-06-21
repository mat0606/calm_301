.. _calm_aws:


Gateway to myraid infrastructure
+++++++++++++++++++++++++++++++++

Nutanix Calm is the gateway to the myraid infrastructure across multiple clouds.  Every infrastructure is exposed as services the developer can consume.  Innovation is the life blood of every organization.  Every key turning innovation starts as an idea.  Public cloud (AWS, Azure, GCP) is an essential infrastructure provider for organization to test out their ideas.  


Provider in Nutanix Calm
........................

Nutanix Calm supports the following providers (AHV, ESXi, AWS, Azure, GCP & Kubernetes).  **The lab was setup with the instructor AWS account. No actions on the trainees required for this section.**  

#. Click on **Setting** in the left hand toolbar .  Click on **Accounts**.

   .. figure:: images/Calm_Providers.png

#. Define the AWS Regions available to the project.

   .. figure:: images/AWS_Region.png


Add AWS Account into Project
............................

#. Click on **Project** in the left hand toolbar.  Drill into the project created earlier.

   .. figure:: images/project_list.png

#. Click on **Add Account**.  

   .. figure:: images/Project_Detail2.png

#. Click on **Select Account**.  Select **MO_AWS**

   .. figure:: images/Add_AWS_Account.png

#. Click on **Save Accounts and Project**.  

   .. figure:: images/AWS_Account_Detail.png.png


Create an AWS Blueprint
.......................

#. Click on **Blueprint** in the left hand toolbar.  Select the **Multi-VM/Pod Blueprint**

   .. figure:: images/Create_Bp.png

#. Fill in your **initial**-aws as the blueprint name and select your project

   .. figure:: images/bp_project.png

#. Click on + to add Service

   .. figure:: images/add_service.png
 
#. On the right side of the screen, select the AWS Account Provider

   .. figure:: images/Select_Account.png

#. On the right side of the screen, select the following:

   .. figure:: images/AWS_Account_Detail.png

#. On the right side of the screen, select the following:

   .. figure:: images/AWS_Account_Detail2.png
 
#. On the right side of the screen, uncheck the **Check Login upon Create**.  The lab was not setup to use elastic IP address.  The public IP address of the AWS EC2 instance may not be accessible from the lab.

#. Click on **Add Credential**.  Fill in the following:

- **Credential Name** - centos
   - **Username** - centos
   - **Secret Type** - ssh private key
   - **Key** - Paste in your own private key, or use:
   ::

     -----BEGIN RSA PRIVATE KEY-----
     MIIEowIBAAKCAQEAm7e5jSovGg6Mt4X5WGF5l0qCMth/sSK+ZVKaMBaQRlKdttrb+O93mTOxXXga
     F+zCGTu9+830peO+L+Yh1sG/ZKPm3kRmit4nZOH5GQeLoX8ivK7o1hvgEoyAxWbEuns39U54/+6J
     jBgnRgzlO5hpY6LJ0lWeFKdqgUN/b1VlPYd6gg3xIzl9ZYqFyTFbwRoSDfEGCP2JKttzpsgIeDBz
     W0wcu12kMQq6WqWraHt7RFWAvojlRA7rqsUL5S/VxDXgBZZQbP1iKeZXQtbeWZ9dMFf/TXvwwpMw
     wXjuhpAUmlX2mBMYEJdvR3LED9wn/t67H5j6h4W5LplhhMErV0mNIwIDAQABAoIBABawTWPpKpXE
     WvJ+ndcn1LybiZ749poLsuw2ferVzs3ASeSTvQtncOispII29q5Xu+xLTSI8XxIwvcxi3rlY35c9
     Xm0yUDKZrenAFzhzZf/w81HEtn5D74EkYbrhf3agb4XZmj3INthnyIknZdsqGOkAliGEghUGU7lj
     6VSCf87YDWtYeseriuPoZYYgknOZaPQRgN0S7+t8we9iYTX5X7HZXWBu68kWnCld0odz0K2BcVzy
     n58+ZOzyd5t0Isl8tm0m3YMYxQw9dwkGvq4AT/8qbC6iAh/JMDIQiFOlRBSW4M/qKnWkXiwdloxC
     SCZXlaewDad0v5QXOg2kamRM8ikCgYEAy0EUWaprRyxuWCNslQASQsOGyasTz2DlY545xPp2qzxC
     1nk5nFGPSmoC04wY4pJHcTEaPRJ1whtbBPMG7+7v8nkqD6IkXc8dU+AUZVl7oYCtk4gMev5Y5t2N
     CKJlyBNtpQBHB2uVpBF7M+EODSbkagwjWdrTGsx3E3//+RowGj8CgYEAxCCefbRQI/Q61hoQXMzG
     z0chzKop05FgNx4Fd7uII+H9hqjCCaRiZBBunzS2PMIw1e3kR69AhuZ6xJh2oz/aSq/bTivPA2qC
     JkBQ3RXvglQnsMa+cjTYJBwKSf3b+Fmuge9vxzFbcsgOYwN8ddEmCtsPnCFVUnbc1qsDF5I8bB0C
     gYB7q4l6VVsY30v0jPlQX868mMO2iUVwdQCd8HQuCkeSQQRaA0CugGGzYXV+ykuJ8H9PvBS+/DBy
     frqO9GBQNQ4Cdv7ErF98RL0Pf9RpJl03E1iJ38nYPFJThpJ9onJTnp6kOtr9BNT0Ez7nfhRSpEtu
     yxvnXGH+eFIrp0JUiz6heQKBgAvZCJoBZYH2hANhCbIBcNUer+0ELoioVI6f0qa7/mpkgYM7+JTK
     iGMRFw2pCoU7GeYie9LUxGohzDLKHwiXl+FBJFdhkBzdt0UGR5xDcfeGi+tC5khR5uivhPOZUUt8
     Z21UAIWg9qxFZ5EVqdQYMVsghp3g6Z2UrpyNMh+fZuUFAoGBAIkV+8vY/b5c6j745IHTBOQIyqfH
     JLlVChAL1PqeqPi9Ffy8iLR6CecOjx+sWwM9ePLt/urLJSrXamfnBK6j0ZY6d4Ps1kWSRIYIECqa
     QrTdxF2BX7ppu4vG66u8wmvSs59ej1D7wRtsMP/VLfVdtZy5PrfxVHXbRHWAZrSOSsOb
     -----END RSA PRIVATE KEY----- 

   .. figure:: images/add_credential.png

#. Click on **Save**

   .. figure:: images/Save_Bp.png


Launch the AWS Blueprint
........................

#. On the top right side of the screen.  Click on **Launch**

#. Fill in the **initial**-aws as the application name.  Click on **Deploy**

   .. figure:: images/Launch_Bp.png

#. Wait a few minutes for the provisioning to complete.  The state will change from orange color "Provisioning" to green color "Running."

   .. figure:: images/application_complete.png

#. Click on **Service**.  Click on **AWS**.  The public IP address of the EC2 instance are available on the right hand side of the screen.

   .. figure:: images/app_service_detail.png

#. Click on **Delete** to delete the AWS EC2 instance to prevent un-necessary consumption of the AWS resource.

   .. figure:: images/delete_aws_app.png

#. Click on **Delete**.

   .. figure:: images/delete_confirmation.png