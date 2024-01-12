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


**Terraform Variables:**

1. **Declaration:**
   - Variables are declared in Terraform configurations using the `variable` keyword.
   - Example:
     ```hcl
     variable "region" {
       type    = string
       default = "us-west-2"
     }
     ```

2. **Data Types:**
   - Terraform supports several variable types, including string, number, bool, list, and map.

3. **Default Values:**
   - You can assign default values to variables using the `default` attribute in the variable declaration.

4. **Input Variables:**
   - Variables can be defined in a separate file (e.g., `variables.tf`) and then referenced in your main configuration.
   - Example:
     ```hcl
     # variables.tf
     variable "region" {
       type    = string
       default = "us-west-2"
     }
     ```
     ```hcl
     # main.tf
     provider "aws" {
       region = var.region
     }
     ```

5. **Variable Overrides:**
   - You can override variable values at runtime using command-line flags or environment variables.
   - Example:
     ```bash
     terraform apply -var="region=us-east-1"
     ```

6. **Input from Files:**
   - Variables can also be loaded from external files, which is useful for handling sensitive information or large configurations.
   - Example:
     ```hcl
     variable "private_key" {
       type    = string
       default = file("private_key.pem")
     }
     ```

8. **Variable Validation:**
   - Terraform allows you to enforce validation rules on variables using the `validation` block within the variable declaration.

9. **Variable Outputs:**
   - You can use output variables to expose certain values from your Terraform configuration for external consumption.

### PRIORITY

1. **Command-Line Flags:**
   - Values provided via command-line flags using the `-var` or `-var-file` options take the highest priority.

   ```bash
   terraform apply -var="variable_name=value"
   ```

2. **Environment Variables:**
   - Values set in environment variables prefixed with `TF_VAR_` are considered next in priority.

   ```bash
   export TF_VAR_variable_name=value
   ```

3. **Terraform Files (`.tf` and `.tfvars`):**
   - Values defined directly in Terraform configuration files (`.tf`) or variable files (`.tfvars`) are considered next.

   ```hcl
   variable "variable_name" {
     type    = string
     default = "default_value"
   }
   ```

   - Variable files can be included using the `-var-file` option or automatically loaded if named according to certain conventions (e.g., `terraform.tfvars`).

   ```bash
   terraform apply -var-file="filename.tfvars"
   ```

4. **Default Values:**
   - If none of the above sources provide a value, Terraform falls back to the default value specified in the variable declaration.

   ```hcl
   variable "variable_name" {
     type    = string
     default = "default_value"
   }
   ```
