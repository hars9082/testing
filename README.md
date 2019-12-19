Create Regional Azure Application Gateway (AAG)with static Front-end
--------------------------------------------------------------------

This runbook is adapted from the following Sites to get what we need for
AAG:

-   [Quickstart: Direct web traffic with Azure Application Gateway -
    Azure
    portal](https://docs.microsoft.com/en-us/azure/application-gateway/quick-create-portal)

-   [Tutorial: Configure an application gateway with SSL termination
    using the Azure
    portal](https://docs.microsoft.com/en-us/azure/application-gateway/create-ssl-portal)

-   [Quickstart: Create a Linux virtual machine in the Azure
    portal](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal)

-   [Setting up SSL/TLS for Apache2 on Ubuntu
    17.04](https://websiteforstudents.com/setting-ssltls-apache2-ubuntu-17-04/)

-   [How to enable mod\_rewrite in
    Apache?](https://askubuntu.com/questions/48362/how-to-enable-mod-rewrite-in-apache)

-   [How To Install the Apache Web Server on Ubuntu 18.04
    \[Quickstart\]](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-18-04-quickstart)

This is the documentation followed to create the QA version of the AAG.
While following this runbook, you should replace all occurences
of **qa-aag** with a prefix for your installation.

### Create AAG

While logged-in to [Azure Portal](https://portal.azure.com/)

-   Select **Create a resource** on the left menu of the Azure portal.
    The **New** window appears.

-   Select **Networking** and then select **Application Gateway** in
    the **Featured** list.

-   On the Basics tab, click on the **Create new** link for Resource
    Group and enter **qa-aag**. This will create the new Resource Group
    where we will place the resource used by the AAG.

-   For **Application gateway name** enter **qa-aag-gateway**

-   For **Region**, select **(US) West US 2** *This may change depending
    on which region you\'re deploying to*

-   For **Tier**, select **WAF V2**.

-   Under **Configure virtual network/Virtual network**, click
    on **Create new** and enter **qa-aag-vnet** for the name.

-   Under **Subnets**, add a second entry with
    name **qa-aag-subnet** and with an appropriate **Address Range**. I
    chose *172.21.1./24*

-   Accept defaults for other options and click **OK** *I tried using
    this VNet with the Linux VM created later, but it didn\'t seem to
    work for me*.

```{=html}
<!-- -->
```
-   For **Subnet**, select the subnet you created
    manually **qa-aag-subnet**

-   Review your settings for **Basics** and click on **Next:
    Frontends \>** 

```{=html}
<!-- -->
```
-   For **Public IP address** click on **Create new** link and
    enter **qa-aag-publicip** for the name and click **OK** to return to
    the **Frontends** tab.
