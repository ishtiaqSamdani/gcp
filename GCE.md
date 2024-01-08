![Screenshot from 2024-01-08 09-45-57](https://github.com/ishtiaqSamdani/gcp/assets/82057297/4bd83467-41e2-417f-915d-5f192d0f25d7)**Compute Engine Machine Families:**

1. **General Purpose (E2, N2, N2D, N1):**
   - *Best price-performance ratio*
   - *Workloads:* Web and application servers, small-medium databases, dev environments.
![Screenshot from 2024-01-03 10-53-45](https://github.com/ishtiaqSamdani/gcp/assets/82057297/818f5356-d8de-4760-9b24-3120ffda392e)

2. **Memory Optimized (M2, M1):**
   - *Ultra high memory workloads*
   - *Workloads:* Large in-memory databases, in-memory analytics.  
![Screenshot from 2024-01-03 10-54-02](https://github.com/ishtiaqSamdani/gcp/assets/82057297/53d269ef-c0ea-4026-9894-a198eb3613b0)

3. **Compute Optimized (C2):**
   - *Compute-intensive workloads*
   - *Workloads:* Gaming applications.
![Screenshot from 2024-01-03 10-53-54](https://github.com/ishtiaqSamdani/gcp/assets/82057297/fa19615a-4d2c-4215-8067-f467a459034d)

**Compute Engine Machine Types:**
   - *Variety of machine types for each family*
   - *Example:* e2-standard-2
     - *e2 - Machine Type Family*
     - *standard - Type of workload*
     - *2 - Number of CPUs*
     - *Memory, disk, and networking capabilities increase with vCPUs*
![Screenshot from 2024-01-04 10-39-34](https://github.com/ishtiaqSamdani/gcp/assets/82057297/3f9ed307-43d8-4b3c-afc2-8ac0072e8339)

![Screenshot from 2024-01-04 10-39-58](https://github.com/ishtiaqSamdani/gcp/assets/82057297/24ce722c-1352-4bf4-830b-96a2c63a9209)


shared cores: Shared-core machine types provide a virtual CPU that can run for a portion of the time on a single hardware hyper-thread on the host CPU. 


**Images:**
1. **Public Images:**
   - *Provided and maintained by Google, open source communities, or third-party vendors*
   - *Examples:* Pre-configured operating systems and software stacks.

2. **Custom Images:**
   - *Created by users for specific projects*
   - *Allows customization of the operating system and software stack*

**Configuring Instances:**
   - *Consider CPU, memory, and disk requirements*
   - *Choose the appropriate machine family and type based on workload characteristics*
   - *Example: e2-standard-2 for a general-purpose workload*



![Screenshot from 2024-01-03 10-29-39](https://github.com/ishtiaqSamdani/gcp/assets/82057297/89563828-89e0-4d0f-b5d6-b3a92f533d6e)
![Screenshot from 2024-01-03 10-29-00](https://github.com/ishtiaqSamdani/gcp/assets/82057297/cc878465-b4c5-45f3-aeff-71b4d057fec0)
![Screenshot from 2024-01-03 10-28-40](https://github.com/ishtiaqSamdani/gcp/assets/82057297/5e2c1ff1-3566-4376-9df8-8b59d2d506dd)
![Screenshot from 2024-01-03 10-30-13](https://github.com/ishtiaqSamdani/gcp/assets/82057297/911d0a75-c688-483d-a8ba-94ab69f91023)


**Allowing ports with firewall rules**:
![Screenshot from 2024-01-04 10-55-07](https://github.com/ishtiaqSamdani/gcp/assets/82057297/ceb91185-a8ac-4069-b19d-3eb83c631077)

**Management section**:
![Screenshot from 2024-01-04 10-57-05](https://github.com/ishtiaqSamdani/gcp/assets/82057297/23201ec2-30ab-42aa-8c47-df11d248ffae)

By setting the deletionProtection flag, a VM instance can be protected from accidental deletion. If a user attempts to delete a VM instance for which you have set the deletionProtection flag, the request fails. Only a user that has been granted a role with compute.instances.create permission can reset the flag to allow the resource to be deleted.

**External (Public) and Internal (Private) IP Addresses:**

1. **External IP Addresses:**
   - *Internet addressable.*
   - *Unique constraint: No two resources can have the same public (external) IP address.*
   - *Lost on stopping a VM instance.*

2. **Internal IP Addresses:**
   - *Internal to a corporate network.*
   - *Different corporate networks can have resources with the same internal (private) IP address.*
   - *All VM instances are assigned at least one internal IP address.*

**Creation and Management of IP Addresses:**
   - *VM instances are assigned at least one internal IP address.*
   - *External (public) IP addresses can be enabled for VM instances.*

**Constant External IP Address for VM Instance:**
   - *Assigning a static IP address to the VM is a quick and dirty way.*

**Static IP Addresses:**
   - *Can be switched to another VM instance within the same project.*
   - *Remains attached even if the instance is stopped (manual detachment required).*
   - *Billed when not in use; explicit release recommended when not needed.*

![Screenshot from 2024-01-03 10-38-06](https://github.com/ishtiaqSamdani/gcp/assets/82057297/a827b36e-73c9-4611-9061-410d824ab316)
![Screenshot from 2024-01-03 10-42-01](https://github.com/ishtiaqSamdani/gcp/assets/82057297/6bad4cb7-c7a8-4fed-a467-5a94e9411ecf)
![Screenshot from 2024-01-03 10-41-52](https://github.com/ishtiaqSamdani/gcp/assets/82057297/4d71f37d-0791-4c51-a48c-ea3c29a78b31)
![Screenshot from 2024-01-03 10-39-43](https://github.com/ishtiaqSamdani/gcp/assets/82057297/cbb32002-3c41-43dc-8100-50d740585bc0)


**Bootstrapping with Startup Script:**

1. **Bootstrapping:**
   - *Install OS patches or software when a VM instance is launched.*
   - *In VM, configure a startup script to bootstrap.*

**Instance Templates:**
   - *Avoid specifying VM instance details (image, type) every launch.*
   - *Define machine type, image, labels, startup script, and other properties.*
   - *Used for creating VM instances and managed instance groups.*
   - *Convenient for creating similar instances.*
   - *Cannot be updated directly; copy and modify for changes.*
   - *Optional: Specify an image family for versioning.*

**Custom Images:**
   - *Installing OS patches and software at launch increases boot time.*
   - *Create a custom image with pre-installed patches and software.*
   - *Can be created from an instance, disk, snapshot, another image, or a file in Cloud Storage.*
   - *Shared across projects.*

**Recommendations for Custom Images:**
   - *Deprecate old images and specify replacement.*
   - *Harden images to corporate security standards.*

### configure the firewall using network tags

![Screenshot from 2024-01-08 09-45-57](https://github.com/ishtiaqSamdani/gcp/assets/82057297/33fae4d8-108f-42ff-9360-09394f1209ee)
![Screenshot from 2024-01-08 09-46-30](https://github.com/ishtiaqSamdani/gcp/assets/82057297/8a1b91c6-36da-402c-8f37-75db31039785)


