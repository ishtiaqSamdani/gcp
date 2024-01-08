### Creating a Group of VM Instances - Managed Instance Groups (MIG)

#### Introduction:
- **Instance Group Definition:** A group of VM instances managed as a single entity.
- **Purpose:** Manage similar VMs with similar lifecycles as one unit.

#### Types of Instance Groups:
1. **Managed Instance Group (MIG):**
   - Identical VMs created using an instance template.
   - Features auto-scaling, auto-healing, and managed releases.
   - Recommended for uniform VM configurations.

2. **Unmanaged Instance Group:**
   - VMs have different configurations.
   - Does not offer auto-scaling, auto-healing, or other services.
   - Not recommended unless different VM configurations are necessary.

#### Managed Instance Group (MIG) Features:
1. **Maintaining Instances:**
   - Ensures a certain number of instances are running.
   - Launches a new instance if one crashes (self-healing).

2. **Health Checks:**
   - Detects application failures.
   - Self-healing mechanism based on health checks.

3. **Auto Scaling:**
   - Adjusts the number of instances based on load.
   - Configurable minimum and maximum number of instances.

4. **Load Balancer Integration:**
   - Distributes load among instances in the group.

5. **Multi-Zone Deployment:**
   - Can create instances in multiple zones for regional MIGs.
   - Regional MIGs provide higher availability compared to zonal MIGs.

6. **Rolling Updates:**
   - Releases new application versions without downtime.
   - Gradual update of instances to the new instance template.

7. **Canary Deployment:**
   - Tests new versions with a subset of instances before full deployment.

#### Instance Template and Auto-Scaling Configuration:
- **Instance Template:** Mandatory for MIG.
- **Auto-Scaling Configuration:**
   - Minimum and maximum number of instances.
   - Auto-scaling metrics (e.g., CPU utilization, load balancer utilization).
   - Cool-down period for metric evaluation.
   - Scale-in controls to prevent sudden drops in instances.

#### Autohealing Configuration:
- **Health Check:** Configurable with an initial delay.
- **Ensures application initialization before running health checks.**

#### Rolling Update Configuration:
- **Gradual Update:**
   - Specifies a new template for instances.
   - Optionally, specifies a template for canary testing.
   - Configures update timing (immediate or opportunistically).
   - Defines maximum surge and maximum unavailable instances.
   - Supports rolling restart/replace for existing instances.
 
     ![Screenshot from 2024-01-05 10-00-44](https://github.com/ishtiaqSamdani/gcp/assets/82057297/2bba0bfb-c290-406f-984c-2432ed7444e2)
     
    ![Screenshot from 2024-01-05 10-00-51](https://github.com/ishtiaqSamdani/gcp/assets/82057297/41e76fa8-1c3f-42ed-bd7f-c3ebe0e063f5)
    
    ![Screenshot from 2024-01-05 10-01-00](https://github.com/ishtiaqSamdani/gcp/assets/82057297/7ac15551-f81b-4f47-b73c-ced702e61713)
    
    ![Screenshot from 2024-01-05 10-01-09](https://github.com/ishtiaqSamdani/gcp/assets/82057297/57a90b77-8bc8-40b8-969e-7f444f68ffca)
    ![Screenshot from 2024-01-05 10-01-15](https://github.com/ishtiaqSamdani/gcp/assets/82057297/9abb8ba7-a5c8-4b41-87a5-73d8527cd859)
    ![Screenshot from 2024-01-05 10-01-39](https://github.com/ishtiaqSamdani/gcp/assets/82057297/b515dbb8-7f34-4edc-a032-297ef60c2234)
    ![Screenshot from 2024-01-05 10-02-13](https://github.com/ishtiaqSamdani/gcp/assets/82057297/e0f2375b-1d15-4236-8a61-6253751ce837)
    ![Screenshot from 2024-01-05 10-04-29](https://github.com/ishtiaqSamdani/gcp/assets/82057297/ec2fbb4c-acb4-4f7d-afb0-8c0353cd4124)
    ![Screenshot from 2024-01-05 10-04-33](https://github.com/ishtiaqSamdani/gcp/assets/82057297/6c00b5e2-0e98-4660-b833-eb457dd91963)


### CHECKING AUTO SCALING

increase cpu usage:
```
sudo apt-get install stress
stress --cpu 2 --timeout 60s
```
![Screenshot from 2024-01-05 11-23-30](https://github.com/ishtiaqSamdani/gcp/assets/82057297/d3f2a180-cb54-4a1f-8db7-06030a0a0043)


## UPDATES

### with new template
![Screenshot from 2024-01-05 10-44-20](https://github.com/ishtiaqSamdani/gcp/assets/82057297/3b665e0a-3d97-40ba-9bc5-4ac01aa80fd1)
![Screenshot from 2024-01-05 10-46-34](https://github.com/ishtiaqSamdani/gcp/assets/82057297/04e5c8f7-51f4-44eb-80ee-20d3107cae9e)
![Screenshot from 2024-01-05 10-46-38](https://github.com/ishtiaqSamdani/gcp/assets/82057297/6a5bf881-774a-43da-8811-2baecae66d6a)

### replace/ restart with same template

![Screenshot from 2024-01-05 10-47-52](https://github.com/ishtiaqSamdani/gcp/assets/82057297/45442f15-c509-4a19-b9ac-19c8dd762a4f)

![Screenshot from 2024-01-05 10-48-05](https://github.com/ishtiaqSamdani/gcp/assets/82057297/53fd0ebc-dee7-4592-844e-d5fdcd2e9a06)


### Cloud Load Balancing

#### Introduction:
- **Purpose:** Distributes user traffic across instances of an application in a single region or multiple regions.
- **Managed Service:** Fully distributed, software-defined, and managed.

#### Key Features:
1. **Health Check:**
   - Ensures routing to healthy instances.
   - Recovers from failures automatically.

2. **Auto Scaling:**
   - Scales resources based on demand.

3. **Global Load Balancing:**
   - Provides a single anycast IP for global reach.
   - Supports both external and internal load balancing.

#### Benefits:
- **Enables:**
  - High Availability
  - Auto Scaling
  - Resiliency

### Networking Layers and Protocols

#### Network Layer:
- **IP (Internet Protocol):** Transfers bytes, unreliable.

#### Transport Layer:
- **TCP (Transmission Control Protocol):** Prioritizes reliability over performance.
- **TLS (Transport Layer Security):** Adds security to TCP.

#### Application Layer:
- **HTTP/HTTPS:** For web apps and REST APIs.
- **SMTP:** Email transfer protocol.

#### Protocol Comparisons:
- **HTTP vs HTTPS vs TCP vs TLS vs UDP:**
  - Most applications communicate at the application layer.
  - TCP/TLS at the network layer for reliability.
  - High-performance applications communicate directly at the transport layer (e.g., gaming, live video streaming using UDP).

### Cloud Load Balancing - Terminology

#### Backend:
- Group of endpoints receiving traffic (e.g., instance groups).

#### Frontend:
- Specifies IP, port, and protocol for client requests.
- For SSL, requires a certificate.

#### Host and Path Rules:
- Define rules redirecting traffic to different backends based on path, host, HTTP headers, and methods.

### SSL/TLS Termination/Offloading

#### Client to Load Balancer:
- Over the internet.
- HTTPS recommended for secure communication.

#### Load Balancer to VM Instance:
- Through Google's internal network.
- HTTP is acceptable; HTTPS is preferred.


![Screenshot from 2024-01-08 11-01-54](https://github.com/ishtiaqSamdani/gcp/assets/82057297/7724c114-c441-4db9-8894-519951c2d429)

![Screenshot from 2024-01-08 11-22-52](https://github.com/ishtiaqSamdani/gcp/assets/82057297/b0273021-3e9e-47e1-a44f-fd047a67776d)
