FROM frappe/erpnext:v16.15.1

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc g++ python3-dev \
    && rm -rf /var/lib/apt/lists/*

USER frappe
WORKDIR /home/frappe/frappe-bench

# Pre-install C-extension packages that require gcc before the main app installs.
RUN env/bin/pip install --quiet greenlet ruamel.yaml.clib

ARG PRESS_REPO=https://github.com/frappe/press
ARG PRESS_BRANCH=master

ARG LMS_REPO=https://github.com/frappe/lms
ARG LMS_BRANCH=v2.52.1

# Fetch apps manually to bypass bench's yarn install step (Node 18 in base, apps need >=20).
# Patch playwright pin: press pins playwright==1.49.1 which requires greenlet==3.1.1 (no Python 3.14 wheel).
# playwright>=1.50.0 relaxes to greenlet>=3.1.1,<4.0.0 which resolves to the available cp314 wheel.
RUN git clone --depth 1 --branch "${PRESS_BRANCH}" "${PRESS_REPO}" apps/press \
    && sed -i 's/"playwright==1.49.1"/"playwright>=1.50.0"/' apps/press/pyproject.toml \
    && env/bin/pip install --quiet -e apps/press \
    && git clone --depth 1 --branch "${LMS_BRANCH}" "${LMS_REPO}" apps/lms \
    && env/bin/pip install --quiet -e apps/lms \
    && printf 'frappe\nerpnext\npress\nlms\n' > sites/apps.txt \
    && bench setup procfile \
    && sed -i '/^redis/d; /^watch/d' Procfile

    