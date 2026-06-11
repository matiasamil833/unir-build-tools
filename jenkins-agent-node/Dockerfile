FROM jenkins/inbound-agent:latest AS agent

FROM node:20-alpine3.20

RUN apk add --no-cache openjdk17-jre-headless git make

COPY --from=agent /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=agent /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]