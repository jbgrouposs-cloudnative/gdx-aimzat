FROM kong:0.14.1

ARG DB_TYPE="postgres"
ARG DB_NAME="kong-database"
ARG PROXY_PORT="8080"
ARG PROXY_PORT_SSL="8443"
ARG ADMIN_PORT="50080"
ARG ADMIN_PORT_SSL="50443"

ENV KONG_DATABASE ${DB_TYPE}
ENV KONG_PG_HOST ${DB_NAME}
ENV KONG_CASSANDRA_CONTACT_POINTS ${DB_NAME}

ENV KONG_PROXY_ACCESS_LOG /dev/stdout
ENV KONG_ADMIN_ACCESS_LOG /dev/stdout
ENV KONG_PROXY_ERROR_LOG /dev/stderr
ENV KONG_ADMIN_ERROR_LOG /dev/stderr

ENV KONG_PROXY_LISTEN "0.0.0.0:${PROXY_PORT}, 0.0.0.0:${PROXY_PORT_SSL} ssl"
ENV KONG_ADMIN_LISTEN "0.0.0.0:${ADMIN_PORT}, 0.0.0.0:${ADMIN_PORT_SSL} ssl"

EXPOSE ${PROXY_PORT}
EXPOSE ${PROXY_PORT_SSL}
EXPOSE ${ADMIN_PORT}
EXPOSE ${ADMIN_PORT_SSL}

CMD ["kong", "start", "--run-migrations"]