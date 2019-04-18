FROM ysslang/finedocker:ubuntu18.04_jdk8_tomcat8.5

WORKDIR $CATALINA_HOME

ENV FINEREPORT_MAJOR 10.0.0
ENV FINEREPORT_VERSION persist_20190306
ENV FINEREPORT_URL https://github.com/ysslang/FineDocker/releases/download/v0.1/FineReport_"$FINEREPORT_MAJOR"_webroot_x86_64_"$FINEREPORT_VERSION".tar.gz

RUN set -eux; \
    cd webapps; \
    wget -O finereport.tar.gz "$FINEREPORT_URL"; \
    tar -xvf finereport.tar.gz; \
    rm finereport.tar.gz*; \
    cd ..

CMD ["catalina.sh", "run"]
