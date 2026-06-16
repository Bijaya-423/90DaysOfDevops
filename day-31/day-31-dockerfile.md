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




