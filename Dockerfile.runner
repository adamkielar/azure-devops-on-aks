FROM ubuntu:22.04
USER root
RUN apt-get -y update && apt-get install -y curl && \
    curl -sL https://aka.ms/InstallAzureCLIDeb | bash && az aks install-cli && \
    curl -fsSL https://get.docker.com -o get-docker.sh && sh ./get-docker.sh && \
    mkdir devops-runner && cd devops-runner && \
    curl -o vsts-agent-linux-x64-3.217.1.tar.gz -L https://vstsagentpackage.azureedge.net/agent/3.217.1/vsts-agent-linux-x64-3.217.1.tar.gz && \
    tar xzf ./vsts-agent-linux-x64-3.217.1.tar.gz && \
    apt-get clean

RUN addgroup --gid 110 devops && adduser devops --uid 111 --system && adduser devops devops && \
  chown -R devops:devops devops-runner

USER devops