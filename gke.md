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

## Choosing between Autopilot and Standard clusters

![Screenshot from 2024-01-23 10-02-10](https://github.com/ishtiaqSamdani/gcp/assets/82057297/3276f0ef-2507-4f6c-92c1-c4a83d23e311)
![Screenshot from 2024-01-23 09-51-19](https://github.com/ishtiaqSamdani/gcp/assets/82057297/0adbfb32-e8a8-4785-b5d4-3f101cd3b56c)

**Management and Configuration:**

* **Autopilot:** Google manages most aspects of your cluster, including nodes, scaling, security, and pre-configured settings. You provide your Kubernetes manifests, and Google optimizes the underlying infrastructure based on best practices. This is great for a hands-off approach and simplifies cluster management.
* **Standard:** You have full control over the cluster configuration, including node types, machine types, scaling policies, and security settings. This offers flexibility for specific workload requirements but requires more operational overhead.

**Scalability:**

* **Autopilot:** Google automatically scales your cluster based on resource needs. It can add or remove nodes to maintain optimal performance and cost efficiency. However, you don't have direct control over scaling decisions.
* **Standard:** You configure scaling policies and manually trigger scaling actions. This gives you greater control but demands more attention to workload resource needs.

**Cost:**

* **Autopilot:** You pay for resources used by your Pods, rather than a fixed fee for nodes. This can be cost-effective for fluctuating workloads but may be more expensive for consistently high resource usage.
* **Standard:** You pay for the capacity of your nodes regardless of Pod utilization. This offers predictable costs but can be wasteful if resources are underutilized.

**Additional Differences:**

* **Monitoring:** Autopilot provides basic monitoring through Cloud Monitoring, while Standard allows integration with any third-party monitoring tool.
* **Kubernetes Version:** Autopilot updates the Kubernetes version automatically using release channels, while Standard allows manual version selection.
* **Security:** Autopilot enforces some security restrictions, like not deploying in GKE-managed namespaces, while Standard offers full control over security configurations.
* **Third-party applications:** Autopilot restricts deploying workloads from Cloud Marketplace, while Standard allows it.



### Pod:
- A **Pod** is the basic unit of deployment in Kubernetes.
- It represents a single instance of a running process in a cluster and encapsulates an application's container(s), storage resources, and a unique network IP.
- Containers within a Pod share the same network namespace, allowing them to communicate with each other using localhost.
- Pods are generally considered ephemeral and can be rescheduled or replaced as needed.

### Deployment:
- A **Deployment** is a higher-level abstraction that manages and scales Pods.
- It ensures that a specified number of replicas of an application are running, and it helps in maintaining the desired state of the application.
- Deployments support rolling updates and rollbacks, making it easier to manage changes to applications over time.
- The configuration for a Deployment includes details such as the container image, number of replicas, and update strategy.

### ReplicaSet:
- A **ReplicaSet** is a lower-level abstraction that ensures a specified number of replicas (identical copies) of a Pod are running at all times.
- It is part of the scaling and healing aspects of a Deployment, ensuring that the desired number of Pods are maintained.
- ReplicaSets are often used by Deployments internally to manage the desired state of the application.

### Types of Services in Kubernetes:
1. **ClusterIP**:
   - Exposes the service on a cluster-internal IP.
   - This type makes the service only reachable from within the cluster.

2. **NodePort**:
   - Exposes the service on each Node's IP at a static port.
   - This type allows external traffic to reach the service on the specified port across all Nodes.

3. **LoadBalancer**:
   - Exposes the service externally using a cloud provider's load balancer.
   - The cloud provider assigns an external IP to the service, and traffic is distributed to the service endpoints.
Certainly! Below are examples for each type of service in Kubernetes:

### 1. ClusterIP Service:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service-clusterip
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```

### 2. NodePort Service:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  type: NodePort
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30080(30000-32767)
```

### 3. LoadBalancer Service:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service-loadbalancer
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: LoadBalancer
```
