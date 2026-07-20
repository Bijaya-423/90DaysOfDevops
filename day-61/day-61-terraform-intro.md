Task 1: Understand Infrastructure as Code
==========================================
What is Infrastructure as Code (IaC)? Why does it matter in DevOps?
--------------------------------------------------------------------
-> infrastructure as code (iac) is a modern it practives that automatically manages and sets up technology a modern IT practice that automatically manages and sets up technology resources (like servers, networks, and databases) using machine-readable definition files, instead of manually configuring them through a graphic interface or physical hardware.


-> The Manual Way: A system administrator logs into a cloud provider's dashboard, clicks buttons, and manually types in settings to create a virtual server.
-> The IaC Way: A developer writes a text file that lists all the needed ingredients (e.g., "give me 2 servers, a firewall, and 2 gigabytes of memory"). An IaC tool reads this file and builds the exact environment automatically.

DevOps is a cultural and technical philosophy that unites software developers and IT operations teams to deliver software faster. IaC is a cornerstone of DevOps for several key reasons

- Version control
- consistency
- speed and scalability
- seamless ci/cd

What problems does IaC solve compared to manually creating resources in the AWS console?
----------------------------------------------------------------------------------------
-> Infrastructure as Code (IaC) is the practice of managing cloud resources using machine-readable configuration files rather than manual clicks. It solves major problems like human error, deployment delays, and "configuration drift" (where manual tweaks over time cause differences between development and production environments).

1. Replicating Exact EnvironmentsManual Console: You have to click through menus over and over, which is tedious and risks missing a step when setting up copies like Development, Testing, and Production.IaC: You write the setup down in a text file. You can deploy this exact same "blueprint" across different AWS accounts or regions with a single command, ensuring all environments are 100% identical.
2. Eliminating Human ErrorManual Console: It is easy to mistype an IP address, forget to encrypt a storage bucket, or select the wrong server size.IaC: The code is the single source of truth. Once tested and verified, it removes human error and ensures settings are applied perfectly every single time.

How is Terraform different from AWS CloudFormation, Ansible, and Pulumi?
-------------------------------------------------------------------------
Terraform is an open-source, declarative Infrastructure as Code (IaC) tool that manages multi-cloud environments using state files.While tools like AWS CloudFormation, Ansible, and Pulumi share similarities, they differ fundamentally in cloud compatibility, language design, state management, and primary purpose

Feature       | Terraform         | AWS CloudFormation | Ansible  | Pulumi
cloud         |Multi-Cloud
support       |
              |
language      |HCL (Declarative)
              |
primary       |Orchestration
use           |
              |
state file    |Yes (Managed)

What does it mean that Terraform is "declarative" and "cloud-agnostic"?











