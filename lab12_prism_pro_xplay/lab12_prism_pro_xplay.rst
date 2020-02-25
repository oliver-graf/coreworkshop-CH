.. _prism_pro_xplay:


Prism Pro: X-Play
--------------------------------------------

Overview
++++++++

Connect to Prism Central

   |image114|

Increase Constrained VM Memory with X-Play
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

In this lab story we will now use X-Play to create a Playbook to automatically add memory to the lab VM that was created earlier, when a memory constraint is detected.

#. Use the search bar to navigate to the **Playbooks** page.

   |image115|

#. We will start by creating a Playbook. Click **Create Playbook** at the top of the table view

   |image116|

#. Select Alert as a trigger

   |image117|

#. Search and select **VM {vm_name} Memory Constrained** as the alert policy, since this is the issue we are looking to take automated steps to remediate.

   |image118|

#. Select the *Specify VMs* radio button and choose the VM you created for the lab. This will make it so only alerts raised on your VM will trigger this Playbook.

   |image119|

#. We will first need to snapshot the VM. Click **Add Action** on the left side and select the **VM Snapshot** action.

   |image120|

#. The Target VM is auto filled with the source entity from the Alert trigger. To finish filling the details for this action, enter a value, such as **1**, in the Time to Live field.

   |image121|

#. Next we would like to remediate the constrained memory by adding more memory to the VM. Click **Add Action** to add the **VM Add Memory** action

   |image122|

#. Set the empty fields according to the screen below.

   |image123|


#. Next we would like to notify someone that an automated action was taken. Click **Add Action** to add the email action

   |image124|

#. Fill in the field in the email action. Here are the examples

**Recipient:** Fill in your email address.

**Subject :**
Playbook: Playbook Name Alert: Alert Name

**Message:**
Prism Pro X-FIT detected Alert: Alert Name in Alert: Source Entity Name  Prism Pro X-Play has run the playbook of Playbook: Playbook Name  As a result, Prism Pro increased 1GB memory in Alert: Source Entity Name

   |image125|

#. Click **Add Action** to add the **Acknowledge Alert** action

   |image126|

#. Click **Save & Close** button and save it with a name “*Initials* - Auto Increase Constrained VM Memory”. **Be sure to enable the ‘Enabled’ toggle.**

   |image127|

#. You should see a new playbook in the “Playbooks” list page.

   |image128|

#. Search for your VM and record the current memory capacity. You can scroll down in the properties widget to see the configured memory.

   |image129|

#. **Switch tabs back to** the http://10.42.247.70 page and press Continue from the Story 1-3 Step, if you have not already.

   |image130|

#. Now we will simulate an alert for ‘VM Memory Constrained’ which will trigger the Playbook we just created. Click the ‘Simulate Alert’ button to create the alert.

   |image131|

#. Go back to Prism page and check your VMs page again, you should now see the memory capacity is increased by 1GB. If the memory does not show updated you can refresh the browser page to speedup the process.

#. You should also receive an email. Check the email to see that its subject and email body have filled the real value for the parameters you set up.

#. Go to the **Playbook** page, click the playbook you just created.

   |image132|

#. Click the **Plays** tab, you should see that a play has just completed.

   |image133|

#. Click the “Play” to examine the details

   |image134|


Using X-Play with 3rd Party API
+++++++++++++++++++++++++++++++++++++++++++++

For this story we will be using Habitica to show how we can use 3rd Party APIs with X-Play. Habitica is a free habit and productivity app that treats your real life like a game. We will be creating a task with Habitica.


#. Use the search bar to navigate to the **Playbooks** page.

   |image135|

#. We will start by creating a Playbook. Click **Create Playbook** at the top of the table view

   |image136|

#. Use the search bar to navigate to the **Action Gallery** page.

   |image137|

#. Click the checkbox next to the item for ‘Rest API’ and then from the actions menu select the ‘Clone’ option.

   |image138|

#. We are creating an Action that we can later use in our playbook to create a Task in Habitica. Fill in the following values replacing your name in the <YOUR NAME HERE> part.

**Name:** *Initials* - Create Habitica Task

**Method:** POST

**URL:** https://habitica.com/api/v3/tasks/user

**Request Body:** ``{"text":"*Initials* Check {{trigger[0].source_entity_info.name}}","type":"todo","notes":"VM has been detected as a bully VM and has been temporarily powered off.","priority":2}``

**Request Header:**

| x-api-user:fbc6077f-89a7-46e1-adf0-470ddafc43cf
| x-api-key:c5343abe-707a-4f7c-8f48-63b57f52257b
| Content-Type:application/json;charset=utf-8


   |image139|

#. Click the **copy** button to save the action.

#. Navigate back to the Playbooks page using the search bar.

#. Select the **Alert trigger** and search for and select the alert policy **VM Bully {vm_name}**. This is the alert that we would like to act on to handle when the system detects a Bully VM.

   |image140|

#. Select the **Specify VMs** radio button and choose the VM you created for the lab. This will make it so only alerts raised on your VM will trigger this Playbook.

   |image141|

#. The first thing we would like to do is Power off the VM, so we can make sure it is not starving other VMs of resources. Click the **Add Action** button and select **Power Off VM**.

   |image142|

#. Next we would like to create a task so that we can look into what is causing this VM to be a Bully. Add another Action. This time select the action you created called, Create Habitica Task.

   |image143|

#. Add one more action, select the Acknowledge Alert action. Use the parameters for this action to fill in the ‘Alert’ parameter.

   |image144|

#. Save & Enable the playbook. You can name it  “*Initials* - Power Off Bully VM for Investigation”. **Be sure to enable the ‘Enabled’ toggle.** Click the Save button.

   |image145|

#. **Switch back to the other tab** running http://10.42.247.70 and Simulate the ‘VM Bully Detected’ alert for Story 5.

   |image146|

#. Once the alert is successfully simulated, you can check that your Playbook ran, and view the details as before.

   |image147|

#. You can verify the Rest API was called for Habitica by logging in from another tab at https://habitica.com using the credentials:

| Username : next19LabUser
| Password: Nutanix.123

And verify your task is created.

   |image148|

Takeaways
+++++++++

- X-Play, the IFTTT for the enterprise, is our engine to enable the automation of daily operations tasks.
- X-Play enables admins to confidently automate their daily tasks within minutes.
- X-Play is extensive that can use customer’s existing APIs and scripts as part of its playbooks.



.. |image114| image:: images/ppro_76.png
.. |image115| image:: images/ppro_26.png
.. |image116| image:: images/ppro_27.png
.. |image117| image:: images/ppro_28.png
.. |image118| image:: images/ppro_29.png
.. |image119| image:: images/ppro_29b.png
.. |image120| image:: images/ppro_30.png
.. |image121| image:: images/ppro_32.png
.. |image122| image:: images/ppro_33.png
.. |image123| image:: images/ppro_34.png
.. |image124| image:: images/ppro_35.png
.. |image125| image:: images/ppro_36.png
.. |image126| image:: images/ppro_37.png
.. |image127| image:: images/ppro_39.png
.. |image128| image:: images/ppro_40.png
.. |image129| image:: images/ppro_41.png
.. |image130| image:: images/ppro_08b.png
.. |image131| image:: images/ppro_64.png
.. |image132| image:: images/ppro_44.png
.. |image133| image:: images/ppro_45.png
.. |image134| image:: images/ppro_46.png
.. |image135| image:: images/ppro_26.png
.. |image136| image:: images/ppro_27.png
.. |image137| image:: images/ppro_47.png
.. |image138| image:: images/ppro_48.png
.. |image139| image:: images/ppro_49.png
.. |image140| image:: images/ppro_50.png
.. |image141| image:: images/ppro_50b.png
.. |image142| image:: images/ppro_51.png
.. |image143| image:: images/ppro_53.png
.. |image144| image:: images/ppro_54.png
.. |image145| image:: images/ppro_55.png
.. |image146| image:: images/ppro_65.png
.. |image147| image:: images/ppro_75.png
.. |image148| image:: images/ppro_57.png
.. |image149| image:: images/ppro_77.png
.. |image150| image:: images/ppro_78.png

