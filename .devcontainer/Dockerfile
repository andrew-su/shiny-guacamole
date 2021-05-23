# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.177.0/containers/go/.devcontainer/base.Dockerfile

# [Choice] Go version: 1, 1.16, 1.15
ARG VARIANT="1"
FROM mcr.microsoft.com/vscode/devcontainers/go:0-${VARIANT}

# [Option] Install Node.js
ARG INSTALL_NODE="true"
ARG NODE_VERSION="lts/*"
RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends vim bash-completion

# [Optional] Uncomment the next line to use go get to install anything else you need
# RUN go get -x <your-dependency-or-tool>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

RUN su vscode -c "git config --global core.editor vim \
  && git config --global alias.co checkout \
  && git config --global alias.br branch \
  && git config --global alias.ci commit \
  && git config --global alias.st status \
  && git config --global alias.unstage 'reset HEAD --' \
  && git config --global alias.last 'log -1 HEAD'"

RUN su vscode -c "git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.config/bash_it && \
  ~/.config/bash_it/install.sh -s"

COPY scripts/.inputrc /tmp/.inputrc
RUN su vscode -c 'cp /tmp/.inputrc ~/.inputrc'
