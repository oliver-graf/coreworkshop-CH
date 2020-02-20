.. _linux_tools_vm:

---------------
Linux Tools VM
---------------

Overview
+++++++++

This CentOS VM image will be staged with packages used to support multiple lab exercises.

Deploy this VM on your assigned cluster if directed to do so as part of **Lab Setup**.

.. raw:: html

  <strong><font color="red">Only deploy the VM once, it does not need to be cleaned up as part of any lab completion.</font></strong>

Click the **gear** icon and in the **Settings** column on the left, locate and click **Image Configuration**.

**1**. Upload the **CentOS ISO** to the Image Configuration:
    
  **a**. Click **+ Upload Image**.

  **b**. Fill in the **Create Image** dialog box fields as follows:

================= =======================
Name              **Linux_ToolsVM**
Image Type        **DISK**
Storage Container **ISOs**
================= =======================


  **c**. In the **Create Image** dialog box, under **Image Source**, click **from URL**.

  **d**. http://10.42.194.11/workshop_staging/Linux_ToolsVM.qcow2

  **e**. Click **Save**.

Deploying CentOS
++++++++++++++++

In **Prism Elements** got to **VM > Table** and **+ Create VM**

Fill out the following fields:

- **Name** - *Initials*-Linux-ToolsVM
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 1
- **Number of Cores per vCPU** - 2
- **Memory** - 2 GiB

- Select **+ Add New Disk**
    - **Type** - DISK
    - **Operation** - Clone from Image Service
    - **Image** - Linux_ToolsVM.qcow2
    - Select **Add**

- Select **Add New NIC**
    - **VLAN Name** - Network-02
    - Select **Add**

Click **Save** to create the VM.

Power on the VM.
