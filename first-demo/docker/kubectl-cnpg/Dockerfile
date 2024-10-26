# Use a lightweight Debian base image
FROM debian:12.7-slim

# Set environment variables
ENV KUBECTL_VERSION=v1.31.0
ENV CNPG_VERSION=1.24.1

# Install dependencies and download kubectl and the CNPG plugin
RUN apt-get update && apt-get install -y --no-install-recommends \
        curl \
        bash \
        ca-certificates \
    && update-ca-certificates \
    && curl -LO "https://dl.k8s.io/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl" \
    && chmod +x kubectl \
    && mv kubectl /usr/local/bin/ \
    && curl -sSfL \
    https://github.com/cloudnative-pg/cloudnative-pg/raw/main/hack/install-cnpg-plugin.sh | \
    sh -s -- -b /usr/local/bin \
    && apt-get purge -y --auto-remove curl \
    && rm -rf /var/lib/apt/lists/*

# Set the entrypoint
ENTRYPOINT ["/usr/local/bin/kubectl"]
