FROM golang:1.10.2-alpine3.7 AS builder

RUN apk add git --no-cache

ENV CGO_ENABLED=0
ENV GOOS=linux 
ENV GOARCH=amd64

RUN go get github.com/zmap/zdns/zdns

################################################################################

#alpine because ....?
FROM scratch

WORKDIR /app

COPY --from=builder /go/bin/zdns .

ENTRYPOINT ["/app/zdns"]
