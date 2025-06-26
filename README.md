## Description
I used this docker-compose to run n8n on a rented cloud server.
The beauty of it is that it shows how to use ./local-files folder in
the project's root as a way to give n8n access to local files.

Also, if you run it on coolify which manages the ssl certificates for you,
then you don't need traeffik set up.

I'll also list some useful information about using qdrant and postgres
from n8n docker service:
1. as they are on the same docker network here, we can access them
  using the next path pattern: `http://<docker_service_name>:<its port>
2. or just use the public domain name, if you have one setup and secured

## Usage
You probably won't use this compose file and repo, however there is 
a chance that writing this down will help you avoid repeating your
configurations from scratch. To set it all up, all you need is to
run the following commands:

```bash
# 1. todo: modify variables to store your data
cp .env.example .env

# 2. todo: ensure that ports for traeffik 443 and 80 are free,
#   and that your dns is bound to the ip where you start the docker compose file
docker-compose up -d
```

## Workflow
To start and stop use:

```bash
docker-compose down
docker-compose up
```

If you make some changes, then add -d option. It doesn't seem to delete any persistent
storage, but you can perform backups if you want:

```bash
docker-compose up -d
```

