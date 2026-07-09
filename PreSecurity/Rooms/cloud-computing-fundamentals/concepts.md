# Concepts: Cloud Computing Fundamentals

## 1. IaaS (Infrastructure as a Service)
Provides on-demand access to virtualised compute, storage, and networking resources. Customers provision and manage VMs, configure firewalls, and install software — the provider manages the physical hardware, hypervisor, and facility. Offers the most flexibility and control but requires significant administration.

## 2. PaaS (Platform as a Service)
Delivers managed runtime environments for developing and deploying applications. Customers write and upload code while the provider handles the OS, runtime, scaling, load balancing, and middleware. PaaS reduces operational overhead but may restrict custom configurations and deployment options.

## 3. SaaS (Software as a Service)
Delivers fully functional software accessible via the internet, typically through a browser. The provider manages everything — infrastructure, platform, application, and data — and customers only manage configuration and user access. Most mainstream productivity tools (email, collaboration, CRM) are SaaS.

## 4. Public Cloud
Infrastructure is owned and operated by a third-party cloud provider and shared across multiple tenants (multi-tenancy). Resources are provisioned on-demand and metered. The provider manages the physical data centre, security, and compliance. Examples: AWS, Azure, GCP.

## 5. Private Cloud
Cloud infrastructure is provisioned for exclusive use by a single organisation, either on-premises or hosted by a third party. Offers more control, customisation, and isolation. Commonly used in regulated industries (finance, healthcare) with strict compliance and data sovereignty requirements.

## 6. Hybrid and Multi-Cloud
Hybrid cloud combines public and private clouds, enabling workload portability and bursting. Multi-cloud uses multiple public providers, avoiding vendor lock-in and increasing redundancy. Both require careful planning for networking, identity federation, and consistent security policies.

## 7. Shared Responsibility Model
The cloud provider is responsible for the security OF the cloud (physical security, hardware, network infrastructure, hypervisor). The customer is responsible for security IN the cloud (OS configuration, applications, IAM, data encryption, network traffic controls). The boundary shifts based on service model — IaaS gives more customer responsibility, SaaS more provider responsibility.

## 8. IAM and Least Privilege
Identity and Access Management controls who can access cloud resources and what actions they can perform. Least privilege dictates granting only the minimum permissions required. A misconfigured IAM role or overly permissive S3 bucket policy is a leading cause of cloud data breaches.