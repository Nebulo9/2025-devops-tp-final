FROM golang:1.23-alpine AS builder

RUN adduser -D go

USER go

WORKDIR /app

COPY . .
RUN go mod download
RUN go build -o bin/server cmd/server/main.go

FROM scratch AS runner
COPY --from=builder /app/bin/server /server

EXPOSE 8080

ENTRYPOINT [ "/server" ]