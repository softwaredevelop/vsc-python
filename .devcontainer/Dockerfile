ARG VARIANT=latest
FROM docker.io/library/alpine:$VARIANT

RUN \
    apk update; \
    apk add --no-cache sudo; \
    rm -rf /var/cache/apk/*

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN \
    addgroup --gid $USER_GID $USERNAME; \
    adduser -G $USERNAME \
    -h /home/$USERNAME \
    -s /bin/ash \
    -u $USER_UID \
    -D \
    $USERNAME; \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME; \
    chmod 0440 /etc/sudoers.d/$USERNAME
