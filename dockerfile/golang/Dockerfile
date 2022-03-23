FROM golang:alpine AS app-builder

RUN apk update

WORKDIR /app

COPY ./main.go /app

COPY ./go.mod /app

RUN go mod tidy

RUN CGO_ENABLED=0 go build -gcflags '-S -N' -o binary *.go

FROM alpine:latest

COPY --from=app-builder /app/binary /app/binary

EXPOSE 3030

CMD [ "/app/binary" ]