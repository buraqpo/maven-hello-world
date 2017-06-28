# Dockerfile based on the latest CentOS 7 image - non-privileged user entry
# this will be merged from master
FROM java

ENV MAVEN_VERSION 3.3.9

RUN mkdir -p /usr/share/maven \
  && curl -fsSL http://apache.osuosl.org/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
    | tar -xzC /usr/share/maven --strip-components=1 \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven


ADD /src /hello/src
ADD /pom.xml /hello/pom.xml

WORKDIR hello

RUN mvn compile

CMD java -cp target/classes com.mycompany.app.App

