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
====================================================================
-> Runs on every worker node.
-> Receives instructions from the Api server.
-> creates and monitors pods.
-> Reports node and pod status back to the API server.






- kube-proxy — handles networking rules so pods can communicate
==================================================================
->  Manages networking .
-> implements service networking.
-> Enables communication between pods and services
-> Performs load balancing.



- Container Runtime — the engine that actually runs containers (containerd, CRI-O)
===============================================================
-> Runs the actual containers.
Examplpe :- contained
CRI-O

After drawing, verify your understanding:
- What happens when you run `kubectl apply -f pod.yaml`? Trace the 
request through each component.
===================================================================
-> kubectl -> api server -> stores desired state in etcd -> scheduler notics pod has no node -> selects best worker node -> api server updted assignement -> kubelet on selectes worker node detectes new pod -> container runtime pulls images -> container starts -> kubelet reports pod status back -> api server updates etcd


steps
=====
i- kubectl apply -f pod.yml
ii- request goes to the api server.
iii- api server validagtes the yml.
iv- Desired state is stored in etcd.
v- schudeler selects a worker node.
vi- kubelet on that node sees the assignment.
vii- containers run time pulls the docker images
viii- pods starts.
ix- kubelet reports the pods status
x- api server updates etcd with the current state.

- What happens if the API server goes down?
===========================================
-> kubectl commands stop working.
-> no new pods can be created.
-> no updated or scalling operationss can occur.
-> controllers and schudeler cannot coordinate changes.
-> existing pods continue running on worker nodes.
-> if configuredd with multiple api server (high availability), another api server can continue serving request.




- What happens if a worker node goes down?
===========================================
-> kubelet stops sending heartbets.
-> controller manager detects the node is unavailable.
-> pods on that node become unavailable.
-> controller manager schudelers replacement pods on healthy worker nodes(if managed by a deployment or repicaset).
-> traffic is redirecred to the healthy pos throught services and kube-proxy
-users expericnce little or no downtiume if replicated are available.



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









