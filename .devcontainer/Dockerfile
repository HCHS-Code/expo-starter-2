ARG VARIANT=22-bookworm
FROM mcr.microsoft.com/devcontainers/javascript-node:1-${VARIANT}

# Install tslint, typescript. eslint is installed by javascript image
ARG NODE_MODULES="tslint-to-eslint-config typescript"
RUN su node -c "umask 0002 && npm install -g ${NODE_MODULES}" \
    && npm cache clean --force > /dev/null 2>&1

# Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends curl

# Uncomment if you want to install an additional version of node using nvm
ARG EXTRA_NODE_VERSION=lts
RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node packages
# RUN su node -c "npm install -g <your-package-list -here>"

# Add extensions for students
RUN code --install-extension burkeholland.simple-react-snippets dbaeumer.vscode-eslint esbenp.prettier-vscode \
expo.vscode-expo-tools formulahendry.auto-close-tag formulahendry.auto-rename-tag jundat95.react-native-snippet \
ms-azuretools.vscode-docker ms-vscode.live-server yoavbls.pretty-ts-errors
