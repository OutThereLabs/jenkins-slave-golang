FROM openshift/jenkins-slave-base-centos7

MAINTAINER Julian Tescher <julian@outtherelabs.com>

ENV GOLANG_VERSION=1.8 \
    PATH=$PATH:/opt/rh/go-toolset-7/root/usr/share/gocode/bin \
    BASH_ENV=/usr/local/bin/scl_enable \
    ENV=/usr/local/bin/scl_enable \
    PROMPT_COMMAND=". /usr/local/bin/scl_enable"

COPY contrib/bin/scl_enable /usr/local/bin/scl_enable

RUN yum install -y centos-release-scl-rh && \
    yum-config-manager --enable centos-sclo-rh-testing && \
    INSTALL_PKGS="go-toolset-7" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

RUN chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME && \
    chown -R 1001:0 /opt/rh/go-toolset-7/root/usr/share/gocode && \
    chmod -R g+rw /opt/rh/go-toolset-7/root/usr/share/gocode

USER 1001
