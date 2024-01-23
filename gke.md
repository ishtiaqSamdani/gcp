![Screenshot from 2024-01-23 11-07-09](https://github.com/ishtiaqSamdani/gcp/assets/82057297/2916ad62-77d9-4de0-856c-26efe8de4173)

### Master Node (Control Plane):
1. **API Server:**
   - Central control point managing the cluster.
   - Exposes Kubernetes API for interaction.

2. **etcd:**
   - Distributed key-value store.
   - Stores cluster configuration data.

3. **Scheduler:**
   - Schedules pods on worker nodes based on resources.

4. **Controller Manager:**
   - Manages controllers (e.g., replication, endpoint, node).

### Controllers:
1. **Replication Controller:**
   - Ensures specified pod replicas are running.
   - Limited capabilities compared to newer controllers.

2. **Endpoint Controller:**
   - Manages network endpoints of services.
   - Syncs service and endpoint configurations.

3. **Node Controller:**
   - Monitors and manages worker nodes.
   - Ensures node health, reschedules pods if needed.


### Worker Nodes:
1. **Kubelet:**
   - Primary agent on worker nodes.
   - Interacts with master, manages container lifecycle.

2. **Container Runtime:**
   - Software for running containers (e.g., Docker).

3. **Kube-proxy:**
   - Handles network routing and load balancing.

### Pods:
- **Fundamental Unit:**
  - Fundamental deployment unit in Kubernetes.
  - Represents one or more tightly coupled containers.
  - Share the same network namespace.


### Google Kubernetes Engine (GKE) Overview:

1. **Managed Kubernetes Service:**
   - GKE is a fully managed Kubernetes service on Google Cloud Platform.
   - Automates container orchestration, scaling, and management.

2. **Key Features:**
   - Seamless integration with Google Cloud services.
   - Automated provisioning, upgrading, and scaling.
   - Monitoring, logging, and security features.

### Architecture:

1. **Control Plane:**
   - Managed by Google.
   - Consists of master nodes, API server, and other control plane components.
   - Users do not manage control plane resources.

2. **Node Pools:**
   - Worker nodes grouped into node pools.
   - Each node pool can have different machine types.

### Cluster Operations:

1. **Cluster Creation:**
   - Easily create GKE clusters using Google Cloud Console or CLI.

2. **Node Management:**
   - Automated addition or removal of nodes based on demand.
   - Automatic updates for node OS and Kubernetes version.

### Integration with GCP Services:

1. **Identity and Access Management (IAM):**
   - Integrated with IAM for fine-grained access control.

2. **Cloud Monitoring and Logging:**
   - Integration with Stackdriver for monitoring and logging.

3. **Google Cloud Storage and Cloud Load Balancing:**
   - Seamless integration with GCS and Cloud Load Balancing.

### Networking:

1. **VPC-native Clusters:**
   - GKE clusters are VPC-native for simplified networking.

2. **Load Balancing:**
   - Supports HTTP(S), TCP/UDP load balancing for services.

### Security:

1. **Node Security:**
   - Automatic security patches for node OS.
   - Encrypted communication between nodes.

2. **Identity-Aware Proxy (IAP):**
   - Integration with IAP for secure access to clusters.

### Scalability and Auto-Scaling:

1. **Horizontal Pod Autoscaling:**
   - Automatically adjusts the number of pods based on demand.

2. **Node Auto-provisioning:**
   - Automatically adds nodes to meet resource requirements.

### Upgrades:

1. **Cluster Upgrades:**
   - Managed upgrades for Kubernetes clusters.
   - Users can control maintenance windows.

### Regional Clusters:

1. **High Availability:**
   - GKE supports regional clusters for high availability.

2. **Multi-Zone Deployment:**
   - Spreads nodes across multiple zones within a region.

### Billing:

1. **Pricing Model:**
   - Pay only for resources used by nodes in the cluster.

2. **Node Pools and Machine Types:**
   - Flexibility to choose different machine types for node pools.
