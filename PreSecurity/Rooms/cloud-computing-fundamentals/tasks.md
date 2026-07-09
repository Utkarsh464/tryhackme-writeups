# Tasks: Cloud Computing Fundamentals

## Task 1: IaaS — Infrastructure as a Service
**Purpose:** Explain on-demand virtualised infrastructure in the cloud.

**Skills:** Provisioning VMs, storage volumes, virtual networks.

**Theory:** IaaS provides virtualised compute, storage, and networking resources on demand. Customers manage the OS, applications, and configurations. The cloud provider maintains the physical hardware, hypervisor, and facility. AWS EC2, Azure VMs, and GCP Compute Engine are IaaS offerings. IaaS offers flexibility but requires the most customer management.

**Commands:** `aws ec2 run-instances`, `az vm create`, `gcloud compute instances create`

---

## Task 2: PaaS — Platform as a Service
**Purpose:** Learn how PaaS abstracts OS management for application focus.

**Skills:** Deploying apps without managing infrastructure.

**Theory:** PaaS provides managed application hosting platforms. The provider handles the OS, runtime, web server, and scaling while the customer deploys code only. AWS Elastic Beanstalk, Azure App Services, Heroku, and Google App Engine are examples. PaaS speeds up development but limits control over the underlying environment.

**Commands:** `eb deploy`, `az webapp create`, `gcloud app deploy`

---

## Task 3: SaaS — Software as a Service
**Purpose:** Describe end-user applications delivered over the internet.

**Skills:** Using cloud applications, managing user access.

**Theory:** SaaS delivers fully functional applications over the internet, accessible via browser or client. Google Workspace, Microsoft 365, Salesforce, and Slack are examples. The provider manages all infrastructure and software — the customer simply uses the application. Security relies on the provider's controls and proper user access management.

**Commands:** (none — browser/API based)

---

## Task 4: Deployment Models and Shared Responsibility
**Purpose:** Understand public, private, hybrid, and multi-cloud strategies.

**Skills:** Choosing deployment models, dividing security responsibilities.

**Theory:** Public cloud (AWS/Azure/GCP) shares infrastructure across tenants. Private cloud is single-tenant, typically on-premises. Hybrid combines both. Multi-cloud uses multiple providers. The shared responsibility model divides security tasks: the provider secures the cloud (physical, network, hypervisor), while the customer secures what is IN the cloud (OS, apps, data, IAM).

**Commands:** `aws s3 ls`, `aws iam list-users`

---

## Task 5: Cloud Security Essentials
**Purpose:** Identify key cloud security risks and mitigation strategies.

**Skills:** IAM best practices, S3 bucket policies, least privilege.

**Theory:** Misconfigured S3 buckets exposing data is one of the most common cloud breaches. IAM policies must follow least privilege — granting only the permissions needed. Cloud-specific threats include credential leakage, privilege escalation via misconfigured IAM roles, and insecure API endpoints. Tools like CloudSploit and ScoutSuite help audit cloud configurations.

**Commands:** `aws s3api put-bucket-public-access-block`, `az role assignment list`

---