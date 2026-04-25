# Frappe Press (Frappe Cloud)

This folder contains a Dockerized baseline for running [frappe/press](https://github.com/frappe/press) with Dokploy.

Press is the open-source self-hosted platform for deploying and managing Frappe applications across multiple sites. It's the foundation of frappe.cloud.

## Files

- `Dockerfile`: Builds an image with the Press app fetched into bench.
- `docker-compose.yml`: Starts MariaDB, Redis services, and a Press app service.
- `.env.example`: Environment variables you should copy to `.env`.

## Usage

1. Copy env file:
   ```bash
   cp .env.example .env
   ```
2. Adjust values in `.env` (especially DB_ROOT_PASSWORD and ADMIN_PASSWORD).
3. Deploy with Dokploy using this folder as the source.

## Notes

- On first boot, the `press` service creates the site and installs the `press` app.
- Persistent data is stored in Docker volumes: `db-data`, `sites`, and `logs`.
- Press listens on port 9000 by default (configurable via APP_PORT env var).
- From Press, you can then provision sites for the other Frappe apps (LMS, CRM, HRMS, etc.).

## Related Apps

Once Press is running, you can use it to provision and manage:
- frappe-lms
- frappe-crm
- frappe-erpnext
- frappe-helpdesk
- frappe-hrms
# Frappe Press (Frappe Cloud)

This folder contains a Dockerized baseline for running [frappe/press](https://github.com/frappe/press) with Dokploy.

Press is the open-source self-hosted platform for deploying and managing Frappe applications across multiple sites. It's the foundation of frappe.cloud.

## Files

- `Dockerfile`: Builds an image with the Press app fetched into bench.
- `docker-compose.yml`: Starts MariaDB, Redis services, and a Press app service.
- `.env.example`: Environment variables you should copy to `.env`.

## Usage

1. Copy env file:
   ```bash
   cp .env.example .env
   ```
2. Adjust values in `.env` (especially DB_ROOT_PASSWORD and ADMIN_PASSWORD).
3. Deploy with Dokploy using this folder as the source.

## Notes

- On first boot, the `press` service creates the site and installs the `press` app.
- Persistent data is stored in Docker volumes: `db-data`, `sites`, and `logs`.
- Press listens on port 9000 by default (configurable via APP_PORT env var).
- From Press, you can then provision sites for the other Frappe apps (LMS, CRM, HRMS, etc.).

## Related Apps

Once Press is running, you can use it to provision and manage:
- frappe-lms
- frappe-crm
- frappe-erpnext
- frappe-helpdesk
- frappe-hrms
