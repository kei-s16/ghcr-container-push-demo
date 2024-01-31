FROM golang:1.21.6-bookworm as builder
WORKDIR /app

COPY ./go.mod /app/go.mod
COPY ./go.sum /app/go.sum
RUN go mod download

COPY ./main.go /app/main.go
RUN go build

FROM gcr.io/distroless/static-debian12:nonroot as runner
WORKDIR /app

COPY --from=builder /app/hello /app/hello

CMD ["./hello"]
