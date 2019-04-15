FROM golang:1.6
WORKDIR /go/src/github.com/cloudflare
RUN wget https://github.com/cloudflare/cfssl/archive/1.2.0.tar.gz && \
    tar xzfv 1.2.0.tar.gz &&\
    mv cfssl-1.2.0 cfssl && cd cfssl &&\
    go get github.com/GeertJohan/go.rice/rice && rice embed-go -i=./cli/serve && \
    cp -R /go/src/github.com/cloudflare/cfssl/vendor/github.com/cloudflare/cfssl_trust /etc/cfssl && \
    go install ./cmd/...

FROM debian:stable-slim
# Install cfssl for kiam installation
COPY configs /configs
COPY --from=0 /go/bin/* /usr/local/bin/
