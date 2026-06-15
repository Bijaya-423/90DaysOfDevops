### Task 1: Docker Images
1. Pull the `nginx`, `ubuntu`, and `alpine` images from Docker Hub


docker pull nginx
docker pull ubuntu
docker pull alpine


2. List all images on your machine — note the sizes
IMAGE                       ID             DISK USAGE   CONTENT SIZE   EXTRA

alpine:latest               a2d49ea686c2       13.1MB         3.95MB
ubuntu:latest               f3d28607ddd7        160MB         45.3MB
nginx:latest                608a100c7165        241MB           66MB


3. Compare `ubuntu` vs `alpine` — why is one much smaller?
Built specifically for lightweight containers
uses musl libc instead of glibc
uses busybox utilities instead of full gnu tools
contains only the essentials needed to run applications
smaller download size , faster images pulls less store usage

4. Inspect an image — what information can you see?

docker inspect nginx
====================
[
    {
        "Id": "sha256:608a100c71651bf5b773c89083b4a1ad7ef4b2bd05d7a7e552271e03123692ad",
        "RepoTags": [
            "nginx:latest"
        ],
        "RepoDigests": [
            "nginx@sha256:608a100c71651bf5b773c89083b4a1ad7ef4b2bd05d7a7e552271e03123692ad"
        ],
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2026-06-11T00:23:30.136519073Z",
        "Config": {
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.31.1",
                "NJS_VERSION=0.9.9",
                "NJS_RELEASE=1~trixie",
                "ACME_VERSION=0.4.1",
                "PKG_RELEASE=1~trixie",
                "DYNPKG_RELEASE=1~trixie"
            ],
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 63125971,
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:f4f8b983b714f130e2cff99176baa26352db6a55d3622e10ada40f2b4720a4eb",
                "sha256:af29206eb654bc703f8ac42874fced4323f978134f7c19e7c0c9edb14d16f2f7",
                "sha256:493aa43406a6150afbb5c00f0b42053768bad005e9a454ca638af8a5af0f9de4",
                "sha256:e8832fb2fc126ce5d91603b931812c2bf941a0169f565c0d777b7c3460a48e6c",
                "sha256:57b80f15e54052ec53ba5a764092724e74d586b7bfef068adc8aadaab4957d2c",
                "sha256:db054fb45c4c4d588f3bb6acd38a3a701426be7588400edba081eebb2e542192",
                "sha256:121b6a4dad004ecad3e8292a919d6a2344153529354a9c9c4718eb38df5048ff"
            ]
        },
        "Metadata": {
            "LastTagTime": "2026-06-15T16:49:15.073365114Z"
        },
        "Descriptor": {
            "mediaType": "application/vnd.oci.image.index.v1+json",
            "digest": "sha256:608a100c71651bf5b773c89083b4a1ad7ef4b2bd05d7a7e552271e03123692ad",
            "size": 10229
        }
    }
]
docker inspect ubuntu
=====================
[
    {
        "Id": "sha256:f3d28607ddd78734bb7f71f117f3c6706c666b8b76cbff7c9ff6e5718d46ff64",
        "RepoTags": [
            "ubuntu:latest"
        ],
        "RepoDigests": [
            "ubuntu@sha256:f3d28607ddd78734bb7f71f117f3c6706c666b8b76cbff7c9ff6e5718d46ff64"
        ],
        "Comment": "Add rock control metadata",
        "Created": "2026-04-21T17:22:47.070440543Z",
        "Config": {
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Labels": {
                "org.opencontainers.image.created": "2026-04-21T17:23:54.324551+00:00",
                "org.opencontainers.image.description": "The Ubuntu container image maintained by Canonical\n\nUbuntu is a Debian-based Linux operating system that runs from the desktop to the cloud, to all your internet connected things.\nIt is the world's most popular operating system across public clouds and OpenStack clouds.\nIt is the number one platform for containers; from Docker to Kubernetes to LXD, Ubuntu can run your containers at scale.\nFast, secure and simple, Ubuntu powers millions of PCs worldwide.\n",
                "org.opencontainers.image.title": "ubuntu",
                "org.opencontainers.image.version": "26.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 41567720,
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:0c3db79307ab91dad11fad2b136a2b56df6efeeb567c4c99e6e316b63885c9f6",
                "sha256:f421a7e99ead34566fcb11403f6f38675b53035f39937394893eaf7d87c39f83"
            ]
        },
        "Metadata": {
            "LastTagTime": "2026-06-15T16:49:48.66748289Z"
        },
        "Descriptor": {
            "mediaType": "application/vnd.oci.image.index.v1+json",
            "digest": "sha256:f3d28607ddd78734bb7f71f117f3c6706c666b8b76cbff7c9ff6e5718d46ff64",
            "size": 6694
        }
    }
]

docker inspect alpine
====================
[
    {
        "Id": "sha256:a2d49ea686c2adfe3c992e47dc3b5e7fa6e6b5055609400dc2acaeb241c829f4",
        "RepoTags": [
            "alpine:latest"
        ],
        "RepoDigests": [
            "alpine@sha256:a2d49ea686c2adfe3c992e47dc3b5e7fa6e6b5055609400dc2acaeb241c829f4"
        ],
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2026-06-09T20:11:31.67032355Z",
        "Config": {
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh"
            ],
            "WorkingDir": "/"
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 3877603,
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:bc5a3fe779ad9e705b6c5d7fb7a482d1bf8b633e4e3e72152ea3f8953460cda9"
            ]
        },
        "Metadata": {
            "LastTagTime": "2026-06-15T16:49:56.143876831Z"
        },
        "Descriptor": {
            "mediaType": "application/vnd.oci.image.index.v1+json",
            "digest": "sha256:a2d49ea686c2adfe3c992e47dc3b5e7fa6e6b5055609400dc2acaeb241c829f4",
            "size": 9218
        }
    }
]

5. Remove an image you no longer need



docker rmi nginx
docker rmi ubuntu
docker rmi alpine




### Task 2: Image Layers
1. Run `docker image history nginx` — what do you see?

ubuntu@ip-172-31-37-148:~$ docker image history nginx
IMAGE          CREATED      CREATED BY                                      SIZE      COMMENT
608a100c7165   4 days ago   CMD ["nginx" "-g" "daemon off;"]                0B        buildkit.dockerfile.v0
<missing>      4 days ago   STOPSIGNAL SIGQUIT                              0B        buildkit.dockerfile.v0
<missing>      4 days ago   EXPOSE map[80/tcp:{}]                           0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENTRYPOINT ["/docker-entrypoint.sh"]            0B        buildkit.dockerfile.v0
<missing>      4 days ago   COPY 30-tune-worker-processes.sh /docker-ent…   16.4kB    buildkit.dockerfile.v0
<missing>      4 days ago   COPY 20-envsubst-on-templates.sh /docker-ent…   12.3kB    buildkit.dockerfile.v0
<missing>      4 days ago   COPY 15-local-resolvers.envsh /docker-entryp…   12.3kB    buildkit.dockerfile.v0
<missing>      4 days ago   COPY 10-listen-on-ipv6-by-default.sh /docker…   12.3kB    buildkit.dockerfile.v0
<missing>      4 days ago   COPY docker-entrypoint.sh / # buildkit          8.19kB    buildkit.dockerfile.v0
<missing>      4 days ago   RUN /bin/sh -c set -x     && groupadd --syst…   87.1MB    buildkit.dockerfile.v0
<missing>      4 days ago   ENV DYNPKG_RELEASE=1~trixie                     0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENV PKG_RELEASE=1~trixie                        0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENV ACME_VERSION=0.4.1                          0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENV NJS_RELEASE=1~trixie                        0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENV NJS_VERSION=0.9.9                           0B        buildkit.dockerfile.v0
<missing>      4 days ago   ENV NGINX_VERSION=1.31.1                        0B        buildkit.dockerfile.v0
<missing>      4 days ago   LABEL maintainer=NGINX Docker Maintainers <d…   0B        buildkit.dockerfile.v0
<missing>      5 days ago   # debian.sh --arch 'amd64' out/ 'trixie' '@1…   87.4MB    debuerreotype 0.17


2. Each line is a **layer**. Note how some layers show sizes and some show 0B

Layer size > 0B 
================
-> These layer add , remove , or modify files

- these create new filesystem data , so docker shown their size.


Layer size with 0B
================
THese only add metadata or configuration.

these do not create files , so they consume no additional storage.

Docker Layer
============
A docker layer is made up multiple read only layers stacked on top of each other


3. Write in your notes: What are layers and why does Docker use them?


Docker images are built using multple read only layers stacked on the top of each other.

each instruction in a docker file , such as FROM, RUN, COPY, ADD creates a new layer
these layer tpgother from a complete docker images




Why Docker Uses Layers
Faster Builds – Docker reuses unchanged layers from the cache, reducing build time.
Storage Efficiency – Multiple containers can share the same image layers, saving disk space.
Faster Downloads – Docker downloads only the layers that have changed instead of the entire image.
Easy Versioning and Rollbacks – Layers are immutable, making it easy to track changes and revert to previous versions.
Improved Portability – Layered images can be efficiently shared across different environments.


### Task 3: Container Lifecycle
Practice the full lifecycle on one container:
1. **Create** a container (without starting it)
=> docker create --name my-container nginx

=> docker ps -a

CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS                      PORTS                                         NAMES
a8f2565ed640   nginx                  "/docker-entrypoint.…"   11 seconds ago   Created                                                                   mycontainer

2. **Start** the container

=> docker start a8f2565ed640
=> docker start mycontainer


3. **Pause** it and check status
=> docker pause mycontainer

4. **Unpause** it

=> docker unpause mycontainer


5. **Stop** it

docker stop mycontainer

6. **Restart** it

docker restart mycontainer


7. **Kill** it

docker kill 
8. **Remove** it

docker remove mycontainer


Check `docker ps -a` after each step — observe the state changes.

CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS                        PORTS                                         NAMES
a8f2565ed640   nginx                  "/docker-entrypoint.…"   5 minutes ago    Exited (137) 38 seconds ago                                                 mycontainer
e220a512f880   6c112c1e6bc0           "/bin/sh -c 'javac H…"   44 minutes ago   Exited (2) 44 minutes ago                                                   modest_snyder
262769750e45   todo-list              "/__cacert_entrypoin…"   46 minutes ago   Exited (1) 46 minutes ago                                                   inspiring_roentgen
18d593e2040d   632a58b961c0           "/__cacert_entrypoin…"   50 minutes ago   Exited (1) 50 minutes ago                                                   sleepy_shamir
32536eecfb9b   826a037d50f6           "/__cacert_entrypoin…"   50 minutes ago   Exited (1) 50 minutes ago                                                   strange_thompson
87e2c908dfaf   826a037d50f6           "/__cacert_entrypoin…"   51 minutes ago   Exited (1) 51 minutes ago                                                   wizardly_vaughan
f0e11309ad53   23f4a6fe1b28           "/bin/sh -c 'javac /…"   53 minutes ago   Exited (2) 53 minutes ago                                                   vigorous_blackwell
06304573ef3f   5a6020bd1428           "/bin/sh -c 'javac s…"   54 minutes ago   Exited (2) 54 minutes ago                                                   inspiring_cori
938f736b6990   5a6020bd1428           "/bin/sh -c 'javac T…"   55 minutes ago   Exited (2) 55 minutes ago                                                   lucid_allen
889f472adc1e   devops-utilities-api   "python main.py"         2 hours ago      Exited (0) 8 minutes ago                                                    hungry_lovelace
7e1eaa2a85f2   devops-utilities-api   "python main.py"         25 hours ago     Up 25 hours                   0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp   peaceful_leakey


