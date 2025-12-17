ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG MESHMESHGO_VERSION BUILD_ARCH
RUN \
    if [[ "${BUILD_ARCH}" = "aarch64" ]]; then ARCH="arm64"; fi \
    && if [[ "${BUILD_ARCH}" = "amd64" ]]; then ARCH="x86_64"; fi \
    && echo "https://github.com/EspMeshMesh/meshmeshgo/releases/download/${MESHMESHGO_VERSION}/meshmeshgo_Linux_${ARCH}.tar.gz" \
    && curl -J -L -o /tmp/meshmeshgo.tgz "https://github.com/EspMeshMesh/meshmeshgo/releases/download/v1.3.4/meshmeshgo_Linux_${ARCH}.tar.gz" \
    && mkdir -p /opt/meshmeshgo && tar zxvf /tmp/meshmeshgo.tgz -C /opt/meshmeshgo && ln -s /opt/meshmeshgo/meshmeshgo /usr/bin/meshmeshgo \
    && rm /tmp/meshmeshgo.tgz

# Copy root filesystem
COPY rootfs /
