FROM hypriot/rpi-java:1.7.0-jdk
ADD proxy /etc/apt/apt.conf.d/proxy
RUN apt-get update -qq && apt-get install -y maven && apt-get clean

WORKDIR /code
ADD settings.xml /root/.m2/
ADD pom.xml /code/pom.xml
RUN ["mvn", "dependency:resolve"]
RUN ["mvn", "verify"]

# Adding source, compile and package into a fat jar
ADD src /code/src
RUN ["mvn", "package"]

CMD ["java", "-jar", "target/worker-jar-with-dependencies.jar"]
