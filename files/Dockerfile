ARG PYTHON_VER=3.9
ARG NAUTOBOT_VERSION=1.3.6
FROM networktocode/nautobot:${NAUTOBOT_VERSION}-py${PYTHON_VER} as base

# NOTE:
# as of 1.2.1 and due to https://github.com/nautobot/nautobot/issues/1068 -
# - NTC made changes to embed deps e.g. LDAP
# - building in django-auth-ldap ought to be unnecessary
# - building in libldap2-dev libsasl2-dev libssl-dev libxml2-dev ought to be unnecessary
# - we do still need custom builds for shell utils and plugins
# .. consider trimming libs and LDAP next time


USER 0
RUN apt-get update -y && \
    apt-get install -y findutils grep vim-tiny

# ---------------------------------
# Stage: Builder
# ---------------------------------
FROM base as builder
LABEL stage=builder
# use LABEL for trimming junk images
#   docker image prune --filter label=stage=builder

RUN apt-get install -y gcc && \
    apt-get autoremove -y && \
    apt-get clean all && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip wheel && \
    pip3 install django-auth-ldap nautobot_plugin_nornir nautobot-golden-config nautobot-device-onboarding nautobot-netbox-importer nautobot_ssot nautobot_ssot_vsphere

# ---------------------------------
# Stage: Final
# ---------------------------------
FROM base as final
ARG PYTHON_VER
USER 0

COPY --from=builder /usr/local/lib/python${PYTHON_VER}/site-packages /usr/local/lib/python${PYTHON_VER}/site-packages
COPY --from=builder /usr/local/bin /usr/local/bin
USER nautobot

WORKDIR /opt/nautobot
