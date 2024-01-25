## Browser, Editor, Owner, Viewer in GCP IAM

In Google Cloud Platform (GCP) Identity and Access Management (IAM), these roles define different levels of access granted to users or groups (principals) for resources within a project.

**1. Viewer:**

* **Permissions:** Can view and list existing resources but cannot modify them. 
* **Use case:** Ideal for monitoring dashboards, reports, or logs without the ability to make changes.

**2. Editor:**

* **Permissions:** Includes all Viewer permissions plus the ability to create, modify, and delete most resources.
* **Use case:** Suitable for managing resources within defined limits, like creating and managing virtual machines or storage buckets.

**3. Owner:**

* **Permissions:** Most powerful role, grants full control over all resources within a project. Includes Editor permissions and additional administrative tasks like managing IAM policies and billing.
* **Use case:** Reserved for highly trusted individuals like project administrators or security leads who require complete control.

**Differences:**

| Feature | Viewer | Editor | Owner |
|---|---|---|---|
| **Permission level** | Read-only | Create, modify, delete most resources | Full control, administrative tasks |
| **Use case** | Monitoring, reports | Managing resources | Project administration, security |
| **Granularity** | Limited | Broad | Most extensive |
| **Security risk** | Low | Moderate | High |
| **Best practice** | Grant only for specific needs | Use for resource management | Grant sparingly, only for trusted individuals |

**Additional points:**

* GCP IAM also offers **predefined roles** with granular access specific to services like Cloud Storage or Compute Engine.
* **Custom roles** can be created for even finer-grained control.
* **Principle of least privilege:** Grant the minimum level of access required for each user to perform their tasks.

## Service Accounts in GCP IAM: Key Points

**What are they?**

* Special accounts used by applications and workloads, not human users.
* Represent non-human identities for accessing GCP resources and performing actions.

**Types:**

* **User-managed:** Created and managed manually by you, granting fine-grained control.
* **Default:** Automatically created by certain Google Cloud services, often with broad access initially.

**Key features:**

* **No password:** Authentication done through private keys downloaded and used by applications.
* **IAM roles & permissions:** Grant specific access to resources like creating VMs or managing storage buckets.
* **Security benefits:** Improved security by separating application access from human users.
* **Best practices:**
    * Create dedicated service accounts for different applications.
    * Grant least privilege: assign only necessary roles.
    * Rotate private keys regularly.
    * Monitor and audit service account activity.

**Additional notes:**

* Service accounts can be attached to VMs or used in serverless environments.
* Google-managed service accounts (service agents) exist for internal Google Cloud services and cannot be modified.
* Multi-factor authentication (MFA) can be required for additional security when accessing credentials.

