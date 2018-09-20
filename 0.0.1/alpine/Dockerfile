FROM nibo/jenkins-slave:0.0.1-alpine
MAINTAINER Richard <nibocn@gmail.com>


ARG MAVEN_VERSION=3.5.4

RUN \
    # Install tools
    apk add --no-cache --update-cache curl \

    # Install Maven
    && mkdir -p /opt/maven \
    && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
       | tar -xzC /opt/maven --strip-components=1 \
    && ln -s /opt/maven/bin/mvn /usr/bin/mvn \

    # Clean resource
    && apk del curl \
    && rm -rf /var/cache/apk/*


ENV MAVEN_HOME /opt/maven
ENV PATH $MAVEN_HOME/bin:$PATH
# End

