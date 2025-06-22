# Kubernetes Administrator (CKA)

### K8s Architecture

![k8s-Architecture-analogy.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/k8s-Architecture-analogy.png)

---

### Kubernetes Architecture Overview: Cargo Ship Analogy

To understand Kubernetes architecture, let’s imagine a fleet of ships, where:

- **Cargo Ships** represent **Worker Nodes** in Kubernetes.
- **Containers** on these ships are your application workloads (like Docker containers).
- The **Control Ship** oversees and manages all the cargo ships. It has different departments to coordinate everything, much like the **Control Plane** in Kubernetes.

---

### **Cargo Ships (Worker Nodes)**

The **Worker Nodes** are responsible for carrying and running the application containers, just like cargo ships transport goods. Each cargo ship (worker node) is equipped with:

- **Containers (Pods)**: The actual application workload running on the worker node, like boxes of cargo on the ship.
- **Kubelet**: This is like the ship’s captain, who ensures that all containers (cargo) are loaded, unloaded, and running smoothly as instructed by the Control Ship.
- **Kube-proxy**: Acts like a communication system between ships and external systems, ensuring that network traffic flows smoothly between containers and services within the cluster.

Cargo ships can come and go (nodes may be added or removed), but as long as the control ship knows what’s happening (via etcd), the system will work smoothly.

---

### **Control Ship (Control Plane)**

The **Control Plane** is like a highly organized control ship, with several departments responsible for overseeing the fleet. It manages the entire operation of cargo ships (worker nodes).

1. **Captain of the Control Ship (Kube-API Server)**:
    - This is the **Kube-API Server**, the main point of communication for all other systems. Like a control tower, it listens to incoming requests (for shipping goods) and delegates tasks to the appropriate department on the control ship.
2. **Shipping Manifest (etcd)**:
    - Every time cargo is loaded or unloaded (containers scheduled or removed), it needs to be recorded. In Kubernetes, **etcd** is the system that stores all the data about the state of the cluster. It keeps track of which containers are running on which ship (worker nodes), making sure that nothing gets lost.
3. **Crane Scheduler (Kube-Scheduler)**:
    - When a new cargo ship arrives, the crane (scheduler) determines which containers (workloads) go where. This is what the **Kube-Scheduler** does — it decides which worker node (cargo ship) should run a particular workload based on available resources, ensuring balance across the fleet.
4. **Various Offices (Controllers)**:
    - There are several specialized offices on the control ship that manage different aspects of the operation:
        - **Node Controller**: Monitors the health of each cargo ship (worker node).
        - **Replication Controller**: Ensures that the right number of copies of containers are running at all times.
        - **Service Controller**: Manages the routing of external traffic to the correct containers.

These offices (controllers) coordinate their work through the **Kube-Controller Manager**, much like a department head ensuring that all operations run smoothly.

---

### **Network Communication (Kube-proxy)**

Communication between ships (worker nodes) and external clients is handled by a **Kube-proxy**. It ensures that requests reach the correct cargo (container) through network rules, similar to how ships communicate through a port authority.

---

### **Container Engine**

The engine of the cargo ships (worker nodes) is the **container runtime**, which is typically Docker or containerd. It’s responsible for actually running the containers, much like the engine is responsible for powering the ship.

---

### Overview of Key Components in Kubernetes

1. **Worker Nodes (Cargo Ships)**: Where containers (your applications) run.
2. **Control Plane (Control Ship)**: Manages and schedules everything.
3. **Kube-API Server (Captain)**: Main point of communication and delegation.
4. **etcd (Shipping Manifest)**: Stores all the cluster’s current state and data.
5. **Kube-Scheduler (Crane)**: Decides which container runs on which node.
6. **Controller Manager (Office)**: Oversees different controllers like Node, Replication, etc.
7. **Kube-proxy (Communication)**: Manages network traffic and communication.
8. **Container Runtime (Engine)**: Runs the containers on worker nodes.

---

![k8s-Architecture.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/k8s-Architecture.png)

### ETCD

### 1. **Etcd: Independent Project Overview**

**Etcd** is a distributed key-value store, originally developed by CoreOS and later adopted widely by projects like Kubernetes. It wasn't designed specifically for Kubernetes but as a general-purpose, highly available and consistent key-value store for any distributed system. This means it’s flexible and can be used independently for various projects needing consistent data storage.

---

### ETCD Cluster Diagram

![ETCD cluster (1).pdf.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/ETCD_cluster_(1).pdf.png)

---

1. **Cluster Setup Environment:**
    - **Ubuntu 23:**The cluster is hosted on Ubuntu 23 virtual machines.
    - **Vagrant + VirtualBox:**These virtual machines are set up using Vagrant to automate the configuration and VirtualBox to provide the virtual environment.
2. **Cluster Components:**
    - **etcd Cluster Nodes:**
        - There are three **etcd nodes** in the cluster (etcd 1, etcd 2, etcd 3), which are responsible for ensuring high availability.
        - Each node is deployed on an Ubuntu system and assigned a unique IP:
            - etcd 1: `192.168.56.11`
            - etcd 2: `192.168.56.12`
            - etcd 3: `192.168.56.13`
    - **Client Requests:**
        - Clients interact with the etcd cluster through a secure connection using the port **2379**.
3. **Ports:**
    - **Client Communication (2379):**
        - All three etcd nodes expose port **2379** to handle secure client requests.
    - **Internal Node Communication (2380):**
        - The etcd nodes communicate with each other on port **2380**. This is essential for synchronizing data and maintaining consistency across the cluster.
        - All communication between the nodes is encrypted.
4. **Secure Communication:**
    - **Certificates (cert, key, cacert):**
        - The diagram shows that secure communication is enforced using certificates:
            - A **certificate authority (CA)** issues and signs the certificates for each etcd node.
            - Each node uses its own **cert** and **key** pair to establish trusted connections.
            - **Client traffic** to the etcd cluster is encrypted using **cacert** for verification.
5. **HA Architecture:**
    - The **high availability (HA)** design ensures that the etcd cluster remains operational even if one or two of the nodes go down.
    - The nodes exchange data and stay in sync using their secure communication channels over **port 2380**.

---

### Key Points About Etcd:

- **Key-Value Database**: It stores data in a simple key-value format, which allows for fast lookups.
- **Distributed**: Designed for distributed systems, it runs across multiple nodes and ensures consistency of data across those nodes.
- **Highly Available**: Uses consensus algorithms like Raft to ensure that even in the case of failure, etcd can still make reliable decisions and keep the data available.
- **Data Consistency**: In distributed systems, consistency is crucial. Etcd ensures that all nodes in the cluster have the same data at any given time, solving the challenge of split-brain issues (i.e., inconsistent data between nodes).

### 2. **Etcd in CNCF**

**CNCF (Cloud Native Computing Foundation)** is an organization that fosters the development of cloud-native technologies. It has a variety of projects at different stages of maturity: sandbox, incubating, and graduated projects. Graduated projects are stable, widely adopted, and meet stringent criteria.

- **Etcd is a Graduated Project** under CNCF, meaning it is a mature project with a large community and broad adoption. It plays a foundational role in cloud-native environments.

### 3. **Understanding Databases and Etcd**

There are two general types of databases:

- **Relational Databases**: Like MySQL, PostgreSQL—focused on structured data with tables, rows, and relationships.
- **NoSQL Databases**: Like etcd, MongoDB—focused on key-value pairs, documents, and wide-column storage.

Etcd falls under the **key-value store** category, which is fast and efficient for storing simple data structures. It doesn't use extra space for unused fields or complex relationships—only storing what’s needed.

- **Keys and Values**: In etcd, data is stored in pairs:
    - A **key** is a unique identifier (e.g., `/kubernetes/nodes/node1`).
    - A **value** is the associated data (e.g., the IP address or status of the node).

### 4. **Etcd in Kubernetes**

Now, let’s explore **etcd’s role in Kubernetes**.

In Kubernetes, etcd acts as the **central data store** for the entire cluster. It stores all configuration data, state information, and metadata about the cluster's objects. Every time you create a pod, service, or update a deployment, the information is saved in etcd, and every Kubernetes component reads from it.

### Key Components:

- **Consistency and State**: Etcd ensures that the state of the Kubernetes cluster is **consistent** across all nodes. When you scale up or down, etcd keeps track of the new or removed resources.
- **Key-Value Data**: All Kubernetes objects—like nodes, pods, config maps—are stored as key-value pairs. This enables quick access and updates.
- **Backup and Restore**: Etcd can be backed up and restored easily, making it crucial for disaster recovery in Kubernetes.

### 5. **How Does It Work?**

- **Raft Consensus Algorithm**: Etcd uses Raft to ensure that any changes are consistently applied across all nodes. Even in the case of failures, the system is resilient and ensures the data is up-to-date.
- **Port Communication**: Etcd typically listens on port `2379` for communication with Kubernetes components like the API server.

### Overview Example

Think of Kubernetes as a fleet of ships. Each ship (worker node) carries containers (cargo), and the control ship (the control plane) oversees and manages all the ships. **Etcd** acts as the **database system** on the control ship, where the status of every ship and every container is stored. When a new container is loaded or unloaded from a cargo ship, the information is recorded in **etcd** so that the control ship always knows what's happening.

### **Key Differences:**

| Feature | etcd | Other NoSQL Databases |
| --- | --- | --- |
| **Purpose** | Service discovery, configuration management | General-purpose data storage for applications |
| **Consistency Model** | Strong consistency via Raft consensus | Eventual consistency (Cassandra), or tunable (MongoDB) |
| **Data Structure** | Simple key-value store | Document-based, wide-column, or key-value models |
| **Use Case** | Cluster state, service discovery, leader election | Application data storage, real-time analytics |
| **Scaling** | Small-scale metadata | Massive data sets with horizontal scaling |
| **Data Querying** | Key-based lookup | Complex queries, indexing, and aggregation |

### ETCD

### 1. **Etcd: Independent Project Overview**

**Etcd** is a distributed key-value store, originally developed by CoreOS and later adopted widely by projects like Kubernetes. It wasn't designed specifically for Kubernetes but as a general-purpose, highly available and consistent key-value store for any distributed system. This means it’s flexible and can be used independently for various projects needing consistent data storage.

---

### ETCD Cluster Diagram

![ETCD cluster (1).pdf.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/ETCD_cluster_(1).pdf.png)

---

1. **Cluster Setup Environment:**
    - **Ubuntu 23:**The cluster is hosted on Ubuntu 23 virtual machines.
    - **Vagrant + VirtualBox:**These virtual machines are set up using Vagrant to automate the configuration and VirtualBox to provide the virtual environment.
2. **Cluster Components:**
    - **etcd Cluster Nodes:**
        - There are three **etcd nodes** in the cluster (etcd 1, etcd 2, etcd 3), which are responsible for ensuring high availability.
        - Each node is deployed on an Ubuntu system and assigned a unique IP:
            - etcd 1: `192.168.56.11`
            - etcd 2: `192.168.56.12`
            - etcd 3: `192.168.56.13`
    - **Client Requests:**
        - Clients interact with the etcd cluster through a secure connection using the port **2379**.
3. **Ports:**
    - **Client Communication (2379):**
        - All three etcd nodes expose port **2379** to handle secure client requests.
    - **Internal Node Communication (2380):**
        - The etcd nodes communicate with each other on port **2380**. This is essential for synchronizing data and maintaining consistency across the cluster.
        - All communication between the nodes is encrypted.
4. **Secure Communication:**
    - **Certificates (cert, key, cacert):**
        - The diagram shows that secure communication is enforced using certificates:
            - A **certificate authority (CA)** issues and signs the certificates for each etcd node.
            - Each node uses its own **cert** and **key** pair to establish trusted connections.
            - **Client traffic** to the etcd cluster is encrypted using **cacert** for verification.
5. **HA Architecture:**
    - The **high availability (HA)** design ensures that the etcd cluster remains operational even if one or two of the nodes go down.
    - The nodes exchange data and stay in sync using their secure communication channels over **port 2380**.

---

### Key Points About Etcd:

- **Key-Value Database**: It stores data in a simple key-value format, which allows for fast lookups.
- **Distributed**: Designed for distributed systems, it runs across multiple nodes and ensures consistency of data across those nodes.
- **Highly Available**: Uses consensus algorithms like Raft to ensure that even in the case of failure, etcd can still make reliable decisions and keep the data available.
- **Data Consistency**: In distributed systems, consistency is crucial. Etcd ensures that all nodes in the cluster have the same data at any given time, solving the challenge of split-brain issues (i.e., inconsistent data between nodes).

### 2. **Etcd in CNCF**

**CNCF (Cloud Native Computing Foundation)** is an organization that fosters the development of cloud-native technologies. It has a variety of projects at different stages of maturity: sandbox, incubating, and graduated projects. Graduated projects are stable, widely adopted, and meet stringent criteria.

- **Etcd is a Graduated Project** under CNCF, meaning it is a mature project with a large community and broad adoption. It plays a foundational role in cloud-native environments.

### 3. **Understanding Databases and Etcd**

There are two general types of databases:

- **Relational Databases**: Like MySQL, PostgreSQL—focused on structured data with tables, rows, and relationships.
- **NoSQL Databases**: Like etcd, MongoDB—focused on key-value pairs, documents, and wide-column storage.

Etcd falls under the **key-value store** category, which is fast and efficient for storing simple data structures. It doesn't use extra space for unused fields or complex relationships—only storing what’s needed.

- **Keys and Values**: In etcd, data is stored in pairs:
    - A **key** is a unique identifier (e.g., `/kubernetes/nodes/node1`).
    - A **value** is the associated data (e.g., the IP address or status of the node).

### 4. **Etcd in Kubernetes**

Now, let’s explore **etcd’s role in Kubernetes**.

In Kubernetes, etcd acts as the **central data store** for the entire cluster. It stores all configuration data, state information, and metadata about the cluster's objects. Every time you create a pod, service, or update a deployment, the information is saved in etcd, and every Kubernetes component reads from it.

### Key Components:

- **Consistency and State**: Etcd ensures that the state of the Kubernetes cluster is **consistent** across all nodes. When you scale up or down, etcd keeps track of the new or removed resources.
- **Key-Value Data**: All Kubernetes objects—like nodes, pods, config maps—are stored as key-value pairs. This enables quick access and updates.
- **Backup and Restore**: Etcd can be backed up and restored easily, making it crucial for disaster recovery in Kubernetes.

### 5. **How Does It Work?**

- **Raft Consensus Algorithm**: Etcd uses Raft to ensure that any changes are consistently applied across all nodes. Even in the case of failures, the system is resilient and ensures the data is up-to-date.
- **Port Communication**: Etcd typically listens on port `2379` for communication with Kubernetes components like the API server.

### Overview Example

Think of Kubernetes as a fleet of ships. Each ship (worker node) carries containers (cargo), and the control ship (the control plane) oversees and manages all the ships. **Etcd** acts as the **database system** on the control ship, where the status of every ship and every container is stored. When a new container is loaded or unloaded from a cargo ship, the information is recorded in **etcd** so that the control ship always knows what's happening.

### **Key Differences:**

| Feature | etcd | Other NoSQL Databases |
| --- | --- | --- |
| **Purpose** | Service discovery, configuration management | General-purpose data storage for applications |
| **Consistency Model** | Strong consistency via Raft consensus | Eventual consistency (Cassandra), or tunable (MongoDB) |
| **Data Structure** | Simple key-value store | Document-based, wide-column, or key-value models |
| **Use Case** | Cluster state, service discovery, leader election | Application data storage, real-time analytics |
| **Scaling** | Small-scale metadata | Massive data sets with horizontal scaling |
| **Data Querying** | Key-based lookup | Complex queries, indexing, and aggregation |

### Kubernetes Volumes: Overview

Volumes in Kubernetes are used to store data for containers. Unlike container storage, which is ephemeral (meaning data is lost when the container is restarted), Kubernetes volumes offer **persistent storage**, ensuring that the data remains available even if the container is recreated.

### Why Use Kubernetes Volumes?

- **Ephemeral Nature of Containers**: By default, data inside a container is lost when the container is terminated or restarted. Volumes provide a way to persist data beyond the container's lifecycle.
- **Shared Data**: Volumes allow multiple containers within the same pod to access the same data, enabling data sharing between them.
- **Data Persistence**: For applications like databases or stateful services, it is important to maintain data even after restarts. Volumes provide this persistence.

### Types of Volumes in Kubernetes

Kubernetes provides various types of volumes, each suited for different use cases. Here are some common types:

1. **EmptyDir**
    - A simple, empty directory created when a pod is assigned to a node. It exists as long as the pod is running, but is deleted when the pod is terminated.
    - **Use Case**: Sharing data between containers in the same pod.
    - **Persistence**: Data lasts only as long as the pod is running.
    
    ```yaml
    volumes:
    - name: shared-data
      emptyDir: {}
    ```
    
2. **HostPath**
    - Mounts a file or directory from the node’s filesystem into your pod.
    - **Use Case**: Useful for accessing data on the host system, but can pose security risks.
    - **Persistence**: Data persists as long as it is on the host.
    
    ```yaml
    volumes:
    - name: host-volume
      hostPath:
        path: /data
    ```
    
3. **PersistentVolumeClaim (PVC)**
    - A PersistentVolume (PV) is a piece of storage provisioned in the cluster. A PVC is a request for storage by a user.
    - **Use Case**: Most common for persistent storage. When a PVC is created, it automatically binds to an available PV.
    - **Persistence**: Data persists across pod restarts.
    
    ```yaml
    volumes:
    - name: my-pvc
      persistentVolumeClaim:
        claimName: my-pv-claim
    ```
    
4. **ConfigMap/Secret**
    - ConfigMaps and Secrets can also be used as volumes to inject configuration data or sensitive information (like passwords) into containers.
    - **Use Case**: Storing configuration files or environment variables.
    - **Persistence**: Typically tied to pod lifecycle.
    
    ```yaml
    volumes:
    - name: config-volume
      configMap:
        name: my-config
    ```
    
5. **NFS (Network File System)**
    - A volume that mounts an NFS share from an external server.
    - **Use Case**: Sharing data across multiple pods in different nodes.
    - **Persistence**: Data persists as long as the NFS server is available.
    
    ```yaml
    volumes:
    - name: nfs-volume
      nfs:
        server: 10.10.10.10
        path: "/var/nfs"
    ```
    
6. **CSI (Container Storage Interface)**
    - A standardized way to interact with various storage providers (e.g., AWS EBS, GCE Persistent Disks, etc.) using a plugin interface.
    - **Use Case**: Used for cloud-based or vendor-specific storage systems.
    - **Persistence**: Data persists according to the storage provider's capabilities.

### Volume Lifecycle

1. **Volume Creation**: Volumes are defined within the pod specification. Volumes can be specific to a pod or requested using PVCs.
2. **Volume Mounting**: Once defined, a volume can be mounted into one or more containers within a pod.
3. **Volume Use**: The containers can now read/write data to/from the mounted volume.
4. **Volume Persistence**: Depending on the type of volume, the data might persist after the pod is deleted or restarted.

![volumes.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/volumes.png)

### Deep Dive Example: Using PersistentVolumeClaim

### Step 1: Define a PersistentVolume (PV)

A **PersistentVolume** is provisioned storage that is either manually created by the administrator or dynamically provisioned.

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: standard
  hostPath:
    path: "/mnt/data"
```

### Step 2: Create a PersistentVolumeClaim (PVC)

A **PersistentVolumeClaim** requests storage from an available PersistentVolume.

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pv-claim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
```

### Step 3: Use the PVC in a Pod

The pod uses the **PersistentVolumeClaim** to mount the volume into the container.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-using-pvc
spec:
  containers:
    - name: app-container
      image: nginx
      volumeMounts:
        - mountPath: "/usr/share/nginx/html"
          name: my-storage
  volumes:
    - name: my-storage
      persistentVolumeClaim:
        claimName: my-pv-claim
```

### Scenario: Before and After Using a Volume

### Before Using a Volume:

- A pod runs an application, but its logs and data are lost every time the container is restarted.
- If multiple containers in the pod need to share data, it becomes difficult because each container has isolated storage.

### After Using a Volume:

- Data generated by the application is stored persistently, and when the container is restarted, the data remains intact.
- Multiple containers in the same pod can share the volume, allowing easy data exchange.

---

### Key Considerations for Using Volumes in Kubernetes:

- **Data Persistence**: Use **PVC** for persistent storage to ensure that data survives pod restarts.
- **Access Modes**:
    - **ReadWriteOnce (RWO)**: The volume can be mounted as read-write by a single node.
    - **ReadOnlyMany (ROX)**: The volume can be mounted as read-only by many nodes.
    - **ReadWriteMany (RWX)**: The volume can be mounted as read-write by many nodes.
- **Storage Classes**: Define how storage is dynamically provisioned in your cluster (e.g., fast SSD storage for high-performance workloads, or slower HDD for archival storage).
- **Security**: Be careful when using **hostPath** or similar volumes, as they can expose your host system's files to containers.

### **Understanding Persistent Volumes (PV) and Persistent Volume Claims (PVC) in Kubernetes**

In Kubernetes, **Persistent Volumes (PV)** and **Persistent Volume Claims (PVC)** handle storage management, providing persistent storage for your applications even after pod restarts or failures.

![image.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/image.png)

### **Diagram Explanation:**

The diagram shows the relationship between **Persistent Volumes (PVs)** and **Persistent Volume Claims (PVCs)**. Each box and icon in the diagram represents the key components of this storage system:

1. **Top Row (Colored Circles) - Data Volumes:**
    - These represent **actual data volumes** that your applications need to store their data persistently. This can be any data required by containers, such as databases or application state.
    - These data volumes are requested by the applications and are associated with PVCs.
2. **Middle Box - Persistent Volume Claim (PVC):**
    - A **Persistent Volume Claim (PVC)** is a **request for storage** by a user (or an application).
    - Applications or users claim storage by creating a PVC. The PVC specifies the **size**, **access mode**, and **storage class** required for the application.
    - This layer helps abstract the physical storage, meaning users don’t need to worry about the underlying storage infrastructure. They simply request storage, and Kubernetes binds the request to a matching **Persistent Volume**.
3. **Bottom Row - Persistent Volumes (PVs):**
    - **Persistent Volumes (PVs)** represent the **actual storage resources** provisioned either by an administrator or dynamically by Kubernetes. These are the physical or cloud-based storage units.
    - Each colored block in the bottom row shows that a **PVC** is bound to a **PV**. PVs can be on a variety of storage backends like NFS, iSCSI, cloud storage, etc.
    - PVs are pre-provisioned storage resources, and once a PVC is created, Kubernetes finds an available PV that matches the request and binds them together.

### **How PV and PVC Work Together:**

1. **Storage Provisioning:**
    - The administrator (or dynamically through a storage class) creates **Persistent Volumes (PVs)** which represent the actual storage available (for example, a 50GB NFS share or a 100GB AWS EBS volume).
2. **Claiming Storage:**
    - Users (or applications) create **Persistent Volume Claims (PVCs)**, requesting a specific amount of storage and defining their access mode (e.g., `ReadWriteOnce` or `ReadOnlyMany`).
3. **Binding:**
    - Kubernetes automatically binds the PVC to an appropriate PV, matching the request based on the PVC’s requirements (such as storage size and access modes).
4. **Using the Storage:**
    - Once the PVC is bound to a PV, the application can use the persistent storage through the PVC. The lifecycle of the data becomes decoupled from the lifecycle of the pod/container. This means that if the pod is destroyed, the data remains intact.

### **Key Features of PVC and PV:**

- **Dynamic Provisioning:**
If no existing PV matches the PVC, Kubernetes can dynamically provision a PV based on the PVC's request, provided a **storage class** is defined.
- **Storage Classes:**
PVs can be tied to different **storage classes** like SSD, HDD, or network-attached storage, giving users flexibility in choosing the appropriate backend for their needs.
- **Retention Policies:**
PVs have retention policies (e.g., **retain**, **delete**) to define what happens to the data when a PVC is deleted.

### **Summary:**

- **PVs** are the actual storage resources, while **PVCs** are the claims made by applications to access those resources.
- **PVs** and **PVCs** allow Kubernetes to separate **storage management** from the application lifecycle, ensuring persistent data even when pods restart or scale.