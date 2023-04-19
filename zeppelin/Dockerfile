FROM apache/zeppelin:0.10.0

ENV ZEPPELIN_NOTEBOOK_DIR /notebooks
ENV ZEPPELIN_INTERPRETER_DEP_MVNREPO https://repo1.maven.org/maven2/
ENV ZEPPELIN_ADDR 0.0.0.0
ENV SPARK_HOME /opt/bitnami/spark

ENV LD_PRELOAD=/usr/lib/libnss_wrapper.so

USER root

# Create the notebooks directory with proper permissions
RUN mkdir -p ${ZEPPELIN_NOTEBOOK_DIR}
RUN chown -R 1000:1000 ${ZEPPELIN_NOTEBOOK_DIR}
RUN chmod -R 755 ${ZEPPELIN_NOTEBOOK_DIR}

# Import GPG keys
RUN apt-get update \
    && apt-get install -y --no-install-recommends gnupg \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 648ACFD622F3D138 0E98404D386FA1D9 DCC9EFBF77E11517 112695A0E562B32A 54404762BBB6E853 \
    && apt-get clean

# Add the Debian Buster repositories
RUN echo "deb http://deb.debian.org/debian buster main" >> /etc/apt/sources.list \
    && echo "deb http://deb.debian.org/debian buster-updates main" >> /etc/apt/sources.list \
    && echo "deb http://security.debian.org/debian-security buster/updates main" >> /etc/apt/sources.list

# Update package lists
RUN apt-get update

# Install gnupg and import GPG keys
RUN apt-get install -y --no-install-recommends gnupg \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 648ACFD622F3D138 0E98404D386FA1D9 DCC9EFBF77E11517 112695A0E562B32A 54404762BBB6E853 \
    && apt-get clean


# Install libnss-wrapper
RUN apt-get install -y libnss-wrapper
RUN rm -rf /var/lib/apt/lists/*

COPY zeppelin-env.sh /zeppelin/conf/zeppelin-env.sh

USER 1000



