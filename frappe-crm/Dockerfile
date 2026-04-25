FROM frappe/erpnext:v15.58.2

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG CRM_REPO=https://github.com/frappe/crm
ARG CRM_BRANCH=main

# Fetch the CRM app into the bench so it can be installed into a site.
RUN bench get-app --branch "${CRM_BRANCH}" crm "${CRM_REPO}"
