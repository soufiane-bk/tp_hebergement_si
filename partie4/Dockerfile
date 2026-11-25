FROM node:22-bookworm-slim

ARG WIKI_VERSION=2.5.317

WORKDIR /wiki

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates curl \
    && curl -fsSL "https://github.com/requarks/wiki-v2/releases/download/v${WIKI_VERSION}/wiki-js.tar.gz" \
       -o /tmp/wiki-js.tar.gz \
    && tar -xzf /tmp/wiki-js.tar.gz \
    && rm /tmp/wiki-js.tar.gz \
    && rm -rf /var/lib/apt/lists/* \
    && chown -R node:node /wiki

ENV NODE_ENV=production

USER node
EXPOSE 3000

CMD ["node", "server"]
