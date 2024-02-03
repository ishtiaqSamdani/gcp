### Infrastructure as a Service (IaaS):
- **Definition:** Use only infrastructure from the cloud provider.
- **Example:** Deploying applications or databases using virtual machines (VMs).
- **Responsibilities:**
  - You are responsible for application code and runtime.
  - Configuring load balancing.
  - Auto-scaling.
  - OS upgrades and patches.
  - Availability.

![Screenshot from 2024-01-12 10-52-40](https://github.com/ishtiaqSamdani/gcp/assets/82057297/2dda5326-243e-493c-947f-a9e6d34f3ff6)

### Platform as a Service (PaaS):
- **Definition:** Use a platform provided by the cloud.
- **Example:** Cloud provider takes care of OS, application runtime, auto-scaling, availability, load balancing.
- **Responsibilities:**
  - You are responsible for configuration (of application and services).
  - Application code (if needed).
- **Varieties:**
  - **CaaS (Container as a Service):** Containers instead of apps.
  - **FaaS (Function as a Service):** Functions instead of apps.
  - **Databases:** Relational & NoSQL.

![Screenshot from 2024-01-12 10-52-54](https://github.com/ishtiaqSamdani/gcp/assets/82057297/0769aabe-8674-401e-939a-ba57ad2b6dc0)


### Microservices:

![Screenshot from 2024-01-12 10-53-03](https://github.com/ishtiaqSamdani/gcp/assets/82057297/a1e3304f-33f7-421a-b4b2-057ea03c3ae8)

- **Definition:** Enterprises are moving towards microservices architectures.
- **Characteristics:**
  - Build small, focused microservices.
  - Flexibility to innovate and build applications in different programming languages (Go, Java, Python, JavaScript, etc.).
  - Deployments can become complex.
- **Challenge:**
  - How to deploy microservices written in different languages consistently?
- **Solution:**
  - **Containers (Docker):**
    - Create Docker images for each microservice.
    - Docker image includes application runtime, code, and dependencies.
    - Runs consistently across various environments (local machine, data center, cloud).
- **Advantages of Containers:**
  - Lightweight compared to virtual machines.
  - Provides isolation.
  - Cloud-neutral.

### Containers - Docker:

![Screenshot from 2024-01-12 10-53-12](https://github.com/ishtiaqSamdani/gcp/assets/82057297/ba5e7342-1fbf-48b7-9219-414c8397629f)


- **Definition:** Docker containers for microservices with runtime, code, and dependencies.
- **Advantages:**
  - Lightweight compared to virtual machines.
  - Provides isolation.
- **Features:**
  - Auto-scaling based on demand.
  - Service discovery.
  - Load balancing.
  - Self-healing.
  - Zero downtime deployments.
- **Container Orchestration:** Tools for managing containers at scale.

![Screenshot from 2024-01-12 10-53-27](https://github.com/ishtiaqSamdani/gcp/assets/82057297/7f27e9b9-ebb4-457d-8e48-60fdbad66ff1)

### Serverless:
- **Definition:** Focus on code without worrying about servers.
- **Key Points:**
  - No need to worry about infrastructure.
  - Flexible scaling and automated high availability.
  - Pay for usage (requests), not servers.
  - Ideally, zero requests mean zero cost.
  
### Google Cloud Platform (GCP) Managed Services for Compute:
- **Compute Engine (IaaS):** High-performance VMs.
- **Google Kubernetes Engine (CaaS):** Orchestrates containerized microservices.
- **App Engine (PaaS/Serverless):** Build scalable applications on a fully managed platform.
- **Cloud Functions (FaaS/Serverless):** Build event-driven applications using single-purpose functions.
- **Cloud Run (CaaS/Serverless):** Deploy scalable containerized applications without needing a cluster.

These concepts and services represent different approaches to deploying and managing applications in the cloud, each catering to specific needs and preferences of developers and organizations.
