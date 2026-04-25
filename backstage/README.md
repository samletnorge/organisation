# Backstage (Dokploy)

This folder contains a Dockerized baseline for running [backstage/backstage](https://github.com/backstage/backstage) with Dokploy.

## Files

- `Dockerfile`: Builds and runs a production Backstage backend + frontend bundle.
- `docker-compose.yml`: Starts PostgreSQL and a Backstage service.
- `.env.example`: Environment variables you should copy to `.env`.

## Usage

1. Copy env file:
   ```bash
   cp .env.example .env
   ```
2. Update `.env` values, especially:
   - `APP_BASE_URL`
   - `BACKEND_BASE_URL`
   - `POSTGRES_PASSWORD`
3. Deploy with Dokploy using this folder as the source.

## Notes

- This compose setup exposes Backstage on `APP_PORT` (default `7007`).
- In Dokploy behind a domain, set both `APP_BASE_URL` and `BACKEND_BASE_URL` to your HTTPS URL.
- PostgreSQL data is persisted in the `postgres-data` Docker volume.
