# [Choice] Python version: 3, 3.8, 3.7, 3.6
FROM mcr.microsoft.com/vscode/devcontainers/python:0-3
#3-bookworm
# ARG with FROM are not working with devcontainers
# ARG VARIANT=3
#FROM mcr.microsoft.com/vscode/devcontainers/python:0-$VARIANT

ENV TZ America/Toronto
ENV PYTHONUNBUFFERED 1

# Update args in docker-compose.yaml to set the UID/GID of the "vscode" user.
ARG USER_UID=1000
ARG USER_GID=$USER_UID
# RUN if ["$USER_GID" != "0" ] && ([ "$USER_GID" != "1000" ] || [ "$USER_UID" != "1000" ]); then groupmod --gid $USER_GID vscode && usermod --uid $USER_UID --gid $USER_GID vscode; fi
RUN  <<EOF
set -e

if ["$USER_GID" != "0" ] && ([ "$USER_GID" != "1000" ] || [ "$USER_UID" != "1000" ]); then 
  groupmod --gid $USER_GID vscode
  usermod --uid $USER_UID --gid $USER_GID vscode
fi

EOF

# # [Choice] Node.js version: none, lts/*, 16, 14, 12, 10, node (current)
# ARG NODE_VERSION="node"
# RUN if [ "${NODE_VERSION}" != "none" ] && [ "$USER_GID" != "0" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi
# RUN if [ "${NODE_VERSION}" != "none" ] && [ "$USER_GID" == "0" ]; then umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1; fi

# [Optional] If your requirements rarely change, uncomment this section to add them to the image.
# COPY requirements.txt /tmp/pip-tmp/
# RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
#    && rm -rf /tmp/pip-tmp

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>



