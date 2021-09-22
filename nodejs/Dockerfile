FROM node:16.9-alpine3.14

RUN apk --no-cache add curl git zsh sudo docker-cli docker-compose

ENV TERM xterm
ENV SHELL /bin/zsh
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
