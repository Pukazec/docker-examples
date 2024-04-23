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
