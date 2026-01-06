# Gitea-woodpecker

Running gitea and woodpecker ci locally

Bassed off blog post https://blog.pnp3.com/ci-cd-in-docker-with-gitea-and-woodpecker-ci/ setup to build Docker images.


## Usage & Setup

## Storage

Create data directories

```bash
sudo mkdir -p /<path_do_data_dir>/docker/volumes/gitea
sudo chown -R 1000:1000 /<path_do_data_dir>/docker/volumes/gitea
```

## Secrets

Create `.env` file with your secrets.

```
IP_ADDRESS=<IP ADDRESS>
WOODPECKER_GITEA_CLIENT=<CLIENT ID>
WOODPECKER_GITEA_SECRET=<CLIENT SECRET>
WOODPECKER_AGENT_SECRET=<AGENT SECRET>
```

## Running

Run Docker compose

```bash
docker-compose --env-file .env up -d
```

## Gitea Prep

Setup Woodpecker access to Gitea, create a new OAuth2 Application

```
Name:  Woodpecker CI
Redirect URI:  http://<ip_address>:8888/authorize
```
Copy the Client ID and Secret into your `.env` file and random string for the agent secret.

Edit Gitea app config in `/<path_to_data_dir>/docker/volumes/gitea/gitea/conf` add this section at the end.

```
[webhook]
ALLOWED_HOST_LIST = external,loopback
```

Then restart

```bash
docker-compose down
docker-compose --env-file .env up -d
```
