FROM golang:1.9-alpine AS builder
WORKDIR /go/src/app
RUN apk --no-cache add curl git && \
    curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh

COPY . .
RUN dep ensure
RUN go build -o auth-api


FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /go/src/app
COPY --from=builder /go/src/app/auth-api .
USER 1001
EXPOSE 8081
CMD ["./auth-api"]
