FROM frappe/erpnext:v16.15.1

USER frappe
WORKDIR /home/frappe/frappe-bench

ARG PRESS_REPO=https://github.com/frappe/press
ARG PRESS_BRANCH=master

ARG LMS_REPO=https://github.com/frappe/lms
ARG LMS_BRANCH=v2.52.1

# Fetch apps manually to bypass bench's yarn install step (Node 18 in base, apps need >=20).
RUN git clone --depth 1 --branch "${PRESS_BRANCH}" "${PRESS_REPO}" apps/press \
    && env/bin/pip install --quiet -e apps/press \
    && git clone --depth 1 --branch "${LMS_BRANCH}" "${LMS_REPO}" apps/lms \
    && env/bin/pip install --quiet -e apps/lms \
    && printf 'frappe\nerpnext\npress\nlms\n' > sites/apps.txt \
    && bench setup procfile \
    && sed -i '/^redis/d; /^watch/d' Procfile
