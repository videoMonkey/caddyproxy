# Caddy Reverse Proxy with Docker and Cloudflare

There is no port-forwarding needed. This server can sit isolated on your home network and serve up locally hosted webpages with valid ssl certs.

Any docker containers on the 'caddyproy' network can be referenced by service name and default port as indicated in the Caddyfile.

## Setup

1. Clone this repo
2. In your cloudflare dashboard create a token that has Zone->DNS->Edit permissions.
3. you need to make sure that you have a DNS entry for your proxied services pointint to the server where docker is running. 
3. make a `.env` file at the same level as the docker-compose.yml file with the two environment variables listed in the docker-compose.yml file
4. Edit the Caddyfile to reflect the hosts and reverse proxies you want
5. Run `docker-compose up -d` it's going to complain either about not having created a network or a volume, follow the instructions docker gives you to resolve the problem.
6. Run `docker-compose up -d` again and do the same thing as step four
7. Run `docker-compose up -d` one last time and this time everything so go ok
8. Getting the certs will take 30 seconds or less, you can use the `docker container logs` command from below to check if it was successful.

I think that is all. 

## Commands I find useful

rebuild the container with dockerfile, docker-compose.yml changes
`sudo docker-compose up -d --no-deps --build`

stop the container to rebuild it
`sudo docker-compose down`

how to reload your caddyfile without any other changes
`sudo docker exec -tw /etc/caddy caddyserver_caddy_1 caddy reload`

validate your caddyfile
`sudo docker exec -tw /etc/caddy caddyserver_caddy_1 caddy validate`

see caddyfile formatting changes suggestions
`sudo docker exec -tw /etc/caddy caddyserver_caddy_1 caddy fmt`

see container logs
`sudo docker container logs caddyserver_caddy_1`
