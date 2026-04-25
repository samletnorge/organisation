FROM frappe/erpnext:v15.58.2

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG PRESS_REPO=https://github.com/frappe/press
ARG PRESS_BRANCH=master

# Fetch the Press app into the bench for site setup and management.
# --skip-assets avoids the yarn/node build step (requires Node >=20, base has 18).
# Assets are built when the app is installed into a site at runtime.
RUN bench get-app --branch "${PRESS_BRANCH}" --skip-assets press "${PRESS_REPO}"
