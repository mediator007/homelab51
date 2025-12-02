FROM python:3.12

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        openssh-client \
        git \
        ca-certificates \
        sshpass \
        sudo && \
        apt-get clean && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir ansible

WORKDIR /work

# ENTRYPOINT ["/bin/bash"]

