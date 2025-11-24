FROM node:current-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

FROM node:current-alpine AS runner

RUN adduser -D node && \
    chown -R node:node /app && \
    chmod -R 755 /app

USER node

COPY --from=builder --chown=node:node /app /app

EXPOSE 5173

ENTRYPOINT [ "node" ]
