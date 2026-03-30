FROM caddy:2.11.2-builder AS builder

RUN xcaddy build \
  --with github.com/mholt/caddy-l4@v0.1.0

FROM caddy:2.11.2
COPY --from=builder /usr/bin/caddy /usr/bin/caddy