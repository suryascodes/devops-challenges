FROM golang:1.24.4

WORKDIR /app
COPY . .

RUN go build -o main .
EXPOSE 8081

CMD ["./main"]
