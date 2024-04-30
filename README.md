![logos](https://github.com/Emergent360/satautomation/assets/18014714/13b3e5b4-0b94-4b0d-b92e-c79b183ffc89)


# Satellite Automation Workshop
Welcome to today's Satellite Automation Workshop! We are very excited to present a bit of a tour along with some exercises that will help your teams understand how Ansible Automation Platform integrates with Red Hat Satellite to manage OS patching and content deployment in a predictable, automated way. 


Before we get started, let's log into your student seat:

> Assign yourself a student number using [Student Assignments](https://aap2-smrtmgmt-april.lab-emergent360.com/)

![student assignment page](https://github.com/Emergent360/satautomation/assets/18014714/cffcfda9-2488-4fe9-b75b-8a935870d960)


> For more information on Ansible Best Practices, playbooks, inventory creation, roles, and modules; take a look at this deck: [Ansible Best Practices](https://aap2.demoredhat.com/decks/ansible_best_practices.pdf) 



## **Use Cases** ##
This workshop currently focuses on 4 main customer pain points: 

- Compliance (OpenSCAP Scanning) and Vulnerability Management
- Patch/Package Management
- CentOS to RHEL conversion
- Vulnerability Management with Insights

## **Presentation** ##
The exercises are self-explanatory and are meant to guide participants through the entire lab. All concepts are explained as they are introduced. 

Today's presentation is available to support the workshop and explain Automation, the basics of Ansible and the topics of the exercises in more detail. Today's Workshop presentation can be downloaded [here](https://uploads-ssl.webflow.com/64dd02f7406bf2448a30e68f/662fdbc786abd010d11d18b8_Satellite%20Automation.pdf)

## **Time Planning and CPE Credits** ##
The time required to do the workshops strongly depends on multiple factors: the number of participants, how familiar those are with Linux in general and how much discussions are done in between.

Having said that, the presentation should take about 40 minutes, with a 10-minute break, then the exercises themselves should take roughly 3 hours. We will break every 40 minutes or so to complete three polling questions, allowing the group to qualify for CPEs. This workshop is accredited by NASBA, which requires one CPE credit to be awarded for every 50 minutes of teaching. The polling questions ensure participants are present and working on presented content. You will be awarded credits as long as you respond to the polling questions. 

Certificates with the awarded amount of CPEs should be sent out to the attendees within 5 business days, post-event. 

## **Welcome to Your Ansible Automation Platform Workshop Tour!**
Get ready to unlock the power of automation! This workshop will guide you through the exciting world of Ansible Automation Platform (AAP), equipping you to automate IT tasks and streamline your processes.

Here's what you can expect today:

An Introduction to Ansible Automation Platform (AAP).

We'll kick things off with an overview of AAP, its key components, and its numerous benefits for automating infrastructure, applications, and IT workflows.
Learn how AAP builds upon the foundation of Ansible Tower and introduces features like centralized management, role-based access control, and enhanced security.

A chart of today's workshop environment looks like this:

![ansible_smart_mgmt_diagram](https://github.com/Emergent360/satautomation/assets/18014714/51aea489-b1f3-4d17-9696-3bc6802a18e2)

## **Environment** ##

![Environment](https://github.com/Emergent360/satautomation/assets/18014714/5f2170d8-4a2f-4a63-b08e-8d1db6f1dde8)


Then, we will dive into the AAP User Interface:

Get comfortable navigating the intuitive AAP user interface. We'll explore dashboards, inventories, projects, and credentials – the building blocks for your automation adventures.
Learn how to manage your infrastructure within AAP, including adding machines, groups, and cloud resources.

Next up, we will build our First Playbook:

Now comes the fun part! We'll delve into the world of Ansible playbooks, the heart of automation. You'll learn how to write playbooks using YAML syntax to automate tasks.
We'll walk you through the structure of a playbook, covering modules, tasks, variables, and conditionals.

Get hands-on experience by building your first basic playbook to automate a simple task on your managed machines.

After building our first playbook, we will use some more advanced Playbook techniques:

Don't stop there! We'll explore advanced playbook features like loops, conditionals, error handling, and templating. These powerful tools will enable you to create sophisticated automations that adapt to various conditions.

Learn how to manage complex workflows by breaking them down into smaller, reusable playbooks.

We will of course take a look at Inventory management as well:

Efficient inventory management is crucial for scaling your automation. We'll explore how to manage inventories in AAP, including adding machines by IP address, hostname, or cloud provider.
Learn how to leverage dynamic inventories to automatically discover and manage your infrastructure.

Finally, we'll take a look at Security and Access Control:

Security is paramount. We'll discuss the robust security features within AAP, including role-based access control (RBAC) and credential management.
Learn how to assign different levels of access to users and teams within your organization.

Putting it All Together:

We'll wrap up by showcasing some real-world examples of how AAP can be used to automate various tasks across IT operations, including provisioning servers, configuring software, and deploying applications.

Gain inspiration for how to leverage AAP to streamline your own processes and boost your team's efficiency.
Throughout the workshop, there will be ample opportunities for hands-on practice, Q&A sessions, and interaction with your fellow participants and trainers.

Get ready to embark on your automation journey with Ansible Automation Platform!

## **Objective** ##

The objective of this exercise is to setup the lab environemnt following an Infrastructure as Code process. This exercise will require you to launch a series of playbooks. The playbooks accomplish the following:

Populate Ansible Controller with an inventory source, add templates, as well as an additional project.
Publish RHEL7 dev content view in Satellite
Register servers to the Satellite installation - RHEL7
Register servers to the Satellite installation - CentOS7
Populate dynamic inventories - RHEL7
Populate dynamic inventories - CentOS7

## **Exercise One** ##
 Log into your Ansible Automation Platform (AAP2) Controller

 Use the link found [here](https://aap2-april26test.lab-emergent360.com/#studentinfo)
 ![Student View](https://github.com/Emergent360/satautomation/assets/18014714/a68794ef-27a2-4e47-a651-5cb90863cc31)


 Select the link noted for "Automation controller"
![AAP2](https://github.com/Emergent360/satautomation/assets/18014714/f8933677-a55e-4284-958e-411620b0e7b5)

Once logged in, you should be able to see the Ansible Automation Platform dashboard:

![Dashboard](https://github.com/Emergent360/satautomation/assets/18014714/84c26793-30d0-4e0b-89dd-424a087f19cd)

Use the side pane menu on the left to select Projects and review the two projects named Automated Management and Fact Scan. These projects, along with the Workshop Inventory under Resources, and Inventories, have been set up for you during the provisioning of the lab environment. 

<img width="1423" alt="Projects" src="https://github.com/Emergent360/satautomation/assets/18014714/aaa8bf2a-b366-4302-944a-cfb04bc1ada2">

## **Exercise Two** ##

Next, we will execute our first job template. We'll be working with several templates during today's workshop, and this step uses a couple of them to initialize the lab environment. 

<img width="1423" alt="Templates" src="https://github.com/Emergent360/satautomation/assets/18014714/c05f3c6c-4264-4e80-8a00-a2eaa4172183">

You should initially see three Templates, named Demo Job Template, Z / CaC / Controller, and Z / CaC / Satellite 

Notice that the Z / CaC / Satellite template has already been run for you.

We will have to run the Z / CaC / Controller job template. To do this, click either into the job template and click Launch, or click the Rocketship icon. 

<img width="1422" alt="controller" src="https://github.com/Emergent360/satautomation/assets/18014714/a2cd2502-1d65-4146-8d00-0ef265de1b04">

You will be taken under the Views, Jobs output window, where you can view the output from the job run. This will display all the tasks executed as part of the playbook. This should take about two minutes to complete and you should see a green "Successful" tag after the name of the playbook in this view once the last task has completed. 

<img width="1425" alt="Controller Play" src="https://github.com/Emergent360/satautomation/assets/18014714/ec278bcb-43f4-4623-aeaa-5811166088f9">

Remember to wait until you see the green "Successful" tag before moving on to the next exercise. 

Then, navigate back to Templates on the left side pane. 

You will notice many more Job Templates have been provisioned in your Controller. We will use some of these in today's workshop. 

<img width="1436" alt="Templates" src="https://github.com/Emergent360/satautomation/assets/18014714/a807edef-6232-44a8-b132-f6966490294f">

Next, let's run SATELLITE / RHEL - Publish Content View job template by clicking the rocketship icon or by pressing the Launch button. When prompted by the survey for the content view to publish, from the drop down menu, select RHEL 7. 

<img width="1432" alt="Publish Content View" src="https://github.com/Emergent360/satautomation/assets/18014714/df91cd75-218b-4b8f-9501-e6ac0aa9b8a6">

<img width="1118" alt="Survey" src="https://github.com/Emergent360/satautomation/assets/18014714/7cdd8bf6-c7ad-4b52-9bdb-6fa190c05ef2">

> Hit Next, then Launch.

You will be taken to the Jobs view, showing the output window for the template SATELLITE / RHEL - Publish Content View. This job will take about a minute to run. 

<img width="1434" alt="Publish Content View" src="https://github.com/Emergent360/satautomation/assets/18014714/35fc21d8-bb3c-455f-a11a-34d722e9f85a">

Next, click on Templates and search for CONVERT2RHEL / 01 - Take node snapshot job template. Click on the rocketship icon or the template, and click Launch. This job template will take longer, about seven minutes to complete. 

<img width="1431" alt="Convert2RHEL Take Snapshot" src="https://github.com/Emergent360/satautomation/assets/18014714/3f8b53bc-9b27-4ad7-a633-c1c723ee4779">

<img width="1436" alt="Node Snapshot Output" src="https://github.com/Emergent360/satautomation/assets/18014714/8b7f0ce8-1374-4e7a-a475-ab6f356fd761">

Next up, click on Templates, search for, and run the SERVER / CentOS7 - Register job template by clicking the rocketship icon or by clicking into the template and selecting Launch. When the survey appears, complete it as follows:

<img width="1433" alt="CentOS Register" src="https://github.com/Emergent360/satautomation/assets/18014714/7dd787a3-cd77-4a68-87e4-d9819016c7e1">

<img width="1120" alt="CentOS Register Survery" src="https://github.com/Emergent360/satautomation/assets/18014714/7584c257-c0f2-4c5e-ab7d-46e97280c17c">

The SERVER / CentOS7 - Register output window will appear, showing you the results of each task executed as part of the playbook. 

<img width="1436" alt="CentOS7 Register Output" src="https://github.com/Emergent360/satautomation/assets/18014714/3794c1c5-9c5b-4754-9d49-a5b61946b2eb">

Next, go back to Templates and run the EC2 / Set instance tags based on the Satellite (Foreman) facts job template by clicking the rocketship icon or clicking into the job template and selecting Launch.

<img width="1432" alt="EC2 instance tags" src="https://github.com/Emergent360/satautomation/assets/18014714/91855439-4681-4db6-8ef9-21f41727e981">

<img width="1434" alt="EC2 set instance tags" src="https://github.com/Emergent360/satautomation/assets/18014714/e3843364-a4c2-4eb1-8f75-a0cf5b620d7c">

Next up, click on Templates, search for EC2 / Set instance tag - Ansible Group template, click the rocketship or click on the template and select Launch 

<img width="1435" alt="EC2 instance tag Ansible Group" src="https://github.com/Emergent360/satautomation/assets/18014714/d774a3ad-d2bd-4e04-b87e-0209a69e3c68">

Note that Ansible is being directed to map nodes to a group name. This will be used later via dynamic inventory building to create Ansible inventory groups. 

<img width="1438" alt="Ansible Inventory Group Tags creation" src="https://github.com/Emergent360/satautomation/assets/18014714/aa04ccf0-8365-4eb0-aa8b-0009f2608385">

## **Exercise Three** ##

Dynamic inventories can be populated via dynamic sources

Before running additional templates, click on the Inventories menu item and select All Development and the Hosts tab. Do the same for CentOS7 and RHEL7 Development inventories. You will notice the Hosts tab on each is empty. Note the Sources tab as well, looking at the Details tab to see the source variables that will be used. 

Let's run a Template to update these inventories. Search and run the CONTROLLER / Update inventories via dynamic sources job template by clicking the rocketship icon or selecting the job template and selecting Launch. 

<img width="1435" alt="Update inventories" src="https://github.com/Emergent360/satautomation/assets/18014714/231270d9-c82a-4418-be25-6e6fc6950000">

Complete the Survey:

<img width="1118" alt="Inventories Survey" src="https://github.com/Emergent360/satautomation/assets/18014714/bcaca8b1-577b-4c8e-b090-f1cbdc71a661">

<img width="1436" alt="Inventories output" src="https://github.com/Emergent360/satautomation/assets/18014714/340be4f2-8247-4b8c-ba8e-13d7ada2e0c4">

Run the same template again, this time to update the CentOS7 instances. You will still need to select the Templates link from the menu, otherwise you will just rerun the template with the same survey if you select the rocketship icon directly from the CONTROLLER / Update inventories via dynamic sources output page you are currently on. 

<img width="1437" alt="Controller for CentOS7 template" src="https://github.com/Emergent360/satautomation/assets/18014714/1b812aab-6702-4da2-8285-6dfd442ad36d">

Complete the survey this time with these variables

<img width="1120" alt="CentOS7 survey variables" src="https://github.com/Emergent360/satautomation/assets/18014714/026c980c-68b9-44dc-9701-e5626d7e37a1">

<img width="1431" alt="CentOS7 inventories output" src="https://github.com/Emergent360/satautomation/assets/18014714/79ae99f9-c119-4310-86e9-b8f79516768b">



## **Satellite Tour**

During this portion of today's workshop, we will give you a comprehensive overview of Red Hat Satellite, a powerful management tool for Red Hat Enterprise Linux (RHEL) deployments. We'll dive into its features, explore its functionalities, and discover how it can streamline your infrastructure management.  By the end of this portion of the workshop, you'll be equipped to leverage Satellite's capabilities to automate tasks, improve security, and achieve greater efficiency in managing your RHEL environment.

Satellite provides many benefits within your IT stack, namely, it serves as...

A centralized management platform for Red Hat Enterprise Linux (RHEL) systems.

Simplifies and automates tasks like provisioning, configuration management, patch management, and subscription management.

Provides a single point of control for managing your entire RHEL infrastructure.

Reduced Costs: Saves time and resources by automating tasks.

Increased Efficiency: Streamlines workflows and simplifies management.

Improved Security: Enhances security posture by automating patch deployment and vulnerability management.

Enhanced Compliance: Simplifies compliance audits with centralized reporting and audit trails.

System Provisioning: Automate the deployment of new RHEL systems with pre-configured settings.

Configuration Management: Apply and enforce consistent configurations across your entire RHEL environment.

Patch Management: Automate the deployment of security patches and software updates to ensure your systems stay up-to-date.

Subscription Management: Manage and track RHEL subscriptions for all your systems from a central location.

Content Delivery: Efficiently distribute content like patches, software updates, and configuration files to your RHEL systems.

Reporting and Auditing: Generate comprehensive reports for compliance audits and track system activity.

Satellite Server: The central management hub that controls and coordinates all Satellite operations.

Capsule Servers (Optional): Optional servers deployed closer to remote systems for faster content delivery and reduced network traffic.

Client Systems: RHEL systems managed by Satellite.

Content Repositories: Repositories containing software packages, patches, and configuration files.

External Systems: External systems like identity management and subscription management services.

We ran several playbooks in Ansible to help configure our Satellite environment. As we are taking our tour today, open your instance of Satellite by clicking the link from your student environment 

![Workbench](https://github.com/Emergent360/satautomation/assets/18014714/400a06cd-b2b7-4b00-abd7-a96d6490ea75)

Once logged into Satellite, click the Hosts button from the side panel menu, then select All Hosts.

<img width="1436" alt="All Hosts" src="https://github.com/Emergent360/satautomation/assets/18014714/bb973cd3-a9d9-4266-b4d8-7534137fba45">

You should see your RHEL 7 and CentOS7 instances appearing in your list of hosts. These nodes are now registered to your instance of Satellite. 

Next, let's verify that all your content is available for your Dev, QA, and Prod environments. To do this, click on Content, then Content Views, then search for RHEL7. 

<img width="1437" alt="Content" src="https://github.com/Emergent360/satautomation/assets/18014714/7c2f9602-ab05-4d8b-8820-468b28c10dbf">

As we continue our tour, we will learn how to configure and perform an OpenSCAP scan using playbooks in Ansible Automation Platform 2 with Satellite. When running multiple Red Hat Enterprise Linux systems, it's important to keep all of these systems compliant with a meaningful security policy and perform security scans often. OpenSCAP is an open source project that is used by government agencies, corporations, as well as e-commerce (just to name a few examples). OpenSCAP provides tools for automated vulnerability checking. Satellite can be loaded with RPM packages for SCAP workbench v1.2.0-8 which will provide scanning capabilities. Satellite is also loaded with the SCAP security guide v0.1.54-3 for RHEL7 and CentOS device which provides the appropriate XCCDF benchmarks for PCI and STIG compliance for the purpose of this exercise. This exercise will focus on RHEL systems, CentOS will be out of scope. 

## **Exercise Four** ##

Now, we will create a new compliance policy. To do this, we will configure a compliance policy that we can use to scan our RHEL nodes. 

In Satellite, hover over Hosts in the panel to the left and click on Policies. 

<img width="1438" alt="Compliance Policies" src="https://github.com/Emergent360/satautomation/assets/18014714/b7bb7bb0-0cb5-4bdd-b9e4-364031a80b24">

Click on New Compliance Policy and complete each of the steps.

<img width="1438" alt="Deployment Options" src="https://github.com/Emergent360/satautomation/assets/18014714/8ed52c93-05cf-4b99-84e9-93e21ec5d3d9">

Leave Manual selected and click on Next. 

<img width="1434" alt="Policy Attributes" src="https://github.com/Emergent360/satautomation/assets/18014714/63000c44-cb78-4b72-af01-7457ea80196b">

Under the Policy Attributes tab, enter PCI_Compliance in both the Name and Description fields. If it gives you an error that the name has already been taken, you can use PCI_Compliance2 

Click on Next. 

Under the SCAP Content tab, select Red Hat rhel7 default content in the SCAP Content drop-down box, followed by PCI-DSS v3.2.1 Control Baseline for Red Hat Enterprise Linux 7 in the XCCDF Profile drop-down box. 

<img width="1437" alt="SCAP Content tab" src="https://github.com/Emergent360/satautomation/assets/18014714/3e1e49da-3cdb-4c52-941e-1b43d2963ce2">

Click on Next. 

Select Weekly and Monday for the Schedule tab. 

<img width="1438" alt="Schedule tab" src="https://github.com/Emergent360/satautomation/assets/18014714/3d314e01-b765-44c9-b02f-fe66c7c60802">

Click on Next. 

Keep the default values for the Locations tab.

<img width="1439" alt="Locations tab" src="https://github.com/Emergent360/satautomation/assets/18014714/d4fcac82-d175-46e0-9eb8-02e84199cdfa">

Click on Next. 

Keep the default values for the Organizations tab.

<img width="1437" alt="Organizations tab" src="https://github.com/Emergent360/satautomation/assets/18014714/7cc3ace0-da86-44a4-bdf8-60a55b4d25da">

Click on Next. 

Keep the default values for the Hostgroups tab. 

<img width="1439" alt="Hostgroups tab" src="https://github.com/Emergent360/satautomation/assets/18014714/b82914ac-90d0-48e2-9d5f-44036fc8e634">

Click Submit. 





## **Convert2RHEL** ##

Next up, let's use Convert2RHEL to upgrade a CentOS 7 node to RHEL. To do this, we will first SSH into a node. We can use Node4 for this exercise. 

1. SSH into Node4

```
   ssh centos@node4
``` 

3. Login and sudo to root

```
   sudo su
```

4. Update CentOS box and reboot
 
```
  yum update -y
```

```
   reboot
```

6. Login again, sudo to root

```
   ssh centos@node4
``` 

```
   sudo su
```

7. Download RH GPG key and install convert2rhel repo

```
   curl -o /etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release https://www.redhat.com/security/data/fd431d51.txt
```

```
    curl -o /etc/yum.repos.d/convert2rhel.repo https://ftp.redhat.com/redhat/convert2rhel/7/convert2rhel.repo
```

8. Install convert2rhel utility

```
   yum -y install convert2rhel
```


10. Add activation key. INI file should look like below after opening file using VI. Update the "activation_key" value to convert2rhel_demo. 

```
vi /etc/convert2rhel.ini
```
        
	# -*- coding: utf-8 -*-
 	# This file should be in mode 0600
        # Example of configuration file convert2rhel.ini for secrets.
        # Possible locations of this file:
        # 1) user specified and passed by -c, --config-file option; highest priority
        # 2) ~/.convert2rhel.ini; lower priority
        # 3) /etc/convert2rhel.ini; the lowest priority

        [subscription_manager]
        # password = <insert_password>
        activation_key = convert2rhel_demo
        org            = 13156267


11. Run convert2rhel command

   ```
   convert2rhel --debug
```


11. IF the conversion fails, the kernel module may cause convert2rhel to fail, so we must ignore that step by setting following environment variable. Run the command below and try again. 

   ```
   export CONVERT2RHEL_ALLOW_UNAVAILABLE_KMODS=1
```


11. Reboot the system


12. Login again, sudo to root, and verify system has been upgraded to RHEL:

```
    uname –r
```

```
    cat /etc/redhat-release
```

```
    subscription-manager list
```

