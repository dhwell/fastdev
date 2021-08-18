FROM golang:1.13.5-alpine3.10 AS builder

WORKDIR /build
COPY . .

RUN CGO_ENABLED=0 GOARCH=amd64 GOOS=linux go build -a -o ping .

FROM alpine:3.10 AS final

WORKDIR /app
COPY --from=builder /build/ping /app/

EXPOSE 80

ENTRYPOINT ["/app/ping"]
