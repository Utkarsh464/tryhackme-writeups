# Introduction to SIEM

## Room Information
- **URL**: https://tryhackme.com/room/introductiontosiem
- **Difficulty**: Easy
- **Subscription**: Premium
- **Estimated Time**: ~1 hour

## Description

Introduction to SIEM provides a comprehensive overview of Security Information and Event Management (SIEM) technology, the central nervous system of modern Security Operations Centers. A SIEM system aggregates log data from diverse sources across an organization, including servers, firewalls, endpoints, applications, cloud services, and network devices. It normalizes this data into a common schema, indexes it for fast searching, and applies correlation rules to identify patterns indicative of security threats. This room covers the complete SIEM architecture and lifecycle. Data collection is performed by forwarding agents installed on source systems, which send logs to the SIEM platform. The processing pipeline parses incoming logs, extracts structured fields (timestamps, source IPs, event types, user names), normalizes field names and values to a common taxonomy, and enriches data with additional context (geo-location of IP addresses, asset ownership, threat intelligence matches). The storage and indexing engine makes terabytes of log data searchable within seconds. The search and visualization interface enables analysts to query data, build dashboards, and configure alerts. The room covers major SIEM platforms: Splunk, the market leader known for its powerful Search Processing Language (SPL) and extensive app ecosystem; the ELK Stack (Elasticsearch, Logstash, Kibana), the leading open-source alternative; IBM QRadar, known for strong correlation engine and offense management; and Microsoft Sentinel, a cloud-native SIEM integrated with the Microsoft security ecosystem. Learners practice writing SIEM queries, understanding correlation rules, building dashboards, and creating alerts. The room also covers SIEM use cases: insider threat detection (unusual access patterns, data exfiltration), external threat detection (known malicious IPs, attack patterns), compliance reporting (PCI DSS log retention, HIPAA access monitoring), and operational troubleshooting.

## Objectives
- Understand SIEM architecture and data flow
- Configure log collection and forwarding
- Write SIEM queries to search log data
- Understand correlation rules and alerting
- Build dashboards for security monitoring
- Recognize SIEM's role in compliance and operations

## Tools
- Splunk (SIEM platform)
- ELK Stack (Elasticsearch, Logstash, Kibana)
- IBM QRadar (conceptual)
- Microsoft Sentinel (conceptual)

## Concepts
- Log collection, parsing, normalization, indexing
- SIEM query languages (SPL, KQL, Lucene)
- Correlation rules and use case management
- SIEM architecture components
- Compliance and reporting with SIEM
- Alert triage and investigation workflows
