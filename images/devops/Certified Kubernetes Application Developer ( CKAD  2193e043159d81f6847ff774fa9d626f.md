# Certified  Kubernetes Application Developer ( CKAD )

### **Kind (Kubernetes in Docker)**

**Overview**:

- **Kind** is a tool for running local Kubernetes clusters using Docker containers.
- It’s primarily used for development and testing purposes, allowing Kubernetes clusters to be spun up quickly on a local machine.

**How Kind Works**:

- Instead of using physical or virtual machines as nodes, **Kind uses Docker containers** to simulate Kubernetes nodes.
- These Docker containers act like nodes in a Kubernetes cluster but rely on the resources of the host machine (CPU, RAM, storage).

**Key Points**:

- **Node Simulation**: In a typical Kubernetes cluster, a node is a machine with its own hardware. In Kind, a **node is just a Docker container**.
- **Shared Resources**: The Docker containers (nodes) in Kind share the resources of the host machine (e.g., your laptop), unlike real nodes that have dedicated hardware.
- **Multi-node Clusters**: Kind allows for multi-node clusters by creating multiple Docker containers, each acting as a node. All these nodes run on the same underlying machine but behave like independent nodes in a Kubernetes cluster.
- **Isolation**: Each container (node) has its own isolated environment, providing a realistic Kubernetes experience without needing multiple physical machines.

**Benefits**:

- **Lightweight and Fast**: Since it runs entirely on Docker containers, it’s faster and uses fewer resources compared to running full virtual machines.
- **Great for CI/CD**: Kind is commonly used in continuous integration pipelines to test Kubernetes deployments without needing full infrastructure.

### **Pods and Containers in Kind**

- **Pods**: Just like in any Kubernetes setup, **Pods are the smallest deployable units** in Kind. They are abstracted from the node and contain one or more containers. When you deploy a Pod in Kind, Kubernetes schedules it to run on one of the Docker containers acting as a node.
- **Containers inside Pods**: Each **Pod can contain one or more containers**, usually Docker containers, that run your actual application. These containers are completely isolated from the underlying Docker container that is simulating the node. This means that even though the node is a Docker container itself, the containers inside Pods are just like they would be on a regular Kubernetes node.

### How this works in **Kind**:

- When you deploy a Pod, Kubernetes schedules it on one of the Kind nodes (which are Docker containers). Inside that Pod, your application’s container(s) run just like they would in any other Kubernetes setup.
- The **node (Docker container)** in Kind is just providing the resources and networking that the Pod needs. It doesn’t matter that the node itself is a Docker container; the containers inside the Pod run the same way, fully managed by Kubernetes.

### Key Points:

- **Pods and Containers Work Normally**: Even though the nodes are Docker containers, Pods inside them behave exactly like they would in any Kubernetes cluster.
- **Isolation**: The containers inside Pods are isolated and managed by Kubernetes, separate from the Docker containers that are simulating the nodes.
- **Container within a Container?**: While it may seem like there’s a container running inside a container (because the node itself is a Docker container), Kubernetes abstracts this, so from the Pod’s perspective, it's just running normally on a node.

### **Minikube**

**Overview**:

- **Minikube** is a tool that allows you to run a single-node Kubernetes cluster on your local machine.
- It’s mainly used for development and testing, offering a simple way to spin up a Kubernetes environment locally without needing a cloud provider.

**How Minikube Works**:

- Minikube runs a **virtual machine (VM)** or a **container** (depending on the driver) to simulate a single-node Kubernetes cluster on your local machine.
- This virtual machine acts as both the **master** and the **worker node** in Kubernetes, managing everything from Pods to deployments.

**Key Points**:

- **Single-Node Cluster**: Unlike Kubernetes clusters with multiple nodes, Minikube creates a single node that acts as both the **control plane** and **worker node**.
- **VM or Container-Based**: By default, Minikube runs a lightweight virtual machine (e.g., VirtualBox, Hyper-V) or a container (if using Docker as the driver). This VM or container acts as your entire Kubernetes environment.
- **Pod Deployment**: Minikube allows you to deploy and manage Pods just like a full Kubernetes cluster, but everything runs on the same VM or container.

### **Pods and Containers in Minikube**

- **Pods**: Just like in any Kubernetes setup, you deploy your applications as **Pods**. In Minikube, these Pods run on the single node (the VM or container) that Minikube sets up.
- **Containers inside Pods**: Each Pod contains one or more containers, which run your application. The containers inside the Pod behave just as they would in any Kubernetes environment, isolated and managed by Kubernetes.

### How this works in **Minikube**:

- When you deploy a Pod in Minikube, Kubernetes schedules it to run on the single node. This node could be a virtual machine or a container, depending on the driver Minikube uses.
- **Pods are fully managed** by Kubernetes, and the **containers inside** them run as usual, whether the node is a VM or a Docker container.

### Key Points:

- **Single Node**: Unlike Kind, which simulates multiple nodes using Docker containers, Minikube runs a single node (either as a VM or container).
- **Pods and Containers Work Normally**: Like with Kind, the Pods and containers inside them work exactly like they do in a full Kubernetes setup. Kubernetes abstracts the complexity, so your containers run just as they would in any other Kubernetes environment.
- **Underlying Virtualization**: Depending on the driver you choose, Minikube runs its Kubernetes node on a **VM** (like VirtualBox) or a **Docker container**.

### Benefits:

- **Easy to Set Up**: You can spin up a local Kubernetes cluster with a single command.
- **Realistic Development Environment**: Even though it’s running on a single node, Minikube offers a real Kubernetes experience for developing and testing applications.

### **Kubeadm**

**Overview**:

- **Kubeadm** is a tool designed to bootstrap and configure a **production-grade** Kubernetes cluster.
- Unlike **Minikube** and **Kind**, Kubeadm is typically used to set up **multi-node** Kubernetes clusters on real or virtual machines.
- It provides the necessary commands to **initialize** a control plane and join worker nodes, making it a popular choice for setting up clusters in real-world environments.

**How Kubeadm Works**:

- **Kubeadm** does not create virtual machines or Docker containers for you. Instead, it expects you to have the infrastructure ready (real machines or VMs) to create a Kubernetes cluster.
- The tool **bootstraps** Kubernetes components (control plane and worker nodes) by configuring your machines and installing the necessary Kubernetes components like `kubelet`, `kube-proxy`, etc.

### **Kubeadm Cluster Setup**:

1. **Control Plane Node Initialization**:
    - **Kubeadm** first sets up the **control plane** on a master node, which manages the cluster, schedules workloads, and monitors worker nodes.
    - The master node runs critical components like the **API server**, **etcd**, **scheduler**, and **controller manager**.
    
    Command: `kubeadm init`
    
2. **Joining Worker Nodes**:
    - After initializing the control plane, you can add **worker nodes** to the cluster by using a join command provided by Kubeadm. These worker nodes are the machines where the actual workloads (Pods) will run.
    
    Command: `kubeadm join <control-plane-node-ip>:<port> --token <token>`
    

### **Pods and Containers in Kubeadm**:

- **Pods**: Once the control plane and worker nodes are set up, Kubeadm clusters handle Pods and containers just like any other Kubernetes cluster.
- **Containers inside Pods**: The containers that run your applications are managed inside Pods, and Kubernetes schedules them across the worker nodes in the cluster.
- **Multiple Nodes**: Unlike Minikube or Kind, Kubeadm clusters can have **multiple worker nodes**, meaning Kubernetes can distribute Pods across several machines (or VMs), making it more suitable for larger-scale production environments.

### Key Points:

- **Infrastructure**: Kubeadm doesn't create virtual machines or containers for the cluster; you need to have the physical or virtual machines ready.
- **Multi-Node Clusters**: Kubeadm is built for setting up multi-node clusters, unlike Minikube or Kind, which are more focused on local single-node or container-based clusters.
- **Pods and Containers**: Pods and containers run across worker nodes, and the control plane manages them just like a typical Kubernetes cluster.

### How this works in **Kubeadm**:

- You start by setting up the control plane on a master node.
- Then, add worker nodes to the cluster. These worker nodes are where Kubernetes schedules Pods and containers.
- **Pods are distributed** across multiple worker nodes, making Kubeadm suitable for larger or more complex production environments.

### Benefits:

- **Production-Ready**: Kubeadm is used for real-world, multi-node Kubernetes deployments.
- **Flexible**: It allows you to manually choose the infrastructure (physical machines or VMs) to run your Kubernetes cluster.
- **Standardized Process**: Kubeadm follows a standardized process to set up Kubernetes, making it easier for anyone familiar with Kubernetes to manage clusters.

### Manual Configuration of kubectl in Production Environments

In real-world Kubernetes deployments, particularly in production settings, you often need to configure **kubectl** to communicate with the cluster manually. Here’s how it works:

### 1. **Kubeconfig File**

- The **kubeconfig file** is essential for managing access to your Kubernetes clusters. It contains:
    - **API Server Endpoint**: The URL or IP address of the Kubernetes API server.
    - **Authentication Credentials**: Tokens, certificates, or other credentials needed for secure access.
    - **Context and Namespace Information**: Details that help identify which cluster or namespace you’re interacting with.

### 2. **Obtaining the Kubeconfig**

- **Get the kubeconfig file** from your cluster administrator. This file is usually provided for production clusters hosted in cloud environments (e.g., AWS EKS, GKE, AKS) or managed on-premises.
- In some cases, you may need to create a kubeconfig file manually using the API server's IP address and authentication details.

### 3. **Setting Up the Kubeconfig**

- Place the kubeconfig file in the default location:
    - `~/.kube/config`
- Alternatively, specify the path to the kubeconfig file directly when using **kubectl** with the `-kubeconfig` flag:
    
    ```bash
    bash
    Copy code
    kubectl --kubeconfig=/path/to/kubeconfig get nodes
    
    ```
    

### 4. **Switching Between Clusters**

- If you manage multiple Kubernetes clusters, your kubeconfig can include multiple contexts, allowing you to switch easily between them.
- Use the following command to view current contexts:
    
    ```bash
    bash
    Copy code
    kubectl config get-contexts
    
    ```
    
- Switch context using:
    
    ```bash
    bash
    Copy code
    kubectl config use-context CONTEXT_NAME
    
    ```
    

### 5. **Kind-Specific Kubeconfig**

- If you’re using **Kind** (Kubernetes IN Docker) for local development, it automatically configures the kubeconfig file for you.
- To find where Kind stores its specific kubeconfig, run:
    
    ```bash
    bash
    Copy code
    kind get kubeconfig-path
    
    ```
    

---

### Summary

In production environments, you typically need to manually configure **kubectl** with a kubeconfig file to access your Kubernetes clusters. This setup ensures that you can securely manage your applications and resources across different environments.

### Kubernetes (k8s) commands

### **Cluster Information**

- Get information about the cluster:
    
    `kubectl cluster-info`
    
- View nodes in the cluster:
    
    `kubectl get nodes`
    

---

### **Working with Pods**

- List all Pods:
    
    `kubectl get pods`
    
- List Pods in a specific namespace:
    
    `kubectl get pods -n <namespace>`
    
- Get detailed information about a Pod:
    
    `kubectl describe pod <pod-name>`
    
- Create a Pod from a YAML file:
    
    `kubectl apply -f <file.yaml>`
    
- Delete a Pod:
    
    `kubectl delete pod <pod-name>`
    
- View logs of a Pod:
    
    `kubectl logs <pod-name>`
    
- Access a running Pod (start a shell session inside the Pod):
    
    `kubectl exec -it <pod-name> -- /bin/bash`
    

---

### **Working with Deployments**

- List Deployments:
    
    `kubectl get deployments`
    
- Get details of a specific Deployment:
    
    `kubectl describe deployment <deployment-name>`
    
- Create a Deployment:
    
    `kubectl apply -f <file.yaml>`
    
- Scale a Deployment (change the number of replicas):
    
    `kubectl scale deployment <deployment-name> --replicas=<number>`
    
- Delete a Deployment:
    
    `kubectl delete deployment <deployment-name>`
    

---

### **Working with ReplicaSets**

- List ReplicaSets:
    
    `kubectl get replicasets`
    
- Get details of a ReplicaSet:
    
    `kubectl describe replicaset <replicaset-name>`
    
- Delete a ReplicaSet:
    
    `kubectl delete replicaset <replicaset-name>`
    

---

### **Services**

- List Services:
    
    `kubectl get services`
    
- Get details of a specific Service:
    
    `kubectl describe service <service-name>`
    
- Create a Service:
    
    `kubectl apply -f <file.yaml>`
    
- Delete a Service:
    
    `kubectl delete service <service-name>`
    

---

### **Namespaces**

- List all namespaces:
    
    `kubectl get namespaces`
    
- Create a namespace:
    
    `kubectl create namespace <namespace-name>`
    
- Delete a namespace:
    
    `kubectl delete namespace <namespace-name>`
    

---

### **ConfigMaps and Secrets**

- List ConfigMaps:
    
    `kubectl get configmaps`
    
- Get details of a ConfigMap:
    
    `kubectl describe configmap <configmap-name>`
    
- Create a ConfigMap:
    
    `kubectl create configmap <configmap-name> --from-literal=<key>=<value>`
    
- List Secrets:
    
    `kubectl get secrets`
    
- Get details of a Secret:
    
    `kubectl describe secret <secret-name>`
    
- Create a Secret:
    
    `kubectl create secret generic <secret-name> --from-literal=<key>=<value>`
    

---

### **Persistent Volumes**

- List Persistent Volumes (PVs):
    
    `kubectl get pv`
    
- List Persistent Volume Claims (PVCs):
    
    `kubectl get pvc`
    
- Create a Persistent Volume:
    
    `kubectl apply -f <file.yaml>`
    
- Delete a Persistent Volume:
    
    `kubectl delete pv <pv-name>`
    

---

### **Other Useful Commands**

- View the current context (current cluster, namespace, etc.):
    
    `kubectl config view`
    
- Switch between contexts:
    
    `kubectl config use-context <context-name>`
    
- View all resources (Pods, services, deployments, etc.):
    
    `kubectl get all`
    
- Get detailed information about a resource (e.g., Pod, Service, Deployment):
    
    `kubectl describe <resource-type> <resource-name>`
    
- Apply multiple YAML files at once:
    
    `kubectl apply -f <directory-with-yaml-files>`
    

### Pod Creation

Creating a Pod in Kubernetes involves writing a YAML manifest file that defines the desired state of the Pod and then using `kubectl` commands to apply that configuration. Here's a detailed breakdown:

### YAML Manifest for a Pod

Here's a basic example of a Pod YAML file:

```yaml
apiVersion: v1                       # Specifies the version of the Kubernetes API
kind: Pod                            # Defines the kind of resource; in this case, a Pod
metadata:                             # Metadata about the Pod
  name: my-pod                       # Name of the Pod
  labels:                            # Optional: key-value pairs for categorizing the Pod
    app: my-app
spec:                                # Specification of the desired behavior of the Pod
  containers:                        # List of containers in the Pod
  - name: my-container               # Name of the container
    image: my-image:latest           # Docker image to use for the container
    ports:                           # List of ports to expose
    - containerPort: 80              # Port that the container listens on
    resources:                       # Optional: Resource requests and limits
      requests:
        memory: "64Mi"              # Minimum memory required
        cpu: "250m"                 # Minimum CPU required
      limits:
        memory: "128Mi"             # Maximum memory allowed
        cpu: "500m"                 # Maximum CPU allowed
  restartPolicy: Always              # Restart policy for the Pod
```

### Important Sections Explained

- **apiVersion**: Specifies which version of the Kubernetes API you're using to create this object.
- **kind**: Indicates the type of resource being created (e.g., Pod, Deployment).
- **metadata**: Contains information about the Pod, including its name and optional labels. Labels help organize and select resources.
- **spec**: Defines the desired state of the Pod.
    - **containers**: A list of containers that will run in the Pod.
        - **name**: The name of the container.
        - **image**: The Docker image to use for the container.
        - **ports**: Specifies which ports the container will expose.
        - **resources**: Defines resource requests and limits for the container.
            - **requests**: Minimum resources required.
            - **limits**: Maximum resources allowed.
    - **restartPolicy**: Defines the restart behavior of the Pod (e.g., Always, OnFailure, Never).

### Commands to Create a Pod

1. **Create the YAML file**: Save the above YAML configuration to a file named `my-pod.yaml`.
2. **Apply the configuration**:
To create the Pod, use the following command:
    
    ```bash
    kubectl apply -f my-pod.yaml
    ```
    
3. **Check the status of the Pod**:
After applying the configuration, you can check the status of the Pod with:
    
    ```bash
    kubectl get pods
    ```
    
4. **Describe the Pod**:
To get more detailed information about the Pod, use:
    
    ```bash
    kubectl describe pod my-pod
    ```
    
5. **View logs**:
To see the logs of the container running inside the Pod, use:
    
    ```bash
    kubectl logs my-pod
    ```
    

### Multi-Container Pods in Kubernetes

In Kubernetes, a Pod can run multiple containers that work together. These containers share the same network namespace, meaning they can communicate easily via `localhost`. Multi-container Pods are useful for tightly coupled applications, where different containers perform complementary functions.

### Types of Multi-Container Pods

1. **Sidecar Container**
    - **Definition**: A Sidecar container extends or enhances the functionality of the main application container. It typically runs alongside the main application, sharing the same lifecycle and resources.
    - **Example**: A common use case is a logging agent that collects logs from the main application. For instance, an Nginx container as the main app and a Fluentd container as a Sidecar for log forwarding.
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: web-app
    spec:
      containers:
        - name: nginx
          image: nginx
        - name: fluentd
          image: fluent/fluent
    ```
    
2. **Ambassador Container**
    - **Definition**: An Ambassador container acts as a proxy for other services, facilitating communication between different Pods or external services. It typically handles networking concerns like load balancing or service discovery.
    - **Example**: You might have a main application container and an Ambassador container that routes traffic to it from outside the cluster.
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: app-ambassador
    spec:
      containers:
        - name: my-app
          image: myapp:latest
        - name: ambassador
          image: ambassador
    ```
    
3. **Adapter Container**
    - **Definition**: An Adapter container translates between the interfaces of the main application and other services or systems. It helps to adapt or modify requests and responses between the application and other services.
    - **Example**: A case could be a main application container that communicates with an external API, while an Adapter container modifies requests or responses to match the required format.
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: app-adapter
    spec:
      containers:
        - name: my-app
          image: myapp:latest
        - name: adapter
          image: adapter-image
    ```
    

### Summary

Multi-container Pods in Kubernetes allow you to run related containers together for specific use cases. Sidecars enhance functionality, Ambassadors facilitate communication, and Adapters bridge interface differences. Each type serves a unique purpose, enhancing the capabilities of your applications within Kubernetes.

### Init Containers in Kubernetes

**Init containers** are specialized containers that run before the main application containers in a Pod. They handle setup tasks that need to be completed before the main containers can start. Unlike regular containers, init containers always run to completion before subsequent containers are started.

### Key Features:

1. **Run sequentially**: Init containers execute in a specified order, one after another.
2. **Must complete successfully**: If an init container fails, the Pod will keep restarting until it completes successfully.
3. **Different runtime environment**: Init containers can have different images, configurations, and permissions compared to the main containers.
4. **Setup tasks**: Used to initialize things like loading config files, waiting for an external service, or preparing a database.

### Example Use Cases:

- Checking if a database is up and running before launching an app.
- Pre-fetching configuration or secrets from a secure storage system.

### Example of an Init Container

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
spec:
  initContainers:
  - name: init-mydb
    image: busybox
    command: ['sh', '-c', 'until nslookup mydb-service; do echo waiting for mydb; sleep 2; done;']
  containers:
  - name: my-app
    image: my-app-image
    ports:
    - containerPort: 80
```

### Explanation:

- **initContainers**:
    - The init container `init-mydb` waits for the `mydb-service` to be ready. It checks continuously until the database is available.
- **Main container**:
    - The main app container (`my-app`) starts only after the init container has successfully completed its job.

### Key Points:

- **Init containers are useful** for performing pre-requisite tasks such as environment setup, service dependency checks, and configuration loading.
- **If an init container fails**, the entire Pod will restart and keep retrying until the init container completes successfully.

Init containers make sure that the environment is fully prepared before the application starts running, ensuring smoother operations.

### Replication Controller in Kubernetes

A **Replication Controller (RC)** ensures that a specified number of Pod replicas are running at any given time. It maintains the desired number of replicas by creating or deleting Pods as needed to match the defined count. While it's now being gradually replaced by **ReplicaSets**, it's still useful to understand, especially in older setups.

### Key Features:

1. **Pod Replication**: Ensures that the specified number of Pod replicas are running.
2. **Self-healing**: If a Pod dies, the RC automatically creates a new Pod to replace it.
3. **Scaling**: You can easily scale up or down by adjusting the replica count.
4. **Pod Monitoring**: Constantly monitors the health of Pods.

### Example of a Replication Controller YAML:

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
spec:
  replicas: 3
  selector:
    app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp-container
        image: nginx
        ports:
        - containerPort: 80
```

### Explanation:

- **replicas**: Specifies the desired number of Pod replicas (3 in this case).
- **selector**: Used to identify which Pods are managed by this Replication Controller (Pods with the label `app: myapp`).
- **template**: The Pod template defines the specifications for the Pods that the RC will create.

### ReplicaSets in Kubernetes

A **ReplicaSet (RS)** ensures that a specified number of Pod replicas are running at any given time, similar to a Replication Controller but with more features. It replaces the older ReplicationController and is mainly used by **Deployments** to manage the lifecycle of Pods.

### How ReplicaSets Work:

- **ReplicaSets monitor Pods** with matching labels and ensure the desired number of replicas are running.
- **If a Pod is deleted**, the ReplicaSet creates a new one to maintain the correct replica count.
- **If additional Pods already exist** (e.g., from manual creation), the ReplicaSet will delete the extra Pods to match the specified replica count.

### Key Differences from Replication Controllers:

- **Label selectors**: Support richer label matching with `matchLabels` and `matchExpressions`.
- **Use in Deployments**: Often managed by Deployments rather than directly by the user.

### Manifest Explanation

Here's a breakdown of the manifest you provided:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-rs
  labels:
    app: front-end-rs
    type: dev
spec:
  replicas: 4
  selector:
    matchLabels:
      app: front-end
  template:
    metadata:
      name: alnafi-pod
      labels:
        app: front-end
    spec:
      containers:
      - name: alpha
        image: nginx
```

### Manifest Breakdown:

1. **apiVersion & kind**:
    - `apiVersion: apps/v1` — Specifies the version of the Kubernetes API.
    - `kind: ReplicaSet` — Indicates that this object is a ReplicaSet.
2. **metadata**:
    - `name: myapp-rs` — The name of the ReplicaSet.
    - `labels` — Additional metadata for the ReplicaSet itself (`app: front-end-rs`, `type: dev`).
3. **spec**:
    - **replicas: 4** — Defines the desired number of Pods (4 replicas).
4. **selector**:
    - `matchLabels: app: front-end` — The ReplicaSet looks for Pods with this label to manage. It will ensure there are exactly 4 Pods with this label.
5. **template**:
    - The `template` defines the Pod that the ReplicaSet will create if required.
    - **metadata**: Labels like `app: front-end` ensure that this Pod will match the ReplicaSet's `matchLabels`.
    - **spec**: Defines the container inside the Pod, with the name `alpha` and image `nginx`.

### How the ReplicaSet Behaves:

- If **no Pods exist** with the label `app: front-end`, the ReplicaSet will create 4 new Pods with the specified `alpha` container.
- If **more than 4 Pods** with the label `app: front-end` already exist, the ReplicaSet will delete extra Pods to maintain 4 replicas.
- If **fewer than 4 Pods** exist, the ReplicaSet will create new Pods to reach 4 replicas.

### Important Note:

- The **selector (`matchLabels`)** and **template (`metadata.labels`)** must match, so the ReplicaSet can correctly identify which Pods to manage. In your example, the Pods must have the label `app: front-end`.

### Kubernetes Deployment

A **Deployment** in Kubernetes is a resource used to manage the lifecycle of applications. It helps with:

- **Scaling** (upscaling and downscaling).
- **Rolling updates**: Seamless updates to new versions.
- **Self-healing**: Automatically restarting Pods when they fail.

### Why Deployments Are Better:

- **Scaling**: Easily scale Pods up or down without downtime.
- **Rollbacks**: If a new version is faulty, you can revert to a previous stable version.
- **Pod management**: Even if a Pod is deleted, the Deployment recreates it.
- **Works with ReplicaSets**: Deployments create and manage ReplicaSets, which in turn manage Pods.

---

### How It Works:

1. **If you delete a Pod**: The Deployment's ReplicaSet will automatically recreate the Pod to match the desired number of replicas.
2. **If you delete the ReplicaSet**: The Deployment will notice that its ReplicaSet is missing and create a new one.
3. **Manual scaling**: You can manually scale up or down using the command `kubectl scale deploy`.
4. **Automatic scaling**: Deployments can be combined with autoscalers to scale based on CPU or memory utilization.

---

### Commands

- `kubectl get pod,rs,deploy` — Lists Pods, ReplicaSets, and Deployments.
- `kubectl scale deploy simple-deploy --replicas 6` — Manually scales the Deployment to 6 replicas.
    - This is **manual scaling**. You can later adjust the replica count back down using the same command.
- `kubectl edit deploy <deploy-name>` — Opens the Deployment in an editor to change configurations such as replicas, container images, etc.
    - If you change replicas in this way and then run `kubectl apply -f file-name`, the settings from the YAML file will override manual edits.
- **If you delete a Deployment**: The associated ReplicaSet and Pods are also deleted.
- **If you specify 0 replicas**, all Pods in the Deployment are deleted.

---

### Deployment Manifest Example (With Comments)

```yaml
apiVersion: apps/v1          # API version of Kubernetes for apps like Deployments
kind: Deployment             # This resource is a Deployment
metadata:
  name: simple-deploy        # Name of the Deployment
spec:
  replicas: 3                # Number of replicas (Pods) to maintain
  selector:                  # Selector to match Pods with the label "app: frontend"
    matchLabels:
      app: frontend          # Label to match the Pods managed by this Deployment
  template:                  # Template used to create Pods
    metadata:
      labels:
        app: frontend        # Labels applied to the Pods created by this Deployment
    spec:
      containers:
      - name: nginix-container   # Name of the container inside the Pod
        image: nginx:1.14.2      # Container image to use (nginx 1.14.2 version)
        ports:
        - containerPort: 80      # Port exposed by the container inside the Pod
```

---

### Key Concepts & Scenarios:

- **Manual Scaling**:
    - If you run `kubectl scale deploy simple-deploy --replicas 6`, the Deployment will adjust to 6 replicas.
    - Scaling down is similar: `kubectl scale deploy simple-deploy --replicas 2`.
- **What happens if you change the replicas in YAML**:
    - If you manually change the replica count in the Deployment YAML file (e.g., change to 4 replicas), then apply the file again with `kubectl apply -f file-name`, the Deployment will adjust to the number of replicas in the file, overriding manual scaling.
- **What happens if you delete a Deployment**:
    - Deleting a Deployment will also delete the associated ReplicaSet and its Pods.

---

Deployments provide a more powerful and flexible way to manage applications compared to directly managing Pods or ReplicaSets. It adds self-healing, rollouts, rollbacks, and scaling features that are essential in a production environment.

### Kubernetes Deployment Updates and Rollbacks

Kubernetes **Deployments** provide built-in mechanisms for updating and rolling back applications. They allow you to deploy new versions of your application seamlessly and revert to previous versions if something goes wrong.

### Update Strategies:

![deploy-stratergies.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/deploy-stratergies.png)

1. **Rolling Update (default strategy)**:
    - **How it works**: Gradually replaces old Pods with new Pods, ensuring that at least some instances of the old version are running while new ones are being started.
    - **Minimizes downtime**: Ensures that there's no downtime during the update process. New Pods are created before the old ones are terminated.
    - **Control over updates**: You can configure how many Pods are updated simultaneously (through `maxUnavailable` and `maxSurge` settings).
    
    Example:
    
    - **maxUnavailable**: The maximum number of Pods that can be unavailable during the update (default is 25% of total replicas).
    - **maxSurge**: The number of extra Pods that can be created temporarily during the update (default is 25% of total replicas).
2. **Recreate Strategy**:
    - **How it works**: Terminates all existing Pods before creating new ones.
    - **Use case**: Suitable when you need all instances of the old version to be stopped before deploying the new version (e.g., for compatibility reasons).

---

### Rolling Update (Default Strategy)

The **Rolling Update** strategy is the default deployment strategy in Kubernetes and works by updating the application gradually. It replaces one or a few Pods at a time, instead of updating them all at once.

- **Why it's used**: Ensures minimal to zero downtime during updates.
- **Configuration**:
    - `maxUnavailable`: Specifies the maximum number of Pods that can be unavailable during the update.
    - `maxSurge`: Specifies the number of extra Pods that can be added temporarily during the update.

### Example:

If you have a Deployment with 4 replicas and set:

- `maxUnavailable: 1`
- `maxSurge: 1`

Then at any point during the update, there will be at least 3 Pods available, and Kubernetes may run up to 5 Pods temporarily (4 replicas + 1 surge Pod).

**Manifest Example for Rolling Update:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rolling-update-deploy
spec:
  replicas: 4
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1   # Maximum number of Pods that can be unavailable during update
      maxSurge: 1         # Maximum number of extra Pods created during the update
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: nginx-container
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

---

### Rollbacks

Kubernetes allows you to **rollback** to previous versions of a Deployment if the update causes issues.

- **How rollbacks work**: Kubernetes keeps track of Deployment revisions. If a new version fails, you can roll back to a previous version.
- **Command to Rollback**:
    
    ```bash
    kubectl rollout undo deployment/<deployment-name>
    ```
    
- **View revision history**:
    
    ```bash
    kubectl rollout history deployment/<deployment-name>
    ```
    

### Example Use Case:

1. You deploy a new version of your application.
2. After the deployment, you notice issues with the new version.
3. You use the rollback command to revert to the previous stable version.

---

### Summary of Update Strategies:

| **Strategy** | **Description** | **Use Case** |
| --- | --- | --- |
| **Rolling Update** | Gradually updates Pods, ensuring minimal downtime (default). | General updates, where high availability is important. |
| **Recreate** | Terminates all old Pods before creating new ones. | When all old versions must be stopped before new ones start. |

### Commands for Deployment Updates, Rollbacks, and Status:

1. **Check deployment status:**
    - View the status of a Deployment, including rollout progress.
    - `kubectl rollout status deployment/<deployment-name>`
2. **Trigger a new deployment:**
    - Update the image or other configuration in the Deployment's manifest and apply it.
    - `kubectl apply -f <deployment-manifest.yml>`
3. **Scale a deployment manually:**
    - Change the number of replicas for a Deployment.
    - `kubectl scale deployment <deployment-name> --replicas=<number-of-replicas>`
4. **Edit a live deployment:**
    - Edit the Deployment’s configuration live.
    - `kubectl edit deployment <deployment-name>`
5. **View the history of a deployment:**
    - Check the revision history of a Deployment (useful for tracking previous versions).
    - `kubectl rollout history deployment/<deployment-name>`
6. **Roll back to a previous version of a deployment:**
    - Reverts to a previous revision of the Deployment.
    - `kubectl rollout undo deployment/<deployment-name>`
7. **Get detailed information about revisions:**
    - View details about a specific revision of the Deployment.
    - `kubectl rollout history deployment/<deployment-name> --revision=<revision-number>`
8. **Pause a deployment (during an update):**
    - Pause the rollout, which stops new pods from being created or terminated.
    - `kubectl rollout pause deployment/<deployment-name>`
9. **Resume a paused deployment:**
    - Continue a paused rollout.
    - `kubectl rollout resume deployment/<deployment-name>`

---

### Flags for Deployment Strategies (Rolling Update):

1. **Set maxUnavailable**:
    - The maximum number of Pods that can be unavailable during the update (default is 25%).
    - In the manifest, this is written under the `strategy.rollingUpdate` section.
    
    ```yaml
    strategy:
      type: RollingUpdate
      rollingUpdate:
        maxUnavailable: 1  # or a percentage like "25%"
    ```
    
2. **Set maxSurge**:
    - The number of extra Pods that can be created temporarily during the update (default is 25%).
    
    ```yaml
    strategy:
      type: RollingUpdate
      rollingUpdate:
        maxSurge: 1  # or a percentage like "25%"
    ```
    

### Other Useful Commands:

- **View all deployments, replica sets, and pods:**
    - `kubectl get deploy,rs,pod`
- **Delete a deployment:**
    - This will delete the Deployment, including its ReplicaSets and Pods.
    - `kubectl delete deployment <deployment-name>`

### Deployment Strategies in Kubernetes: Blue/Green & Canary Deployment

In Kubernetes, **Blue/Green** and **Canary** deployments are strategies used to minimize downtime and reduce risks during application updates.

### 1. **Blue/Green Deployment:**

**Definition:**

- In a Blue/Green deployment, two environments (versions) are maintained:
    - **Blue**: The current production environment (live version).
    - **Green**: The new version to be deployed.

**How it works:**

- **Blue** is the currently running version of the application.
- The **Green** version is deployed alongside the Blue version but does not receive traffic until testing is complete.
- Once the **Green** version is fully tested, traffic is switched from **Blue** to **Green** with no downtime.
- If issues are found in the Green version, traffic can be easily switched back to Blue (rollback).

**Advantages:**

- Minimal downtime as the traffic switch happens instantly.
- Easy rollback as both versions exist simultaneously.

**Disadvantages:**

- Requires double the resources (both versions need to run simultaneously).

**How to Implement in Kubernetes:**

- Create separate Kubernetes services for the Blue and Green deployments.
- Use a service like **Ingress** or a load balancer to switch traffic from Blue to Green.

---

### 2. **Canary Deployment:**

**Definition:**

- In a Canary deployment, a small percentage of users are routed to the new version while the majority continue using the current version.
- Gradually, more traffic is routed to the new version until 100% of the traffic is served by the new deployment.

**How it works:**

- A small portion (e.g., 10%) of user traffic is directed to the **Canary** version (the new version).
- The **Canary** version is monitored for errors or performance issues.
- If the Canary version performs well, traffic is gradually increased until it completely replaces the older version.
- If any issues are detected, the deployment can be rolled back to the previous version without affecting most users.

**Advantages:**

- Limits the risk of introducing new versions by only exposing a small subset of users.
- Allows real-world testing with actual users.

**Disadvantages:**

- Rollbacks are more complicated than in Blue/Green as part of the user base is already using the new version.

**How to Implement in Kubernetes:**

- Use Kubernetes **ReplicaSets** and **Services**.
- Modify the number of replicas gradually to shift traffic from the old version to the new version.
- You can configure **Ingress** or a service mesh like **Istio** to route a portion of the traffic to the Canary pods.

---

### Example: Canary Deployment in Kubernetes (YAML)

This example shows how to implement a basic Canary deployment by specifying two different sets of replicas for the Canary and Stable releases.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-stable
spec:
  replicas: 4
  selector:
    matchLabels:
      app: myapp
      version: stable
  template:
    metadata:
      labels:
        app: myapp
        version: stable
    spec:
      containers:
      - name: app-container
        image: myapp:stable
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-canary
spec:
  replicas: 1  # Small percentage of traffic will go to the Canary version
  selector:
    matchLabels:
      app: myapp
      version: canary
  template:
    metadata:
      labels:
        app: myapp
        version: canary
    spec:
      containers:
      - name: app-container
        image: myapp:canary
```

In this example, you have:

- **Stable Deployment**: Receives most traffic.
- **Canary Deployment**: Receives a small percentage of traffic.

### Blue/Green Deployment Example

To implement Blue/Green deployment, you would typically deploy two separate sets of pods and switch the traffic routing using a **Service** or **Ingress**. Example for switching between Blue and Green services:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-blue
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
      version: blue
  template:
    metadata:
      labels:
        app: myapp
        version: blue
    spec:
      containers:
      - name: app-container
        image: myapp:blue
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-green
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
      version: green
  template:
    metadata:
      labels:
        app: myapp
        version: green
    spec:
      containers:
      - name: app-container
        image: myapp:green
```

Then, use a **Service** to switch between the Blue and Green versions:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
    version: green  # Change to 'blue' or 'green' as needed
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

By updating the `version` in the service selector, you can switch between Blue and Green deployments.
# You can then ssh to the node which has the pod and then curl it 

### Namespaces in Kubernetes

**Namespaces** are a way to divide Kubernetes cluster resources between multiple users. They provide a mechanism for isolating resources and organizing objects in a cluster.

---

### 1. **Default Namespace**

- When you create resources like pods, services, etc., without specifying a namespace, they are placed in the `default` namespace.
- If no namespace is mentioned in the manifest or command, Kubernetes assumes it's in the `default` namespace.

---

### 2. **Some Other Built-in Namespaces**

- `kube-system`: Contains Kubernetes system components (e.g., API server, controller manager).
- `kube-public`: Accessible by all users and contains publicly accessible data.
- `kube-node-lease`: Contains node lease objects used for node heartbeats.

---

### 3. **Namespace - Isolation**

Namespaces are useful for isolating workloads in the following ways:

- **Logical Separation**: Different teams or environments (e.g., `development`, `staging`, `production`) can have isolated resources.
- **Access Control**: By combining namespaces with Role-Based Access Control (RBAC), you can restrict access to certain namespaces for specific users or groups.

---

### 4. **Namespace Resource Limits**

Namespaces can have resource limits applied to them, which ensures that users or workloads within a namespace don't consume more than a set amount of cluster resources.

- **ResourceQuota** objects can limit the number of resources (e.g., pods, CPU, memory) that can be created in a namespace.

Example of a resource quota manifest:

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: namespace-quota
  namespace: dev
spec:
  hard:
    pods: "10"              # Max 10 pods
    requests.cpu: "4"        # Max 4 CPU cores
    requests.memory: "8Gi"   # Max 8GB memory
```

---

### 5. **Connecting to a Different Namespace Resource**

If you need to access resources from another namespace (e.g., get pods in the `dev` namespace), you can use the `-n` flag:

```bash
kubectl get pods -n dev
```

---

### 6. **Getting Information from a Different Namespace**

You can retrieve resources like pods, services, or other objects from a specific namespace using the following commands:

- Get pods in a specific namespace:
    
    ```bash
    kubectl get pods -n dev
    ```
    
- Get services in the `kube-system` namespace:
    
    ```bash
    kubectl get svc -n kube-system
    ```
    

---

### 7. **Specifying Namespace in the Manifest File**

To create a resource in a specific namespace using a YAML file, you can add the `namespace` field under `metadata`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  namespace: dev
spec:
  containers:
  - name: my-container
    image: nginx
```

---

### 8. **Creating a Namespace**

To create a new namespace, you can use `kubectl` or create it via a manifest file.

- Using `kubectl`:
    
    ```bash
    kubectl create namespace dev
    ```
    
- Using a manifest file:
    
    ```yaml
    apiVersion: v1
    kind: Namespace
    metadata:
      name: dev
    ```
    
- Apply the file:
    
    ```bash
    kubectl apply -f namespace.yml
    ```
    

---

### 9. **Switching Between Namespaces**

To switch between namespaces, you can either specify the namespace in each command or change your current namespace context using `kubectl config set-context`:

- Temporarily, using `n`:
    
    ```bash
    kubectl get pods -n dev
    ```
    
- To permanently switch to a namespace:
    
    ```bash
    kubectl config set-context --current --namespace=dev
    ```
    

---

### 10. **Resource Quota**

Resource quotas are used to manage and limit the amount of resources used within a namespace, such as CPU, memory, and the number of objects (pods, services).

- Example resource quota:
    
    ```yaml
    apiVersion: v1
    kind: ResourceQuota
    metadata:
      name: my-quota
      namespace: dev
    spec:
      hard:
        pods: "10"                 # Limits to 10 pods
        requests.cpu: "4"           # Limits to 4 CPU cores
        requests.memory: "8Gi"      # Limits to 8GB memory
    ```
    

Apply the quota to your namespace:

```bash
kubectl apply -f resource-quota.yml
```

---

By using namespaces, you can isolate resources, limit their usage, and organize them in a way that makes the management of clusters easier and more secure.

### Diff of Namespace & Context

### **1. Namespace**

- **Purpose**: Namespaces are used to divide and isolate resources within a Kubernetes cluster. They allow for the logical separation of resources (pods, services, deployments, etc.) so that different teams or environments (e.g., `dev`, `staging`, `production`) can operate within the same cluster without interference.
- **Scope**: Namespaces isolate resources *within* the same Kubernetes cluster.
- **Examples**: `default`, `kube-system`, `dev`, `staging`, `production`.

### **Key Points:**

- Each Kubernetes resource (like a pod, service, deployment) belongs to a namespace.
- Namespaces provide resource isolation and management (you can apply quotas, RBAC rules, etc.).
- Resources in different namespaces can have the same name, but within a namespace, names must be unique.

```bash
kubectl get pods -n dev  # Get pods in the 'dev' namespace
```

---

### **2. Context**

- **Purpose**: A context in Kubernetes defines access to a specific cluster and namespace for `kubectl`. It combines three key pieces of information: the cluster (API server endpoint), the user (authentication information), and the namespace.
- **Scope**: Contexts allow you to easily switch between clusters or between namespaces within a cluster. A context is stored in your `kubeconfig` file and allows you to connect to different Kubernetes clusters or namespaces without manually specifying the cluster or credentials each time.
- **Examples**: You may have a context to connect to a production cluster (`prod-context`) and another to connect to a development cluster (`dev-context`), each pointing to different namespaces or clusters.

### **Key Points:**

- A context is a combination of cluster, user, and namespace.
- You can switch between different contexts when managing multiple clusters or namespaces.
- When you change the context, `kubectl` uses the associated cluster, user, and namespace for the commands you run.

```bash
kubectl config get-contexts  # List all contexts
kubectl config use-context dev-context  # Switch to a different context
```

---

### **Comparison**

| Feature | **Namespace** | **Context** |
| --- | --- | --- |
| **Purpose** | Isolate resources within a single cluster | Define access to a cluster and namespace |
| **Scope** | A single Kubernetes cluster | Can span across multiple clusters |
| **Switching** | Use the `-n` flag to specify a namespace | Use `kubectl config use-context` to switch |
| **Example** | Separate environments like `dev` and `prod` | Switch between `dev-context` and `prod-context` |
| **Config** | Specified in the resource manifest or `kubectl` commands | Stored in the `kubeconfig` file, managed by `kubectl config` |

---

### **Example:**

- **Namespace**: You have a `development` and a `production` namespace in the same Kubernetes cluster. These namespaces help you separate the resources for development and production environments within the same cluster.
- **Context**: You have different clusters for `development` and `production`, and each has its own namespace. You can define contexts like `dev-context` (pointing to the development cluster and namespace) and `prod-context` (pointing to the production cluster and namespace). By switching between contexts, you can easily manage different clusters or namespaces.

---

**In summary**, namespaces help divide and manage resources inside a cluster, while contexts are used to define how `kubectl` interacts with different clusters or namespaces, often stored in your `kubeconfig` file.

### **Kubernetes Jobs**

A Kubernetes Job is a resource that allows you to run one or more pods to completion. Unlike Deployments, Jobs ensure that a certain number of pods successfully terminate. Jobs are useful for running short-lived tasks or batch processes, unlike typical workloads (like Deployments) which run continuously.

### **Workloads and Types of Jobs**

1. **Jobs**: Run a pod until a task is complete.
2. **CronJobs**: A time-scheduled version of Jobs.
3. **Parallel Jobs**: Jobs that require running multiple pods at once.

### **Restart Policies**

- **`Never`**: (default) If the pod fails, it is not restarted.
- **`OnFailure`**: Pod is restarted only if it fails.
- **`Always`**: Continuously restarts the pod (not applicable for Jobs).

---

### **Job Manifest Example with Explanation**

```yaml
apiVersion: batch/v1          # Specifies that this is a Job resource from the batch API.
kind: Job                     # This declares the resource type as a Job.
metadata:
  name: my-job                # Name of the Job resource.
spec:
  template:                   # Defines the pod template (the specification of the pod to be created).
    spec:
      containers:
      - name: example-job      # Name of the container in the Job.
        image: busybox:stable  # The container image to use (busybox in this case).
        command: ['echo', 'this is a job']  # Command to be executed in the container.
      restartPolicy: Never      # Ensures that the pod will not restart if it fails or completes (default for Jobs).

  backoffLimit: 4              # Number of times to retry the job on failure before marking it as failed.
  activeDeadlineSeconds: 40     # Maximum time in seconds before the Job times out, regardless of success or failure.
```

---

### **Key Fields Explained**

- **`spec.template.spec.containers`**: Defines the container (or multiple containers) that will run in the pod.
    - **`name`**: Name of the container.
    - **`image`**: Docker image to run in the container.
    - **`command`**: The command that the container runs.
- **`restartPolicy`**: Defines whether and when a container should be restarted.
    - **`Never`**: The pod won't restart on failure.
- **`backoffLimit`**: Defines the number of retry attempts for the Job if it fails.
- **`activeDeadlineSeconds`**: The total duration (in seconds) the Job is allowed to run before it is terminated.

---

### **Creating, Viewing, and Deleting a Job**

- **Create a Job**:`kubectl apply -f job.yml`
- **View Jobs**:`kubectl get jobs`
- **Describe a Job**:`kubectl describe job my-job`
- **View Job Logs**:`kubectl logs job/my-job`
- **Delete a Job**:`kubectl delete job my-job`

---

### **Multiple Pods and Completions**

Kubernetes Jobs allow you to specify the number of pods to run concurrently and the number of successful completions.

```yaml
spec:
  completions: 3              # The job is considered successful when 3 pods complete successfully.
  parallelism: 2              # Specifies that 2 pods should run in parallel.
```

- **`completions`**: The number of successful pod completions needed to mark the Job as complete.
- **`parallelism`**: The number of pods to run concurrently.

---

### **What Happens if a Job Fails?**

- If a pod in the job fails, Kubernetes will retry up to `backoffLimit` times.
- After `backoffLimit` retries, the Job is marked as "failed."

For example, if `backoffLimit: 3` is specified, and the Job fails 3 times, Kubernetes will not retry the Job any further.

---

### **Parallelism**

- **Parallelism** is the ability of Kubernetes Jobs to run multiple pods concurrently.
- This is useful for tasks that can be broken down into smaller, parallelizable units.

Example manifest with parallelism:

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: parallel-job
spec:
  parallelism: 3               # Run 3 pods simultaneously.
  completions: 6               # Job is successful when 6 pods complete successfully.
  template:
    spec:
      containers:
      - name: example-job
        image: busybox:stable
        command: ['echo', 'this is a parallel job']
      restartPolicy: Never
  backoffLimit: 4
  activeDeadlineSeconds: 60
```

### **Commands Summary**

- To create a job:`kubectl apply -f job.yml`
- To get job details:`kubectl get jobs`
- To view logs from the job:`kubectl logs job/my-job`
- To delete a job:`kubectl delete job my-job`

---

**In Summary**:

- Jobs are short-lived, ensuring that the desired number of pods complete successfully.
- They are useful for batch processing, data processing, or tasks that don’t run continuously.
- You can control retries (`backoffLimit`) and the maximum execution time (`activeDeadlineSeconds`).
- Jobs support parallel execution using `parallelism` and `completions`.

### **Imperative Commands in Kubernetes**

- **Command to make a pod and deploy container using nginx docker image:**
    
    `kubectl run nginx --image=nginx`
    
- **Command to check the status of pods:**
    
    `kubectl get pods`
    
- **Command to get a specific pod:**
    
    `kubectl get pods name_of_pod`
    
- **Command for detailed information of a pod:**
    
    `kubectl describe pod nginx`
    
- **Command to check the status of pods with wide output:**
    
    `kubectl get pods -o wide`
    
- **Command to make pods from a YAML configuration file:**
    
    `kubectl create -f "name_of_YAML_file.yml"`
    
    or
    
    `kubectl apply -f "name_of_YAML_file.yml"`
    
- **Command to check the number of nodes in a cluster:**
    
    `kubectl get nodes`
    
- **Command to check the status of nodes with more detail:**
    
    `kubectl get node -o wide`
    
- **Command to check the image used to create a container in a pod:**
    
    `kubectl describe pod name_of_pod | grep -i image`
    
- **Command to create a pod using a YAML file (dry-run):**
    
    `kubectl run redis --image=redis123 --dry-run=client -o yaml > pod.yaml`
    
- **Command to see the list of replication controllers created:**
    
    `kubectl get replicationcontroller`
    
- **Command to get a list of all replica sets:**
    
    `kubectl get replicaset`
    
- **Command to execute an existing replica set file after changes:**
    
    `kubectl replace -f "name_of_changed_replicaset.yml"`
    
- **Command to delete a replica set with all its underlying pods:**
    
    `kubectl delete replicaset "name_of_replicaset"`
    
- **Command to scale replicas to 6 if they were 3 initially:**
    
    `kubectl scale --replicas=6 -f replicaset-definition.yml`
    
    or
    
    `kubectl scale replicaset myapp-replicaset --replicas=6`
    
- **Command to edit a replica set file in terminal:**
    
    `kubectl edit replicaset myapp-replicaset`
    
- **Command to get the list of deployments:**
    
    `kubectl get deployments`
    
- **Command to get deployment, replica set, and pods list at once (get all objects in the cluster):**
    
    `kubectl get all`
    
- **Command to see information about a rollout:**
    
    `kubectl rollout status deployment/mydeployment`
    
- **Command to see the history of revisions in rollout:**
    
    `kubectl rollout history deployment/mydeployment`
    
- **Command to undo rolling updates (roll back current changes):**
    
    `kubectl rollout undo deployment/mydeployment`
    
- **Command to record the cause of change in a rollout:**
    
    `kubectl create -f deployment.yaml --record`
    
- **Command to change an image in a deployment:**
    
    `kubectl set image deployment myapp-deployment nginx=nginx:1.18 --record`
    
- **Command to get the IP of a service in Minikube:**
    
    `minikube service myapp-service --url`
    
- **Command to make a service from the terminal:**
    
    `kubectl expose deployment simple-webapp-deployment --name=webapp-service --targetPort=8080 --type=NodePort --port=8080 --nodePort=30080 --dry-run=client -o yaml > svc.yaml`
    
- **Command to get information regarding clusters:**
    
    `kubectl cluster-info`
    
- **Command to get a list of nodes in a cluster:**
    
    `kubectl get nodes`
    
- **Command to create a deployment from terminal:**
    
    `kubectl create deployment httpd-frontend --image=httpd:2.4-alpine`
    
    or
    
    `kubectl create deployment --image=redis redis`
    
- **Command to see pods in a specific namespace:**
    
    `kubectl get pods --namespace="name_of_any_namespace"`
    
    or
    
    `kubectl -n "name_of_namespace" get pods`
    
    or
    
    `kubectl -n "name_of_namespace" get pods --no-headers`
    
- **Command to create a pod in a specific namespace:**
    
    `kubectl create -f "pod_definition_file.yaml" --namespace="name_of_namespace"`
    
- **Command to create a namespace:**
    
    `kubectl create namespace "name_of_namespace"`
    
- **Command to set the current default namespace to some other namespace:**
    
    `kubectl config set-context $(kubectl config current-context) --namespace="name_of_the_namespace"`
    
- **Command to see pods in all namespaces:**
    
    `kubectl get pods --all-namespaces`
    
- **Command to get a list of namespaces:**
    
    `kubectl get namespaces`
    
    or
    
    `kubectl get ns`
    
- **Command to access a specific service in another namespace:**
    
    `db-service.dev.svc.cluster.local`
    
- **Command to get the number of pods in all namespaces without headers:**
    
    `kubectl get ns --no-headers | wc -l`
    
- **Command to get a specific pod in any namespace:**
    
    `kubectl get pods --all-namespaces | grep blue`
    
- **Command to get services in a specific namespace:**
    
    `kubectl -n "name_of_namespace" get svc`
    
- **Command to create a Service named `redis-service` of type ClusterIP to expose pod redis on port 6379:**
    
    `kubectl expose pod redis --port=6379 --name=redis-service --dry-run=client -o yaml`
    
    or
    
    `kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml`
    
- **Command to create a Service named `nginx` of type NodePort to expose pod `nginx`'s port 80 on port 30080:**
    
    `kubectl expose pod nginx --port=80 --name=nginx-service --type=NodePort --dry-run=client -o yaml`
    
    or
    
    `kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml`
    
- **Command to create a pod using image and labels in the terminal:**
    
    `kubectl run redis --image=redis-alpine --labels="tier=db"`
    
- **Command to create a configmap using an imperative way:**
    
    `kubectl create configmap "name_of_configmap" --from-literal=key=value`
    
- **Command to create a configmap for multiple key-value pairs:**
    
    `kubectl create configmap "name_of_configmap" --from-literal=key=value --from-literal=key=value --from-literal=key=value`
    
- **Command to create configmap from a file using an imperative way:**
    
    `kubectl create configmap "name_of_configmap" --from-file=app_config.properties`
    
- **Command to get the list of configmaps:**
    
    `kubectl get configmaps`
    
- **Command to get extra information regarding configmaps:**
    
    `kubectl describe configmap "name_of_configmap"`
    
- **Command to create a secret in an imperative way:**
    
    `kubectl create secret generic "secret_name" --from-literal=key=value`
    
- **Command to create a secret from a file in an imperative way:**
    
    `kubectl create secret generic app_secret --from-file=app_secret.properties`
    
- **Command to get a list of secrets:**
    
    `kubectl get secrets`
    
- **Command to see additional information about secrets:**
    
    `kubectl describe secret "name_of_secret"`
    

### Commands and Arguments in Docker and Kubernetes & Port Forwarding & Editing Resource

### Docker: `CMD` and `ENTRYPOINT`

In Docker, `CMD` and `ENTRYPOINT` are used to define the behavior of a container when it starts.

- **`CMD`**: Specifies default commands and arguments that can be overridden by passing arguments in the `docker run` command.
    - Example:
        
        ```yaml
        CMD ["echo", "Hello World"]
        ```
        
    - When running this Docker container, it will print "Hello World" by default. However, if you pass other arguments (e.g., `docker run myimage echo "Hi"`), the command will be overridden.
- **`ENTRYPOINT`**: Defines the executable that will run when the container starts and **cannot** be overridden by passing arguments.
    - Example:When running the container, the command will always use `echo`. You can only pass arguments to the `echo` command (e.g., `docker run myimage "Hello"`).
        
        ```yaml
        ENTRYPOINT ["echo"]
        ```
        
- **Combining `ENTRYPOINT` and `CMD`**:
    - The `ENTRYPOINT` defines the executable, while the `CMD` defines default arguments.
    - Example:
        
        ```yaml
        ENTRYPOINT ["echo"]
        CMD ["Hello World"]
        ```
        
        - This will print "Hello World" by default, but you can override the argument (e.g., `docker run myimage "Hi"` will print "Hi").

### Kubernetes: `command` and `args`

In Kubernetes, `command` and `args` are used similarly to `ENTRYPOINT` and `CMD` in Docker.

- **`command`**: Specifies the command to run inside the container, similar to Docker’s `ENTRYPOINT`.
    - Example:
        
        ```yaml
        spec:
          containers:
            - name: my-container
              image: busybox
              command: ["sleep"]
        ```
        
- **`args`**: Specifies the arguments to pass to the `command`, similar to Docker’s `CMD`.
    - Example:In this example, the container will run the `sleep` command with the argument `3600` (i.e., sleep for 3600 seconds).
        
        ```yaml
        spec:
          containers:
            - name: my-container
              image: busybox
              command: ["sleep"]
              args: ["3600"]
        ```
        

---

### Port Forwarding in Kubernetes

Port forwarding allows you to access a Kubernetes service from your local machine by forwarding traffic from a local port to a port in the cluster.

- **Command for Port Forwarding**:
    
    ```bash
    kubectl port-forward pod/<pod-name> <local-port>:<container-port>
    ```
    
    Example:
    
    ```bash
    kubectl port-forward pod/my-pod 8080:80
    ```
    
    This will forward traffic from local port `8080` to the container's port `80` on the specified pod.
    
- **Port Forwarding for a Service**:
    
    ```bash
    kubectl port-forward service/<service-name> <local-port>:<service-port>
    ```
    
    Example:
    
    ```bash
    kubectl port-forward service/my-service 8080:80
    ```
    
    This forwards traffic from local port `8080` to port `80` of the service.
    

---

### Editing Resource Arguments and Using `replace --force`

When you edit the arguments or configurations of a container resource in Kubernetes, it creates a temporary file where the changes are saved. You can then apply these changes using the `replace --force` command.

### Steps:

1. **Edit the resource**:
Use `kubectl edit` to modify the resource.
    
    ```bash
    kubectl edit deployment my-deployment
    ```
    
    This opens the YAML configuration file where you can modify settings like container arguments, images, replicas, etc.
    
2. **Create a Temporary File**:
Kubernetes creates a temporary file with your changes.
3. **Apply Changes with `replace --force`**:
After editing, you may need to forcefully replace the resource with the new configuration using:
    
    ```bash
    kubectl replace --force -f <path-to-temporary-file>
    ```
    
    This forcefully replaces the existing resource with the new configuration defined in the YAML file. The `--force` flag is useful when you need to recreate resources without waiting for normal Kubernetes garbage collection.
    

### Environment Variables

Environment variables are dynamic values that can affect the behavior of processes on an operating system. They're often used to configure settings for software applications without hardcoding values. In Linux, for example, you can set, view, or modify environment variables using commands like `export`, `printenv`, or `env`.

- **Setting an environment variable in Linux:**
    
    `export MY_VAR="HelloWorld"`
    
- **Viewing an environment variable:**
    
    `echo $MY_VAR`
    

### Environment Variables in Kubernetes

In Kubernetes, environment variables can be passed to containers, allowing you to configure settings dynamically. This is useful for passing credentials, configuration options, or other information without embedding it directly in the application code.

### Example of specifying environment variables in a Kubernetes Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: env-demo
spec:
  containers:
  - name: demo-container
    image: busybox
    command: ['sh', '-c', 'echo The secret value is $SECRET_ENV; sleep 3600']
    env:
    - name: SECRET_ENV  # Name of the environment variable
      value: "my_secret_value"  # The value passed to the container
```

- The `env` field specifies the environment variables.
- `SECRET_ENV` will be available inside the container.

### Commands to view and modify environment variables in Kubernetes:

- **To view the environment variables of a Pod:**
    
    `kubectl exec env-demo -- printenv`
    
- **To apply the configuration:**
    
    `kubectl apply -f env-demo.yaml`
    

This will create a pod where the container will print the environment variable and hold it for an hour (`sleep 3600`).

### Modifying Environment Variables in Kubernetes

You can edit environment variables of a running pod using commands, but you'll usually recreate or replace the deployment if a permanent change is needed.

### ConfigMaps in Kubernetes

**ConfigMaps** are used to store non-confidential data in key-value pairs. They help in separating configuration details from the application code and make applications more portable across environments.

### 1. **Creating ConfigMaps**

There are two main ways to create ConfigMaps: *Imperative* and *Declarative*.

---

### **Imperative Way**

You can create ConfigMaps directly from the command line using the `kubectl` command.

- **Creating from literal values:**
    
    ```bash
    kubectl create configmap my-config --from-literal=key1=value1 --from-literal=key2=value2
    ```
    
    - This will create a ConfigMap named `my-config` with two key-value pairs: `key1=value1` and `key2=value2`.
- **Creating from a file:**
    
    ```bash
    kubectl create configmap my-config --from-file=path/to/config/file
    ```
    
    - This takes the contents of a file and stores it in the ConfigMap.

---

### **Declarative Way**

You can also define a ConfigMap in a YAML file.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  key1: value1
  key2: value2
```

- To create the ConfigMap using this YAML file, run:
    
    ```bash
    kubectl apply -f my-config.yaml
    ```
    

---

### 2. **Using ConfigMaps in Pods**

You can inject ConfigMaps into Pods as environment variables or mounted files.

- **Injecting as environment variables:**
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: my-pod
    spec:
      containers:
      - name: my-container
        image: busybox
        envFrom:
        - configMapRef:
            name: my-config
    ```
    
- **Mounting ConfigMaps as files:**
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: my-pod
    spec:
      containers:
      - name: my-container
        image: busybox
        volumeMounts:
        - name: config-volume
          mountPath: /etc/config
      volumes:
      - name: config-volume
        configMap:
          name: my-config
    ```
    

---

### 3. **Viewing ConfigMaps**

- **To list all ConfigMaps:**`kubectl get configmaps`
- **To view details of a specific ConfigMap:**`kubectl describe configmap my-config`
- **To view the data of a ConfigMap:**`kubectl get configmap my-config -o yaml`

---

### Example: **`kodekloud/webapp-color`**

Let's assume we are using the `kodekloud/webapp-color` app that reads color data from a ConfigMap.

1. **Create the ConfigMap:**

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: webapp-config
data:
  APP_COLOR: blue
```

1. **Use the ConfigMap in the Deployment:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: kodekloud/webapp-color
        env:
        - name: APP_COLOR
          valueFrom:
            configMapKeyRef:
              name: webapp-config
              key: APP_COLOR
```

This deployment will use the `APP_COLOR` value from the `webapp-config` ConfigMap, which sets the webapp color to blue.

### Kubernetes Secrets

**What are Secrets?**

Secrets in Kubernetes are used to store and manage sensitive information such as passwords, tokens, and keys. Unlike ConfigMaps, Secrets are base64-encoded by default but not encrypted.

---

### Example of Creating Secrets

1. **Imperative Command**You can create a secret using the `kubectl` command:

`kubectl create secret generic my-secret --from-literal=username=myUser --from-literal=password=myPass`

This command creates a secret named `my-secret` with two key-value pairs, `username` and `password`.

1. **Declarative Method**You can define a secret in a YAML file:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  username: bXlVc2Vy  # This is base64 encoded value of 'myUser'
  password: bXlQYXNz  # This is base64 encoded value of 'myPass'
```

**Explanation:**

- `apiVersion: v1`: Specifies the API version.
- `kind: Secret`: Declares that the resource is a secret.
- `metadata`: Contains the name of the secret.
- `data`: Contains base64-encoded data (username and password).

---

### **Using Secrets in Pods**

Secrets can be injected into Pods as **environment variables** or mounted as **files**.

### **1. Injecting Secrets as Environment Variables**

You can inject specific keys from a secret into environment variables.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: busybox
    env:
    - name: USERNAME
      valueFrom:
        secretKeyRef:
          name: my-secret       # Reference the secret by name
          key: username         # Specify which key from the secret to inject
    - name: PASSWORD
      valueFrom:
        secretKeyRef:
          name: my-secret       # Reference the same secret
          key: password         # Inject the 'password' key
```

- **env**: Defines environment variables inside the container.
- **secretKeyRef**: References a specific key from the `my-secret` Secret.

---

### **2. Mounting Secrets as Files**

Instead of injecting Secrets as environment variables, you can mount them as files.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: busybox
    volumeMounts:
    - name: secret-volume       # Define the volume where the secret will be mounted
      mountPath: "/etc/secret"  # Mount path inside the container
  volumes:
  - name: secret-volume
    secret:
      secretName: my-secret     # Reference the secret by name
```

- **volumeMounts**: Specifies where in the container the secret will be available as files.
- **volumes.secret**: Links the volume to a secret (`my-secret`).

This example mounts the secret as files inside the container at `/etc/secret`.

---

### **Viewing Secrets**

1. **List all Secrets**: `kubectl get secrets`
2. **View details of a Secret**: `kubectl describe secret my-secret`
3. **View base64 encoded data**: `kubectl get secret my-secret -o yaml`
4. **Decode base64 encoded value**:
    
    ```bash
    echo 'bXlVc2Vy' | base64 --decode   # Decodes the base64 value to plain text
    ```
    

---

### **Example: kodekloud/webapp-color with Secrets**

Let's assume the `kodekloud/webapp-color` app needs a sensitive `APP_PASSWORD`. We’ll store it as a secret and inject it into the container.

1. **Create the Secret**:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: webapp-secret
type: Opaque
data:
  APP_PASSWORD: bXlTZWN1cmVQYXNz   # base64 encoded 'mySecurePass'
```

- **data**: Contains the sensitive data (`APP_PASSWORD`), encoded using base64.
1. **Use the Secret in a Deployment**:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: kodekloud/webapp-color
        env:
        - name: APP_PASSWORD
          valueFrom:
            secretKeyRef:
              name: webapp-secret    # Reference the 'webapp-secret' secret
              key: APP_PASSWORD      # Inject the 'APP_PASSWORD' key from the secret
```

- **env**: Injects the `APP_PASSWORD` secret into the container’s environment.

This setup passes the sensitive password from the secret to the `kodekloud/webapp-color` container.

---

### Using Secrets in Pods

To use the secret in a pod:

```yaml
yapiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx
    envFrom:
      secretRef:
        name: my-secret  # Referencing the secret created earlier
```

**Explanation:**

- `envFrom`: This is used to load the entire secret as environment variables in the container.
- `secretRef`: References the secret by name (`my-secret`).

---

### Points to Consider

1. **Secrets are Encoded, Not Encrypted**
    
    Base64 encoding is just a way to represent binary data as text, which can be easily decoded. This means **secrets are not secure by default** unless extra measures (like encryption) are taken.
    
2. **Don’t Push Secrets to Public Repositories**
    
    Keep secret manifests out of version control to prevent accidental exposure.
    
3. **Secrets are not Encrypted at ETCD**
    
    Kubernetes stores secrets in the ETCD database, which is not encrypted by default. You need to enable encryption at rest for sensitive data.
    
4. **Enable Encryption at Rest**
    
    You should configure encryption at rest for ETCD to protect secrets and other sensitive information.
    
5. **Namespace Access and Secrets**
    
    Anyone who can create pods in a namespace can potentially access secrets within that namespace. It's essential to limit access using RBAC.
    
6. **Configure Least Privilege Access**
    
    Follow the principle of least privilege for granting access to secrets, ensuring that only the necessary workloads and users have access.
    
7. **Third-Party Secret Providers**
    
    Consider using external secret management systems like:
    
    - **HashiCorp Vault**
    - **AWS Secrets Manager**
    - **Google Cloud Secrets Manager**

These services can provide more robust security and encryption for managing sensitive information.

---

### Viewing Secrets

To view a secret in base64 format:
`kubectl get secret my-secret -o yaml`

To decode a specific secret:
`echo 'bXlVc2Vy' | base64 --decode`

This will decode the base64 encoded value and display the original content.

### Kubernetes Security

Security in Kubernetes is critical for protecting workloads, data, and infrastructure. Let’s go through various security mechanisms focusing on:

1. **Pod and Container Level Security**
2. **Capabilities and Users**
3. **Sidecar Containers and Security Implications**

---

### Pod and Container Level Security

Kubernetes provides security at both the **Pod** and **Container** levels using security contexts. These contexts help control permissions, users, and capabilities.

### Example: Security Context for a Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secure-pod
spec:
  securityContext:         # Applies security at the Pod level
    runAsUser: 1000        # Forces all containers to run as user with UID 1000
    fsGroup: 2000          # Ensures that mounted volumes are owned by the group ID 2000
  containers:
  - name: secure-container
    image: busybox
    securityContext:       # Security settings specific to the container
      runAsUser: 3000      # Overrides Pod-level user and runs this container as user UID 3000
      capabilities:
        drop:
        - ALL              # Drops all Linux capabilities for this container
        add:
        - NET_ADMIN        # Only adds the NET_ADMIN capability for network admin tasks
    command: ["sleep", "3600"]
```

**Explanation:**

- **Pod-Level Security Context**:
    - `runAsUser: 1000`: Ensures all containers run as this user unless overridden by a container-specific security context.
    - `fsGroup: 2000`: Any volumes mounted by the Pod will have their group ownership set to this group.
- **Container-Level Security Context**:
    - `runAsUser: 3000`: Overrides the Pod-level `runAsUser` and runs this container with UID 3000.
    - **Capabilities**: Linux capabilities control permissions. The container drops all default capabilities but adds `NET_ADMIN` for network-related tasks.

---

### Capabilities and Users

**Capabilities** allow containers to run with limited privileges rather than full root access, and you can selectively grant them.

- **Drop All Capabilities**: Good practice to remove unnecessary privileges.
- **Add Specific Capabilities**: Grant only the minimum required privileges, such as `NET_ADMIN` or `SYS_TIME`.

**Users**:

- **Pod-Level Users**: Setting `runAsUser` at the Pod level applies to all containers unless overridden at the container level.
- **Container-Level Users**: If `runAsUser` is defined for both Pod and container, the container value takes precedence.

**What happens if users are defined for both Pod and container?**

- The container-level `runAsUser` setting will override the Pod-level one.

---

### Sidecar Containers and Security Implications

When a Pod has multiple containers, such as a main container and a sidecar, security settings can apply differently.

**Example: Pod with a Sidecar Container**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-with-sidecar
spec:
  containers:
  - name: main-container
    image: nginx
    securityContext:
      runAsUser: 1000           # Runs the main container as user 1000
  - name: sidecar-container
    image: busybox
    securityContext:
      runAsUser: 2000           # Sidecar runs as a different user (2000)
      capabilities:
        add:
        - SYS_TIME              # Sidecar has SYS_TIME capability for time-related operations
```

**Security Considerations**:

- **Different Users for Containers**: The main container runs as UID 1000, and the sidecar runs as UID 2000. Each container can have different privileges.
- **Capabilities**: Only the sidecar has the `SYS_TIME` capability, meaning it can modify the system clock while the main container cannot.
- **Pod-Level vs. Container-Level Security**: If there’s a conflict (e.g., `runAsUser` defined for both Pod and container), the container-level setting takes precedence.

---

### Security Best Practices

1. **Drop Unnecessary Capabilities**: Minimize attack surface by removing all capabilities and only adding what’s required.
2. **Run as Non-Root**: Always configure containers to run as non-root users using `runAsUser`.
3. **Apply Network Policies**: Use Kubernetes Network Policies to limit network traffic between pods.
4. **Use Pod Security Admission Controllers**:
    - **PodSecurityPolicy** (deprecated in newer versions) or use **Pod Security Admission** to enforce security constraints like non-root user enforcement.

---

### Key Security Points

- **Security Context**: Defines security settings at the Pod and container levels.
- **Capabilities**: Control the privileges granted to containers, and limiting them is crucial for reducing attack surfaces.
- **Pod-Level vs. Container-Level Security**: Container-level settings override Pod-level ones.
- **Sidecar Containers**: Sidecars can have different privileges and users, so ensure that they are properly secured.

### Common Questions

1. **What happens if security context is specified at both Pod and container levels?**
    - The container-level security context overrides the Pod-level one for that container.
2. **What if there is a sidecar container?**
    - Each container in a Pod can have its own security context. If not specified, the Pod-level context applies to all containers.
3. **How to manage container capabilities?**
    - Always remove unnecessary capabilities (e.g., drop `ALL`) and only add those needed (e.g., `NET_ADMIN` for network).

---

### Example of Using `kubectl` for Security Operations

- **Apply a Pod Security Context**:
    
    `kubectl apply -f secure-pod.yaml`
    
- **Describe a Pod’s Security Context**:
    
    `kubectl describe pod secure-pod`
    
- **Check Capabilities**:
    
    `kubectl get pod secure-pod -o yaml | grep capabilities`
    

### Kubernetes Service Accounts

**Service Accounts** in Kubernetes are used to provide identities for processes that run in Pods. They allow Pods to interact with the Kubernetes API, manage permissions, and control what resources the Pods can access.

By default, every namespace in Kubernetes comes with a **default service account**, but custom service accounts can be created for specific Pods to enhance security and assign different permissions.

---

### Key Concepts

- **Service Account**: An identity that provides Pods with permissions to interact with the Kubernetes API.
- **RBAC (Role-Based Access Control)**: Determines what a service account can do. You assign roles and permissions to service accounts through RBAC.
- **Default Service Account**: If no custom service account is specified, Pods use the default service account of the namespace.

---

### Creating a Service Account

1. **Imperative Command**
    
    You can create a service account using the following command:
    
    `kubectl create serviceaccount custom-sa`
    
2. **Declarative Method**
    
    You can define a service account in a YAML file:
    
    ```yaml
    apiVersion: v1
    kind: ServiceAccount
    metadata:
      name: custom-sa
    ```
    

**Explanation**:

- `apiVersion: v1`: Specifies the API version.
- `kind: ServiceAccount`: Declares that this resource is a service account.
- `metadata`: Contains the name of the service account (`custom-sa`).

---

### Using a Service Account in a Pod

To assign a custom service account to a Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-using-sa
spec:
  serviceAccountName: custom-sa  # Assigning the custom service account to this Pod
  containers:
  - name: my-container
    image: nginx
```

**Explanation**:

- `serviceAccountName`: Specifies the service account that this Pod will use. The Pod will interact with the Kubernetes API using the permissions granted to `custom-sa`.

---

### Assigning Permissions to Service Accounts

Service accounts themselves do not have permissions by default. You need to assign roles and permissions using **RBAC** (Role-Based Access Control).

### Example: Assigning a Role to a Service Account

First, create a **Role**:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: read-pods
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

**Explanation**:

- `kind: Role`: Creates a role that is specific to a namespace (`default`).
- `resources: ["pods"]`: Grants permissions for Pods.
- `verbs: ["get", "watch", "list"]`: Allows this role to read Pods.

Next, bind the role to the service account using a **RoleBinding**:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods-binding
  namespace: default
subjects:
- kind: ServiceAccount
  name: custom-sa  # Binding this role to the 'custom-sa' service account
roleRef:
  kind: Role
  name: read-pods  # Refers to the 'read-pods' role created earlier
  apiGroup: rbac.authorization.k8s.io
```

**Explanation**:

- `kind: RoleBinding`: Links a role to a user or service account.
- `subjects`: Specifies that this role applies to the `custom-sa` service account.
- `roleRef`: Refers to the role `read-pods` that gives permissions to read Pods.

---

### Viewing Service Accounts

- **List all service accounts**:
    
    `kubectl get serviceaccounts`
    
- **View details of a specific service account**:
    
    `kubectl describe serviceaccount custom-sa`
    

---

### Key Security Points

1. **Use Custom Service Accounts for Different Workloads**
    
    Each workload should have its own service account to ensure that permissions are least privileged. Avoid using the default service account if possible.
    
2. **RBAC (Role-Based Access Control)**
    
    Always assign the minimum required permissions using RBAC to ensure Pods cannot access more than they need.
    
3. **Default Token Injection**
    
    By default, Kubernetes injects a token in the Pod so that it can interact with the Kubernetes API. If the Pod does not need to communicate with the API, you can disable this feature by setting `automountServiceAccountToken: false`.
    
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: pod-without-token
    spec:
      automountServiceAccountToken: false  # Disables API token injection
      containers:
      - name: my-container
        image: nginx
    ```
    
    **Explanation**:
    
    - `automountServiceAccountToken: false`: Prevents Kubernetes from mounting the API token in the Pod.
4. **Use Least Privilege**
    
    Grant the service account only the permissions it needs. Always follow the principle of least privilege.
    
5. **Namespace-Specific Permissions**
    
    RBAC roles can be defined at the namespace level to limit access within specific namespaces.
    

---

### Common Questions

1. **What happens if no service account is specified in the Pod?**
    - The Pod uses the default service account for that namespace, which usually has limited or no permissions.
2. **Can a service account be used across namespaces?**
    - No, service accounts are scoped to a namespace. You would need to create and assign separate service accounts in each namespace.
3. **What if I don’t want the Pod to communicate with the Kubernetes API?**
    - Set `automountServiceAccountToken: false` in the Pod specification to prevent the API token from being injected into the Pod.

---

### Example: Using a Service Account in a kodekloud/webapp-color Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      serviceAccountName: custom-sa  # Assigning a custom service account to this deployment
      containers:
      - name: webapp
        image: kodekloud/webapp-color
```

In this example, the `custom-sa` service account is assigned to the `kodekloud/webapp-color` container. This ensures that the container runs with the permissions assigned to the `custom-sa` service account.

---

### Difference Between User Accounts and Service Accounts

- **User Accounts**:
    - Typically represent human users.
    - Managed outside of Kubernetes, using external identity providers (e.g., LDAP, SSO).
    - Users are generally given access to the Kubernetes cluster via **kubectl**.
    - **RBAC** is used to define what actions users can perform on the cluster.
- **Service Accounts**:
    - Represent machine identities (used by applications running inside Pods).
    - Managed within Kubernetes itself.
    - Pods use service accounts to authenticate and interact with the Kubernetes API.
    - Each namespace has a default service account, but custom ones can be created for specific use cases.

---

### Tokens

- **Tokens** are used by both user and service accounts to authenticate with the Kubernetes API.
- **Service Account Tokens** are long-lived and mounted into Pods automatically unless specified otherwise.

---

### Default Service Account and Token Mounting

- By default, Kubernetes creates a **default service account** in each namespace. If you don’t explicitly specify a service account in your Pod spec, the default one is used.
- When a Pod uses a service account, Kubernetes **automatically mounts a token** for that service account into the Pod’s filesystem. This token allows the Pod to interact with the Kubernetes API.

### Disabling Token Mounts

You can prevent this behavior by setting `automountServiceAccountToken: false` in your Pod spec:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-without-token
spec:
  automountServiceAccountToken: false  # Prevents Kubernetes from mounting the service account token
  containers:
  - name: my-container
    image: nginx
```

---

### Decoding the Token

Tokens are **JWT (JSON Web Tokens)**. You can decode a token to see its claims (e.g., issuer, expiration, subject). You can decode the base64-encoded token using:

`echo '<token-string>' | base64 --decode`

There are also online tools for decoding JWT tokens:

- [jwt.io](https://jwt.io/)
- [Token Decoder](https://token.dev/)

---

### History and Kubernetes Enhancement Proposals (KEPs)

### **KEP 1205: Service Account Token Volume Projection**

- **Introduced in Kubernetes v1.22**.
- This enhancement improved the security of service account tokens by introducing **short-lived tokens** instead of the previous long-lived tokens that could be vulnerable if compromised.
- The tokens are automatically rotated and expire after a configurable amount of time.
- The **TokenRequest API** was introduced as part of this enhancement, enabling Pods to request tokens directly from the Kubernetes API server.

Reference: [KEP 1205](https://github.com/kubernetes/enhancements/issues/1205)

### **KEP 2799: Bound Service Account Token Volumes**

- This proposal built on KEP 1205, enforcing the use of the **TokenRequest API** for getting tokens.
- Bound tokens are mounted into Pods and are scoped to the Pod, meaning they can only be used from within that specific Pod.
- Tokens can also have **audiences**, which restrict where they can be used (e.g., for accessing a specific API server or service).

Reference: [KEP 2799](https://github.com/kubernetes/enhancements/issues/2799)

---

### TokenRequest API

The **TokenRequest API** is a Kubernetes API used by Pods to request short-lived tokens. The API server automatically rotates these tokens. Pods use them to interact with the API securely, reducing the security risks associated with long-lived tokens.

Example of manually requesting a token using the TokenRequest API:

```bash
kubectl create token <service-account-name> --duration=1h
```

**Explanation**:

- `kubectl create token <service-account-name>`: Requests a token for the specified service account.
- `-duration=1h`: Specifies that the token should be valid for 1 hour.

---

### Summary of Key Points

- **User Accounts vs. Service Accounts**: Human users versus machine identities used by Pods.
- **Service Account Tokens**: Mounted into Pods for API access by default.
- **TokenRequest API**: Introduced to enhance security with short-lived, auto-rotating tokens.
- **KEP 1205**: Introduced in Kubernetes v1.22, enabling short-lived tokens via the TokenRequest API.
- **KEP 2799**: Builds on KEP 1205, enforcing the use of bound tokens.

For additional details, you can refer to the KEP documentation:

- [KEP 1205](https://github.com/kubernetes/enhancements/issues/1205)
- [KEP 2799](https://github.com/kubernetes/enhancements/issues/2799)

**JWT Token Decoders**:

- [jwt.io](https://jwt.io/)
- [Token Decoder](https://token.dev/)

### **Resource Requirements**

Kubernetes allows you to define resource requests and limits for your pods.

- **Resource Requests**: These specify the minimum amount of resources (CPU, memory) a container needs. The scheduler uses this information to place the pod on a node with enough resources.
- **Resource Limits**: These are the maximum amounts of CPU and memory a container can use. If a container exceeds the limit, Kubernetes throttles (CPU) or terminates (memory) the container.

### 2. **Scheduler and Scheduling Logic**

The Kubernetes scheduler assigns pods to nodes based on:

- **Node resources**: Ensures the node has enough CPU and memory.
- **Node selector/affinity**: Assign pods based on labels or affinity rules.
- **Taints and tolerations**: Prevent or allow pods to run on certain nodes.
- **Resource requests and limits**: The scheduler uses the **requests** to find nodes that can accommodate the pod.

### 3. **Can Resources Be Shared Across Nodes?**

No, Kubernetes does not share resources like memory from one node and disk from another. Each pod runs on a single node, and it uses the resources (CPU, memory, disk) available on that node only.

### 4. **Resource Requests and Limits**

- **CPU**:
    - Requests are specified in **millicores** (1 core = 1000m).
    - You can request values like `0.5`, `100m`, or `1` (which means 1 core).
- **Memory**:
    - Memory is specified in **bytes**, with units like `Mi` (mebibytes) or `Gi` (gibibytes).
    - For example: `128Mi`, `2Gi`.
- **Format Example**:
    
    ```yaml
    resources:
      requests:
        memory: "128Mi"
        cpu: "500m"
      limits:
        memory: "256Mi"
        cpu: "1"
    ```
    

### 5. **What Happens If a Pod Exceeds Limits?**

- **CPU**: The container is throttled (limited in its CPU use).
- **Memory**: If a container exceeds its memory limit, it is killed by the Kubernetes Out of Memory (OOM) killer and restarted.

### 6. **Defaults and Minimum Values**

- **CPU**: The minimum request is `1m` (1 millicore = 0.001 core).
- **Memory**: You can request as little as `1Mi` (1 mebibyte).

### 7. **Units**

- **CPU**:
    - `1m` = 1 millicore (1/1000th of a CPU core).
    - `1` = 1 CPU core.
- **Memory**:
    - `M` = megabytes, `Mi` = mebibytes (binary system).
    - `G` = gigabytes, `Gi` = gibibytes (binary system).

### Node Selectors, Labels, Taints, Tolerations, Node Affinity, and Annotations

These are key Kubernetes concepts used to influence **where** and **how** pods are scheduled onto nodes. Each serves a different purpose:

---

### 1. **Node Selectors**

- **Purpose**: Allows you to specify that a pod should only run on nodes with certain labels.
- **How It Works**: When you define a `nodeSelector`, the scheduler only considers nodes that have the specified label(s).
- **Example**:
    
    ```yaml
    spec:
      nodeSelector:
        disktype: ssd
    ```
    
    This pod will only be scheduled on nodes with the label `disktype=ssd`.
    
- **Limitations**:
    - **Exact matching only**: You can't use expressions (greater than, less than, etc.) with `nodeSelector`.

---

### 2. **Node Affinity**

- **Purpose**: Provides a more expressive way to control pod placement than `nodeSelector`. It allows for **rules** and **preferences**.
- **Types**:
    - **Hard Node Affinity**: Similar to `nodeSelector`, it requires the node to have certain labels.
    - **Soft Node Affinity**: A preferred rule, which the scheduler tries to satisfy but will still place the pod elsewhere if necessary.
- **Example**:
    
    ```yaml
    affinity:
      nodeAffinity:
        requiredDuringSchedulingIgnoredDuringExecution:
          nodeSelectorTerms:
          - matchExpressions:
            - key: disktype
              operator: In
              values:
              - ssd
        preferredDuringSchedulingIgnoredDuringExecution:
        - weight: 1
          preference:
            matchExpressions:
            - key: region
              operator: In
              values:
              - us-west-1
    ```
    
    This pod **requires** a node with `disktype=ssd` and **prefers** nodes in `region=us-west-1`.
    
- **Limitations**:
    - **Hard Node Affinity** is mandatory. If no suitable node is found, the pod will remain unscheduled.
    - if not used with Taints and toleration then other pods can also be deployed on the same node as this one

---

### 3. **Taints and Tolerations**

- **Purpose**: Used to **prevent** pods from being scheduled on certain nodes unless the pod can **tolerate** the taint.
- **Taints**: Applied to a node to **repel** pods that don’t tolerate the taint.
- **Tolerations**: Defined on pods to allow them to **tolerate** certain taints and thus be scheduled on nodes with those taints.
- **Example (Taint)**:
    
    ```bash
    kubectl taint nodes node1 key=value:NoSchedule
    ```
    
    This command adds a taint to `node1` that **prevents scheduling** unless the pod tolerates the taint.
    
- **Example (Toleration)**:
    
    ```yaml
    spec:
      tolerations:
      - key: "key"
        operator: "Equal"
        value: "value"
        effect: "NoSchedule"
    ```
    
    This pod will tolerate the taint `key=value:NoSchedule` and can be scheduled on the tainted node.
    
- **Limitations**:
    - **Taints are node-specific**: Pods without tolerations won’t be scheduled on tainted nodes, regardless of their resource requirements.
    - it only prevents the pods that does not have a toleration, so even if a pod has a toleration that pod can still be deployed by the Schedular on a different node rather then the one we tainted

---

### 4. **Labels**

- **Purpose**: Used for organizing and selecting Kubernetes objects like nodes and pods.
- **How It Works**: Labels are key-value pairs attached to objects (e.g., nodes or pods) that can be used for filtering and grouping objects.
- **Example**:
    
    ```bash
    kubectl label nodes node1 disktype=ssd
    ```
    
- **Use Cases**:
    - Can be used with `nodeSelector`, `affinity`, and service selectors.

---

### 5. **Annotations**

- **Purpose**: Annotations provide **non-identifying metadata** to objects, which can be used by tools and libraries but not directly by Kubernetes for scheduling or selection.
- **How It Works**: Annotations store arbitrary data and are typically used for metadata that isn't required for identification but might be needed by external systems.
- **Example**:
    
    ```yaml
     metadata:
      annotations:
        owner: "team-a"
        cost-center: "1234"
    ```
    
- **Limitations**:
    - **No direct use in scheduling**: Unlike labels or node affinity, annotations don't influence the scheduling of pods.

---

### 6. **Differences and Usage Scenarios**

| Concept | Used For | Scheduling Effect | Scope |
| --- | --- | --- | --- |
| **Node Selector** | Basic node selection | Exact matching of labels | Simple label-based scheduling |
| **Node Affinity** | Advanced node selection | Hard or soft rules | More flexible than selectors |
| **Taints** | Preventing pod scheduling | Nodes repel pods | Restrictive, used with tolerations |
| **Tolerations** | Allow scheduling on tainted nodes | Tolerating taints | Pod-level definition |
| **Labels** | Identifying and grouping objects | Filtering nodes/pods | Flexible, used with selectors, services |
| **Annotations** | Non-scheduling metadata | No direct effect | External system or tooling usage |

---

### 7. **Important Points to Clear**

- **NodeSelector** is a basic filter with exact matching, but for more control, **Node Affinity** should be used.
- **Taints and Tolerations** work together to repel or tolerate scheduling on certain nodes.
- **Labels** are used for selection and identification, while **Annotations** are used for metadata that does not affect scheduling.
- **Node Affinity** provides flexibility with preferred scheduling rules, while **NodeSelector** requires exact matches.
- **Taints** are stronger restrictions than **Node Affinity**: taints prevent scheduling unless explicitly tolerated.

### **Kubernetes Probes**

**1. Overview**
Kubernetes **probes** are essential mechanisms that periodically check the health and status of containers within pods. They allow Kubernetes to monitor the state of a container, ensuring that applications run smoothly and take appropriate actions when issues arise.

There are two main types of probes:

- **Liveness Probes**: Checks whether the application inside a container is running (alive).
- **Readiness Probes**: Determines if the container is ready to accept traffic or connections.

---

### **2. Liveness Probe**

The **liveness probe** checks if the application within the container is still functioning. If the liveness probe fails, Kubernetes assumes the application is unhealthy and will restart the container based on the defined restart policy.

### **Key Configuration Parameters**

- **Initial Delay** (`initialDelaySeconds`): Time to wait before starting to probe after the container starts.
- **Timeout** (`timeoutSeconds`): Maximum time for the probe to complete.
- **Period** (`periodSeconds`): Frequency at which the probe runs.
- **Failure Threshold** (`failureThreshold`): Number of consecutive failed probes before Kubernetes considers the container unhealthy.

### **Liveness Probe Types**

1. **HTTP GET**: Kubernetes sends an HTTP request to the container, and if it gets a success response (2xx or 3xx), the probe is successful.
2. **TCP Socket**: Kubernetes opens a TCP connection to a specified port. If it succeeds, the container is considered live.
3. **Exec Command**: Kubernetes runs a specified command inside the container. If the command exits with code 0, the container is considered healthy.

### **Example YAML for Liveness Probe**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: liveness-demo
spec:
  containers:
  - name: myapp
    image: myapp:latest
    livenessProbe:
      httpGet:
        path: /health
        port: 8080
      initialDelaySeconds: 10
      periodSeconds: 5
```

---

### **3. Readiness Probe**

The **readiness probe** determines if the container is ready to serve requests. Even if the container is running, it may not be ready to handle traffic yet (e.g., waiting for an external dependency). Kubernetes uses readiness probes to manage whether traffic should be sent to the pod.

### **Key Configuration Parameters**

- Similar to **liveness** but controls when traffic is routed to the container.
- If the readiness probe fails, the pod is removed from the service's endpoints until it passes again.

### **Readiness Probe Types**

- Same as **liveness**: HTTP GET, TCP Socket, Exec Command.

### **Example YAML for Readiness Probe**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: readiness-demo
spec:
  containers:
  - name: myapp
    image: myapp:latest
    readinessProbe:
      httpGet:
        path: /ready
        port: 8080
      initialDelaySeconds: 5
      periodSeconds: 10
```

---

### **4. Pod Lifecycle and Probes**

Understanding **pod lifecycle** is critical when discussing probes. A pod goes through the following states:

1. **Pending**: Pod is accepted by the Kubernetes system but is not yet running.
2. **Running**: Pod has been bound to a node, and containers are created.
3. **Succeeded**: Containers in the pod have successfully completed execution.
4. **Failed**: All containers in the pod have failed.
5. **Unknown**: Kubernetes can’t determine the pod state.
- **Pod Conditions**: These are various conditions that reflect the current status of a pod, such as `PodScheduled`, `Ready`, and `Initialized`. Probes play a role in changing these conditions.

---

### **5. Before Probes: Issues They Solved**

Before Kubernetes implemented probes, there were challenges in managing application health:

- **No Mechanism for Self-Healing**: If an application inside a container crashed or was stuck, Kubernetes would not detect it and take action.
- **Manual Restarts**: Administrators had to manually restart containers when they became unhealthy.
- **Lack of Control over Traffic Routing**: Applications could start receiving traffic even when they weren't ready to handle it.

**Probes** solved these problems by:

- Allowing automatic restarts for unhealthy containers (via **liveness** probes).
- Ensuring applications receive traffic only when they are ready (via **readiness** probes).

---

### **6. Pod Status**

- **Pod status** includes overall health and readiness. Kubernetes checks conditions using the probes and updates the pod status accordingly.
- **Pod Conditions** give insights into what part of the lifecycle the pod is in, such as `Initialized`, `Ready`, and `ContainersReady`.

---

### **Key Points to Remember**

- **Liveness Probes** help ensure that a container is still running properly. If it fails, Kubernetes restarts the container.
- **Readiness Probes** help ensure that a container is ready to serve traffic. If it fails, traffic is routed elsewhere until the probe passes.
- Probes are essential in ensuring Kubernetes manages resources efficiently and keeps services healthy.

### K8s Logs

**Logs** in Kubernetes are crucial for debugging, monitoring, and understanding the behavior of your applications and system components. Logs can be generated by various components like containers, pods, the control plane, or the kubelet. Here's a deep dive into different aspects of Kubernetes logs:

### **Types of Logs**

1. **Container Logs**:
    - These logs are related to the output generated by your containers, including the application running inside the containers.
    - Kubernetes provides a way to access container logs using the `kubectl logs` command.
2. **Kubelet Logs**:
    - These logs are from the **kubelet**, the agent that runs on each node. It is responsible for managing the containers on the node.
    - Typically located on the host node, you can view them by accessing the node.
3. **Control Plane Logs**:
    - Control plane components like the **API server**, **scheduler**, and **controller manager** generate logs.
    - These are often stored in a centralized location or accessible via cloud provider logs.
4. **Cluster Component Logs**:
    - Logs from services like the **etcd** database (where Kubernetes stores cluster data) and other critical cluster-level services.

---

### **How to Access Logs**

1. **Accessing Container Logs**:
    - You can fetch logs from running pods with:
        
        ```bash
        bash
        Copy code
        kubectl logs <pod-name>
        
        ```
        
        - For logs of a specific container in a multi-container pod:
        
        ```bash
        bash
        Copy code
        kubectl logs <pod-name> -c <container-name>
        
        ```
        
    - To view previous logs from a crashed container:
        
        ```bash
        bash
        Copy code
        kubectl logs <pod-name> -p
        
        ```
        
2. **Log Aggregation Tools**:
    - Kubernetes doesn't store logs permanently on nodes. Logs are ephemeral, meaning if a pod is deleted, the logs are lost unless they are stored externally.
    - Tools like **Fluentd**, **ELK Stack (Elasticsearch, Logstash, Kibana)**, or **Prometheus** can aggregate and centralize logs for long-term storage and analysis.

---

### **Pod Status, Pod Condition, and Lifecycle Events in Relation to Logs**

1. **Pod Status**:
    - The status of the pod can help you understand if the pod is in a `Running`, `Pending`, `Failed`, or `Succeeded` state.
    - Logs can often help diagnose why a pod is stuck in `Pending` or `Failed`.
    
    Check pod status with:
    
    ```bash
    bash
    Copy code
    kubectl get pods <pod-name> -o wide
    
    ```
    
2. **Pod Conditions**:
    - These are specific conditions that reflect the current state of a pod (e.g., `Ready`, `Initialized`, etc.).
    - Use the `kubectl describe pod <pod-name>` command to get detailed condition information.
3. **Pod Lifecycle**:
    - Pods have different lifecycle phases like `Pending`, `Running`, `Succeeded`, and `Failed`.
    - Logs from the kubelet or container runtime can give insights into lifecycle transitions (e.g., why a pod might be stuck in `Pending`).

---

### **Common Logging Issues and Solutions**

1. **Log Rotation**:
    - Logs can quickly consume disk space if not managed properly. Kubernetes does not automatically rotate logs; you may need to configure log rotation in the container runtime (e.g., Docker) or use external log management solutions.
2. **CrashLoopBackOff**:
    - If a pod is constantly crashing and restarting, you’ll see `CrashLoopBackOff` in the pod status. Access logs using `kubectl logs <pod-name> -p` to diagnose the crash cause.
3. **No Logs from a Container**:
    - If you’re not seeing logs, the issue might be related to:
        - A misconfigured logging driver.
        - The container may not have started properly, and you’ll need to check events related to the pod using:
            
            ```bash
            bash
            Copy code
            kubectl describe pod <pod-name>
            
            ```
            
4. **Centralizing Logs**:
    - Use logging agents like **Fluentd** to ship logs to a centralized storage or monitoring tool for better visibility and long-term storage.

---

### **Monitoring and Analyzing Logs**

1. **Log Querying**:
    - When using log aggregators like **ELK Stack**, you can query logs based on fields like pod name, namespace, or severity level (info, warning, error).
2. **Log Visualization**:
    - Tools like **Kibana** or **Grafana** can help visualize log data, allowing you to spot trends, issues, or spikes in errors.

---

Logs in Kubernetes provide a wealth of information for troubleshooting and monitoring your cluster and applications. By combining pod and container logs with aggregated, searchable systems, you can gain deep insights into the health of your environment.

### Kubernetes Services Overview

**Kubernetes Services** provide a stable way for other pods and external users to communicate with your pods, abstracting the network details. While pods get their own IP addresses, these IPs change when the pod is restarted. Services ensure that even if the pod IP changes, the communication remains consistent.

---

### How Services Work (Networking and IPs)

- **Pod IPs**: Pods in Kubernetes get dynamically assigned IP addresses from the node’s internal network. When a pod dies and is replaced, the new pod may have a different IP.
- **Service IP**: A service has a stable IP that remains constant, allowing for consistent communication with the pods, even when the underlying pod IPs change.
- **ClusterIP**: The default service type creates an internal IP address for use within the cluster. Other services or pods in the same cluster can access this service.

When a user or another service sends a request to the **Service IP**, Kubernetes uses **iptables** or **IPVS** rules to route traffic to one of the available pods. The routing is handled using load balancing.

---

### Types of Services

![service types.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/service_types.png)

1. **ClusterIP (Default)**:
    - Exposes the service on an internal IP that is only accessible within the Kubernetes cluster.
    - Use case: Internal communication between microservices within the cluster.
    
    ![clusterIp.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/clusterIp.png)
    
2. **NodePort**:
    - Exposes the service on a static port on each node (the same port number for all nodes), making it accessible from outside the cluster.
    - Use case: Exposing services to external traffic without using an external load balancer.
    
    ![nodePort.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/nodePort.png)
    
    ![nodePort-2.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/nodePort-2.png)
    
3. **LoadBalancer**:
    - Provisions an external load balancer in cloud environments (AWS, GCP, Azure).
    - Use case: When you need automatic load balancing for external traffic.
4. **ExternalName**:
    - Maps a service to an external DNS name.
    - Use case: Redirecting to external services (e.g., third-party APIs).

---

### NodePort in Detail

- **Port Components**:
    - **Port**: The port that the service exposes internally within the cluster.
    - **TargetPort**: The port on the container that receives the traffic.
    - **NodePort**: The port that the service exposes on the node. This port is chosen from a range (usually between **30000 and 32767**).
- **How NodePort Works**:
    - When you define a NodePort service, Kubernetes opens the specified port on every node.
    - Incoming traffic sent to the node’s IP on this port is forwarded to one of the pods (depending on load-balancing rules) that match the service selector.
    - **Path**:
        - A user sends a request to a node’s IP address and the exposed NodePort.
        - The node forwards the request to the appropriate pod’s **TargetPort** based on the service’s selector (using round-robin or IP hashing).

---

### Example of a NodePort Service:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80           # Port exposed internally (Service Port)
      targetPort: 8080    # Port on the pod (Container Port)
      nodePort: 30007     # Port exposed on the node (NodePort)
```

- If a user requests `http://<node-ip>:30007`, the request will be forwarded to one of the pods’ port `8080`.

---

### Multiple Nodes and Pods with Services

- When there are **multiple nodes**, the **NodePort** will expose the service on all nodes. A user can access any node IP to reach the service.
- The service routes traffic to **multiple pods** using a load-balancing mechanism, either round-robin or IP hashing.
- **Deployments and Services**:
    - When creating services, you usually point the service to the **Deployment’s selector**, not individual pods. The service will automatically discover all pods created by that deployment based on labels.
    
    ```yaml
    selector:
      app: my-app
    ```
    
    This way, any pod that matches the `app: my-app` label will be part of the service.
    

---

### Important Points to Note

1. **Service Discovery**:
    - Pods can communicate with each other using **service names**. For example, if there is a service `my-service` exposing a web application, another pod can reach it using `http://my-service`.
2. **Cluster DNS**:
    - Kubernetes provides an internal DNS that automatically resolves service names to their ClusterIP.
3. **Service without Selectors**:
    - You can create a service without selectors and manually define the endpoints that the service should route traffic to. This is useful when integrating non-Kubernetes systems.

---

### Default Service in Kubernetes

- **kubernetes.default.svc**: This is a service created automatically within every Kubernetes cluster. It provides access to the Kubernetes API, which other components inside the cluster use to communicate with the API server.
    
    ```bash
    $ kubectl get svc
    NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
    kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d
    ```
    

---

- **NodePort Range**: By default, NodePorts use the range **30000-32767**, but this can be customized.
- **Service Scaling**: When scaling deployments, services automatically adapt to route traffic to new pods.
- **Resource Sharing**: Resources such as memory or CPU cannot be shared between nodes. Each pod can only use the resources available on the node it is scheduled on.

---

### Handling node IPs

- **Manual Node IPs**: You can access a NodePort using any node IP, but this is not ideal for production (only for development/test environments).
- **Load Balancer**: Best approach for production. It gives you a single IP (or DNS) that distributes traffic across the nodes.
- **DNS Round-Robin**: Useful if you have multiple node IPs but don't want to manage a Load Balancer. Not as reliable as load balancing.
- **External LoadBalancer (Cloud)**: Automatically provisioned in cloud environments. Use this to expose a service with a public IP.
- **Ingress Controller**: Preferred for HTTP/HTTPS traffic. It provides domain-based routing and works well with multiple services.

### **Ingress** in Kubernetes

### What is **Ingress** in Kubernetes?

**Ingress** is a Kubernetes API object that provides **HTTP and HTTPS routing** to services inside a Kubernetes cluster. It acts as a **gateway** that manages external access to services, allowing users to define routing rules based on URLs, domains, or paths. Instead of exposing each service individually (as in NodePort or LoadBalancer), Ingress centralizes the access to multiple services under one entry point (domain or IP), simplifying management and control over traffic routing.

![ingress-1.png](Kubernetes%20(%20All-in-one%20)%202193e043159d810aaf0ed36127bbcf43/ingress-1.png)

---

### How Ingress Works

1. **Client Request**: A client sends a request, e.g., `https://example.com/api`.
2. **Ingress Entry Point**: The request first hits the Ingress Controller, which is listening for traffic on the external IP or LoadBalancer.
3. **Routing**: The Ingress Controller checks the rules defined in the Ingress resource and routes the request to the correct service. In this case, it routes `/api` requests to **backend-api-service**.
4. **TLS Termination** (Optional): If TLS is configured, the Ingress Controller decrypts the traffic.
5. **Backend Service**: The request is forwarded to the appropriate service. The service may forward the request to one of its pods, based on internal Kubernetes Service routing.

---

### Different Types of Ingress Controllers

Some commonly used Ingress Controllers are:

1. **NGINX Ingress Controller**:
    - The most commonly used Ingress controller.
    - Supports path-based and host-based routing.
    - Built-in TLS termination, header rewriting, and load balancing.
2. **Traefik**:
    - Lightweight Ingress controller often used for dynamic environments.
    - Supports advanced routing features like load balancing, retry logic, and WebSocket support.
3. **HAProxy**:
    - Known for its performance and flexibility.
    - Offers detailed configuration and logging capabilities.
4. **Cloud-Specific Controllers**:
    - **AWS ALB** Ingress Controller
    - **GCE** Ingress Controller
    - These integrate directly with cloud provider Load Balancers.

---

### Default Ingress in Kubernetes

Kubernetes itself does not include a default Ingress resource or controller. You need to choose an Ingress controller (such as NGINX) based on your environment and deploy it in your cluster.

---

### Key Benefits of Ingress

- **Simplifies Traffic Management**: Instead of exposing multiple services individually, you can centralize routing through one entry point.
- **Path and Host-based Routing**: You can serve multiple services based on paths or hosts (e.g., `/api` for one service, `/login` for another).
- **SSL/TLS Support**: Ingress makes it easy to configure SSL certificates for your services.
- **Scalability**: Handles a large number of services behind one public-facing interface.

---

### Ingress Setup: Required Components

To set up **Ingress** in Kubernetes, several components need to be configured:

1. **Ingress Controller**:
    
    A dedicated controller must be installed in your cluster to manage Ingress resources. Common options include:
    
    - **NGINX Ingress Controller** (most popular)
    - **Traefik**
    - **HAProxy**
    
    Example installation of NGINX Ingress Controller:
    
    ```bash
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
    ```
    
2. **Ingress Resource**:
    
    Defines the routing rules, such as paths and hosts. It directs external requests to the correct services within your cluster.
    
3. **Service**:
    
    Each backend service must be defined to handle the traffic routed by the Ingress resource. These services expose your applications (Pods) to the Ingress Controller.
    
4. **ConfigMaps**:
    
    Some Ingress Controllers, like NGINX, use **ConfigMaps** to manage specific configurations, such as timeouts or header rewrites. Example:
    
    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: nginx-configuration
      namespace: ingress-nginx
    data:
      proxy-body-size: 8m
    ```
    
5. **TLS/Certificates** (Optional):
    
    If you want HTTPS traffic, you need to configure TLS certificates. You can use Kubernetes Secrets to store these certificates and configure the Ingress resource to use them.
    
6. **Roles and RoleBindings**:
    
    Ensure proper **RBAC (Role-Based Access Control)** permissions for the Ingress Controller to function correctly in the cluster.
    
    Example of creating RBAC roles:
    
    ```yaml
    apiVersion: rbac.authorization.k8s.io/v1
    kind: Role
    metadata:
      namespace: ingress-nginx
      name: ingress-role
    rules:
    - apiGroups: ["extensions", "networking.k8s.io"]
      resources: ["ingresses", "services", "configmaps"]
      verbs: ["get", "list", "watch"]
    ```
    

---

### Before **Ingress** in Kubernetes

Before the introduction of **Ingress**, exposing services to the outside world in Kubernetes was done using services like **NodePort** or **LoadBalancer**. However, each of these had its limitations, especially when managing multiple services or needing complex routing. Here’s a scenario of what happened before **Ingress** was available:

### Scenario Before Ingress:

Let’s say you had three different microservices running in Kubernetes:

- **Service A** (for user management)
- **Service B** (for payments)
- **Service C** (for notifications)

You wanted all these services to be accessible from the internet.

### Using NodePort or LoadBalancer:

1. **NodePort**:
    - You could expose each service by assigning a port on each node. For example:
        - **Service A** on NodePort **30001**
        - **Service B** on NodePort **30002**
        - **Service C** on NodePort **30003**
    - This means that external users would have to access the services using the **Node IP** and the specific NodePort, e.g., `http://<Node-IP>:30001` for Service A.
    - **Issues**:
        - You'd have multiple ports to manage.
        - If you wanted to add more services, you would have to keep assigning more NodePorts.
        - NodePort exposes the service on every node, even if you don't need it on all nodes.
        - Harder to manage when scaling up microservices.
2. **LoadBalancer**:
    - Alternatively, you could create a **LoadBalancer** service for each service:
        - Each service would get its own external IP, and requests would be routed directly to that IP.
        - For example:
            - **Service A** on external IP `192.168.1.10`
            - **Service B** on external IP `192.168.1.11`
            - **Service C** on external IP `192.168.1.12`
    - **Issues**:
        - Each service requires its own LoadBalancer, which can be expensive and inefficient.
        - Management of multiple IPs for different services.
        - Difficult to handle routing rules or shared access under a single domain name.

In both cases, you'd end up with scattered IPs and ports to manage. This approach lacks flexibility, especially for complex applications that require domain-based routing, SSL termination, or load balancing across different services under the same domain.

---

### After **Ingress** in Kubernetes

**Ingress** was introduced to solve these issues. It acts as an **API gateway** to manage external access to services within the cluster. Ingress allows you to define rules for routing traffic to services based on the request's path or host. This centralizes the management of access to multiple services.

### Scenario with Ingress:

You have the same three microservices:

- **Service A** (for user management)
- **Service B** (for payments)
- **Service C** (for notifications)

You want to expose all these services under the same domain (`example.com`) with specific paths:

- `/users` → Service A
- `/payments` → Service B
- `/notifications` → Service C

### Using Ingress:

- Instead of assigning multiple IPs or ports, you create an **Ingress resource** that will manage all incoming requests.
- You can now have **one entry point** (single domain/IP) and configure path-based routing:
    - `example.com/users` routes to **Service A**.
    - `example.com/payments` routes to **Service B**.
    - `example.com/notifications` routes to **Service C**.

**How it works**:

- The Ingress resource listens to HTTP/HTTPS traffic and routes the request to the appropriate service based on the request's path or host header.
- You can even apply SSL termination at the Ingress level.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /users
        pathType: Prefix
        backend:
          service:
            name: service-a
            port:
              number: 80
      - path: /payments
        pathType: Prefix
        backend:
          service:
            name: service-b
            port:
              number: 80
      - path: /notifications
        pathType: Prefix
        backend:
          service:
            name: service-c
            port:
              number: 80
```

In this case:

- **Service A** is exposed at `example.com/users`.
- **Service B** is exposed at `example.com/payments`.
- **Service C** is exposed at `example.com/notifications`.

### Advantages with Ingress:

- **Single IP or domain** for all services.
- **Path-based or host-based routing** simplifies the management of multiple services.
- Centralized control of access and routing rules.
- Can handle **SSL termination** at the Ingress level (no need to configure SSL for each service).
- You only expose one LoadBalancer IP (if necessary) instead of one per service, reducing cost and complexity.

---

**Ingress** can be thought of as a "service for services" in Kubernetes, specifically for managing **external HTTP/HTTPS access** to multiple internal services.

Here’s a breakdown:

- **Ingress** allows you to define rules that route external traffic (HTTP/HTTPS requests) to specific **Services** inside the Kubernetes cluster.
- Without Ingress, you'd typically expose each service separately using **NodePort** or **LoadBalancer**, which can become complex and inefficient when managing many services.
- With Ingress, you can expose **multiple services** through **one single entry point** (like a domain or IP), using **path-based** or **host-based** routing.

### Example

Imagine you have three services inside your Kubernetes cluster:

1. **User Service** (`/users`)
2. **Payment Service** (`/payments`)
3. **Notification Service** (`/notifications`)

Instead of exposing these services individually, you can use an **Ingress** resource to manage access through one external IP or domain.

- **example.com/users** routes to the User Service.
- **example.com/payments** routes to the Payment Service.
- **example.com/notifications** routes to the Notification Service.

The **Ingress Controller** is responsible for processing these routing rules and forwarding the traffic to the right service based on the path or host.

### Key Points

- **Ingress** is not a service itself but rather an API object that provides **routing rules** for **Services**.
- An **Ingress Controller** is required to implement these routing rules and handle the actual traffic (e.g., NGINX, Traefik).
- It centralizes access and simplifies management by avoiding multiple LoadBalancer or NodePort services for each individual service.

So, in simple terms, **Ingress** is like a "traffic manager" for your services.

In summary, **Ingress** simplifies service exposure, consolidates access under one domain or IP, provides flexibility with routing, and centralizes SSL handling

---

### Kubernetes Network Policies

A **NetworkPolicy** in Kubernetes controls the traffic flow to and from pods. You can define rules for both **ingress** (incoming traffic) and **egress** (outgoing traffic) between pods, namespaces, or external sources. Without NetworkPolicies, all traffic is allowed by default.

---

### **Ingress and Egress Rules**

1. **Ingress**: Specifies rules that allow inbound traffic to the pod. If no ingress rule exists, the pod denies all incoming connections except from within the same pod namespace.
2. **Egress**: Specifies rules that allow outbound traffic from the pod. Without egress rules, pods can communicate with any other pods or external services.

---

### **Scenario: Before vs. After Applying Network Policies**

### Before Applying a Policy:

- By default, all pods can communicate freely with each other across all namespaces.
- All pods can send traffic to external services (e.g., databases, web services) and receive traffic.
- **No restrictions** are applied to ingress/egress.

### After Applying a Policy:

- Pods are restricted by the rules defined in the NetworkPolicy.
- You can allow traffic **only** from certain sources (other pods, namespaces, IPs, or CIDR ranges).
- Only **specified traffic** can leave or enter the pod.

---

### **Cross-Namespace Traffic: Does a NetworkPolicy Apply?**

- **NetworkPolicies** are **namespace-scoped**, meaning they only apply to pods within the same namespace. However, you can define rules that allow or deny traffic **from or to other namespaces** by specifying the `namespaceSelector`.

Example:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: cross-namespace-policy
  namespace: my-namespace
spec:
  podSelector: {}
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: other-namespace
```

This allows ingress traffic from pods in a different namespace (`other-namespace`).

---

### **Does a Database Need an Egress Rule?**

Yes, **if the database pod needs to send traffic outside its namespace**, such as connecting to external services (e.g., another database cluster or external backups). Defining egress rules ensures that **only approved outgoing traffic** is allowed.

Example egress rule allowing access to an external DB:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-db-egress
spec:
  podSelector:
    matchLabels:
      app: db
  egress:
    - to:
        - ipBlock:
            cidr: 10.0.0.0/16
```

---

### **What if We Only Specify a Namespace and Not the Resources?**

If you specify only a namespace (without defining specific resources or pods), the policy will apply **to all pods in the specified namespace** that match the `namespaceSelector`.

For example, this will allow traffic from **all pods** in the `dev` namespace:

```yaml
ingress:
  - from:
      - namespaceSelector:
          matchLabels:
            name: dev
```

---

### **Backup Server Access to a DB (IP Block and Other Options)**

To allow a **Backup Server** (with a known IP range) to access the database, you can use an `ipBlock` in the NetworkPolicy. You can also restrict traffic using the `podSelector` to limit traffic only from certain pods or services.

Example allowing a backup server with specific IP range:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-backup-access
spec:
  podSelector:
    matchLabels:
      app: db
  ingress:
    - from:
        - ipBlock:
            cidr: 192.168.1.0/24  # Backup server IP range
```

---

### **Using AND + OR Logic in the Manifest**

In Kubernetes NetworkPolicies:

- **AND Logic**: By default, all conditions within a single rule (such as both `podSelector` and `namespaceSelector`) work together, meaning all must be true for the rule to apply.
- **OR Logic**: To apply OR logic, you can define multiple entries within `ingress` or `egress` rules, meaning that if any one condition is met, the traffic is allowed.

Example combining AND and OR logic:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: combined-policy
spec:
  podSelector:
    matchLabels:
      app: frontend
  ingress:
    - from:
        - namespaceSelector:
            matchLabels:
              name: dev
        - podSelector:
            matchLabels:
              app: monitoring  # OR rule: Allow traffic from the monitoring pod
    - from:
        - ipBlock:             # AND rule: Allow traffic from IP range
            cidr: 192.168.1.0/24
```

In this example, traffic is allowed either from:

1. Pods in the `dev` namespace.
2. The monitoring pod.
3. The specified IP range.

---

### Allowing Traffic From Either Pod A or Pod B

To allow traffic from **either Pod A or Pod B** to a specific pod, you can combine multiple rules in the `NetworkPolicy` using **logical operators** such as `OR` by listing multiple selectors in the policy.

Example:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-from-multiple-pods
  namespace: my-namespace
spec:
  podSelector:       # Apply this policy to the target pod
    matchLabels:
      app: my-app
  ingress:          # Ingress rules to allow traffic into the pod
  - from:
    - podSelector:   # Allow traffic from Pod A
        matchLabels:
          app: pod-a
    - podSelector:   # Allow traffic from Pod B (OR condition)
        matchLabels:
          app: pod-b
```

Here, **either Pod A or Pod B** can send traffic to `my-app`. The **OR logic** is achieved by adding multiple `from` clauses in the `ingress` block.

---

### Network Plugins (CNI) and Policy Enforcement

Kubernetes relies on **Container Network Interface (CNI)** plugins for managing network connectivity. Different CNI plugins handle **networking** and **NetworkPolicy enforcement** differently.

- **CNI Plugins**: Provide network connectivity for pods.
- **NetworkPolicy Enforcement**: Ensures traffic rules are applied as defined in `NetworkPolicies`.

### Popular CNI Plugins and Their Enforcement Capabilities:

1. **Calico**:
    - Fully supports **NetworkPolicies** for both **Ingress** and **Egress**.
    - Provides additional capabilities like IP address-based policies, NAT, and encryption.
    - Best for environments where fine-grained policy controls are needed.
2. **Cilium**:
    - Focuses on networking and security using eBPF.
    - Provides **deep visibility** into network flows and can enforce both **Ingress** and **Egress** rules with enhanced flexibility, such as DNS-aware policies.
3. **Weave**:
    - Supports Kubernetes `NetworkPolicies`, but limited in **Egress** rule enforcement compared to Calico or Cilium.
    - Focuses on simplicity and ease of use.
4. **Flannel**:
    - Primarily for basic networking and does **not** enforce `NetworkPolicies`.
    - Often used in setups where basic connectivity is enough, and policies are handled by another layer.

### Rule Enforcement:

- **Calico, Cilium, and Weave**: Enforce NetworkPolicies directly, meaning traffic is blocked/allowed as defined.
- **Flannel**: Requires additional tools (e.g., Calico for policy enforcement) since it doesn’t enforce policies natively.

> [https://artturik.github.io/network-policy-viewer/](https://artturik.github.io/network-policy-viewer/)
For viewing NetworkPolicies Graphically
>