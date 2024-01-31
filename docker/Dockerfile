FROM golang:1.21.6-bookworm as src
WORKDIR /app

COPY ./main.go /app/main.go
COPY ./go.mod /app/go.mod
COPY ./go.sum /app/go.sum

FROM src as builder
RUN go get -v
RUN go build

FROM gcr.io/distroless/static-debian12:nonroot as runner
WORKDIR /app

COPY --from=builder /app/hello /app/hello

CMD ["./hello"]
