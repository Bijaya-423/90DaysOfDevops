### Task 1: Your First Dockerfile
1. Create a folder called `my-first-image`
2. Inside it, create a `Dockerfile` that:
   - Uses `ubuntu` as the base image
   - Installs `curl`
   - Sets a default command to print `"Hello from my custom image!"`
3. Build the image and tag it `my-ubuntu:v1`
4. Run a container from your image

**Verify:** The message prints on `docker run`


FROM ubuntu:latest

RUN apt-get update && \
    apt-get install -y curl && \
    apt-get clean

CMD ["echo", "Hello from my custom image!"]


docker build -t my-ubuntu:v1 .

docker run my-ubuntu:v1

docker images

docker inspect my-ubuntu:v1

docker logs 00ebbbe545dc


### Task 2: Dockerfile Instructions
Create a new Dockerfile that uses **all** of these instructions:
- `FROM` — base image
- `RUN` — execute commands during build
- `COPY` — copy files from host to image
- `WORKDIR` — set working directory
- `EXPOSE` — document the port
- `CMD` — default command

Build and run it. Understand what each line does.
=============================================
FROM python:3.14

WORKDIR /app

COPY requirements.txt .

RUN pip install  -r requirements.txt

COPY . .

CMD ["python", "qrGenerator.py"]





### Task 3: CMD vs ENTRYPOINT
1. Create an image with `CMD ["echo", "hello"]` — run it, then run it with a custom command. What happens?

FROM ubuntu:latest

CMD ["echo", "Hello"]


docker build -t cmd-demo .
docer run cmd-demo
docker ps
docker inspect cmd-demo


2. Create an image with `ENTRYPOINT ["echo"]` — run it, then run it with additional arguments. What happens?


FROM ubuntu:latest

ENTRYPOINT ["echo"]

docker build -f Dockerfile.entrypoint -t entrypoint-demo .
docker run entrypoint-demo
docker ps
docker inspect entrypoint-demo


3. Write in your notes: When would you use CMD vs ENTRYPOINT?

CMD
===
provides a default command
can be overridden at run time
flexible for different command

CMD ["python"m "app.py"]


ENTRYPOINT
==========
provides a fixed executable
arguments are appended to it
best for single -purpose containers

ENTRYPOINT ["nginx"]


### Task 4: Build a Simple Web App Image
1. Create a small static HTML file (`index.html`) with any content
2. Write a Dockerfile that:
   - Uses `nginx:alpine` as base
   - Copies your `index.html` to the Nginx web directory
3. Build and tag it `my-website:v1`
4. Run it with port mapping and access it in your browser







create a index.html and write the html static page code

then write the Dockerfile.nginx


FROM nginx:alpine

COPY index.html /usr/share/nginx/html/

EXPOSE 80


then
docker build -f Dockerfile.nginx -t my-website .
docker run -d -p 8001:80 --name website-container my-website

docker ps
docker images
docker logs my-website
docker inspect my-website



### Task 5: .dockerignore
1. Create a `.dockerignore` file in one of your project folders
2. Add entries for: `node_modules`, `.git`, `*.md`, `.env`
3. Build the image — verify that ignored files are not included

---

### Task 6: Build Optimization
1. Build an image, then change one line and rebuild — notice how Docker uses **cache**
2. Reorder your Dockerfile so that frequently changing lines come **last**
3. Write in your notes: Why does layer order matter for build speed?




















