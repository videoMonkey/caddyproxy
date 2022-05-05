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
