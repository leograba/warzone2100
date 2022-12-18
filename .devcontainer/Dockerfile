# if you get error: 
# "pull access denied for sha256, repository does not exist or may require 'docker login' : denied: requested access to the resource is denied"
# when opening the project, this may mean that base SDK container has been deleted 
# or that the project has been moved to a different machine where such container does not exist, 
# you can re-build it by pressing F1 in Visual Studio Code and selecting:
# "Torizon: Rebuild SDK and reload in container"
# after this operation you should be able to re-open your project inside a container
FROM warzone2100_arm64v8-wayland-base-vivante-no-ssh_bullseye_debug_45e143ca-ac6e-42dc-8c6f-45e536787f2d_sdk_image

# add automake/autoconf to our base SDK container
RUN apt-get update && apt-get install -y \
    --no-install-recommends --no-install-suggests \
    pkg-config cmake \
    && apt-get clean && apt-get autoremove \
    && rm -rf /var/lib/apt/lists/*

# This is required to allow regular user inside the container to access docker socket
RUN addgroup docker && groupmod --non-unique --gid 999 docker && adduser torizon docker
