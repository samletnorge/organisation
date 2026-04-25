FROM frappe/erpnext:v15.58.2

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       git \
       curl \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG PRESS_REPO=https://github.com/frappe/press
ARG PRESS_BRANCH=main

# Fetch the Press app into the bench for site setup and management.
RUN bench get-app --branch "${PRESS_BRANCH}" press "${PRESS_REPO}"
