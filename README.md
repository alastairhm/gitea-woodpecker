# Gitea-woodpecker

Running gitea and woodpecker ci locally

Bassed off blog post https://blog.pnp3.com/ci-cd-in-docker-with-gitea-and-woodpecker-ci/ setup to build Docker images.


## Usage

Create `.env` file with your secrets.

```
IP_ADDRESS=<IP ADDRESS>
WOODPECKER_GITEA_CLIENT=<CLIENT ID>
WOODPECKER_GITEA_SECRET=<CLIENT SECRET>
WOODPECKER_AGENT_SECRET=<AGENT SECRET>
```

Run Docker compose

```bash
docker-compose --env-file .env up -d
```
