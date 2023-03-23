FROM tuanonehour/workspace:1.2

# Add autocompletion for commandline
RUN apt-get install -y bash-completion
RUN echo 'source /usr/share/bash-completion/bash_completion' >>/root/.bashrc

RUN kubectl completion bash | tee /etc/bash_completion.d/kubectl > /dev/null

RUN kind completion bash | tee /etc/bash_completion.d/kind > /dev/null

RUN skaffold completion bash | tee /etc/bash_completion.d/skaffold > /dev/null

# Install nvm
RUN wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
ENV NVM_DIR /root/.nvm
ENV NODE_VERSION v16
RUN /bin/bash -c "source $NVM_DIR/nvm.sh && nvm install $NODE_VERSION && nvm use $NODE_VERSION"
ENV NODE_PATH $NVM_DIR/versions/node/$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/versions/node/$NODE_VERSION/bin:$PATH

RUN echo 'export PATH=/usr/local/bin/aws_completer:$PATH' >>/root/.bashrc
RUN /bin/bash -c "source /root/.bashrc && complete -C '/usr/local/bin/aws_completer' aws"
