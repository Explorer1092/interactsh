# Build
FROM golang:1.18.1-alpine AS build-env
RUN apk add build-base
RUN go install -v github.com/Explorer1092/interactsh/cmd/interactsh-server@v1.0.6

# Release
FROM alpine:3.15.4
RUN apk -U upgrade --no-cache \
    && apk add --no-cache bind-tools ca-certificates
COPY --from=build-env /go/bin/interactsh-server /usr/local/bin/interactsh-server

ENTRYPOINT ["interactsh-server"]