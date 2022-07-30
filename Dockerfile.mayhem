FROM --platform=linux/amd64 ubuntu:22.04 as builder

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential imagemagick

COPY . /repo
WORKDIR /repo/src/main/cpp
ENV DESTDIR=/install
RUN make -j8
RUN make install

FROM ubuntu:22.04 as package
COPY --from=builder /install /install
