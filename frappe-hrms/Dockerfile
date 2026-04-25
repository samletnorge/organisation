FROM frappe/erpnext:v15.58.2

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG HRMS_REPO=https://github.com/frappe/hrms
ARG HRMS_BRANCH=version-15

# Fetch the HRMS app into the bench so it can be installed into a site.
RUN bench get-app --branch "${HRMS_BRANCH}" hrms "${HRMS_REPO}"
