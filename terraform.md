### What is Terraform?

- **Infrastructure as Code (IaC):** Terraform is an open-source Infrastructure as Code (IaC) tool developed by HashiCorp.

### Key Concepts:

1. **Infrastructure as Code (IaC):**
   - Code-based representation of infrastructure.
   - Enables version control, collaboration, and repeatability.

2. **Declarative Syntax:**
   - Describe what you want to achieve, not how to achieve it.
   - Terraform interprets and plans the necessary steps.

3. **Providers:**
   - Interfaces with different cloud providers (AWS, Azure, GCP, etc.) and services.
   - Each provider has its set of resources and configurations.

4. **Resources:**
   - Basic building blocks defined in Terraform configurations.
   - Examples include virtual machines, networks, databases.

5. **State File:**
   - Terraform maintains a state file to store the current state of the infrastructure.
   - Crucial for tracking changes and managing resources.

### Basic Workflow:

1. **Initialization:**
   - `terraform init` initializes a working directory.
   - Downloads necessary plugins and sets up the backend.

2. **Configuration:**
   - Define infrastructure in a `.tf` file using HashiCorp Configuration Language (HCL).

3. **Planning:**
   - `terraform plan` examines the configuration and generates an execution plan.
   - Describes what Terraform will do before actually doing it.

4. **Execution:**
   - `terraform apply` executes the plan to create, update, or delete infrastructure.
   - Interactively confirms the proposed changes.

5. **Destroy:**
   - `terraform destroy` tears down the infrastructure created by Terraform.
