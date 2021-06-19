
FROM golang:1.16-alpine
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=1000

# Configure user
RUN adduser $USERNAME -s /bin/sh -D -u $USER_UID $USER_GID && \
    mkdir -p /etc/sudoers.d && \
    echo "$USERNAME ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

RUN apk --no-cache add curl git zsh sudo

# Configure zsh
USER $USERNAME

ENV TERM xterm
ENV SHELL /bin/zsh
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true

# zsh configuration
USER root

# Install Taskfile
RUN sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin

# Install gopls
RUN go get -u -v golang.org/x/tools/gopls 2>&1

# Install golangci-lint
RUN export PATH="$PATH:$(go env GOPATH)/bin"
RUN curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin v1.41.0