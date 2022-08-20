FROM ubuntu:20.04
ENV DEBIAN_FRONTEND noninteractive
WORKDIR /fb
COPY ./fluent.conf .
RUN apt-get update
RUN apt-get install -y git
RUN git clone https://github.com/fluent/fluent-bit.git
WORKDIR /fb/fluent-bit
RUN git checkout fc325524d50fe179b76f127243ab9e03ddbdaaa4
RUN apt-get install -y build-essential make cmake g++ flex bison
WORKDIR /fb/fluent-bit/build
RUN cmake -DFLB_CONFIG_YAML=Off ../
RUN make
RUN make install
CMD ["bin/fluent-bit", "-c", "/fb/fluent.conf"]