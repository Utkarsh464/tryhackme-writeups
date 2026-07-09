# Cloud Computing

## Definition
Cloud computing delivers on-demand computing resources (servers, storage, databases, networking, software) over the internet. Three service models: **IaaS** (Infrastructure as a Service — virtual machines, networking), **PaaS** (Platform as a Service — runtime environment for apps), **SaaS** (Software as a Service — ready-to-use applications). Deployment models: public, private, hybrid, multi-cloud.

## Why It Matters
Cloud adoption is ubiquitous. Security responsibilities are shared (Shared Responsibility Model): the provider secures *of* the cloud, the customer secures *in* the cloud. Misconfigurations (S3 buckets, IAM roles) are leading causes of breaches. Cloud-specific threats include credential exposure, insecure APIs, and metadata service attacks.

## Where It Appears in the Path
- Introduction to Cybersecurity

## Prerequisites
- Basic networking, OS concepts

## Key Points
- IaaS: most control, most customer security responsibility
- SaaS: least control, provider handles most security
- Shared Responsibility Model differs by service type
- Common threats: misconfigured storage, overly permissive IAM, exposed secrets

## Common Interview Questions
1. What is the Shared Responsibility Model?
**Answer:** The cloud provider secures the infrastructure; the customer secures their data, configs, and access.
2. What is a cloud security group?
**Answer:** A virtual firewall controlling inbound/outbound traffic to cloud resources.

## Further Reading
- NIST SP 800-145 (Cloud Computing Definition)
- CSA Security Guidance
- AWS Well-Architected Framework