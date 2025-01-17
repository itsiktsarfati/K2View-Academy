# Installation and Configuration

The installation and configuration of BI includes the following steps:

- [Installation](01_Installation.md#installation) - the installation of Exago server and Storage Management DB.
- [Configuration](01_Installation.md#configuration) - Fabric config.ini parameters configuration.
- [Project Initialization in BI](01_Installation.md#Project-Initialization-in-BI). 

### Installation

* Install **the latest available Exago version** using the [ExagoBI Installation document](/articles/98_maintenance_and_operational/BI_Installation/01_ExagoBI_Installation.md).
* Install **Storage Management DB**, the database that keeps the report definition such as report type and metadata, currency, decimal setting, fonts, colors and more. 


**Installation Recommendations**

Following are the installation and setup recommendations:

- It is recommended to have 3 separate ExagoBI installations. One each for Dev, QA and Production environments.

  - Linux installation is a must for UAT / Production environments.
  - Installation on Windows (as a docker) can be done for development or demo purposes.

- The recommended Storage Management DB type is PostgreSQL.

  - PostgreSQL is a must for UAT / Production environments, but it is preferable to use it for Dev and QA as well.

  - Default SQLite DB can be used for demo purposes. It doesn't require installation as it comes as part of ExagoBI installation.

  - [Click for more information about Exago Storage Management](https://support.exagoinc.com/hc/en-us/articles/360042587313-Storage-Management-Introduction).

### Configuration

Update the **[bi]** section parameters of the Fabric **config.ini** as follows:

* **BI_PORT**, the listener port for BI. The default is 5432.
* **BI_HOST**, the IP address of the BI server.
* **STORAGE_MGMT_DB_NAME**, the name of the Storage Management DB. The default is StorageMgmt.
* **STORAGE_MGMT_HOST**, the IP address of the Storage Management DB. Empty for SQLite DB.
* **STORAGE_MGMT_DB_TYPE**, the type of Storage Management DB. The default is SQLite. The recommended Storage Management DB type is PostgreSQL.
* **STORAGE_MGMT_DB_PROVIDER**, the Storage Management DB provider. The default is SQLite. When the Storage Management DB type is PostgreSQL, the provider is Npgsql.
* **STORAGE_MGMT_DB_USER** / **STORAGE_MGMT_DB_PASSWORD**, the Storage Management DB user and password. Empty for SQLite DB. The password is automatically encrypted upon saving the config.ini.
* **TABLE_PREFIX**, the Storage Management DB table prefix. Should be populated when you want to re-use the same Storage Management DB for several environments. For example, set TABLE_PREFIX=dev1_.
* **BI_REST_KEY**, a key to be used to authenticate REST requests. [Click to get the explanation about how to setup the REST key](99_bi_admin_config.md#REST-Key-Initialization). 

~~~
[bi]
## Listener port for bi
#BI_PORT=5432
## Bi host
#BI_HOST=
## Bi Storage Management name, default = StorageMgmt for SQLite and PostgreSQL
#STORAGE_MGMT_DB_NAME=StorageMgmt
## Bi Storage Management host, empty for SQLite
#STORAGE_MGMT_HOST=
## Bi Storage Management type SQLite/PostgreSQL
#STORAGE_MGMT_DB_TYPE=SQLite
## Bi Storage Management provider SQLite/Npgsql
#STORAGE_MGMT_DB_PROVIDER=SQLite
## Bi Storage Management user
#STORAGE_MGMT_DB_USER=
## Bi Storage Management password
#STORAGE_MGMT_DB_PASSWORD=
## Bi Storage Management table prefix
#TABLE_PREFIX=dev_
## Bi rest key
#BI_REST_KEY=
~~~
### Project Initialization in BI

Upon the completion of installation and configuration setup, deploy the Fabric project. As a result, the Storage Management DB is initialized with 4 basic tables and the <project name> folder is created in the Storage Management DB metadata, with the default read-only access level.  

Now any user accessing this project can have the read-only access to the project's reports within the BI Designer. [Access Permissions Setup](02_Permissions_Setup.md) article explains how to setup the access permissions per Fabric role. 

​

[![Previous](/articles/images/Previous.png)](00_BI_user_guide_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](02_Permissions_Setup.md) 



