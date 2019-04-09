FROM arm7/ubuntu

RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y \
  build-essential \
  wget \
  vim \
  curl \
  gcc \
  libc6-dev \
  xz-utils \
  git

ARG RUST_VERSION=stable

# install rustup with raspberry target
RUN curl https://sh.rustup.rs -sSf > $HOME/install_rustup.sh
RUN sh $HOME/install_rustup.sh -y --default-toolchain $RUST_VERSION
RUN $HOME/.cargo/bin/rustup target add arm-unknown-linux-gnueabihf

# configure cargo
RUN mv $HOME/.cargo/bin/* /usr/local/bin/
RUN rustup target add armv7-unknown-linux-gnueabihf

RUN mkdir /home/bin
RUN mkdir /home/Projects
WORKDIR "/home/Projects"

