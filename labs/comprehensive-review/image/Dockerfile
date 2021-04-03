FROM	ubi7/ubi:7.7

MAINTAINER ccaswara username@mail.com

ARG	NEXUS_VERSION=2.14.3-02 

ENV	NEXUS_HOME=/opt/nexus

RUN	yum install -y java-1.8.0-openjdk-devel && \
	yum clean all -y

RUN	groupadd -r -f -g 1001 nexus && \
	useradd -r -g 1001 nexus -m -d ${NEXUS_HOME} && \ 
	chown -R nexus:nexus ${NEXUS_HOME} && chmod -R 755 ${NEXUS_HOME}
USER	nexus

ADD	nexus-2.14.3-02-bundle.tar.gz ${NEXUS_HOME}/ 

ADD	nexus-start.sh	${NEXUS_HOME}/

RUN	ln -s ${NEXUS_HOME}/nexus-${NEXUS_VERSION} ${NEXUS_HOME}/nexus2 

WORKDIR	${NEXUS_HOME}

VOLUME	["/opt/nexus/sonatype-work"]

ENTRYPOINT	["/bin/bash", "nexus-start.sh"]

