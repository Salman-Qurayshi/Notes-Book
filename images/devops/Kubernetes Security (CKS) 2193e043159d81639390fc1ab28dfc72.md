# Kubernetes Security (CKS)

### **Overview**

CKS demonstrates advanced knowledge in securing Kubernetes clusters and container-based applications during build, deployment, and runtime.

**Pre-requisite**

- **CKA Certification** is required to sit for the CKS exam.

**Who Is It For**

- A **CKS** is an accomplished Kubernetes practitioner (must hold an active **CKA** certification).
- Competence in securing Kubernetes platforms and container-based applications during their lifecycle (build, deployment, runtime).

**About This Certification**

- **Performance-based exam:** The CKS tests your security knowledge in real-world, simulated environments.
- **Pre-requisite:** CKA certification must be active before scheduling the CKS exam.

**Demonstrated Skills**

- Proficiency in securing Kubernetes clusters and container-based applications.
- Ability to secure applications at all stages (build, deploy, runtime).

---

### **Securing Kubernetes Clusters**

This course focuses on securing Kubernetes environments, covering essential practices and techniques.

### **Cluster Setup**

1. **Network Security Policies (NSPs)**
    - **Objective:** Restrict cluster-level access and control pod-to-pod communication.
    - **Benefits:**
        - Limit the traffic flow within the cluster to enhance security.
        - NSPs target specific pods, namespaces, or labels to manage communication.
2. **CIS Benchmark**
    - **Use Case:** Review the security configuration of Kubernetes components.
    - **Components Checked:**
        - etcd
        - kubelet
        - kubedns
        - kubeapi-server
    - **Purpose:** Ensure pre-defined security standards are met, addressing any security misconfigurations.
3. **Secure Ingress Setup**
    - **Objective:** Expose services to external users securely.
    - **Mechanisms:** Implement authentication (e.g., TLS, basic auth) for controlled access.
4. **Node Metadata & Endpoint Protection**
    - **Risk Mitigation:** Reduce risks associated with exposed node metadata.
    - **Control:** Use RBAC or Network Policies to restrict access.
5. **Minimal GUI Use**
    - **Recommendation:** Minimize the use of GUIs for cluster management.
    - **Reasoning:** GUIs introduce additional attack surfaces, while **kubectl** is more secure.
6. **Verify Platform Binaries**
    - **Purpose:** Ensure that Kubernetes platform binaries are authentic and not tampered with.
    - **Method:** Use checksums or trusted repositories to verify before deployment.

---

### **Using Network Security Policies (NSPs)**

- **Function:** Define how traffic flows between pods.
- **Granular Control:** NSPs allow fine-tuning of both ingress (incoming) and egress (outgoing) traffic.
- **Targeting:** NSPs can be applied to specific:
    - Pods
    - Namespaces
    - Labels

### setting up a Kubernetes environment with Minikube and Docker.

### 1. **System Update & Preparation**

```bash
sudo apt-get update
```

- **Purpose:** This ensures the package lists on your system are up-to-date.

### 2. **Install `kubectl` (Kubernetes CLI)**

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256) kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

- **Downloads `kubectl`**: This retrieves the latest stable release of the Kubernetes CLI tool, `kubectl`.
- **Verifies the integrity of `kubectl`**: The `sha256sum` ensures the downloaded binary is untampered.
- **Installs `kubectl`**: It's installed with appropriate permissions in `/usr/local/bin`.

### 3. **Install Minikube**

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

- **Downloads Minikube**: Minikube helps run Kubernetes locally.
- **Installs Minikube**: It's placed in `/usr/local/bin` to be globally accessible.

### 4. **Install Docker**

```bash
sudo apt install docker.io
```

- **Purpose**: Installs Docker, which is required by Minikube to run containers.

### 5. **Configure Docker**

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

- **GPG Key & Repository Setup**: Adds Docker’s GPG key and sets up the official Docker repository for Ubuntu.
- **Install Docker Components**: Installs Docker's core components, including Docker Engine (`docker-ce`), CLI, `containerd`, `docker-buildx`, and `docker-compose`.

### 6. **Add User to Docker Group**

```bash
sudo usermod -aG docker $USER && newgrp docker
```

- **Purpose**: Adds your user to the `docker` group so you can run Docker commands without needing `sudo`.

### 7. **Start Minikube**

```bash
minikube start
```

- **Purpose**: This starts a local Kubernetes cluster using Minikube.

### 8. **Reboot**

```bash
sudo reboot now
```

- **Reboot the system** to apply changes, especially for Docker group changes.

### 9. **Validate Kubernetes Setup**

```bash
kubectl get pod -A
kubectl version --client
kubectl version --client --output=yaml
```

- **Check Pods**: `kubectl get pod -A` shows all pods running across namespaces.
- **Check `kubectl` Version**: Confirms the `kubectl` client is installed correctly.

### **CIS Kubernetes Benchmark**

**CIS Kubernetes Benchmark**  is a set of best practices and security guidelines provided by the Center for Internet Security (CIS) to help organizations secure their Kubernetes clusters. These benchmarks cover a wide range of security configurations for various components of Kubernetes and are intended to harden the cluster against potential vulnerabilities.

### 1. **What is the CIS Kubernetes Benchmark?**

- **Purpose**: The CIS Kubernetes Benchmark provides a comprehensive set of security recommendations to ensure that Kubernetes clusters are configured securely. It focuses on minimizing the attack surface of Kubernetes deployments by hardening components such as the API server, etcd, kubelet, and others.
- **Applicability**: The benchmark is applicable to both on-premise and cloud-hosted Kubernetes clusters.

### 2. **Key Areas of the CIS Benchmark**

The CIS Kubernetes Benchmark is organized into several sections based on the different components of a Kubernetes cluster. Each recommendation includes detailed steps to audit and fix security gaps. Below are the key areas covered:

### a. **Control Plane Components**

These recommendations focus on the security of the Kubernetes control plane, including:

- **API Server** (`kube-apiserver`)
- **Controller Manager** (`kube-controller-manager`)
- **Scheduler** (`kube-scheduler`)

### b. **Node Components**

Security guidelines for Kubernetes nodes:

- **Kubelet** (`kubelet`)
- **Kube Proxy** (`kube-proxy`)

### c. **Policies and RBAC**

- **RBAC** (Role-Based Access Control): Enforces least privilege principles by limiting what actions users or services can perform within the cluster.
- **Pod Security Policies (PSPs)**: Defines security restrictions for pod configurations, such as disallowing privileged containers or restricting the use of certain volume types.
- **Network Policies**: Recommendations on using network policies to control ingress and egress traffic between pods, services, and namespaces to restrict unauthorized communications.

### d. **Audit Logging**

- Ensures that proper audit logging is enabled for the API server and other key components. This allows monitoring of all API requests and helps detect potential security incidents.

### 3. **How to Use the CIS Kubernetes Benchmark**

- **Audit Your Cluster**: The benchmark can be used as a checklist to audit your Kubernetes cluster. You can go through each recommendation, review your current configuration, and identify areas that need improvement.
- **Automated Tools**: Tools such as **kube-bench** ( Available on github ) can be used to automate the auditing of your Kubernetes cluster against the CIS benchmark. This tool runs checks on the configuration of control plane components and worker nodes and reports on compliance with the benchmark.

### 5. **Benefits of Following the CIS Kubernetes Benchmark**

- **Enhanced Security Posture**: Following these recommendations significantly reduces the risk of potential attacks on your Kubernetes cluster.
- **Compliance**: Many organizations need to adhere to security standards and frameworks. The CIS Kubernetes Benchmark helps meet compliance requirements.
- **Best Practices**: The benchmark serves as a guide for following Kubernetes security best practices across different environments.

### 6. **CNCF and Kubernetes**

- **CNCF (Cloud Native Computing Foundation)**: Kubernetes is a project under the CNCF, which hosts numerous open-source projects. The **CNCF** provides governance, support, and oversight for the development of cloud-native software. Kubernetes, being a graduated project, has matured to a point where it is used widely in production environments.

The **CIS Kubernetes Benchmark** ensures that organizations are following best practices to secure their Kubernetes environments against evolving threats.

### Cluster setup security

### 1. **Use Network Security Policies to Restrict Cluster-Level Access**

- **Purpose**: Control traffic flow within the cluster.
- **Ingress and Egress**: Define rules to restrict which pods/services can send or receive traffic.
- **Granular Control**: Apply policies to specific pods, namespaces, or labels for fine-grained network segmentation.
- **Security Impact**: Reduces attack surface by limiting unnecessary internal/external communication.

---

### 2. **Properly Set Up Ingress Objects with Security Control**

- **Purpose**: Securely expose services to external users.
- **TLS Termination**: Use **TLS** to ensure encrypted traffic between users and services.
- **Authentication and Authorization**: Implement mechanisms like **basic auth** or **OAuth** to control access to services.
- **Best Practice**: Define **Ingress rules** carefully to avoid unintended exposure of services.

---

### 3. **Protect Node Metadata and Endpoints**

- **Purpose**: Prevent unauthorized access to sensitive information stored on nodes (e.g., instance metadata).
- **Techniques**:
    - **RBAC**: Use Role-Based Access Control to limit who/what can access node endpoints.
    - **Network Policies**: Define policies to block access to node metadata APIs.
- **Security Impact**: Reduces the risk of attackers gaining control over nodes or accessing sensitive cluster data.

---

### 4. **Minimize Use of, and Access to, GUI Elements**

- **Purpose**: Limit reliance on graphical interfaces to reduce the attack surface.
- **Security Risk**: GUI-based tools (like dashboards) may introduce vulnerabilities if misconfigured.
- **Best Practice**: Use secure CLI tools (e.g., `kubectl`) for cluster management to minimize potential risks. Or Create a Service account for the Gui api and give only read, list permissions

---

### 5. **Verify Platform Binaries Before Deploying**

- **Purpose**: Ensure integrity and authenticity of binaries.
- **Verification Methods**: Use checksums or GPG keys to confirm binaries are untampered.
- **Trusted Repositories**: Always download from official or trusted sources to prevent malicious code deployment.
- **Security Impact**: Prevents running compromised or vulnerable versions of software on your cluster.

### **Cluster Hardening**

---

### 1. **Restrict Access to Kubernetes API**

- **Purpose**: Limit who can access and interact with the Kubernetes API.
- **Techniques**:
    - Use **firewalls** or **Network Security Policies** to restrict external access.
    - Expose the API server only to trusted IPs or internal networks.
- **Security Impact**: Prevents unauthorized users from managing the cluster and deploying potentially malicious workloads.

---

### 2. **Use Role-Based Access Controls (RBAC) to Minimize Exposure**

- **Purpose**: Ensure only authorized users/services can perform actions in the cluster.
- **Granular Permissions**: Assign permissions based on the principle of least privilege (only give users/services the permissions they need).
- **Roles and RoleBindings**: Define specific roles for different cluster functions and bind them to appropriate users or service accounts.
- **Security Impact**: Reduces the risk of compromised accounts having too much control over the cluster.

---

### 3. **Exercise Caution in Using Service Accounts**

- **Disable Default Service Accounts**: Avoid using default service accounts which might have more permissions than needed.
- **Minimize Permissions for New Service Accounts**: Assign the minimum necessary permissions to service accounts based on their function.
- **Best Practice**:
    - Create separate service accounts for each workload.
    - Review service account usage regularly.
- **Security Impact**: Prevents over-privileged service accounts from being exploited by attackers.

---

### 4. **Update Kubernetes Frequently**

- **Purpose**: Ensure the cluster is running the latest, most secure version of Kubernetes.
- **Patch Management**: Regularly apply security patches and updates to Kubernetes components (e.g., API server, kubelet, etcd).
- **Automated Updates**: Use automated tools to check for new releases and implement upgrades systematically.
- **Security Impact**: Reduces exposure to known vulnerabilities that can be exploited in outdated versions.

### **System Hardening**

---

### 1. **Minimize Host OS Footprint (Reduce Attack Surface)**

- **Purpose**: Reduce the number of applications, services, and processes running on the host to minimize potential attack vectors.
- **Techniques**:
    - Install only the necessary packages and services required to run Kubernetes.
    - Use lightweight, minimal base operating systems (e.g., **Alpine Linux** or **Container-optimized OS**).
- **Security Impact**: Fewer running components mean fewer potential vulnerabilities, making the system more secure and easier to manage.

---

### 2. **Minimize IAM Roles**

- **Purpose**: Restrict the number of Identity and Access Management (IAM) roles used within the infrastructure.
- **Techniques**:
    - Assign least privilege roles to users and services.
    - Avoid assigning broad permissions across multiple services.
    - Regularly audit and clean up unused or over-privileged IAM roles.
- **Security Impact**: Limits the damage in case of compromised credentials or misconfigurations, reducing unauthorized access.

---

### 3. **Minimize External Access to the Network**

- **Purpose**: Limit external access points to reduce exposure to attacks from the outside.
- **Techniques**:
    - Use **firewalls** or **Network Security Policies** to block unwanted traffic.
    - Restrict access to the Kubernetes API and other sensitive components to internal networks or specific IP ranges.
    - Disable any unused services and ports.
- **Security Impact**: Prevents unauthorized access to cluster components from external networks and reduces the cluster's exposure to external attacks.

---

### 4. **Appropriately Use Kernel Hardening Tools (AppArmor, seccomp)**

- **Purpose**: Harden the underlying kernel to prevent privilege escalation and system compromise.
- **Tools**:
    - **AppArmor**: Enforce mandatory access control policies, limiting what applications can do (e.g., file access).
    - **seccomp**: Limit system calls that containers or processes can make to the kernel, reducing the attack surface.
- **Best Practice**:
    - Enable AppArmor or seccomp profiles for workloads to ensure only necessary system calls are allowed.
    - Regularly audit and update these profiles to match workload requirements.
- **Security Impact**: Reduces the ability of compromised containers to access critical kernel resources, improving system security.

### **Minimize Microservice Vulnerabilities**

1. **Set up appropriate OS-level security domains**
    - **Purpose**: Isolate workloads within security domains at the OS level to contain compromises.
    - **Techniques**: Use namespaces, control groups (cgroups), and tools like SELinux or AppArmor.
    - **Impact**: Limits vulnerability spread across services.
2. **Manage Kubernetes Secrets**
    - **Purpose**: Securely manage sensitive data like passwords, API keys, and certificates.
    - **Techniques**: Store secrets in Kubernetes Secrets, encrypt them in transit and at rest, and use RBAC to control access.
    - **Impact**: Prevents unauthorized access to sensitive information.
3. **Use container runtime sandboxes in multi-tenant environments**
    - **Purpose**: Isolate containers in environments with multiple tenants.
    - **Tools**: gVisor, Kata Containers for enhanced isolation.
    - **Impact**: Reduces container breakout or escalation attacks.
4. **Implement pod-to-pod encryption using mTLS**
    - **Purpose**: Secure communication between pods.
    - **Techniques**: Use mutual TLS (mTLS) and integrate with service mesh solutions like Istio.
    - **Impact**: Prevents unauthorized traffic interception between pods.

### **Supply Chain Security**

1. **Minimize base image footprint**
    - **Purpose**: Reduce image size to limit the attack surface.
    - **Techniques**: Use minimal base images (e.g., Alpine, Distroless) and avoid unnecessary packages.
    - **Impact**: Fewer dependencies result in fewer vulnerabilities.
2. **Secure your supply chain**
    - **Purpose**: Ensure only trusted images are used.
    - **Techniques**: Whitelist trusted registries and use image signing (e.g., Notary).
    - **Impact**: Blocks untrusted or malicious images.
3. **Use static analysis of user workloads**
    - **Purpose**: Detect misconfigurations in Kubernetes manifests and container images.
    - **Techniques**: Tools like kube-score, KubeLinter, and Hadolint for static analysis.
    - **Impact**: Catches security issues early, before deployment.
4. **Scan images for known vulnerabilities**
    - **Purpose**: Identify and fix vulnerabilities in container images.
    - **Techniques**: Use scanners like Trivy, Clair, or Anchore.
    - **Impact**: Prevents known vulnerabilities from entering the environment.

### **Monitoring, Logging, and Runtime Security**

1. **Perform behavioral analytics of syscall and file activities**
    - **Purpose**: Detect abnormal behavior in system calls and file activities.
    - **Techniques**: Use tools like Falco and Sysdig to monitor behaviors.
    - **Impact**: Identifies malicious activities at the host and container level.
2. **Detect threats across infrastructure and applications**
    - **Purpose**: Monitor threats across all infrastructure layers—apps, networks, users, etc.
    - **Impact**: Ensures a holistic view of security across all environments.
3. **Detect all phases of an attack**
    - **Purpose**: Identify all stages of an attack, from initial intrusion to spread.
    - **Impact**: Provides a complete picture of attack vectors and progression.
4. **Deep investigative analysis**
    - **Purpose**: Conduct in-depth investigations of bad actors and threats.
    - **Impact**: Helps identify root causes and take corrective actions.
5. **Ensure immutability of containers at runtime**
    - **Purpose**: Prevent changes to containers once they are running.
    - **Impact**: Ensures consistent container behavior and prevents unauthorized modifications.
6. **Use Audit Logs to monitor access**
    - **Purpose**: Track who accessed what in the environment.
    - **Impact**: Provides a log of activities for monitoring and incident response.