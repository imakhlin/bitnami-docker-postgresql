FROM bitnami/minideb-extras:stretch-r259
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages libbsd0 libc6 libedit2 libgcc1 libicu57 liblzma5 libncurses5 libnss-wrapper libssl1.1 libstdc++6 libtinfo5 libxml2 libxslt1.1 zlib1g
RUN bitnami-pkg unpack postgresql-10.6.0-28 --checksum 9f4147a9326e351e9889004ba9813f9a6b98c890745f8839449ecef3c4952fef
RUN echo 'en_GB.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen
RUN echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen
RUN mkdir /docker-entrypoint-initdb.d /opt/bitnami/postgresql/conf/
RUN chmod -R g+rwX /opt/bitnami/postgresql/conf/

COPY rootfs /
ENV BITNAMI_APP_NAME="postgresql" \
    BITNAMI_IMAGE_VERSION="10.6.0-debian-9-r66" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/postgresql/bin:$PATH" \
    POSTGRESQL_CLUSTER_APP_NAME="walreceiver" \
    POSTGRESQL_DATABASE="" \
    POSTGRESQL_MASTER_HOST="" \
    POSTGRESQL_MASTER_PORT_NUMBER="5432" \
    POSTGRESQL_NUM_SYNCHRONOUS_REPLICAS="0" \
    POSTGRESQL_PASSWORD="" \
    POSTGRESQL_PORT_NUMBER="5432" \
    POSTGRESQL_REPLICATION_MODE="master" \
    POSTGRESQL_REPLICATION_PASSWORD="" \
    POSTGRESQL_REPLICATION_USER="" \
    POSTGRESQL_SYNCHRONOUS_COMMIT_MODE="on" \
    POSTGRESQL_USERNAME="postgres"

EXPOSE 5432

USER 1001
ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "/run.sh" ]
