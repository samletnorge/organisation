FROM frappe/erpnext:v15.58.2

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG ERPNEXT_REPO=https://github.com/frappe/erpnext
ARG ERPNEXT_BRANCH=version-15

# Fetch the ERPNext app into the bench so it can be installed into a site.
RUN bench get-app --branch "${ERPNEXT_BRANCH}" erpnext "${ERPNEXT_REPO}"
