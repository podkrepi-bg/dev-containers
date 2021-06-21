FROM golang:1.16-alpine

RUN apk --no-cache add curl git zsh sudo

ENV CGO_ENABLED 0
ENV TERM xterm
ENV SHELL /bin/zsh
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true

# Install gopls
RUN go get -v golang.org/x/tools/gopls@latest

# Install Taskfile
RUN sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin

# Install golangci-lint
RUN export PATH="$PATH:$(go env GOPATH)/bin"
RUN curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin v1.41.0