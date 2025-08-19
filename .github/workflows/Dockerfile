FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y \
    curl \
    ca-certificates \
    gnupg \
    lsb-release \
    unzip \
    sed \
    # xz is required for compactc
    xz-utils \
    && rm -rf /var/lib/apt/lists/*

RUN curl --proto '=https' --tlsv1.2 -LsSf https://github.com/midnightntwrk/compact/releases/latest/download/compact-installer.sh | sh
ENV PATH="/root/.local/bin:$PATH"
RUN ls -l /root/.local/bin
RUN echo $PATH
RUN which compact
RUN compact update
RUN compact --version
RUN ls -l ~/.compact/bin
COPY ./counter.compact .

CMD compact compile counter.compact out
