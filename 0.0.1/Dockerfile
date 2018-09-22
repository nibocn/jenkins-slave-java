FROM nibo/jenkins-slave:0.0.1
MAINTAINER Richard <nibocn@gmail.com>


ARG MAVEN_VERSION=3.5.4
ARG GRADLE_VERSION=4.10.2

RUN \
    # Install tools
    apk add --no-cache --update-cache curl unzip git \
        \
    # Install Maven
    && mkdir -p /opt/maven \
    && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
       | tar -xzC /opt/maven --strip-components=1 \
    && ln -s /opt/maven/bin/mvn /usr/bin/mvn \
        \
    # Install Gradle
    && cd /opt \
    && curl -OL https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
    && unzip gradle-${GRADLE_VERSION}-bin.zip \
    && ln -s /opt/gradle* /opt/gradle \
    && ln -s /opt/gradle/bin/gradle /usr/bin/gradle \
        \
    # Clean resource
    && apk del curl unzip \
    && rm -rf /tmp/* \
    && rm -rf /var/cache/apk/* \
    && rm -rf /opt/gradle-${GRADLE_VERSION}-bin.zip

VOLUME /root/.gradle
VOLUME /root/.m2

ENV MAVEN_HOME /opt/maven
ENV GRADLE_HOME /opt/gradle
ENV PATH $MAVEN_HOME/bin:$GRADLE_HOME/bin:$PATH
