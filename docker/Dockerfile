FROM alpine:3.6 as alpine
RUN apk add -U --no-cache ca-certificates

FROM node:14-alpine
ENV GODEBUG netdns=go

COPY --from=alpine /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/

RUN npm install netlify-cli -g

ADD release/linux/amd64/plugin /bin/
ENTRYPOINT ["/bin/plugin"]