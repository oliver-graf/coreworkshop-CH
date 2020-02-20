.. _windows_tools_vm:

----------------
Windows Tools VM
----------------

Upload image
++++++++++++

This Windows Server 2012 R2 image comes pre-installed with a number of tools, including:

- Microsoft Remote Server Administration Tools (RSAT)
- PuTTY, CyberDuck, WinSCP
- Sublime Text 3, Visual Studio Code
- OpenOffice
- Python
- pgAdmin
- Chocolatey Package Manager

Deploy this VM on your assigned cluster if directed to do so as part of **Lab Setup**.

.. raw:: html

  <strong><font color="red">Only deploy the VM once, it does not need to be cleaned up as part of any lab completion.</font></strong>

Click the **gear** icon and in the **Settings** column on the left, locate and click **Image Configuration**.

**1**. Upload the **Windows disk image** to the Image Configuration:
    
  **a**. Click **+ Upload Image**.

  **b**. Fill in the **Create Image** dialog box fields as follows:

================= =======================
Name              **WinToolsVM**
Image Type        **DISK**
Storage Container **ISOs**
================= =======================


  **c**. In the **Create Image** dialog box, under **Image Source**, click **from URL**.

  **d**. http://10.42.194.11/workshop_staging/ToolsVM_02032020.qcow2

  **e**. Click **Save**.


Deploying Tools VM
++++++++++++++++++

In **Prism Elements** got to **VM > Table** and **+ Create VM**

Fill out the following fields:

- **Name** - *Initials*-Windows-ToolsVM
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 1
- **Number of Cores per vCPU** - 2
- **Memory** - 4 GiB

- Select **+ Add New Disk**
    - **Type** - DISK
    - **Operation** - Clone from Image Service
    - **Image** - ToolsVM.qcow2
    - Select **Add**

- Select **Add New NIC**
    - **VLAN Name** - Network-02
    - Select **Add**

Click **Save** to create the VM.

Power on the VM.

Login to the VM via RDP or Console session, using the following credentials:

- **Username** - NTNXLAB\\Administrator
- **password** - nutanix/4u
