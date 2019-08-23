FROM ysslang/finedocker:ubuntu18.04_jdk8_tomcat8.5

ARG FINEBI_MAJOR=5.1.0
ARG FINEBI_VERSION=20190403
ARG RELEASE_TAG=v0.1
ARG FINEBI_URL=https://github.com/ysslang/FineDocker/releases/download/v0.1/FineBI_"$FINEBI_MAJOR"_webroot_x86_64_"$FINEBI_VERSION".tar.gz

WORKDIR $CATALINA_HOME

RUN set -eux; \
    cd webapps; \
    wget -O finebi.tar.gz "$FINEBI_URL"; \
    tar -xvf finebi.tar.gz; \
    rm finebi.tar.gz*; \
    cd ..

CMD ["catalina.sh", "run"]
