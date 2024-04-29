# Satellite Automation Workshop
Welcome to today's Satellite Automation Workshop! We are very excited to present a bit of a tour along with some exercises that will help your teams understand how Ansible Automation Platform integrates with Red Hat Satellite to manage OS patching and content deployment in a predictable, automated way. 


Before we get started, let's log into your student seat:

> Assign yourself a student number using [Student Assignments](https://aap2-april26test.lab-emergent360.com/#studentinfo)

![student assignment page](https://github.com/Emergent360/satautomation/assets/18014714/cffcfda9-2488-4fe9-b75b-8a935870d960)


> For more information on Ansible Best Practices, playbooks, inventory creation, roles, and modules; checkout this deck: [Ansible Best Practices](https://aap2.demoredhat.com/decks/ansible_best_practices.pdf) 



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

1. Introduction to Ansible Automation Platform (AAP):

We'll kick things off with an overview of AAP, its key components, and its numerous benefits for automating infrastructure, applications, and IT workflows.
Learn how AAP builds upon the foundation of Ansible Tower and introduces features like centralized management, role-based access control, and enhanced security.

A chart of today's workshop environment looks like this:

![ansible_smart_mgmt_diagram](https://github.com/Emergent360/satautomation/assets/18014714/51aea489-b1f3-4d17-9696-3bc6802a18e2)

## **Environment** ##

**Role**	                        **Inventory name**


mindmap
  ansible-1 satellite
    RHEL
      node1
      node2
      node3
    CentOS
      node4
      node5
      node6




2. Diving into the AAP User Interface:

Get comfortable navigating the intuitive AAP user interface. We'll explore dashboards, inventories, projects, and credentials – the building blocks for your automation adventures.
Learn how to manage your infrastructure within AAP, including adding machines, groups, and cloud resources.
3. Building Your First Playbook:

Now comes the fun part! We'll delve into the world of Ansible playbooks, the heart of automation. You'll learn how to write playbooks using YAML syntax to automate tasks.
We'll walk you through the structure of a playbook, covering modules, tasks, variables, and conditionals.
Get hands-on experience by building your first basic playbook to automate a simple task on your managed machines.
4. Advanced Playbook Techniques:

Don't stop there! We'll explore advanced playbook features like loops, conditionals, error handling, and templating. These powerful tools will enable you to create sophisticated automations that adapt to various conditions.
Learn how to manage complex workflows by breaking them down into smaller, reusable playbooks.
5. Inventory Management:

Efficient inventory management is crucial for scaling your automation. We'll explore how to manage inventories in AAP, including adding machines by IP address, hostname, or cloud provider.
Learn how to leverage dynamic inventories to automatically discover and manage your infrastructure.
6. Security and Access Control:

Security is paramount. We'll discuss the robust security features within AAP, including role-based access control (RBAC) and credential management.
Learn how to assign different levels of access to users and teams within your organization.
7. Putting it All Together:

We'll wrap up by showcasing some real-world examples of how AAP can be used to automate various tasks across IT operations, including provisioning servers, configuring software, and deploying applications.
Gain inspiration for how to leverage AAP to streamline your own processes and boost your team's efficiency.
Throughout the workshop, there will be ample opportunities for hands-on practice, Q&A sessions, and interaction with your fellow participants and trainers.

Get ready to embark on your automation journey with Ansible Automation Platform!



## **Satellite Tour**

During this portion of today's workshop, we will give you a comprehensive overview of Red Hat Satellite, a powerful management tool for Red Hat Enterprise Linux (RHEL) deployments. We'll delve into its features, explore its functionalities, and discover how it can streamline your infrastructure management.  By the end of this workshop, you'll be equipped to leverage Satellite's capabilities to automate tasks, improve security, and achieve greater efficiency in managing your RHEL environment.

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

