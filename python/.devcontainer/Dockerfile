ARG VARIANT="hirsute"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

COPY .devcontainer/linux-packages.txt /tmp/tmp-pkgs/
RUN apt update && export DEBIAN_FRONTEND=noninteractive \
    && apt -y --no-install-recommends install $(cat /tmp/tmp-pkgs/linux-packages.txt | tr '\n' ' ') \
    && rm -rf /tmp/tmp-pkgs

COPY .devcontainer/requirements.txt /tmp/pip-tmp/
RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
   && rm -rf /tmp/pip-tmp
