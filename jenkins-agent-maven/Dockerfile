FROM jenkins/inbound-agent as agent

FROM maven:3.9.16-amazoncorretto-21

RUN yum update && \
    yum install -y \
    git \
    libfontconfig1 \
    libfreetype6

COPY --from=agent /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=agent /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
