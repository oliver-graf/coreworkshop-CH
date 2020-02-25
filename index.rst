.. title:: Nutanix Core Workshop

.. toctree::
  :maxdepth: 2
  :caption: MANAGING THE NUTANIX CLUSTER
  :name: _lab1_managing_the_nutanix_cluster
  :hidden:

  lab1_managing_the_nutanix_cluster/lab1_managing_the_nutanix_cluster

.. toctree::
  :maxdepth: 2
  :caption: SECURING THE NUTANIX CLUSTER
  :name: _lab2_Securing the Nutanix Cluster
  :hidden:

  lab2_securing_nutanix_cluster/lab2_securing_nutanix_cluster

.. toctree::
  :maxdepth: 2
  :caption: NETWORKING
  :name: _networking
  :hidden:

  lab3_networking/lab3_networking

.. toctree::
  :maxdepth: 2
  :caption: VM Managment
  :name: __vm_managment
  :hidden:

  lab4_vm_managment/lab4_vm_managment


.. toctree::
  :maxdepth: 2
  :caption: Healt Monitoring and Alerts
  :name: _Healtsmonitoring_and_alerts
  :hidden:

  lab5_healt_mintoring_and_alerts/lab5_healt_mintoring_and_alerts


.. toctree::
  :maxdepth: 2
  :caption: DISTRIBUTED STORAGE FABRIC  
  :name: _distributed_storage_fabric
  :hidden:

  lab6_distributed_storage_fabric/lab6_distributed_storage_fabric

.. toctree::
  :maxdepth: 2
  :caption: FILES DEPLOYMENT 
  :name: _files_deploy
  :hidden:

  lab7_files_deploy/lab7_files_deploy

.. toctree::
  :maxdepth: 2
  :caption: FILES SMB SHARE
  :name: _files_smb_share
  :hidden:

  lab8_files_smb_share/lab8_files_smb_share

.. toctree::
  :maxdepth: 2
  :caption: FILES NFS EXPORT
  :name: _files_nfs_export
  :hidden:

  lab9_files_nfs_export/lab9_files_nfs_export

.. toctree::
  :maxdepth: 2
  :caption: FILE ANALYTICS DEPLOY
  :name: _file_analytics_deploy
  :hidden:

  lab10_file_analytics_deploy/lab10_file_analytics_deploy

.. toctree::
  :maxdepth: 2
  :caption: FILE ANALYTICS SCAN
  :name: _file_analytics_scan
  :hidden:

  lab11_file_analytics_scan/lab11_file_analytics_scan

.. toctree::
  :maxdepth: 2
  :caption: XPLAY
  :name: _prism_pro_xplay
  :hidden:

  lab12_prism_pro_xplay/lab12_prism_pro_xplay

  :maxdepth: 2
  :caption: KNOWLEDGE CHECK
  :name: _Knowledge_Check
  :hidden:

  Knowledge_Check/Knowledge_Check

    :maxdepth: 2
  :caption: KNOWLEDGE CHECK ANSWER KEY
  :name: _Knowledge_Check_Answer_Key
  :hidden:

  Knowledge_Check_Answer_Key/Knowledge_Check_Answer_Key

.. toctree::
  :maxdepth: 2
  :caption: APPENDIX  
  :name: _appendix
  :hidden:

  appendix/glossary


.. _Getting_Started:

---------------
Getting Started
---------------

Welcome to the Nutanix Core Workshop! This workshop may accompany an instructor-led session that introduces Nutanix Core technologies and many common management tasks.

You will explore Prism Element and become familiar with its features and navigation. You will use Prism to perform basic cluster administration tasks, including storage and networking. You will also walk through basic VM deployment and management tasks with Prism and AHV. Finally, you will explore VM data protection, including snapshots and replication. The instructor explains the exercises and answers any additional questions that you may have.

At the end of the bootcamp, attendees should understand the Core concepts and technologies that make up the Nutanix Enterprise Cloud stack.

What's New
++++++++++

..

 * Workshop updated for the following software versions:
    
    * AOS & PC 5.11.x

 * Optional Lab Updates:

    * This Workshop has been done with the 1-Click-Demo 


Agenda
++++++

- Introductions
- Nutanix Technology Overview
- Nutanix Configuration
- Deploying and Managing Workloads
- Security Compliance

Introductions
+++++++++++++

- Name
- Familiarity with Nutanix
- Expectations

Initial Setup
+++++++++++++

- There will be a handout with all the information you need to connect to the Lab

Environment Details
+++++++++++++++++++

Nutanix Workshops are intended to be run in the Nutanix Hosted POC environment. Your cluster will be provisioned with all necessary images, networks, and VMs required to complete the exercises.

Networking
..........

Hosted POC clusters follow a standard naming convention:

=================== ====================
**Cluster Name**    PHX-xxx
**Subnet**          255.255.255.192
**Cluster IP**      10.xxx.yyy.zzz
=================== ====================

For example:

=================== ==========
**Cluster Name**    PHX-POC034
**Subnet**          255.255.255.192
**Cluster IP**      10.21.55.71
=================== ==========

Throughout the Workshop there are multiple instances where you will need to substitute *xxx.yyy.zzz* with the correct octet for your subnet, for example:


====================== ==============================================
IP Address             Description
====================== ==============================================
10.xxx.yyy.71          Nutanix Cluster Virtual IP
10.xxx.yyy.74          **PC** VM IP, Prism Central
10.xxx.yyy.79          **DC1** VM IP, <POCname>.nutanix.local Domain Controller
10.xxx.yyy.80          **DC2** VM IP, <POCname>.nutanix.local Domain Controller
10.xxx.yyy.65          **Gateway** for subnet 10.xxx.yyy.64/26
====================== ==============================================


Each cluster is configured with 1 VLAN which can be used for VMs:


================= ========================= ====== =============================================
Network           Name Address              VLAN   DHCP Scope
================= ========================= ====== =============================================
Network-01        10.xxx.yyy.64/26          0      10.xxx.yyy.97-10.xxx.yyy.125
...               ...  OPTIONAL             ...    ...
Network-02        10.xxx.yyy.128/25         yyy1   10.xxx.yyy.132-10.xxx.yyy.254
Unmanaged Network                           71
================= ========================= ====== =============================================



Credentials
...........

.. note::

  The *<Password>* is the Same for all except Windows Tools VM and Linux Tools VM

============= ============= ====================
Credential    Username      Password
============= ============= ====================
Prism Element admin         *<Password>*
Prism Central admin         *<Password>*
Controller VM nutanix       *<Password>*
Prism Central VM nutanix    *<Password>*
...           ...           ...
LinuxToolsVM  root          *nutanix/4u*
WinToolsVM    administrator *nutanix/4u*
============= ============= ====================



Each cluster has a dedicated domain controller VM, **DC1**, **DC2** responsible for providing AD services for the **<POCname>.nutanix.local** domain. The domain is populated with the following Users and Groups:

================================= ============================================================================================== ====================
Group                             Username(s)                                                                                    Password
================================= ============================================================================================== ====================
Customer-A-Admin-Accounts-Group   adm-User-1-A, adm-User-2-A, adm-User-3-A, adm-User-4-A, adm-User-5-A                           *<Password>*
Customer-A-Service-Accounts-Group ntnx-bck-svc-A, ntnx-exc-svc-A, ntnx-ntx-svc-A, ntnx-psr-svc-A, ntnx-sql-svc-A, ntnx-xda-svc-A *<Password>*
Customer-A-User-Accounts-Group    user-1-A, user-2-A, user-3-A, user-4-A, user-5-A                                               *<Password>*
Customer-B-Admin-Accounts-Group   adm-User-1-B, adm-User-2-B, adm-User-3-B, adm-User-4-B, adm-User-5-B                           *<Password>*
Customer-B-Service-Accounts-Group ntnx-bck-svc-B, ntnx-exc-svc-B, ntnx-ntx-svc-B, ntnx-psr-svc-B, ntnx-sql-svc-B, ntnx-xda-svc-B *<Password>*
Customer-B-User-Accounts-Group    user-1-B, user-2-B, user-3-B, user-4-B, user-5-B                                               *<Password>*
Customer-C-Admin-Accounts-Group   adm-User-1-C, adm-User-2-C, adm-User-3-C, adm-User-4-C, adm-User-5-C                           *<Password>*
Customer-C-Service-Accounts-Group ntnx-bck-svc-C, ntnx-exc-svc-C, ntnx-ntx-svc-C, ntnx-psr-svc-C, ntnx-sql-svc-C, ntnx-xda-svc-C *<Password>*
Customer-C-User-Accounts-Group    user-1-C, user-2-C, user-3-C, user-4-C, user-5-C                                               *<Password>*
Customer-D-Admin-Accounts-Group   adm-User-1-D, adm-User-2-D, adm-User-3-D, adm-User-4-D, adm-User-5-D                           *<Password>*
Customer-D-Service-Accounts-Group ntnx-bck-svc-D, ntnx-exc-svc-D, ntnx-ntx-svc-D, ntnx-psr-svc-D, ntnx-sql-svc-D, ntnx-xda-svc-D *<Password>*
Customer-D-User-Accounts-Group    user-1-D, user-2-D, user-3-D, user-4-D, user-5-D                                               *<Password>*
================================= ============================================================================================== ====================

Nutanix Image web Address
+++++++++++++++++++++++++

http://10.42.194.11/workshop_staging/


Access Instructions
+++++++++++++++++++

The Nutanix Hosted POC environment can be accessed a number of different ways:


Parallels VDI this is slow and shoudl only be used if any thing else dose not work.
...................................................................................

Login to: https://xld-uswest1.nutanix.com (for PHX) or https://xld-useast1.nutanix.com (for RTP)

**Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Employee Pulse Secure VPN
.........................

To download the client: login to https://xlv-uswest1.nutanix.com or https://xlv-useast1.nutanix.com - **Username:** POCxxx-User01 (up to POCxxx-User20), **Password:** *<Provided by Instructor>*

Download and install the client.

In Pulse Secure Client, **Add** a connection:

For PHX:

============== ========================================
**Type**       Policy Secure (UAC) or Connection Server
**Name**       X-Labs - PHX
**Server URL** xlv-uswest1.nutanix.com
============== ========================================

For RTP:

============== ========================================
**Type**       Policy Secure (UAC) or Connection Server
**Name**       X-Labs - RTP
**Server URL** xlv-useast1.nutanix.com
============== ========================================

Bootcamp WLAN Connection
........................

============ ==========
ntnx_hpoc_5G nutanix/4u
ntnx_hpoc    nutanix/4u
============ ==========


Nutanix Version Info
++++++++++++++++++++

  * **AHV Version** - AHV 20170830.301  (5.11+/5.11+)
  * **AOS Version** - 5.11.1
  * **PC Version** - 5.11.1

----------------------
**Indices and tables**
----------------------

* :ref:`genindex`
* :ref:`search`
