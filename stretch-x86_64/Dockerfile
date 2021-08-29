FROM debian:stretch

# Add PATH entry for Rust
ENV PATH /root/.cargo/bin:$PATH

# Install ripgrep requirements
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    asciidoctor \
    zsh \
    xz-utils \
    liblz4-tool \
    musl-tools \
    curl \
    build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Rust
RUN curl --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

RUN cargo install cargo-deb

COPY scripts /

ENTRYPOINT [ "/scripts/ripgrep/build-deb" ]
