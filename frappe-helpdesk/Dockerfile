FROM frappe/erpnext:v15.58.2

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG HELPDESK_REPO=https://github.com/frappe/helpdesk
ARG HELPDESK_BRANCH=main

# Fetch the Helpdesk app into the bench so it can be installed into a site.
RUN bench get-app --branch "${HELPDESK_BRANCH}" helpdesk "${HELPDESK_REPO}"
