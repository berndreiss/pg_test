FROM postgres:18

RUN apt-get update && apt-get install -y \
    git \
    build-essential \
    cmake \
    ninja-build \
    postgresql-server-dev-18 \
    libssl-dev \
    pkg-config \
    liblz4-dev \
    libicu-dev \
    libreadline-dev \
    zlib1g-dev \
    libxml2-dev \
    libxslt-dev \
    libc++-dev \
    libc++abi-dev \
    libglib2.0-dev \
    libstdc++-14-dev \
    libcurl4-openssl-dev \
    flex \
    bison \
    xsltproc \
    ccache \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/duckdb/pg_duckdb.git /tmp/pg_duckdb

WORKDIR /tmp/pg_duckdb
RUN make install

RUN rm -rf /tmp/pg_duckdb

RUN echo "shared_preload_libraries = 'pg_duckdb'" >> /usr/share/postgresql/postgresql.conf.sample

WORKDIR /
