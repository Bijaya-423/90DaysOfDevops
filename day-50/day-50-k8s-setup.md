### Task 1: Recall the Kubernetes Story
Before touching a terminal, write down from memory:

1. Why was Kubernetes created? What problem does it solve that Docker alone cannot?

-> Kubernetes was created to automate the deployment, scalling and management of the containerized application. Docker is great for creating and running containers , but it can not efficiently manage large number of containers across multiple servers. kubernetes solves problems like container orchestration , load balancing , service discovery, auto-scling , slef -healing , rolling updateds, and high availability.





2. Who created Kubernetes and what was it inspired by?

-> Kubernetes was originally created by  google and later donated to thr cloud native computing foundationn(CNCF). it was inspired by google's internal container management system called BROG, which google used to manage workloads at massive scale.


3. What does the name "Kubernetes" mean?

-> The word kubernetes comes from greek and means "Helmsman" or "Polit" , someone who streers a ship. THis represents how kubernetes manages and orchestrates containers its abbreviation in k8s , where the 8 represents the eight letters between k and s

Do not look anything up yet. Write what you remember from the session, then verify against the official docs.

### Task 2: Draw the Kubernetes Architecture
From memory, draw or describe the Kubernetes architecture. Your diagram should include:

**Control Plane (Master Node):**
- API Server — the front door to the cluster, every command goes through it
========================================================================
-> Entry point of the kubernetes cluster.
-> receives all requests from kubectl.
-> validates requests.
-> Stores cluster information in etcd
-> communicates with all other control plane components.


- etcd — the database that stores all cluster state
====================================================
-> Distributed key-value database.
-> Stores the complete cluster state.
-> Stores Pods , Deployments , services , secrets, ConfigMpas, etc.
-> Considered the single source of truth.




- Scheduler — decides which node a new pod should run on
=========================================================
-> Watches for Pods without assigned nodes.
-> Chooses the best worker node based on available CPU, memory , affinity, taints, tolerations, etc.
Assigns the Pod to a worker node.



- Controller Manager — watches the cluster and makes sure the desired state matches reality
========================================================================
-> Continuously watches the cluster.
-> Ensures the actual state matches the desired state.
-> Create or replace Pods if needed.
-> handles ReplicaSet, Nodes , Jobs, Deployments and more.

**Worker Node:**
- kubelet — the agent on each node that talks to the API server and manages pods
- kube-proxy — handles networking rules so pods can communicate
- Container Runtime — the engine that actually runs containers (containerd, CRI-O)

After drawing, verify your understanding:
- What happens when you run `kubectl apply -f pod.yaml`? Trace the request through each component.
- What happens if the API server goes down?
- What happens if a worker node goes down?



                    +----------------------+
                    |      kubectl         |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |      API Server      |
                    +----------+-----------+
                               |
        +----------------------+----------------------+
        |                      |                      |
        v                      v                      v
+---------------+     +----------------+     +----------------------+
|     etcd      |     |   Scheduler    |     | Controller Manager   |
| Cluster State |     | Selects Node   |     | Maintains Desired    |
+---------------+     +----------------+     | State                |
                                              +----------------------+
                               |
                               v
                 -------------------------------------
                 |                                   |
                 v                                   v
         +-------------------+              +-------------------+
         |   Worker Node 1   |              |   Worker Node 2   |
         +-------------------+              +-------------------+
         | kubelet           |              | kubelet           |
         | kube-proxy        |              | kube-proxy        |
         | Container Runtime |              | Container Runtime |
         | (containerd/CRI-O)|              | (containerd/CRI-O)|
         |       Pods        |              |       Pods        |
         +-------------------+              +-------------------+




