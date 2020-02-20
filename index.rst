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
**Cluster Name**    POC\ *xxx*
**Subnet**          10.*xxx*.\ *yyy*\ .0
**Cluster IP**      10.*xxx*.\ *yyy*\ .7
=================== ====================

For example:

=================== ==========
**Cluster Name**    POC055
**Subnet**          10.21.55.0
**Cluster IP**      10.21.55.7
=================== ==========

Throughout the Workshop there are multiple instances where you will need to substitute *XYZ* with the correct octet for your subnet, for example:


====================== ==============================================
IP Address             Description
====================== ==============================================
10.*xxx*.\ *xxx*\ .7   Nutanix Cluster Virtual IP
10.*xxx*.\ *xxx*\ .10  **PC** VM IP, Prism Central
10.*xxx*.\ *xxx*\ .15  **DC1** VM IP, nutanix.local Domain Controller
10.*xxx*.\ *xxx*\ .16  **DC2** VM IP, nutanix.local Domain Controller
10.*xxx*.\ *yyy*\ .65  **Gateway** 10.*xxx*.\ *yyy*\ .64/26
10.*xxx*.\ *yyy*\ .128 **Gateway** 10.*xxx*.\ *yyy*\ .128/25
====================== ==============================================


Each cluster is configured with 1 VLAN which can be used for VMs:


================= ========================= ====== =============================================
Network           Name Address              VLAN   DHCP Scope
================= ========================= ====== =============================================
Network-01        10.*xxx*.\ *yyy*\ .64/26  0      10.*xxx*.\ *yyy*\ .97-10.*xxx*.\ *yyy*\ .125
Network-02        10.*xxx*.\ *yyy*\ .129/25 yyy1   10.*xxx*.\ *yyy*\ .132-10.*xxx*.\ *yyy*\ .254
Unmanaged Network                           71
================= ========================= ====== =============================================



Credentials
...........

.. note::

  The *<Password>* is the Same for all

============= ========== ====================
Credential    Username   Password
============= ========== ====================
Prism Element admin      *<Password>*
Prism Central admin      *<Password>*
Controller VM nutanix    *<Password>*
Prism Central VM nutanix *<Password>*
============= ========== ====================



Each cluster has a dedicated domain controller VM, **DC1**, **DC2** responsible for providing AD services for the **nutanix.local** domain. The domain is populated with the following Users and Groups:

================================ ============================================================================================== ====================
Group                            Username(s)                                                                                    Password
================================ ============================================================================================== ====================
Customer-A-Admin-Account-Group   adm-User-1-A, adm-User-2-A, adm-User-3-A, adm-User-4-A, adm-User-5-A                           *<Password>*
Customer-A-Service-Account-Group ntnx-bck-svc-A, ntnx-exc-svc-A, ntnx-ntx-svc-A, ntnx-psr-svc-A, ntnx-sql-svc-A, ntnx-xda-svc-A *<Password>*
Customer-A-User-Account-Group    user-1-A, user-2-A, user-3-A, user-4-A, user-5-A                                               *<Password>*
Customer-B-Admin-Account-Group   adm-User-1-B, adm-User-2-B, adm-User-3-B, adm-User-4-B, adm-User-5-B                           *<Password>*
Customer-B-Service-Account-Group ntnx-bck-svc-B, ntnx-exc-svc-B, ntnx-ntx-svc-B, ntnx-psr-svc-B, ntnx-sql-svc-B, ntnx-xda-svc-B *<Password>*
Customer-B-User-Account-Group    user-1-B, user-2-B, user-3-B, user-4-B, user-5-B                                               *<Password>*
Customer-C-Admin-Account-Group   adm-User-1-C, adm-User-2-C, adm-User-3-C, adm-User-4-C, adm-User-5-C                           *<Password>*
Customer-C-Service-Account-Group ntnx-bck-svc-C, ntnx-exc-svc-C, ntnx-ntx-svc-C, ntnx-psr-svc-C, ntnx-sql-svc-C, ntnx-xda-svc-C *<Password>*
Customer-C-User-Account-Group    user-1-C, user-2-C, user-3-C, user-4-C, user-5-C                                               *<Password>*
Customer-D-Admin-Account-Group   adm-User-1-D, adm-User-2-D, adm-User-3-D, adm-User-4-D, adm-User-5-D                           *<Password>*
Customer-D-Service-Account-Group ntnx-bck-svc-D, ntnx-exc-svc-D, ntnx-ntx-svc-D, ntnx-psr-svc-D, ntnx-sql-svc-D, ntnx-xda-svc-D *<Password>*
Customer-D-User-Account-Group    user-1-D, user-2-D, user-3-D, user-4-D, user-5-D                                               *<Password>*
================================ ============================================================================================== ====================


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
