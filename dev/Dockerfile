FROM golang:1.11-alpine as base
MAINTAINER "Hunter Long (https://github.com/hunterlong)"
ARG VERSION
ENV DEP_VERSION v0.5.0
RUN apk add --no-cache libstdc++ gcc g++ make git ca-certificates linux-headers wget curl jq
RUN curl -L -s https://assets.statping.com/sass -o /usr/local/bin/sass && \
    chmod +x /usr/local/bin/sass
WORKDIR /go/src/github.com/hunterlong/statping
ADD . /go/src/github.com/hunterlong/statping
RUN go mod vendor
RUN make dev-deps
RUN make install

ENV IS_DOCKER=true
ENV STATPING_DIR=/app
WORKDIR /app

CMD ["statping"]
