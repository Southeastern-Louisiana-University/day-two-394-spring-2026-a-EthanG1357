FROM ubuntu:22.04 AS build

RUN apt-get update && apt-get install -y \
curl \
ca-certificates \
tar \
build-essential

ENV GO_VERSION=1.22.0
RUN curl -fsSL https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz -o go.tar.gz \
&& tar -C /usr/local -xzf go.tar.gz \
&& rm go.tar.gz

ENV PATH="/usr/local/go/bin:${PATH}"

WORKDIR /app
COPY main.go .
RUN go build -o hello main.go

FROM alpine:latest
WORKDIR /app
COPY --from=build /app/hello .
CMD ["./hello"]