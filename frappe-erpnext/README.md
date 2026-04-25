# Frappe ERPNext (Dokploy)

This folder contains a Dockerized baseline for running [frappe/erpnext](https://github.com/frappe/erpnext) with Dokploy.

## Files

- `Dockerfile`: Builds an image with the ERPNext app fetched into bench.
- `docker-compose.yml`: Starts MariaDB, Redis services, and a Frappe ERPNext app service.
- `.env.example`: Environment variables you should copy to `.env`.

## Usage

1. Copy env file:
   ```bash
   cp .env.example .env
   ```
2. Adjust values in `.env`.
3. Deploy with Dokploy using this folder as the source.

## Notes

- On first boot, the `erpnext` service creates the site and installs the `erpnext` app.
- Persistent data is stored in Docker volumes: `db-data`, `sites`, and `logs`.
- This stack is a practical baseline; for high-traffic production you will usually split workers/websocket/frontend into dedicated services.
