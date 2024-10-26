# Use a lightweight Debian image as the base
FROM debian:bullseye-slim

# Install necessary packages and PostgreSQL client
RUN apt-get update && \
    apt-get install -y postgresql-client jq && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set the entry point to psql
ENTRYPOINT ["psql"]
