FROM node:14

# Install basic development tools
RUN apt update && apt install -y less man-db sudo
# install java
RUN sudo apt install -y default-jdk unzip

# install tinkerpop gremlin console in /workspaces/tinkerpop-cmd
WORKDIR /workspaces
RUN sudo chmod 777 -R /workspaces/ && mkdir tinkerpop-cmd
RUN sudo wget https://dlcdn.apache.org/tinkerpop/3.6.4/apache-tinkerpop-gremlin-console-3.6.4-bin.zip
RUN sudo unzip apache-tinkerpop-gremlin-console-3.6.4-bin.zip
RUN sudo mv apache-tinkerpop-gremlin-console-3.6.4/* tinkerpop-cmd/ 
RUN sudo rmdir apache-tinkerpop-gremlin-console-3.6.4
    
# Ensure default `node` user has access to `sudo`
ARG USERNAME=node
RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Set `DEVCONTAINER` environment variable to help with orientation
ENV DEVCONTAINER=true
