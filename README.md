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
