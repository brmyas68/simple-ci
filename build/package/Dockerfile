FROM golang:alpine AS builder

RUN apk add git

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN go build -o /simple-ci

FROM alpine:latest AS runtime

LABEL maintainer="Mohammad Nasr <mohammadne.dev@gmail.com>"

WORKDIR /app

COPY --from=builder /simple-ci .

ENTRYPOINT ["./simple-ci"]
