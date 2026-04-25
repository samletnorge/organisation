FROM frappe/erpnext:v15.58.2

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG PRESS_REPO=https://github.com/frappe/press
ARG PRESS_BRANCH=master

# Fetch Press manually to bypass bench's yarn install step.
# bench get-app runs yarn install unconditionally; press dev deps require Node >=20
# but the base image ships Node 18. Cloning + pip-installing directly skips yarn.
RUN git clone --depth 1 --branch "${PRESS_BRANCH}" "${PRESS_REPO}" apps/press \
    && env/bin/pip install --quiet -e apps/press \
    && printf 'frappe\nerpnext\npress\n' > sites/apps.txt \
    && bench setup procfile \
    && sed -i '/^redis/d' Procfile
