## Exam details
# Site
- http://vcsa7.vua.cloud/
- username: `infoeduka_name`
- password: `Pa$$w0rd`

# VM
- username: `student`
- password `student`
- root user: `root`
- password: `centos`

## Mysql root user

- username: `root`
- password: `secret`

## Which ports are exposed to host machine?

- Nginx is running on port `80` & `81`
- Mysql is running on port `3306`

## Which versions of services does docker compose use?

- Mysql version is `5.7.42`
- Nginx version is `1.25`
- PHP version is `7.4`

## Can I add my own initialization script for mysql?

Yes, you can change existing one `- ./algebra.sql:/docker-entrypoint-initdb.d/1.sql` or add another one `- ./new.sql:/docker-entrypoint-initdb.d/2.sql`

- Notice the number `1`, this means this script or dump will execute first
- All dumps and scripts in `docker-entrypoint-initdb.d` will run only once, on container creation

## Lab2

### pull, inspect, start, stop, save, inport, list all
  - porman pull nginx:latest
  - podman image incpect nginx
  - podman run -d -p 8080:80 --name web8080 nginx
  - podman stop web8080
  - podman image save -o web8080.tar docker.io/library/nginx:latest
  - porman load -i web8080.tar
  - podman ps -a

### modify
  - podman run -it --name mymodifiedcontainer ubuntu /bin/bash
  -   apt update && apt install -y nginx
  -   exit
  - podman commit mymodifiedcontainer mynewimage
  - podman run -d --name newcontainer mynewimage

### change running and inspect
  - podman exec web8080 sh -c 'echo "Hello, this is the new content!" > /usr/share/nginx/html/index.html'
  - curl http://localhost:8080

## Lab3

###
  - https://docs.docker.com/get-started/02_our_app/
  - git clone https://github.com/docker/getting-started-app.git
  - VIM
    - cat 'filename' print content
    - vim 'filename'
    - i  -edit file
    - :wq  -save and exit
  - podman build -t getting-started .
  - podman run -dp 127.0.0.1:3000:3000 getting-started
  - podman push lskvorc/getting-started

### Startup app
  - Containerfile
    - FROM rhel7
    - RUN yum -y update && yum clean all
    - RUN yum -y install httpd && yum clean all
    - CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
    - EXPOSE 80
  - podman build -t myweb:0.0.1 .

## Lab4
  - podman network create labnet
  - podman network ls
  - podman network inspect labnet
  - podman-compose.yml  -file
  - sudo dnf install podman-compose
  - podman-compose up
  - podman-compose down

run on start
  -https://www.redhat.com/sysadmin/quadlet-podman

## RH Lab 1

  - oc login -u developer -p developer https://api.ocp4.example.com:6443
  - oc whoami --show-console
  - username/password: developer
  - username/password: admin/redhatocp

### lara

https://github.com/KrzakLara/DocumentationForDevOps2
https://github.com/KrzakLara/DocumentationForDevOps
