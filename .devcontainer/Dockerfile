ARG VARIANT=slim
FROM docker.io/library/python:$VARIANT

RUN \
    apt-get update; \
    apt-get install --no-install-recommends --assume-yes \
    sudo \
    locales; \
    echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen; \
    locale-gen; \
    apt-get clean && rm -fr /var/lib/apt/lists/*

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN \
    groupadd --gid $USER_GID $USERNAME; \
    useradd --gid $USER_GID \
    --create-home $USERNAME \
    --shell /bin/bash \
    --uid $USER_UID; \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME; \
    chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME

RUN \
    /usr/local/bin/python3 -m pip install --no-cache-dir --upgrade --user --force-reinstall \
    pip \
    setuptools \
    wheel; \
    pip3 install --disable-pip-version-check --no-cache-dir --user --upgrade --force-reinstall \
    pipx \
    ipykernel

RUN \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" autopep8; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" bandit; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" black; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" flake8; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" mypy; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pipenv; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" poetry; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" prospector; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pycodestyle; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pydocstyle; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pylama; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pylint; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" pytest; \
    /usr/local/bin/python3 -m pipx install --system-site-packages --pip-args "--no-cache-dir --force-reinstall" yapf
