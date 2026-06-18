FROM golang:1.26-alpine AS builder

WORKDIR /app

COPY main.go .

RUN go build -o server main.go

FROM alpine:3.20

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

WORKDIR /app

COPY --from=builder /app/server .

USER appuser

EXPOSE 8080

CMD ["./server"]
