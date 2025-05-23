# DevSecOps-Pipeline-for-Secure-File-Access-and-Audit-Visibility

A secure, cloud-native, DevSecOps-driven document management system. This project leverages HashiCorp Vault for access control, Ansible for automation, Jenkins for orchestration, AWS S3 for secure file storage, and the **ELK Stack** (Elasticsearch, Logstash, Kibana) for centralized audit logging.

This solution is ideal for organizations managing sensitive files such as legal case documents, internal reports, or client records, requiring strict access control and complete auditability.

---

## Key Features

- Role-based access to confidential documents via Vault policies
- Secure storage and retrieval of files from AWS S3
- Automated user lifecycle management using Ansible
- CI/CD integration with Jenkins for end-to-end orchestration
- Real-time audit logging and visual monitoring via the ELK Stack

---

## Technology Stack

| Tool              | Purpose                                              |
|-------------------|------------------------------------------------------|
| **Vault**         | Secure access control and user authentication        |
| **AWS S3**        | Secure, encrypted document storage                   |
| **Ansible**       | Automation of Vault user provisioning and audits     |
| **Jenkins**       | CI/CD pipeline orchestration                         |
| **Logstash**      | Collection and shipping of Vault audit logs          |
| **Elasticsearch** | Storage and indexing of logs for search              |
| **Kibana**        | Visualization of audit data                          |

---

## System Architecture

This system is composed of four EC2 instances on AWS:

- **Vault Server**: Hosts Vault for access control and audit logging
- **Ansible Node**: Runs playbooks for user access and audit management
- **Jenkins Server**: Automates access control lifecycle and document operations
- **ELK Stack Server**: Collects, indexes, and visualizes audit logs


## Project Structure

vault-devops-secure-access/
│
├── ansible/
│   ├── assign_access.yml               # Adds a Vault user with policy
│   ├── revoke_access.yml               # Removes a Vault user
│   ├── audit_access.yml                # Fetches audit logs from Vault
│   ├── inventory/hosts.ini             # Defines Vault host
│   └── group_vars/all.yml              # Vault address and root token
│
├── jenkins/
│   └── Jenkinsfile                     # Pipeline for CI/CD automation
│
├── vault/
│   ├── config/vault.hcl                # Vault server configuration
│   ├── policies/case_documents_policy.hcl  # Vault policy file
│   └── scripts/
│       ├── vault_init.sh              # Initializes Vault
│       └── create_users.sh            # Sets up default users
│
├── elk/
│   ├── logstash.conf                   # Logstash file reader config
│   └── kibana_dashboard_export.ndjson # Prebuilt dashboard export
│
├── diagrams/
│   └── architecture.png                # System architecture diagram
│
└── docs/
    ├── access_audit_report_sample.txt # Sample output from audit logs
    ├── jenkins_pipeline.png           # Screenshot of Jenkins job
    └── kibana_dashboard.png           # Kibana dashboard screenshot

