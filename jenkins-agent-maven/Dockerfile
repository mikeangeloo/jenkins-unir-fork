FROM jenkins/inbound-agent as agent

FROM maven:3.8.4-openjdk-17-slim

RUN apt-get update && \
    apt-get install -y \
    git \
    libfontconfig1 \
    libfreetype6 \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

COPY --from=agent /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=agent /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]