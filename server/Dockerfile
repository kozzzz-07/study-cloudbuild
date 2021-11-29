FROM golang:1.16 as builder

WORKDIR /go/src/github.com/kozzzz-07/study-cloudbuild/server/src

COPY go.mod ./
COPY go.sum ./
RUN go mod download

COPY ./src ./

ARG CGO_ENABLED=0
ARG GOOS=linux
ARG GOARCH=amd64

RUN go build \
  -o /app \
  -ldflags '-s -w'

FROM scratch as runner

COPY --from=builder /app /app

ENTRYPOINT ["./app"]

